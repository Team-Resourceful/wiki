# Honeycombs

Schema reconstructed from Resourceful Bees HoneycombSetup,
HoneycombRegistry, OutputVariation, tier codecs, TradeData, and
ItemStackTemplate usage.

## Example

``` json
{
  "honeycomb": {
    "name": "example",
    "color": "#ffffff",
    "edible": true,
    "block": true,
    "enchanted": false,
    "tradeData": {
      "amount": {
        "min": 1,
        "max": 1
      },
      "secondaryItem": "minecraft:air",
      "secondaryItemCost": {
        "min": 1,
        "max": 4
      },
      "priceMultiplier": 0.05,
      "maxTrades": 8,
      "xp": 3
    }
  },
  "variations": [
    {
      "identifier": "example",
      "hiveCombs": {
        "resourcefulbees:t1": {
          "id": "resourcefulbees:example_honeycomb",
          "count": 1
        },
        "resourcefulbees:t2": {
          "id": "resourcefulbees:example_honeycomb",
          "count": 1
        },
        "resourcefulbees:t3": {
          "id": "resourcefulbees:example_honeycomb",
          "count": 1
        },
        "resourcefulbees:t4": {
          "id": "resourcefulbees:example_honeycomb",
          "count": 1
        }
      },
      "apiaryCombs": {
        "resourcefulbees:t1": {
          "id": "resourcefulbees:example_honeycomb",
          "count": 1
        },
        "resourcefulbees:t2": {
          "id": "resourcefulbees:example_honeycomb",
          "count": 1
        },
        "resourcefulbees:t3": {
          "id": "resourcefulbees:example_honeycomb",
          "count": 1
        },
        "resourcefulbees:t4": {
          "id": "resourcefulbees:example_honeycomb",
          "count": 1
        }
      },
      "defaultComb": {
        "id": "resourcefulbees:example_honeycomb",
        "count": 1
      },
      "defaultCombBlock": {
        "id": "resourcefulbees:example_honeycomb_block",
        "count": 1
      }
    }
  ]
}
```

## Fields

  ---------------------------------------------------------------------------------------
  Field          Type                    Required       Default        Description
  -------------- ----------------------- -------------- -------------- ------------------
  `honeycomb`    honeycombRegistryData   No             ---            Honeycomb
                                                                       item/block
                                                                       registration data.
                                                                       The name field is
                                                                       read separately by
                                                                       HoneycombSetup to
                                                                       override the
                                                                       filename-derived
                                                                       honeycomb name;
                                                                       RegistryData
                                                                       itself receives
                                                                       that name as a
                                                                       codec point.

  `variations`   array                   No             `[]`           Output variations
                                                                       registered from
                                                                       this honeycomb
                                                                       file.
  ---------------------------------------------------------------------------------------

## Runtime notes

`tradeData` has an important omitted-vs-explicit distinction: omitting
the entire field uses the serializer's non-tradable zero-valued default,
while an explicit empty object uses the `TradeData` codec's normal field
defaults.

For output variations, `identifier` should be treated as required. Hive
comb mappings are normalized at runtime, and some apiary defaults depend
on configuration rather than JSON alone.

## Schema and template

The source files used for this page are included in the `reference/`
directory:

-   `resourcefulbees-honeycomb-template.json`
-   `resourcefulbees-honeycomb.schema.json`

> The schema is the machine-readable reference. Runtime notes document
> codec or game behavior that JSON Schema cannot fully express.
