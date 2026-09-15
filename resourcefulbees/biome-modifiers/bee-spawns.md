# Bee Spawn Biome Modifier

Schema reconstructed from BeeBiomeModifier, ModBiomeModifiers, Weighted,
MobSpawnSettings.SpawnerData, LocationPredicate, RegistryCodecs,
HolderSetCodec, LightPredicate, BlockPredicate, FluidPredicate, and
MinMaxBounds.

## Example

```json
{
  "type": "resourcefulbees:spawns",
  "whitelist": "#minecraft:is_overworld",
  "blacklist": "minecraft:deep_dark",
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

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `type` | enum | Yes | — | One of `resourcefulbees:spawns`, `resourcefulbees:dev_spawns`, or `resourcefulbees:supporter_spawns`. |
| `whitelist` | biome holder set | Yes | — | Biomes in which this spawn may be added. Accepts a biome tag, a single biome ID, a list of biome IDs, or a custom NeoForge holder-set object. |
| `blacklist` | biome holder set | No | `[]` | Biomes excluded from spawning. Accepts the same holder-set forms as `whitelist`; the default empty holder set excludes no biomes. |
| `spawn` | spawn | Yes | — | Flattened weighted SpawnerData. Requires entity `type`, `minCount >= 1`, `maxCount >= 1`, and `weight >= 0`; runtime additionally requires `minCount <= maxCount`. |
| `spawnPredicate` | locationPredicate | No | — | Optional Minecraft LocationPredicate restricting where the spawn may occur. |

## Holder set forms

`whitelist` and `blacklist` are each a single biome holder set. A holder set may be a biome tag:

```json
"whitelist": "#minecraft:is_overworld"
```

A single biome ID:

```json
"blacklist": "minecraft:deep_dark"
```

Or a compact list of biome IDs:

```json
"whitelist": [
  "minecraft:plains",
  "minecraft:forest"
]
```

The array form is one holder set containing multiple individual biome holders; it is not a list of holder sets. Custom NeoForge holder-set dispatch objects are also accepted.

## Runtime notes

The modifier runs during the biome modifier `ADD` phase. A biome must
match the `whitelist` holder set and must not match the `blacklist`
holder set. `resourcefulbees:dev_spawns` and
`resourcefulbees:supporter_spawns` are additionally gated by their
respective configuration options.

`spawn.minCount` must be less than or equal to `spawn.maxCount`. This is
codec validation that Draft 2020-12 JSON Schema cannot express as a
direct comparison between sibling properties.

## Schema and template

The source files used for this page are included in the `reference/`
directory:

- `resourcefulbees-biome-modifier-template.json`
- `resourcefulbees-biome-modifier.schema.json`

> The schema is the machine-readable reference. Runtime notes document
> codec or game behavior that JSON Schema cannot fully express.
