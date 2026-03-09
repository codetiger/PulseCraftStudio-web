# Camera Reference

User cameras use `PCSCameraComponent`. The editor has its own separate camera.

## Properties

| Property | Range | Default | Description |
|----------|-------|---------|-------------|
| fieldOfView | 1–179° | 60 | Vertical FOV |
| zNear | 0–100 | 0.01 | Near clipping plane |
| zFar | 0–1000 | 100 | Far clipping plane |
| wantsDepthOfField | bool | false | Enable DOF blur |
| focalDistance | 0–100 | 2.0 | DOF focus distance |
| fStop | 0–100 | 5.6 | Aperture (lower = more blur) |
| wantsHDR | bool | false | HDR rendering |

## Notes

- Camera position and rotation are set via the entity transform, not camera properties.
- Point the camera by rotating the entity. Default looks along -Z.
- All camera parameters are animatable.
- Multiple cameras can exist in a scene.
