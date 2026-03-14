# MacSoccle

A laser-cut bamboo base plate ("socle") for a MacBook Pro 16" M1, with integrated storage for 4 Samsung T7 SSDs and a Satechi USB-C hub.

![](soccle/layout.svg)

## What is it?

A flat plate that sits under a MacBook Pro 16", matching its exact footprint (355.7 x 248.1 mm) and corner rounding. It hides 4 SSDs and a USB-C hub inside, connected with short cables, keeping the desk clean. Only one USB-C cable exits the soccle to connect to the MacBook.

## Construction

4 layers of laser-cut [bamboo plywood](snijlab/material.md), total height ~13 mm:

| Layer      | Thickness | Function                           |
|------------|-----------|------------------------------------|
| 1 (bottom) | 1.5 mm    | Solid bottom plate                 |
| 2          | 5 mm      | Internal frame with cutouts        |
| 3          | 5 mm      | Internal frame with cutouts        |
| 4 (top)    | 1.5 mm    | Removable top plate (velcro mount) |

Layers 1-3 are glued. Layer 4 is removable for SSD access.
Inside faces of layers 1 and 4 are lined with aluminium foil for heat spreading.

## Internal components

* **4x Samsung T7 SSD** — 85 x 57 x 8 mm each
* **1x Satechi 4-Port USB-C Hub** (ST-H4CPDM) — 60 x 60 x 10 mm

## Documentation

* [Soccle design](soccle/index.md) — full design spec, dimensions, component layout
* [Component layout](soccle/layout.md) — exact coordinates and cable routing
* [Laser cutting specs](snijlab/specs.md) — Snijlab layer names, colors, file formats
* [Design workflow](snijlab/design.md) — how to create a design for laser cutting
* [Material](snijlab/material.md) — bamboo plywood properties and pricing

## Manufacturing

Laser cutting by [Snijlab](https://snijlab.nl/en) (Netherlands). Files exported as DXF at 1:1 scale in mm.
