# Bee Jar Ingredient

Resourceful Bees registers the custom NeoForge ingredient type `resourcefulbees:bee_jar`. The ingredient matches a bee jar by the entity type stored in its `resourcefulbees:jar_bee` data component rather than by the jar item ID alone.

## Format

```json
{
  "id": "resourcefulbees:iron_bee",
  "neoforge:ingredient_type": "resourcefulbees:bee_jar"
}
```

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `neoforge:ingredient_type` | string | Yes | NeoForge custom ingredient dispatch ID. Must be `resourcefulbees:bee_jar`. |
| `id` | identifier | Yes | Entity type that must be stored in the jar. |

The Resourceful Bees `BeeJarIngredient` map codec itself contains the `id` field. NeoForge's ingredient dispatch supplies the `neoforge:ingredient_type` discriminator that selects that codec.

## Matching behavior

The ingredient reads the `resourcefulbees:jar_bee` component from the tested stack. It fails when the stack is null, when the component is absent, or when the stored occupant has no entity data. Otherwise, it resolves the occupant's entity type ID and compares it exactly with `id`.

This means the ingredient is **entity-specific**. For example, an ingredient with `"id": "resourcefulbees:iron_bee"` accepts a jar whose occupant is the Iron Bee but rejects a jar containing a different bee.

`BeeJarIngredient` is a non-simple custom ingredient and reports no fixed item stream. Consumers should rely on ingredient testing rather than treating it as a static list of acceptable item IDs.

## Usage in breeder recipes

Generated breeder recipes use Bee Jar Ingredients for `parent1.parent` and `parent2.parent`:

```json
{
  "parent1": {
    "parent": {
      "id": "resourcefulbees:iron_bee",
      "neoforge:ingredient_type": "resourcefulbees:bee_jar"
    },
    "feedItems": "minecraft:poppy"
  }
}
```

This allows the breeder recipe to distinguish two stacks of the same physical bee-jar item based on which bee is actually inside each jar. See [Breeder Recipe](breeder.md) for the complete recipe format.

## Bee Jar Ingredient vs. bee jar item ingredient

A Bee Jar Ingredient is different from a normal ingredient that simply references `resourcefulbees:bee_jar`. The custom ingredient checks the stored occupant entity ID. A normal bee-jar item ingredient only identifies the jar item and does not use the `BeeJarIngredient` entity-specific test.
