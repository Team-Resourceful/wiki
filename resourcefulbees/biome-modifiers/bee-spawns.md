# Bee Spawn Biome Modifier

Schema reconstructed from BeeBiomeModifier, ModBiomeModifiers, Weighted,
MobSpawnSettings.SpawnerData, LocationPredicate, RegistryCodecs,
HolderSetCodec, LightPredicate, BlockPredicate, FluidPredicate, and
MinMaxBounds.

## Example

``` json
{
  "type": "resourcefulbees:spawns",
  "whitelist": [
    "#minecraft:is_overworld"
  ],
  "blacklist": [
    "minecraft:deep_dark"
  ],
  "spawn": {
    "type": "resourcefulbees:ruby_bee",
    "minCount": 1,
    "maxCount": 3,
    "weight": 10
  },
  "spawnPredicate": {
    "position": {
      "y": {
        "min": 60.0,
        "max": 128.0
      }
    },
    "biomes": "#minecraft:is_overworld",
    "dimension": "minecraft:overworld",
    "smokey": false,
    "light": {
      "light": {
        "min": 8
      }
    },
    "block": {
      "blocks": [
        "minecraft:grass_block",
        "minecraft:dirt"
      ]
    },
    "fluid": {
      "fluids": "minecraft:water"
    },
    "can_see_sky": true
  }
}
```

## Fields

  -----------------------------------------------------------------------------------
  Field              Type                Required       Default        Description
  ------------------ ------------------- -------------- -------------- --------------
  `type`             enum                Yes            ---            ---

  `whitelist`        array               Yes            ---            Required list
                                                                       of biome
                                                                       holder sets.
                                                                       An empty list
                                                                       is codec-valid
                                                                       but matches no
                                                                       biomes.

  `blacklist`        array               No             `[]`           ---

  `spawn`            spawn               Yes            ---            SpawnerData
                                                                       requires
                                                                       minCount \<=
                                                                       maxCount.
                                                                       Draft 2020-12
                                                                       cannot
                                                                       directly
                                                                       compare
                                                                       sibling
                                                                       numeric
                                                                       properties, so
                                                                       that codec
                                                                       validation is
                                                                       documented
                                                                       rather than
                                                                       enforced here.

  `spawnPredicate`   locationPredicate   No             ---            ---
  -----------------------------------------------------------------------------------

## Runtime notes

The modifier runs during the biome modifier `ADD` phase. A biome must
match at least one `whitelist` holder set and none of the `blacklist`
holder sets. `resourcefulbees:dev_spawns` and
`resourcefulbees:supporter_spawns` are additionally gated by their
respective configuration options.

`spawn.minCount` must be less than or equal to `spawn.maxCount`. This is
codec validation that Draft 2020-12 JSON Schema cannot express as a
direct comparison between sibling properties.

## Schema and template

The source files used for this page are included in the `reference/`
directory:

-   `resourcefulbees-biome-modifier-template.json`
-   `resourcefulbees-biome-modifier.schema.json`

> The schema is the machine-readable reference. Runtime notes document
> codec or game behavior that JSON Schema cannot fully express.
