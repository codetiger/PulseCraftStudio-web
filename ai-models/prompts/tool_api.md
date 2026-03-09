# Tool API Reference

5 tools available. Always call `pcs_query` first to discover entity IDs before modifying.

## pcs_query — Read Scene State

### List all entities
```json
{"select": "entities"}
```

### Filter entities
```json
{"select": "entities", "filter": {"type": "geometry"}}
{"select": "entities", "filter": {"type": "light"}}
{"select": "entities", "filter": {"type": "camera"}}
{"select": "entities", "filter": {"geometryType": "sphere"}}
{"select": "entities", "filter": {"selected": true}}
```

### Control returned fields
```json
{"select": "entities", "fields": ["id", "name", "type", "position", "material"]}
```
Available fields: `id`, `name`, `type`, `geometryType`, `position`, `eulerAngles`, `scale`, `hidden`, `opacity`, `geometry`, `material`, `light`, `camera`, `parentId`, `hasAnimation`.
Default fields (list query): `id`, `name`, `type`.
Default fields (single entity): all fields.

### Get single entity details
```json
{"select": "entity", "id": "<uuid>"}
```

### Get scene info
```json
{"select": "scene"}
```
Returns: `totalFrames`, `fps`, `durationSeconds`, `isPlaying`, `entityCount`, `background`, `environment`, `canUndo`, `canRedo`.

### Get keyframes for an entity
```json
{"select": "keyframes", "id": "<uuid>"}
```
Returns keyframes grouped by category: `transform`, `geometry`, `light`, `camera`.

---

## pcs_create — Create Entities

Batch-create up to 20 entities per call.

```json
{
  "entities": [
    {
      "type": "sphere",
      "name": "My Sphere",
      "position": [0, 1, 0],
      "eulerAngles": [0, 0, 0],
      "scale": [1, 1, 1],
      "geometry": {"radius": 0.5},
      "material": {"baseColor": "#FF0000", "metalness": 0.8, "roughness": 0.3},
      "light": {"intensity": 1000, "color": "#FFFFFF"},
      "camera": {"fieldOfView": 60}
    }
  ]
}
```

### Valid types
**Geometry:** `plane`, `box`, `sphere`, `cylinder`, `cone`, `capsule`, `pyramid`, `torus`, `tube`, `text`
**Lights:** `light_ambient`, `light_directional`, `light_omni`, `light_spot`
**Camera:** `camera`

### Text geometry
Use both `geometry` and `text` objects:
```json
{
  "type": "text",
  "name": "Hello",
  "geometry": {"fontSize": 1, "extrusionDepth": 0.2},
  "text": {"string": "Hello World", "font": "Helvetica"}
}
```

### Geometry parameters by type

Defaults are large (2–10m). Use smaller explicit values for AI-created scenes.

| Type | Parameters (defaults) |
|------|----------------------|
| plane | width (10), height (10) |
| box | width (2), height (2), length (2), chamferRadius (0) |
| sphere | radius (3) |
| cylinder | radius (3), height (3) |
| cone | bottomRadius (3), height (3) |
| capsule | capRadius (0.5), height (3) |
| pyramid | width (3), height (3), length (3) |
| torus | ringRadius (3), pipeRadius (1) |
| tube | innerRadius (2), outerRadius (3), height (3) |
| text | fontSize (1), extrusionDepth (1) |

### Material properties (PBR)
| Property | Type | Default |
|----------|------|---------|
| baseColor | hex #RRGGBB | #FFFFFF |
| metalness | 0–1 | 0 |
| roughness | 0–1 | 0.5 |
| specular | 0–1 | 0.5 |
| ior | 1–3 | 1.5 |
| transmission | 0–1 | 0 |
| opacity | 0–1 | 1 |
| clearcoat | 0–1 | 0 |
| clearcoatRoughness | 0–1 | 0.03 |
| emissionColor | hex | #000000 |
| emissionIntensity | float | 0 |
| isDoubleSided | bool | false |

### Light properties
| Property | Applies to | Type | Default |
|----------|-----------|------|---------|
| color | all | hex #RRGGBB | #FFFFFF |
| intensity | all | int (0–100000) | 1000 |
| temperature | all | int Kelvin (0–40000) | 6500 |
| castsShadow | directional, omni, spot | bool | true |
| shadowRadius | directional, omni, spot | float (0–100) | 1 |
| spotInnerAngle | spot only | float degrees (0–180) | 0 |
| spotOuterAngle | spot only | float degrees (0–180) | 45 |
| attenuationStart | omni, spot | float (0–100) | 0 |
| attenuationEnd | omni, spot | float (0–100) | 100 |
| attenuationFalloff | omni, spot | float (0–100) | 1 |

