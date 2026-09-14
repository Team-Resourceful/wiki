# Bee Trade Serializer

Serializer ID: `resourcefulbees:trade/v1`

The trade serializer configures beekeeper trade quantities, optional secondary costs, price scaling, trade limits, and XP.

## Fields

| Field | Type | Required | Default | Range / accepted forms |
| --- | --- | --- | --- | --- |
| `amount` | uniform generator | No | `{ "min": 1, "max": 1 }` | Both `min` and `max` are number providers. |
| `secondaryItem` | item identifier | No | `minecraft:air` | Registered item ID. |
| `secondaryItemCost` | uniform generator | No | `{ "min": 1, "max": 4 }` | Both `min` and `max` are number providers. |
| `priceMultiplier` | number | No | `0.05` | `>= 0` |
| `maxTrades` | integer | No | `8` | `1` through `64` |
| `xp` | integer | No | `3` | `1` through `64` |

## Example

```json
{
  "resourcefulbees:trade/v1": {
    "amount": {
      "min": 1,
      "max": 4
    },
    "secondaryItem": "minecraft:emerald",
    "secondaryItemCost": {
      "min": 1,
      "max": 2
    },
    "priceMultiplier": 0.05,
    "maxTrades": 8,
    "xp": 3
  }
}
```

## Uniform generators

A uniform generator is an object with required `min` and `max` fields:

```json
{
  "min": 1,
  "max": 4
}
```

Each endpoint is a Minecraft number provider. Constant providers encode directly as numbers. Other registered providers encode as typed objects and are intentionally left extensible by the schema.

```json
{
  "type": "minecraft:uniform",
  "min": 1,
  "max": 3
}
```

The exact fields of non-constant number-provider objects depend on the registered provider type.

## Serializer-level default caveat

Resourceful Bees also has serializer-level default objects used internally when a whole trade section is absent. Those internal zero-like defaults are separate from the field defaults above. When an explicit `resourcefulbees:trade/v1` object is authored, omitted fields use the codec defaults in this table and explicit `maxTrades`/`xp` values must satisfy the `1..64` ranges.
