# Trait Potion and Damage Entries

## Potion damage effects

Entries in `potionDamageEffects` use:

| Field | Type | Required | Default | Range |
| --- | --- | --- | --- | --- |
| `effect` | mob-effect identifier | No | `minecraft:luck` | Registered effect ID |
| `strength` | integer | No | `1` | `0` through `4` |

Example:

```json
{
  "effect": "minecraft:poison",
  "strength": 1
}
```

## Damage types

Entries in `damageTypes` use:

| Field | Type | Required | Default | Range / notes |
| --- | --- | --- | --- | --- |
| `damageType` | string | No | `""` | Codec does not restrict this to a documented enum. |
| `amplifier` | integer | No | `0` | `>= 0` |

Example:

```json
{
  "damageType": "setOnFire",
  "amplifier": 2
}
```

The codec accepts arbitrary strings for `damageType`; any semantic restrictions come from runtime handling rather than the JSON codec itself.
