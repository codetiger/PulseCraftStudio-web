# Animation Reference

## Basics

- Frame rate: 60 fps (fixed)
- Default duration: 240 frames (4 seconds)
- Frame math: `frame = seconds × 60`
- Interpolation: linear between keyframes (slerp for large rotations)

## Frame-to-Time Conversion

| Time | Frame |
|------|-------|
| 0.5s | 30 |
| 1s | 60 |
| 2s | 120 |
| 3s | 180 |
| 4s | 240 |
| 5s | 300 |
| 10s | 600 |

## Animatable Properties by Category

| Category | Properties |
|----------|-----------|
| Transform | position, eulerAngles, scale, hidden, opacity |
| Geometry | width, height, length, radius, bottomRadius, capRadius, chamferRadius, ringRadius, pipeRadius, innerRadius, outerRadius, fontSize, extrusionDepth |
| Light | intensity, color, temperature, castsShadow, shadowRadius, spotInnerAngle, spotOuterAngle, attenuationStart, attenuationEnd, attenuationFalloff |
| Camera | fieldOfView, focalDistance, fStop, zNear, zFar |

**NOT animatable:** Materials. Use `pcs_modify` to change materials.

## Compound Entity IDs

Keyframes target specific parts of an entity:

| Category | Compound ID |
|----------|-------------|
| transform | `entityId` (plain) |
| geometry | `entityId##geometry` |
| light | `entityId##light` |
| camera | `entityId##camera` |

## Keyframe Workflow

1. Query the scene to get entity IDs and current total frames
2. Set keyframe values at the start frame
3. Set keyframe values at the end frame
4. Playback interpolates between them linearly
