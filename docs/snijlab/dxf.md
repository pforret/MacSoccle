# DXF file format for Snijlab

Learnings from analyzing `Snijlab-template-crate.dxf`.

## DXF version

* Version: AC1021 (AutoCAD 2007)
* Use `ezdxf.new("R2007")` or `ezdxf.new("R2010")` in Python

## Units

| Header variable | Value | Meaning          |
|-----------------|-------|------------------|
| $INSUNITS       | 4     | millimeters      |
| $MEASUREMENT    | 1     | metric           |
| $LUNITS         | 2     | decimal           |
| $LUPREC         | 3     | 3 decimal places |

## Layers

| Layer name   | Color | Purpose                                      |
|--------------|-------|----------------------------------------------|
| `vector-cut` | 5 (blue) | All cut lines — this is what the laser cuts |
| `notes`      | 18 (gray) | Annotations, dimensions, visual guides (not cut) |
| `0`          | 7 (white) | Default layer (unused in template)           |

**Key insight:** Snijlab uses `vector-cut` as the layer name (not just `cut`). Color is set on the **layer**, not on individual entities. All entities use `color=BYLAYER`.

## Entity types

The template uses only these entity types on the `vector-cut` layer:

* **POLYLINE** (2D) — all 11 cut shapes are closed polylines
* No LINE, CIRCLE, ARC, or SPLINE on the cut layer

### Polyline conventions

* All cut polylines are **closed** (`is_closed=True`)
* Rounded corners use **bulge values** on vertices:
    * `bulge = 0.4142` → 90° arc (quarter circle), used for standard rounded corners
    * `bulge = 2.4142` → 270° arc (three-quarter circle), used for round holes defined as 2-vertex polylines
    * `bulge = 1.0000` → 180° semicircle
* Straight segments have `bulge = 0`
* No LWPOLYLINE used — template uses legacy POLYLINE with VERTEX sub-entities

### Round holes as 2-vertex polylines

The template creates circular holes using closed 2-vertex polylines with bulge values, not CIRCLE entities:

```
vertex 0: (x1, y1) bulge=2.4142  (270° arc)
vertex 1: (x2, y2) bulge=0.4142  (90° arc)
```

This defines a full circle as two arcs. The 4 corner holes in the template use this pattern.

## Entity colors

* All entities use `color=BYLAYER` (inherit from layer)
* Never set color on individual entities — set it on the layer

## Geometry notes

* All coordinates in mm
* Scale 1:1
* Template crate bounding box: 753 x 615 mm (multiple parts laid out on one sheet)
* Multiple separate parts (panels) are placed as separate closed polylines
* Parts can be arranged freely within the 1200 x 600 mm max sheet size

## Python (ezdxf) example

```python
import ezdxf

doc = ezdxf.new("R2007")
doc.header['$INSUNITS'] = 4      # mm
doc.header['$MEASUREMENT'] = 1   # metric
doc.header['$LUNITS'] = 2        # decimal
doc.header['$LUPREC'] = 3        # 3 decimal places

# Create cut layer — blue, matching Snijlab convention
doc.layers.add("vector-cut", color=5)

msp = doc.modelspace()

# Add a closed polyline (rectangle example)
msp.add_lwpolyline(
    [(0, 0), (100, 0), (100, 50), (0, 50)],
    close=True,
    dxfattribs={"layer": "vector-cut"}
)

doc.saveas("output.dxf")
```

## Checklist before uploading to Snijlab

* [ ] All cut geometry on `vector-cut` layer, color 5 (blue)
* [ ] All shapes are closed polylines
* [ ] Units in mm, scale 1:1
* [ ] No text, dimensions, or annotations on the cut layer
* [ ] No overlapping or duplicate cut lines
* [ ] Minimum 2mm spacing between parts (4mm for foam)
* [ ] Total size within 1200 x 600 mm sheet

cf [snijlab.nl/en/pages/drawing-rules](https://snijlab.nl/en/pages/drawing-rules)
