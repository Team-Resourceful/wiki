# Honey Bottle Serializer

Serializer ID: `resourcefulbees:bottle/v1`

This is the required built-in honey serializer. It controls bottle color, food behavior, rarity, and optional trade data. The registered honey bottle item is derived from the honey filename rather than configured by a serializer field.

## Fields

| Field | Type | Required | Default | Range / notes |
| --- | --- | --- | --- | --- |
| `color` | ResourcefulLib color | No | `#ffffff` | Number, color string/special name, or RGBA object |
| `food` | food object | No | codec defaults | See below |
| `rarity` | enum name or ordinal | No | `COMMON` | `COMMON`, `UNCOMMON`, `RARE`, `EPIC` case-insensitively; ordinals `0..3` accepted |
| `tradeData` | trade object | No | `TradeData.DEFAULT` | Explicit `{}` uses trade-field defaults |

## Food object

| Field | Type | Required | Default | Range / notes |
| --- | --- | --- | --- | --- |
| `hunger` | integer | No | `1` | No additional codec range supplied |
| `saturation` | number | No | `1.0` | No additional codec range supplied |
| `canAlwaysEat` | boolean | No | `false` | |
| `consumeSeconds` | number | No | `2.0` | |
| `effects` | array | No | `[]` | Potion-effect entries |

## Potion-effect entries

| Field | Type | Required | Default | Range / notes |
| --- | --- | --- | --- | --- |
| `effect` | mob-effect identifier | **Yes** | none | Registered effect ID |
| `duration` | integer | No | `300` | No extra codec range supplied |
| `strength` | integer | No | `0` | No extra codec range supplied |
| `chance` | number | No | `1.0` | No range was imposed by the supplied codec |

## Example

```json
{
  "resourcefulbees:bottle/v1": {
    "color": "#f6b83f",
    "food": {
      "hunger": 2,
      "saturation": 1.0,
      "canAlwaysEat": false,
      "consumeSeconds": 2.0,
      "effects": [
        {
          "effect": "minecraft:speed",
          "duration": 300,
          "strength": 0,
          "chance": 1.0
        }
      ]
    },
    "rarity": "COMMON"
  }
}
```

The honey identifier and registered bottle item are derived from the filename. There is no bottle-item field in `resourcefulbees:bottle/v1`.

Although the serializer is required, its object may be `{}` because all of its nested fields have defaults.
