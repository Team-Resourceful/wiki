# Flow Hive Recipe

Draft 2020-12 schema reconstructed from FlowHiveRecipe, ResourcefulLib
HolderSetCodec, and NeoForge FluidStackTemplate.

## Example

``` json
{
  "type": "resourcefulbees:flow_hive",
  "bees": [
    "minecraft:bee",
    "resourcefulbees:ruby_bee"
  ],
  "fluid": {
    "id": "resourcefulbees:ruby_honey_fluid_source",
    "amount": 1000,
    "components": {}
  }
}
```

## Fields

  ----------------------------------------------------------------------------------------------------------
  Field          Type                 Required       Default                       Description
  -------------- -------------------- -------------- ----------------------------- -------------------------
  `type`         string               Yes            `resourcefulbees:flow_hive`   ---

  `bees`         entityHolderSet      Yes            ---                           Entity holder set
                                                                                   accepted by
                                                                                   HolderSetCodec: a #tag, a
                                                                                   single entity ID, or a
                                                                                   list of entity IDs.

  `fluid`        fluidStackTemplate   Yes            ---                           NeoForge
                                                                                   FluidStackTemplate. A
                                                                                   bare fluid ID is
                                                                                   shorthand for that fluid
                                                                                   with
                                                                                   FluidType.BUCKET_VOLUME
                                                                                   (1000) and no component
                                                                                   patch.
  ----------------------------------------------------------------------------------------------------------

## Runtime notes

The fluid result supports a shorthand non-empty fluid ID string or an
object with required `id` and positive `amount`. `minecraft:empty` is
not a valid result fluid.

## Schema and template

The source files used for this page are included in the `reference/`
directory:

-   `resourcefulbees-flow-hive-recipe-template.json`
-   `resourcefulbees-flow-hive-recipe.schema.json`

> The schema is the machine-readable reference. Runtime notes document
> codec or game behavior that JSON Schema cannot fully express.
