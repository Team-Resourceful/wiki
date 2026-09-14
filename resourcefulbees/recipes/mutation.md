# Mutation Recipe

Draft 2020-12 schema reconstructed from MutationRecipe, MutationEntry,
MutationCodec, built-in mutation serializers, and predicate codecs.

## Example

``` json
{
  "type": "resourcefulbees:mutation",
  "pollenBaseColor": 12681264,
  "pollenTopColor": 13408304,
  "mutations": [
    {
      "input": {
        "type": "item",
        "item": {
          "id": "minecraft:diamond"
        },
        "chance": 1.0,
        "weight": 10.0
      },
      "outputs": [
        {
          "type": "block",
          "block": {
            "id": "minecraft:diamond_block"
          },
          "chance": 1.0,
          "weight": 10.0
        },
        {
          "type": "fluid",
          "fluid": "minecraft:water",
          "chance": 1.0,
          "weight": 10.0
        },
        {
          "type": "entity",
          "entity": {
            "type": "minecraft:cow"
          },
          "chance": 1.0,
          "weight": 10.0
        }
      ]
    }
  ]
}
```

## Fields

  -----------------------------------------------------------------------------------------------
  Field               Type           Required       Default                      Description
  ------------------- -------------- -------------- ---------------------------- ----------------
  `type`              string         Yes            `resourcefulbees:mutation`   ---

  `pollenBaseColor`   color          No             `12681264`                   ResourcefulLib
                                                                                 Color. Accepted
                                                                                 forms include
                                                                                 numeric values,
                                                                                 string
                                                                                 values/special
                                                                                 color names, or
                                                                                 RGBA objects.

  `pollenTopColor`    color          No             `13408304`                   ResourcefulLib
                                                                                 Color. Accepted
                                                                                 forms include
                                                                                 numeric values,
                                                                                 string
                                                                                 values/special
                                                                                 color names, or
                                                                                 RGBA objects.

  `mutations`         array          Yes            ---                          ---
  -----------------------------------------------------------------------------------------------

## Runtime notes

`mutations` is required, but the codec permits an empty list. Mutation
entries contain one required `input` mutation and a required plain list
of `outputs`.

## Schema and template

The source files used for this page are included in the `reference/`
directory:

-   `resourcefulbees-mutation-recipe-template.json`
-   `resourcefulbees-mutation-recipe.schema.json`

> The schema is the machine-readable reference. Runtime notes document
> codec or game behavior that JSON Schema cannot fully express.
