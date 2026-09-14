# Honeycomb JSON Reference

Honeycomb files have two top-level sections: optional honeycomb registration data and an optional list of output variations.

## Top-level fields

| Field | Type | Required | Default | Purpose |
| --- | --- | --- | --- | --- |
| `honeycomb` | registration object | No | omitted | Item/block registration and trade data |
| `variations` | array of output variations | No | `[]` | Hive/apiary output mappings |

## Registration data

See [Honeycomb Registration](registration.md) for `name`, `color`, `edible`, `block`, `enchanted`, and `tradeData`.

## Output variations

See [Output Variations](variations.md) for `identifier`, tier comb maps, defaults, and runtime normalization behavior.

## Example

```json
{
  "honeycomb": {
    "name": "ruby",
    "color": "#c62828",
    "edible": true,
    "block": true,
    "enchanted": false
  },
  "variations": [
    {
      "identifier": "ruby",
      "defaultComb": "resourcefulbees:ruby_honeycomb"
    }
  ]
}
```

The complete machine-readable reference is available in [`resourcefulbees-honeycomb.schema.json`](../../reference/resourcefulbees-honeycomb.schema.json).
