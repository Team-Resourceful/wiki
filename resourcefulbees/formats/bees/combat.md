# Bee Combat Serializer

Serializer ID: `resourcefulbees:combat/v1`

The combat serializer controls passive/aggressive behavior and the base attributes assigned to the bee.

## Fields

| Field | Type | Required | Default | Range / accepted forms |
| --- | --- | --- | --- | --- |
| `isPassive` | boolean | No | `false` | `true` or `false` |
| `removeStingerOnAttack` | boolean | No | `true` | `true` or `false` |
| `inflictsPoison` | boolean | No | `true` | `true` or `false` |
| `isInvulnerable` | boolean | No | `false` | `true` or `false` |
| `attributes` | object map | No | see below | Attribute ID → number |

## Default attributes

```json
{
  "minecraft:max_health": 10.0,
  "minecraft:flying_speed": 0.6,
  "minecraft:movement_speed": 0.3,
  "minecraft:attack_damage": 1.0,
  "minecraft:follow_range": 48.0,
  "minecraft:armor": 0.0,
  "minecraft:armor_toughness": 0.0,
  "minecraft:attack_knockback": 0.0
}
```

The map is keyed by Minecraft attribute resource identifiers and accepts numeric values.

## Example

```json
{
  "resourcefulbees:combat/v1": {
    "isPassive": false,
    "removeStingerOnAttack": true,
    "inflictsPoison": true,
    "isInvulnerable": false,
    "attributes": {
      "minecraft:max_health": 20.0,
      "minecraft:attack_damage": 4.0
    }
  }
}
```

All fields are optional. Supplying a custom `attributes` map replaces the value decoded for that field; authors should include every attribute value they intend to customize explicitly.
