# Honey Generator Recipe

Schema reconstructed from HoneyGenRecipe and NeoForge FluidIngredient
codecs.

## Example

```json
{
  "type": "resourcefulbees:honey_gen",
  "honey": "resourcefulbees:ruby_honey_fluid_source",
  "energyFillRate": 125,
  "honeyDrainRate": 5
}
```

## Fields

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `type` | string | Yes | `resourcefulbees:honey_gen` | Recipe serializer identifier. |
| `honey` | fluidIngredient | Yes | — | Fluid ingredient accepted as honey input. |
| `energyFillRate` | integer | No | `125` | Energy generated per fill operation. Must be non-negative. |
| `honeyDrainRate` | integer | No | `5` | Honey consumed per drain operation. Must be non-negative. |

## Runtime notes

Both rate fields use non-negative integer codecs. `energyFillRate`
defaults to `125` and `honeyDrainRate` defaults to `5`.

## Schema and template

The source files used for this page are included in the `reference/`
directory:

-   `resourcefulbees-honey-gen-recipe-template.json`
-   `resourcefulbees-honey-gen-recipe.schema.json`

> The schema is the machine-readable reference. Runtime notes document
> codec or game behavior that JSON Schema cannot fully express.
