# Custom Honey

JSON reference for Resourceful Bees.

## Example

```json
{
  "resourcefulbees:block/v1": {
    "color": "#ffffff",
    "jumpFactor": 0.5,
    "speedFactor": 0.4,
    "tradeData": {
      "amount": { "min": 1, "max": 1 },
      "secondaryItem": "minecraft:air",
      "secondaryItemCost": { "min": 1, "max": 4 },
      "priceMultiplier": 0.05,
      "maxTrades": 8,
      "xp": 3
    }
  },
  "resourcefulbees:fluid/v1": {
    "rendering": {
      "color": "#ffffff",
      "still": "resourcefulbees:block/honey/custom_honey_still",
      "flowing": "resourcefulbees:block/honey/custom_honey_flow",
      "face": "resourcefulbees:block/honey/custom_honey_flow",
      "overlay": "resourcefulbees:textures/block/honey/custom_honey_underwater.png"
    },
    "attributes": {
      "lightLevel": 1,
      "density": 1000,
      "temperature": 300,
      "viscosity": 1000,
      "fallDistanceModifier": 0.5,
      "motionScale": 0.014,
      "canPushEntities": true,
      "canSwimIn": true,
      "canDrownIn": true,
      "canExtinguish": false,
      "canConvertToSource": false,
      "supportsBoating": false,
      "canHydrate": false,
      "rarity": "common",
      "fillSound": "minecraft:item.bucket.fill",
      "emptySound": "minecraft:item.bucket.empty"
    },
    "tradeData": {
      "amount": { "min": 1, "max": 1 },
      "secondaryItem": "minecraft:air",
      "secondaryItemCost": { "min": 1, "max": 4 },
      "priceMultiplier": 0.05,
      "maxTrades": 8,
      "xp": 3
    }
  },
  "resourcefulbees:bottle/v1": {
    "color": "#ffffff",
    "food": {
      "hunger": 1,
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
    "rarity": "COMMON",
    "tradeData": {
      "amount": { "min": 1, "max": 1 },
      "secondaryItem": "minecraft:air",
      "secondaryItemCost": { "min": 1, "max": 4 },
      "priceMultiplier": 0.05,
      "maxTrades": 8,
      "xp": 3
    }
  }
}
```

## Fields

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `resourcefulbees:block/v1` | blockData | No | --- | Block serializer data. |
| `resourcefulbees:fluid/v1` | fluidData | No | --- | Fluid serializer data. |
| `resourcefulbees:bottle/v1` | bottleData | Yes | --- | Bottle serializer data. |

## Runtime notes

Honey data is a flat serializer map. `resourcefulbees:bottle/v1` is
required; the block and fluid serializers are optional. The honey name
and registered honey content are derived from the filename rather than
root or serializer-level item/block identifier fields. In particular,
the bottle item and the honey block/block item do not need to be named
in JSON.

An explicit empty rendering object is not valid because
`rendering.color` is required when the rendering object is present.

## Schema and template

The source files used for this page are included in the `reference/`
directory:

- `resourcefulbees-honey-template.json`
- `resourcefulbees-honey.schema.json`

> The schema is the machine-readable reference. Runtime notes document
> codec or game behavior that JSON Schema cannot fully express.
