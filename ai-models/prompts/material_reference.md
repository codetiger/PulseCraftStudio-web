# Material Reference

PBR (Physically Based Rendering) material properties. Materials are NOT animatable — use pcs_modify to change them.

## Properties

### Surface
| Property | Range | Default | Description |
|----------|-------|---------|-------------|
| baseColor | #hex | #FFFFFF | Diffuse/albedo color |
| metalness | 0–1 | 0 | 0=dielectric, 1=metal |
| roughness | 0–1 | 0.5 | 0=mirror, 1=diffuse |
| specular | 0–1 | 0.5 | Specular intensity |
| ior | 1–3 | 1.5 | Index of refraction |

### Transparency
| Property | Range | Default |
|----------|-------|---------|
| transmission | 0–1 | 0 |
| opacity | 0–1 | 1 |

### Clearcoat
| Property | Range | Default |
|----------|-------|---------|
| clearcoat | 0–1 | 0 |
| clearcoatRoughness | 0–1 | 0.03 |

### Emission
| Property | Range | Default |
|----------|-------|---------|
| emissionColor | #hex | #000000 |
| emissionIntensity | 0–100 | 0 |

### Other
| Property | Type | Default |
|----------|------|---------|
| isDoubleSided | bool | false |

## Common Material Recipes

| Material | baseColor | metalness | roughness | Other |
|----------|-----------|-----------|-----------|-------|
| Gold metal | #FFD700 | 1.0 | 0.3 | — |
| Mirror | #FFFFFF | 1.0 | 0.0 | — |
| Glass | #FFFFFF | 0.0 | 0.0 | transmission 1.0, ior 1.5 |
| Matte plastic | any | 0.0 | 0.8 | — |
| Glowing | any | — | — | emissionColor #FF0000, emissionIntensity 5.0 |
