# Light Reference

4 light types. All light parameters are animatable.

## Common Properties (all types)

| Parameter | Range | Default |
|-----------|-------|---------|
| color | #hex | #FFFFFF |
| intensity | 0–100000 | 1000 |
| temperature | 0–40000 K | 6500 |

Temperature guide: 2700K warm/yellow, 5000K neutral, 6500K daylight, 10000K cool/blue.

## Ambient (`light_ambient`)

Uniform illumination, no direction or position. Only uses common properties above.

## Directional (`light_directional`)

Sun-like parallel rays. Direction set by entity rotation.

| Parameter | Range | Default |
|-----------|-------|---------|
| castsShadow | bool | true |
| shadowRadius | 0–100 | 1 |

## Omni / Point (`light_omni`)

Radiates from a point in all directions.

| Parameter | Range | Default |
|-----------|-------|---------|
| castsShadow | bool | true |
| shadowRadius | 0–100 | 1 |
| attenuationStart | 0–100 | 0 |
| attenuationEnd | 0–100 | 100 |
| attenuationFalloff | 0–100 | 1 |

## Spot (`light_spot`)

Cone-shaped light from a point.

| Parameter | Range | Default |
|-----------|-------|---------|
| castsShadow | bool | true |
| shadowRadius | 0–100 | 1 |
| spotInnerAngle | 0–180° | 0 |
| spotOuterAngle | 0–180° | 45 |
| attenuationStart | 0–100 | 0 |
| attenuationEnd | 0–100 | 100 |
| attenuationFalloff | 0–100 | 1 |

Inner/outer angles control the falloff cone: inner = full intensity, outer = edge.
