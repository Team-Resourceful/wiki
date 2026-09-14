# Solidification Recipe

Draft 2020-12 schema reconstructed from SolidificationRecipe, NeoForge
SizedFluidIngredient, and NeoForge FluidIngredient dispatch codecs.

## Example

``` json
{
  "type": "resourcefulbees:solidification",
  "fluid": {
    "ingredient": "minecraft:lava",
    "amount": 1000
  },
  "result": {
    "id": "minecraft:obsidian",
    "count": 1,
    "components": {}
  },
  "time": 200
}
```

## Fields

  -----------------------------------------------------------------------------------------------------------
  Field          Type                   Required       Default                            Description
  -------------- ---------------------- -------------- ---------------------------------- -------------------
  `type`         string                 Yes            `resourcefulbees:solidification`   ---

  `fluid`        sizedFluidIngredient   Yes            ---                                ---

  `result`       itemStackTemplate      Yes            ---                                Minecraft
                                                                                          ItemStackTemplate
                                                                                          compact string or
                                                                                          expanded object
                                                                                          form.

  `time`         integer                No             `200`                              ---
  -----------------------------------------------------------------------------------------------------------

## Runtime notes

The documented `time` field is non-negative and defaults to `200`. Fluid
ingredients support direct fluid IDs, fluid tags, and extensible
NeoForge custom ingredient objects.

## Schema and template

The source files used for this page are included in the `reference/`
directory:

-   `resourcefulbees-solidification-recipe-template.json`
-   `resourcefulbees-solidification-recipe.schema.json`

> The schema is the machine-readable reference. Runtime notes document
> codec or game behavior that JSON Schema cannot fully express.
