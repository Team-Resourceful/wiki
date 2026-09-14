# Honey Fluid Serializer

Serializer ID: `resourcefulbees:fluid/v1`

This optional serializer controls custom honey fluid rendering, physical/gameplay attributes, and trade data.

## Fields

| Field | Type | Required | Default | Notes |
| --- | --- | --- | --- | --- |
| `rendering` | rendering object | No | serializer default | If present, `color` is required. |
| `attributes` | fluid-attributes object | No | codec defaults | All nested fields optional. |
| `tradeData` | trade object | No | `TradeData.DEFAULT` | Explicit `{}` uses trade-field defaults. |

## Rendering object

| Field | Type | Required | Default |
| --- | --- | --- | --- |
| `color` | ResourcefulLib color | **Yes, when `rendering` is present** | none |
| `still` | resource identifier | No | `resourcefulbees:block/honey/custom_honey_still` |
| `flowing` | resource identifier | No | `resourcefulbees:block/honey/custom_honey_flow` |
| `face` | resource identifier | No | `resourcefulbees:block/honey/custom_honey_flow` |
| `overlay` | resource identifier | No | `resourcefulbees:textures/block/honey/custom_honey_underwater.png` |

An explicit empty rendering object is invalid:

```json
"rendering": {}
```

If `rendering` is written, supply at least `color`.

## Fluid attributes

| Field | Type | Required | Default | Range / accepted values |
| --- | --- | --- | --- | --- |
| `lightLevel` | integer | No | `1` | `0` through `15` |
| `density` | integer | No | `1000` | No extra codec range supplied |
| `temperature` | integer | No | `300` | No extra codec range supplied |
| `viscosity` | integer | No | `1000` | No extra codec range supplied |
| `fallDistanceModifier` | number | No | `0.5` | No extra codec range supplied |
| `motionScale` | number | No | `0.014` | No extra codec range supplied |
| `canPushEntities` | boolean | No | `true` | |
| `canSwimIn` | boolean | No | `true` | |
| `canDrownIn` | boolean | No | `true` | |
| `canExtinguish` | boolean | No | `false` | |
| `canConvertToSource` | boolean | No | `false` | |
| `supportsBoating` | boolean | No | `false` | |
| `canHydrate` | boolean | No | `false` | |
| `rarity` | string | No | `common` | `common`, `uncommon`, `rare`, `epic` |
| `fillSound` | resource identifier | No | `minecraft:item.bucket.fill` | |
| `emptySound` | resource identifier | No | `minecraft:item.bucket.empty` | |

## Example

```json
{
  "resourcefulbees:fluid/v1": {
    "rendering": {
      "color": "#f6b83f"
    },
    "attributes": {
      "lightLevel": 1,
      "density": 1000,
      "temperature": 300,
      "viscosity": 1000
    }
  }
}
```
