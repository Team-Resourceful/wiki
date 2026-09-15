# Traits

Schema reconstructed from TraitSetup, Trait, PotionEffect,
TraitDamageType, DamageEffect, Aura, AuraType, and CodecExtras.set.

## Example

```json
{
  "name": "fiery",
  "displayItem": "minecraft:blaze_powder",
  "potionDamageEffects": [
    {
      "effect": "minecraft:poison",
      "strength": 1
    }
  ],
  "damageImmunities": [
    "inFire",
    "onFire",
    "lava"
  ],
  "potionImmunities": [
    "minecraft:poison"
  ],
  "damageTypes": [
    {
      "damageType": "setOnFire",
      "amplifier": 2
    }
  ],
  "specialAbilities": [
    "flammable"
  ],
  "particleType": [
    "minecraft:flame"
  ],
  "auras": [
    {
      "aura": "BURNING",
      "modifier": 0,
      "calmingDisabled": false
    },
    {
      "aura": "DAMAGING",
      "damageEffect": {
        "source": "minecraft:generic",
        "hasEntity": false,
        "strength": 3
      }
    }
  ]
}
```

## Fields

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `name` | string | No | --- | Optional trait name override. If omitted, the filename-derived name is used. Runtime lowercases the name and replaces spaces with underscores. |
| `displayItem` | identifier | No | `"minecraft:nether_star"` | --- |
| `potionDamageEffects` | array | No | `[]` | --- |
| `damageImmunities` | array | No | `[]` | --- |
| `potionImmunities` | array | No | `[]` | --- |
| `damageTypes` | array | No | `[]` | --- |
| `specialAbilities` | array | No | `[]` | --- |
| `particleType` | array | No | `[]` | --- |
| `auras` | array | No | `[]` | --- |

## Runtime notes

Trait set-like arrays are decoded through a list and converted to a
`HashSet`. Duplicate entries are accepted by the codec and collapse at
runtime; ordering is not semantically preserved.

## Schema and template

The source files used for this page are included in the `reference/`
directory:

- `resourcefulbees-trait-template.json`
- `resourcefulbees-trait.schema.json`

> The schema is the machine-readable reference. Runtime notes document
> codec or game behavior that JSON Schema cannot fully express.
