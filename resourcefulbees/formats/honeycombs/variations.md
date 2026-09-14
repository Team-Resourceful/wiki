# Honeycomb Output Variations

Each entry in the top-level `variations` array controls which comb items are produced by hive and apiary tiers.

## Fields

| Field | Type | Required | Default | Notes |
| --- | --- | --- | --- | --- |
| `identifier` | string | **Yes** | none | Variation identifier. Runtime code assumes a non-null value. |
| `hiveCombs` | tier → item stack map | No | `{}` | Keys are registered beehive tier IDs. |
| `apiaryCombs` | tier → item stack map | No | `{}` | Keys are registered apiary tier IDs. |
| `defaultComb` | item stack template | No | omitted | Fallback comb output. |
| `defaultCombBlock` | item stack template | No | omitted | Fallback comb-block output used by apiary-related behavior. |

## Example

```json
{
  "identifier": "ruby",
  "hiveCombs": {
    "resourcefulbees:t1": "resourcefulbees:ruby_honeycomb",
    "resourcefulbees:t2": {
      "id": "resourcefulbees:ruby_honeycomb",
      "count": 2
    }
  },
  "apiaryCombs": {
    "resourcefulbees:t1": "resourcefulbees:ruby_honeycomb"
  },
  "defaultComb": "resourcefulbees:ruby_honeycomb",
  "defaultCombBlock": "resourcefulbees:ruby_honeycomb_block"
}
```

## Built-in tier identifiers

Resourceful Bees registers built-in beehive and apiary tiers `resourcefulbees:t1` through `resourcefulbees:t4`. The tier registries are extensible, so add-ons may provide additional valid keys.

## Item stack values

Map values and the two default fields use item stack templates. They may be compact item IDs or expanded objects with required `id`, optional `count` (`1..99`, default `1`), and optional `components`.

## Hive fallback behavior

When `hiveCombs` is empty, runtime normalization uses `defaultComb` to populate missing hive tiers. If both `hiveCombs` and `defaultComb` are absent/empty, runtime code rejects the variation.

When some hive tiers are present, missing tiers are normalized by runtime code. Do not rely on JSON object ordering to express tier inheritance; tier iteration comes from the tier registry/runtime data rather than an ordered JSON contract.

## Apiary fallback behavior

Apiary output normalization is partly configuration-dependent. If `apiaryCombs` is empty, Resourceful Bees derives/validates defaults based on configured apiary output types. Because of that configuration dependency, JSON Schema cannot universally require either `defaultComb` or `defaultCombBlock`.
