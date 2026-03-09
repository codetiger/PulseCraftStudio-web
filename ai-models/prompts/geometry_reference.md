# Geometry Reference

11 geometry types. All parameters are animatable. Units are meters.

| Type | Parameters (default) | Notes |
|------|---------------------|-------|
| plane | width (10), height (10) | Flat quad |
| box | width (2), height (2), length (2), chamferRadius (0) | Rounded edges via chamfer |
| sphere | radius (3) | UV sphere |
| cylinder | radius (3), height (3) | Capped cylinder |
| cone | bottomRadius (3), height (3) | Pointed cone (no top radius) |
| capsule | capRadius (0.5), height (3) | Cylinder with spherical caps |
| pyramid | width (3), height (3), length (3) | 4-sided pyramid |
| torus | ringRadius (3), pipeRadius (1) | Donut shape |
| tube | innerRadius (2), outerRadius (3), height (3) | Hollow cylinder |
| text | fontSize (1), extrusionDepth (1) | 3D extruded text |
| imported | — | Placeholder for imported models |

Defaults are large (2-10m). For AI-created scenes, use smaller explicit values (e.g. radius 0.5, width 1).

## Text Geometry

- `string`: the text content (default "Text")
- `font`: font name (system fonts, e.g. "Helvetica")
- `fontSize`: range 0.1–10, default 1
- `extrusionDepth`: range 0–100, default 1
