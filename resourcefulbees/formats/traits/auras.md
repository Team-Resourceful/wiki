# Trait Auras

Aura entries combine an aura type with optional damage/potion subobjects and modifiers.

## Aura fields

| Field | Type | Required | Default | Range / notes |
| --- | --- | --- | --- | --- |
| `aura` | enum name or ordinal | **Yes** | none | See aura types below. |
| `damageEffect` | damage-effect object | No | default damage effect | Optional regardless of aura type. |
| `potionEffect` | potion-effect object | No | default potion effect | Optional regardless of aura type. |
| `modifier` | integer | No | `0` | Unrestricted integer in the supplied codec. |
| `calmingDisabled` | boolean | No | `false` | |

## Aura types

The enum codec accepts case-insensitive names and numeric ordinals:

| Name | Ordinal |
| --- | ---: |
| `BURNING` | 0 |
| `POTION` | 1 |
| `HEALING` | 2 |
| `EXPERIENCE` | 3 |
| `DAMAGING` | 4 |
| `EXPERIENCE_DRAIN` | 5 |

## Damage-effect object

| Field | Type | Required | Default | Range / notes |
| --- | --- | --- | --- | --- |
| `source` | damage-type identifier | No | `minecraft:generic` | Registered damage type ID |
| `hasEntity` | boolean | No | `false` | |
| `strength` | integer | No | `0` | `0` through `20` |

## Potion-effect object

| Field | Type | Required | Default | Range |
| --- | --- | --- | --- | --- |
| `effect` | mob-effect identifier | No | `minecraft:luck` | Registered effect ID |
| `strength` | integer | No | `1` | `0` through `4` |

## Example

```json
{
  "aura": "DAMAGING",
  "damageEffect": {
    "source": "minecraft:generic",
    "hasEntity": false,
    "strength": 3
  },
  "modifier": 0,
  "calmingDisabled": false
}
```

The codec does not conditionally require `damageEffect` for damaging auras or `potionEffect` for potion auras. Those objects remain optional at the JSON level.
