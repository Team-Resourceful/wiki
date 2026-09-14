# Honeycomb Registration Data

The optional `honeycomb` object controls the custom honeycomb item/block registration.

## Fields

| Field | Type | Required | Default | Range / notes |
| --- | --- | --- | --- | --- |
| `name` | string | No | filename-derived name | Loader lowercases the name and replaces spaces with `_`. |
| `color` | ResourcefulLib color | No | `#ffffff` | Number, string/special color, or RGBA object |
| `edible` | boolean | No | `true` | Global config may still affect edible behavior. |
| `block` | boolean | No | `true` | `true` registers block + block item + comb item; `false` registers only the comb item. |
| `enchanted` | boolean | No | `false` | Enables enchanted glint behavior. |
| `tradeData` | trade object | No | `TradeData.DEFAULT` | Explicit `{}` uses normal trade field defaults. |

## Example

```json
{
  "honeycomb": {
    "name": "ruby",
    "color": "#c62828",
    "edible": true,
    "block": true,
    "enchanted": false
  }
}
```

## `name`

The file name normally supplies the honeycomb name. `name` is an optional override parsed separately by the loader before the registration codec is applied.

## `tradeData`

Omitting `tradeData` is **not** equivalent to writing an empty object. Omission uses the serializer's non-tradable `TradeData.DEFAULT`; explicit `{}` activates the trade codec defaults (`amount` 1..1, secondary item air, secondary cost 1..4, multiplier 0.05, max trades 8, XP 3).