### Camera properties
| Property | Type | Default |
|----------|------|---------|
| fieldOfView | float (1–179) | 60 |
| zNear | float | 0.01 |
| zFar | float | 100 |
| wantsDepthOfField | bool | false |
| focalDistance | float | 2.0 |
| fStop | float | 5.6 |
| wantsHDR | bool | false |

### Response
Returns array of `{"id": "<uuid>", "name": "...", "type": "..."}` for each created entity. Use the returned `id` for subsequent modify/keyframe calls.

---

## pcs_modify — Modify Existing Entities

Batch-modify up to 50 entities per call. Only include properties you want to change.

```json
{
  "modifications": [
    {
      "id": "<uuid>",
      "name": "New Name",
      "position": [1, 2, 3],
      "eulerAngles": [0, 1.5708, 0],
      "scale": [2, 2, 2],
      "hidden": false,
      "opacity": 0.5,
      "geometry": {"radius": 1.0},
      "material": {"baseColor": "#00FF00", "metalness": 1.0},
      "materialIndex": 0,
      "light": {"intensity": 5000},
      "camera": {"fieldOfView": 90}
    }
  ]
}
```

`id` is required. All other fields are optional — only specified properties change.

Use `materialIndex` (default 0) to target a specific material slot on multi-material objects.

---

## pcs_keyframe — Animation Keyframes

60fps timing: frame 60 = 1 second. Batch up to 200 keyframes per call.

### Set keyframes
```json
{
  "action": "set",
  "keyframes": [
    {"entityId": "<uuid>", "property": "position", "category": "transform", "frame": 0, "value": [0, 0, 0]},
    {"entityId": "<uuid>", "property": "position", "category": "transform", "frame": 120, "value": [0, 5, 0]}
  ]
}
```

### Remove specific keyframes
```json
{
  "action": "remove",
  "keyframes": [
    {"entityId": "<uuid>", "property": "position", "category": "transform", "frame": 60}
  ]
}
```

### Clear all keyframes for an entity
```json
{
  "action": "clear",
  "entityId": "<uuid>"
}
```

### Set total animation length
```json
{
  "action": "set",
  "totalFrames": 600,
  "keyframes": []
}
```

### Category values
| Category | Compound ID | Animatable properties |
|----------|------------|----------------------|
| `transform` | entityId | position, eulerAngles, scale, hidden, opacity |
| `geometry` | entityId##geometry | All geometry params (width, height, radius, etc.) |
| `light` | entityId##light | intensity, color, temperature, spotInnerAngle, spotOuterAngle |
| `camera` | entityId##camera | fieldOfView, focalDistance, fStop, zNear, zFar |

**NOT animatable:** Materials. Use `pcs_modify` to change materials at specific frames.

### Value formats
- **Vector3** (position, eulerAngles, scale): `[x, y, z]`
- **Float** (radius, intensity, etc.): `0.5`
- **Integer** (intensity, temperature): `2000`
- **Boolean** (hidden): `true` / `false`
- **Color** (light color): `"#FF0000"`

---

## pcs_scene — Scene Operations

Batch up to 20 operations per call.

### Delete entity
```json
{"operations": [{"op": "delete", "entityId": "<uuid>"}]}
```

### Duplicate entity
```json
{"operations": [{"op": "duplicate", "entityId": "<uuid>"}]}
```
Returns `{"newId": "<uuid>"}` for the duplicated entity.

### Undo / Redo
```json
{"operations": [{"op": "undo"}]}
{"operations": [{"op": "redo"}]}
```

### Set background color
```json
{"operations": [{"op": "setBackground", "background": {"colorHex": "#1A1A2E"}}]}
```

### Set environment
```json
{"operations": [{"op": "setEnvironment", "environment": {"imageName": "studio", "intensity": 1.0}}]}
```

### Set total frames
```json
{"operations": [{"op": "setTotalFrames", "totalFrames": 600}]}
```

### Save project
```json
{"operations": [{"op": "save"}]}
```

---

## Workflow

1. Call `pcs_query` with `select: "entities"` to discover IDs and current state
2. Use `pcs_create` / `pcs_modify` / `pcs_keyframe` / `pcs_scene` with the returned IDs
3. Summarize what you did after executing tools
