# Centrifuge Recipe

Schema reconstructed from `CentrifugeRecipe`, its item/fluid output codecs, ResourcefulLib `WeightedCollection`, Minecraft `Ingredient` and `ItemStackTemplate`, and NeoForge `FluidStackTemplate`.

## Example

```json
{
  "type": "resourcefulbees:centrifuge",
  "ingredient": "resourcefulbees:iron_honeycomb",
  "inputAmount": 1,
  "itemOutputs": [
    {
      "chance": 0.8,
      "pool": [
        {
          "item": {
            "id": "minecraft:raw_iron",
            "count": 3
          },
          "weight": 25
        },
        {
          "item": "minecraft:raw_iron",
          "weight": 50
        }
      ]
    }
  ],
  "fluidOutputs": [
    {
      "chance": 1.0,
      "pool": [
        {
          "fluid": {
            "id": "resourcefulbees:honey_fluid_source",
            "amount": 100
          },
          "weight": 1
        }
      ]
    }
  ],
  "time": 200,
  "energyPerTick": 10
}
```

## Fields

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `type` | string | Yes | `resourcefulbees:centrifuge` | Recipe serializer identifier. |
| `ingredient` | Minecraft Ingredient | Yes | — | Item ingredient tested against the centrifuge input stack. Simple Resourceful Bees recipes use a direct item ID; Minecraft/NeoForge ingredient objects remain codec-driven. |
| `inputAmount` | integer | No | `1` | Required stack count for the recipe match. The codec itself applies no numeric range. |
| `itemOutputs` | array of item output rolls | No | `[]` | Independent item-output rolls. Each roll has a chance and a weighted pool of possible item results. |
| `fluidOutputs` | array of fluid output rolls | No | `[]` | Independent fluid-output rolls. Each roll has a chance and a weighted pool of possible fluid results. |
| `time` | integer | No | configured default (`200` initially) | Recipe time. The codec uses `CentrifugeConfig.defaultCentrifugeRecipeTime`; the recipe field itself uses an unrestricted integer codec. |
| `energyPerTick` | integer | No | configured default (`10` initially) | Energy value from `CentrifugeConfig.centrifugeRfPerTick`. The recipe field itself uses an unrestricted integer codec. |
| `rotations` | integer | No | derived from `time` | Optional explicit rotation count. If omitted, runtime computes `((time / 20) / 8) * 2` using integer division. |

## Output rolls

Each entry in `itemOutputs` or `fluidOutputs` is an independent roll:

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `chance` | number | No | `1.0` | Probability that this output roll occurs. Range `0.0` through `1.0`, inclusive. |
| `pool` | array | No | `[]` | Weighted collection from which one result is selected when the roll succeeds. In practical recipes, provide at least one result. |

Multiple output-roll entries can succeed during the same recipe completion. `chance` controls whether a roll occurs; `weight` only controls which member of that roll's `pool` is selected.

### Item pool entries

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `item` | ItemStackTemplate | Yes | — | Item result, using the compact item ID or expanded item-stack-template form. |
| `weight` | number | No | `1.0` | Relative selection weight. Range `1.0` through `1000.0`, inclusive. |

### Fluid pool entries

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `fluid` | FluidStackTemplate | Yes | — | Fluid result. A compact non-empty fluid ID or expanded `{id, amount, components}` form is accepted by the underlying template codec. |
| `weight` | number | No | `1.0` | Relative selection weight. Minimum `1.0`; the codec's upper bound is `Double.MAX_VALUE`. |

## Runtime notes

The recipe matches only when `ingredient.test(input)` succeeds **and** the input stack's count is exactly equal to `inputAmount`.

The current centrifuge completion code consumes one input item after a match, even though `inputAmount` participates in exact-count matching. This is a runtime behavior worth keeping in mind when authoring recipes with `inputAmount` other than `1`.

Each successful output roll calls into its weighted pool to choose one result. Although an omitted `pool` codec-decodes to an empty weighted collection, an empty pool cannot provide a random result at runtime. Treat a non-empty pool as practically required for every output roll that can succeed.

The current manual centrifuge uses `rotations` when supplied. Otherwise, rotations are derived from `time` with integer division. With the stock `time` default of `200`, the derived value is `2` rotations.

`time`, `energyPerTick`, `inputAmount`, and `rotations` are all plain `Codec.INT` fields in the recipe codec; the configuration ranges on the default config values do not impose equivalent per-recipe validation ranges.

## Ingredient codec scope

`ingredient` is delegated directly to Minecraft's `Ingredient.CODEC`. The schema intentionally models the common direct item/tag forms and leaves custom ingredient objects extensible rather than guessing every Minecraft/NeoForge ingredient subtype. If stricter completion for the exact Minecraft version is desired, the external `Ingredient.CODEC` definitions can be incorporated separately.

## Schema and template

The source files used for this page are included in the `reference/` directory:

- `resourcefulbees-centrifuge-recipe-template.json`
- `resourcefulbees-centrifuge-recipe.schema.json`

> The schema is the machine-readable reference. Runtime notes document codec or game behavior that JSON Schema cannot fully express.
