# Component layout reference

All coordinates in mm, origin (0,0) = top-left corner of soccle.
X axis = width (355.7 mm), Y axis = depth (248.1 mm).

## Outer plate

| Parameter     | Value                         |
|---------------|-------------------------------|
| Width         | 355.7                         |
| Depth         | 248.1                         |
| Corner radius | 7.25                          |
| Border        | 5 mm solid frame on all sides |

## USB Hub — Satechi ST-H4CPDM

| Parameter       | Value                                                                           |
|-----------------|---------------------------------------------------------------------------------|
| Cutout size     | 62 x 62                                                                         |
| Position (x, y) | (20, 93.05)                                                                     |
| Extent          | x: 20–82, y: 93.05–155.05                                                       |
| North port 1    | (46, 93.05) — connects to SSD1                                                  |
| North port 2    | (56, 93.05) — connects to SSD2                                                  |
| South port 1    | (46, 155.05) — connects to SSD3                                                 |
| South port 2    | (56, 155.05) — connects to SSD4                                                 |
| Cable exit      | Own USB-C cable exits at x=0, y=119–129 (middle of left short side)             |

## SSDs — Samsung T7 x4

All SSD cutouts are 87 x 59 mm.

### SSD 1 (top-left)

| Parameter       | Value                                   |
|-----------------|-----------------------------------------|
| Position (x, y) | (97, 55)                                |
| Extent          | x: 97–184, y: 55–114                    |
| USB-C connector | right side (x=184), centered vertically |
| Hub port        | north                                   |

### SSD 2 (top-right)

| Parameter       | Value                                  |
|-----------------|----------------------------------------|
| Position (x, y) | (244, 35)                              |
| Extent          | x: 244–331, y: 35–94                   |
| USB-C connector | left side (x=244), centered vertically |
| Hub port        | north                                  |

### SSD 3 (bottom-left)

| Parameter       | Value                                   |
|-----------------|-----------------------------------------|
| Position (x, y) | (97, 134)                               |
| Extent          | x: 97–184, y: 134–193                   |
| USB-C connector | right side (x=184), centered vertically |
| Hub port        | south                                   |

### SSD 4 (bottom-right)

| Parameter       | Value                                  |
|-----------------|----------------------------------------|
| Position (x, y) | (244, 154)                             |
| Extent          | x: 244–331, y: 154–213                 |
| USB-C connector | left side (x=244), centered vertically |
| Hub port        | south                                  |

## Gaps

| Gap                      | Distance        |
|--------------------------|-----------------|
| Hub to left edge         | 20              |
| SSD1 ↔ SSD3 (vertical)   | 20              |
| SSD2 ↔ SSD4 (vertical)   | 60              |
| SSD columns (horizontal) | 60 (x: 184–244) |

## Cable routing

All cables run from SSD connector → center gap → outside edge → back to hub.

| Cable | Route                                                                        |
|-------|------------------------------------------------------------------------------|
| SSD1  | right (x=184) → center gap → up to top edge (y=20) → left to hub north       |
| SSD2  | left (x=244) → center gap → up to top edge (y=14) → left to hub north        |
| SSD3  | right (x=184) → center gap → down to bottom edge (y=228) → left to hub south |
| SSD4  | left (x=244) → center gap → down to bottom edge (y=234) → left to hub south  |

## Cable length estimates

Calculated by summing the routed path segments + ~10% for bends.

Cable conduits run inside the 30mm frame (not through it).

| Cable | Segment 1             | Segment 2            | Segment 3             | Segment 4            | Path total | With bends |
|-------|-----------------------|----------------------|-----------------------|----------------------|------------|------------|
| SSD1  | (186,84)→(200,84) 14  | (200,84)→(200,38) 46 | (200,38)→(51,38) 149  | (51,38)→(51,93) 55  | 264 mm     | ~29 cm     |
| SSD2  | (242,64)→(210,64) 32  | (210,64)→(210,33) 31 | (210,33)→(45,33) 165  | (45,33)→(45,93) 60  | 288 mm     | ~32 cm     |
| SSD3  | (186,164)→(200,164) 14 | (200,164)→(200,210) 46 | (200,210)→(51,210) 149 | (51,210)→(51,155) 55 | 264 mm    | ~29 cm     |
| SSD4  | (242,184)→(210,184) 32 | (210,184)→(210,215) 31 | (210,215)→(45,215) 165 | (45,215)→(45,155) 60 | 288 mm    | ~32 cm     |

All 4 cables are approximately **~30 cm** routed path. Stock Samsung T7 cables (45 cm) fit with ample slack.

## Velcro dots (16x, 10 mm diameter)

Holes in layer 3, connecting layer 2 to layer 4.
4 per side, grouped near corners (~20 mm from corner).

| Side             | Count | Positions (along side)      |
|------------------|-------|-----------------------------|
| Left (x=8)       | 4     | y: 20, 60, 188.1, 228.1    |
| Right (x=347.7)  | 4     | y: 20, 60, 188.1, 228.1    |
| Top (y=8)        | 4     | x: 20, 60, 295.7, 335.7    |
| Bottom (y=240.1) | 4     | x: 20, 60, 295.7, 335.7    |
