# Breeder Recipe

Breeder recipes use the `resourcefulbees:breeder` serializer to match two parent inputs, their feed items, an additional ingredient slot, and a weighted collection of possible child outputs.

## Example

```json
{
  "type": "resourcefulbees:breeder",
  "parent1": {
    "parent": {
      "id": "resourcefulbees:iron_bee",
      "neoforge:ingredient_type": "resourcefulbees:bee_jar"
    },
    "displayEntity": "resourcefulbees:iron_bee",
    "feedAmount": 1,
    "feedItems": "minecraft:poppy"
  },
  "parent2": {
    "parent": {
      "id": "resourcefulbees:iron_bee",
      "neoforge:ingredient_type": "resourcefulbees:bee_jar"
    },
    "displayEntity": "resourcefulbees:iron_bee",
    "feedAmount": 1,
    "feedItems": "minecraft:poppy"
  },
  "outputs": [
    {
      "child": {
        "id": "resourcefulbees:bee_jar",
        "components": {
          "resourcefulbees:jar_bee": {
            "entity_type": "resourcefulbees:iron_bee",
            "insertion_game_time": 0,
            "display_name": {
              "translate": "entity_type.resourcefulbees.iron_bee"
            },
            "color": -13159
          }
        }
      },
      "entity": "resourcefulbees:iron_bee",
      "weight": 10.0,
      "chance": 1.0
    }
  ],
  "time": 2400
}
```

## Fields

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `type` | string | Yes | `resourcefulbees:breeder` | Recipe serializer identifier. |
| `parent1` | ParentInput | Yes | — | First parent and its feed requirements. |
| `parent2` | ParentInput | Yes | — | Second parent and its feed requirements. |
| `optional` | Minecraft Ingredient | No | `resourcefulbees:bee_jar` | Ingredient matched against the breeder's additional input slot. When omitted, an empty Resourceful Bees bee jar is required. |
| `outputs` | weighted array of ChildOutput | Yes | — | Possible child results. Selection is weighted by each entry's `weight`. |
| `time` | integer | No | `2400` | Base processing time. Range `100` through `72000`, inclusive. |

## Parent inputs

Each parent uses the `ParentInput` codec.

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `parent` | Minecraft Ingredient | Yes | — | Ingredient matched against the parent input slot. Generated custom-bee recipes use the [Bee Jar Ingredient](bee-jar-ingredient.md) to require a jar containing a specific bee entity type. |
| `displayEntity` | identifier | No | absent | Entity ID used for display/client presentation. It does not participate in `ParentInput.matches`. |
| `feedAmount` | integer | No | `1` | Number of feed items consumed after a successful breed. The current codec uses unrestricted `Codec.INT`. |
| `feedItems` | Minecraft Ingredient | Yes | — | Ingredient matched against this parent's feed slot. |
| `returnItem` | ItemStackTemplate | No | absent | Item returned after feed consumption. When present, the breeder returns `feedAmount` copies. |

Parent matching tests `parent` against the parent stack and `feedItems` against the feed stack. `displayEntity`, `feedAmount`, and `returnItem` do not change the ingredient match itself.

## Child outputs

`outputs` is a `WeightedCollection<ChildOutput>`. One entry is selected according to its relative `weight`, then that selected entry's independent `chance` determines whether breeding succeeds.

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `child` | ItemStackTemplate | Yes | — | Item produced on a successful breed. Generated recipes use a bee jar carrying the child's `resourcefulbees:jar_bee` component. |
| `entity` | identifier | No | absent | Child entity ID used for display/client presentation. |
| `weight` | number | No | `10.0` | Relative weighted-selection value. Range `0.0` through `Double.MAX_VALUE`. |
| `chance` | number | No | `1.0` | Success chance after this output is selected. Range `0.0` through `1.0`, inclusive. |

A higher `weight` makes an output more likely relative to the other entries. `chance` is applied only after the weighted output has been selected. If that chance roll fails, no child is delivered and the successful-breed consumption transaction is not performed.

## Optional ingredient

`optional` is genuinely optional in the JSON. If it is omitted, the codec supplies `Ingredient.of(resourcefulbees:bee_jar)`, so the additional input slot must contain an empty Resourceful Bees bee jar. Authors only need to specify `optional` when the recipe should require a different ingredient.

The resolved ingredient always participates in recipe matching. On a successful breed, one item is consumed from the additional input slot.

## Runtime notes

The current `BreederRecipe.matches` implementation requires both parents, both feed ingredients, and the resolved `optional` ingredient to match their respective input slots.

On a successful output chance roll, the breeder consumes one item from the additional input slot, consumes `feedAmount` from each parent's feed slot, creates the selected `child`, and returns each parent's `returnItem` in a quantity equal to that parent's `feedAmount`.

The `outputs` field is required by the codec, but the weighted-collection codec itself does not establish a non-empty-list constraint here. Runtime processing calls `outputs.next()`, so recipes should provide at least one output.

The breeder's processing time can be modified by breeder upgrades at runtime; the recipe's `time` is the base value before that modifier.

## Ingredient codec scope

`parent`, `feedItems`, and `optional` delegate to Minecraft/NeoForge `Ingredient.CODEC`. The schema models common item/tag/list forms and the Resourceful Bees Bee Jar Ingredient explicitly, while leaving other custom NeoForge ingredient objects extensible rather than guessing their external codecs.

## Schema and template

- `resourcefulbees-breeder-recipe-template.json`
- `resourcefulbees-breeder-recipe.schema.json`

> The schema is the machine-readable reference. Runtime notes document behavior that JSON Schema or the field codecs alone cannot fully express.
