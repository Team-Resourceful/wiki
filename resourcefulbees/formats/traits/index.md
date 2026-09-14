# Custom Trait JSON Reference

Standalone trait files define reusable behavior that bees can reference from their `resourcefulbees:trait/v1` serializer.

## Top-level fields

| Field | Type | Required | Default | Notes |
| --- | --- | --- | --- | --- |
| `name` | string | No | filename-derived | Lowercased; spaces become `_`. |
| `displayItem` | item identifier | No | `minecraft:nether_star` | Display item for the trait. |
| `potionDamageEffects` | array | No | `[]` | Potion-effect entries. |
| `damageImmunities` | array of strings | No | `[]` | Free-form damage immunity names used by the trait runtime. |
| `potionImmunities` | array of mob-effect IDs | No | `[]` | Registered effect identifiers. |
| `damageTypes` | array | No | `[]` | Trait damage-type entries. |
| `specialAbilities` | array of strings | No | `[]` | Free-form special ability names. |
| `particleType` | array of particle IDs | No | `[]` | Exact JSON key is singular `particleType`. |
| `auras` | array | No | `[]` | Aura entries; see [Auras](auras.md). |

All fields are optional.

## Set semantics

Several arrays are decoded through a list and then converted to a `HashSet`. Duplicates are accepted by the codec but collapse at runtime; ordering is not semantically preserved.

## Nested objects

- [Potion and damage types](effects.md)
- [Auras](auras.md)

The machine-readable source remains [`resourcefulbees-trait.schema.json`](../../reference/resourcefulbees-trait.schema.json).
