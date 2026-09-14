# Honey Block Serializer

Serializer ID: `resourcefulbees:block/v1`

This optional serializer controls the custom honey block's appearance and movement behavior, which existing block/item definitions it is based on, and optional beekeeper trade data.

## Fields

| Field | Type | Required | Default | Range / notes |
| --- | --- | --- | --- | --- |
| `color` | ResourcefulLib color | No | `#ffffff` | Number, color string/special name, or RGBA object |
| `jumpFactor` | number | No | `0.5` | No additional codec range supplied |
| `speedFactor` | number | No | `0.4` | No additional codec range supplied |
| `honeyBlockItem` | item identifier | No | `minecraft:honey_block` | Registered item ID |
| `honeyBlock` | block identifier | No | `minecraft:honey_block` | Registered block ID |
| `tradeData` | trade object | No | serializer-level `TradeData.DEFAULT` | See omitted-vs-explicit behavior below |

## Example

```json
{
  "resourcefulbees:block/v1": {
    "color": "#f6b83f",
    "jumpFactor": 0.5,
    "speedFactor": 0.4,
    "honeyBlockItem": "minecraft:honey_block",
    "honeyBlock": "minecraft:honey_block"
  }
}
```

## Serializer default vs explicit object

The entire block serializer is optional. If it is absent, Resourceful Bees uses its serializer-level block default internally.

`tradeData` has a second important distinction: omitting `tradeData` uses `TradeData.DEFAULT` (the non-tradable/zero-valued serializer default), while explicitly writing an empty object causes the trade codec's own field defaults to apply.

```json
"tradeData": {}
```

is therefore not semantically identical to omitting `tradeData`.
