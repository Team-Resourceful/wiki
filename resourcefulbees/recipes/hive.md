# Hive Recipe

Schema reconstructed from HiveRecipe, HolderSetCodec, tier codecs, and
ItemStackTemplate.

## Example

```json
{
  "type": "resourcefulbees:hive",
  "bees": [
    "minecraft:bee",
    "resourcefulbees:ruby_bee"
  ],
  "hiveCombs": {
    "resourcefulbees:t1": "resourcefulbees:ruby_honeycomb",
    "resourcefulbees:t2": {
      "id": "resourcefulbees:ruby_honeycomb",
      "count": 2
    }
  },
  "apiaryCombs": {
    "resourcefulbees:t1": {
      "id": "resourcefulbees:ruby_honeycomb",
      "count": 2
    }
  }
}
```

## Fields

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `type` | string | Yes | `resourcefulbees:hive` | Recipe serializer identifier. |
| `bees` | entityHolderSet | Yes | — | Bee/entity holder set matched by the recipe. |
| `hiveCombs` | tierCombMap | No | `{}` | Per-tier hive comb outputs. |
| `apiaryCombs` | tierCombMap | No | `{}` | Per-tier apiary comb outputs. |

## Runtime notes

`bees` is a holder set. Tier maps are keyed by registered tier
identifiers and are extensible beyond the built-in Resourceful Bees
tiers.

## Schema and template

The source files used for this page are included in the `reference/`
directory:

-   `resourcefulbees-hive-recipe-template.json`
-   `resourcefulbees-hive-recipe.schema.json`

> The schema is the machine-readable reference. Runtime notes document
> codec or game behavior that JSON Schema cannot fully express.
