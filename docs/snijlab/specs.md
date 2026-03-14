# Snijlab specs

* Accepted filetypes: DWG, DXF, AI, PDF
* Scale: 1:1
* Units: mm
* Maximum dimension: 2400 x 1200 mm
* Outlines: Convert text and fills to outlines
* Clean files: No size markings, frames, centerlines, etc.
* Layer name and line color: As described below

## Layers and colors

Use the appropriate layer name and line color for laser cutting or engraving.
The preview in the uploader shows how your drawing is loaded, we produce what the preview shows.

| Type            | Color	                  | Layer name      | Layer Type                                  | 
|-----------------|-------------------------|-----------------|---------------------------------------------|
| Cut             | Blue (rgb 0,0,255)      | cut             | lines, polylines, curves, splines           |
| Line engraving  | Red (rgb 255,0,0)       | line engraving  | lines, polylines, curves, splines           |
| Plane engraving | Magenta (rgb 255,0,255) | plane engraving | closed lines, polylines, curves and splines |

## Drawing tips

* Convert text elements to vector lines
* Convert shapes to lines according to drawing rules
* Convert overlapping tessellations to shapes
* Merge overlapping cut lines
* Draw a frame around engravings to upload them



cf [snijlab.nl/en/pages/drawing-rules](https://snijlab.nl/en/pages/drawing-rules)