# Creator Workflow Examples

## Create a Gold Sphere with Lighting

```json
{"name": "pcs_create", "arguments": {"entities": [
  {"type": "sphere", "name": "Gold Sphere", "geometry": {"radius": 0.5}, "material": {"baseColor": "#FFD700", "metalness": 1.0, "roughness": 0.3}},
  {"type": "light_directional", "name": "Key Light", "position": [2, 3, 2], "eulerAngles": [-0.7854, 0.7854, 0], "light": {"intensity": 2000, "castsShadow": true}}
]}}
```

## Spinning Cube Animation

Step 1: Create
```json
{"name": "pcs_create", "arguments": {"entities": [
  {"type": "box", "name": "Spinning Cube", "geometry": {"width": 1, "height": 1, "length": 1}}
]}}
```

Step 2: Animate (use ID from create result)
```json
{"name": "pcs_keyframe", "arguments": {"action": "set", "keyframes": [
  {"entityId": "<id>", "property": "eulerAngles", "category": "transform", "frame": 0, "value": [0, 0, 0]},
  {"entityId": "<id>", "property": "eulerAngles", "category": "transform", "frame": 120, "value": [0, 6.2832, 0]}
]}}
```

## Three-Point Lighting Setup

```json
{"name": "pcs_create", "arguments": {"entities": [
  {"type": "light_ambient", "name": "Fill", "light": {"intensity": 500}},
  {"type": "light_directional", "name": "Key", "position": [0, 5, 3], "eulerAngles": [-1.0472, 0, 0], "light": {"intensity": 2000, "castsShadow": true, "shadowRadius": 2}},
  {"type": "light_directional", "name": "Rim", "position": [0, 3, -3], "eulerAngles": [0.5236, 3.1416, 0], "light": {"intensity": 1000}}
]}}
```

## Modify Selected Entity

Step 1: Find selected
```json
{"name": "pcs_query", "arguments": {"select": "entities", "filter": {"selected": true}, "fields": ["id", "name", "type", "position", "material"]}}
```

Step 2: Modify (use returned ID)
```json
{"name": "pcs_modify", "arguments": {"modifications": [
  {"id": "<id>", "material": {"baseColor": "#FF0000", "metalness": 1.0, "roughness": 0.0}}
]}}
```

## Cornell Box

```json
{"name": "pcs_create", "arguments": {"entities": [
  {"type": "plane", "name": "Back Wall", "position": [0, 0, -2], "geometry": {"width": 4, "height": 4}, "material": {"baseColor": "#FFFFFF"}},
  {"type": "plane", "name": "Left Wall", "position": [-2, 0, 0], "eulerAngles": [0, 1.5708, 0], "geometry": {"width": 4, "height": 4}, "material": {"baseColor": "#FF0000"}},
  {"type": "plane", "name": "Right Wall", "position": [2, 0, 0], "eulerAngles": [0, -1.5708, 0], "geometry": {"width": 4, "height": 4}, "material": {"baseColor": "#00FF00"}},
  {"type": "plane", "name": "Floor", "position": [0, -2, 0], "eulerAngles": [-1.5708, 0, 0], "geometry": {"width": 4, "height": 4}, "material": {"baseColor": "#FFFFFF"}},
  {"type": "plane", "name": "Ceiling", "position": [0, 2, 0], "eulerAngles": [1.5708, 0, 0], "geometry": {"width": 4, "height": 4}, "material": {"baseColor": "#FFFFFF"}},
  {"type": "light_omni", "name": "Ceiling Light", "position": [0, 1.8, 0], "light": {"intensity": 3000, "castsShadow": true}},
  {"type": "sphere", "name": "Mirror Sphere", "position": [-0.6, -1.3, -0.5], "geometry": {"radius": 0.7}, "material": {"baseColor": "#FFFFFF", "metalness": 1.0, "roughness": 0.0}},
  {"type": "box", "name": "Tall Box", "position": [0.6, -0.8, -0.8], "eulerAngles": [0, 0.3, 0], "geometry": {"width": 1, "height": 2.4, "length": 1}, "material": {"baseColor": "#FFFFFF", "roughness": 0.8}}
]}}
```

## Bouncing Ball Animation

Step 1: Create
```json
{"name": "pcs_create", "arguments": {"entities": [
  {"type": "sphere", "name": "Ball", "position": [0, 3, 0], "geometry": {"radius": 0.3}, "material": {"baseColor": "#FF6600"}}
]}}
```

Step 2: Animate bounce (use ID from result)
```json
{"name": "pcs_keyframe", "arguments": {"action": "set", "keyframes": [
  {"entityId": "<id>", "property": "position", "category": "transform", "frame": 0, "value": [0, 3, 0]},
  {"entityId": "<id>", "property": "position", "category": "transform", "frame": 30, "value": [0, 0.3, 0]},
  {"entityId": "<id>", "property": "position", "category": "transform", "frame": 50, "value": [0, 1.5, 0]},
  {"entityId": "<id>", "property": "position", "category": "transform", "frame": 70, "value": [0, 0.3, 0]},
  {"entityId": "<id>", "property": "position", "category": "transform", "frame": 85, "value": [0, 0.8, 0]},
  {"entityId": "<id>", "property": "position", "category": "transform", "frame": 100, "value": [0, 0.3, 0]}
]}}
```

## Delete and Replace

```json
{"name": "pcs_scene", "arguments": {"operations": [
  {"op": "delete", "entityId": "<id>"}
]}}
```

Then create a replacement:
```json
{"name": "pcs_create", "arguments": {"entities": [
  {"type": "sphere", "name": "Replacement", "position": [0, 0, 0]}
]}}
```

## Set Scene Background

```json
{"name": "pcs_scene", "arguments": {"operations": [
  {"op": "setBackground", "background": {"colorHex": "#0A0A1A"}},
  {"op": "setTotalFrames", "totalFrames": 600}
]}}
```
