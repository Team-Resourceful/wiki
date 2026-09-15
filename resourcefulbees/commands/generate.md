# Generate Commands

The `generate` command group creates supplemental JSON from the currently loaded Resourceful Bees registries.

All executable `generate` subcommands require gamemaster command permission.

## Recipe generators

### Honeycomb crafting recipes

```text
/resourcefulbees generate recipe honeycomb
```

Writes crafting recipes beneath:

```text
config/resourcefulbees/resources/data/resourcefulbees/recipe/crafting/
```

For every custom honeycomb that has a usable storage-block item, the command generates both directions:

- four honeycombs in a 2x2 shaped recipe -> one honeycomb block
- one honeycomb block -> four honeycombs

Honeycombs without a storage-block item, or whose resolved storage item is `minecraft:air`, are skipped.

### Honey crafting recipes

```text
/resourcefulbees generate recipe honey
```

Writes crafting recipes to the same `recipe/crafting/` directory. For each registered honey, recipes are generated when the required bottle, bucket, and/or block items exist.

Possible conversions are:

| Conversion | Generated filename |
| --- | --- |
| 4 honey bottles -> honey block | `<honey>_honey_block.json` |
| honey block + 4 glass bottles -> 4 honey bottles | `<honey>_honey_bottle.json` |
| bucket + 4 honey bottles -> honey bucket | `<honey>_bottle_to_bucket.json` |
| honey bucket + 4 glass bottles -> 4 honey bottles | `<honey>_bucket_to_bottle.json` |
| honey block + bucket -> honey bucket | `<honey>_block_to_bucket.json` |
| honey bucket -> honey block | `<honey>_bucket_to_block.json` |

A conversion is skipped when one of the required generated items resolves to `minecraft:air`.

### Breeder recipes

```text
/resourcefulbees generate recipe breeder
```

Writes recipes beneath:

```text
config/resourcefulbees/resources/data/resourcefulbees/recipe/breeder/
```

The generator walks the loaded bee family tree and builds breeder recipes from the registered family data. Recipes are encoded through `BreederRecipe.MAP_CODEC` with registry-aware JSON operations, which allows the generated child bee jars and other item-stack data components to be serialized after registries are available.

Generated filenames use:

```text
<parent1>_<parent2>_<child>.json
```

The serializer ID `resourcefulbees:breeder` is added to each generated recipe. See [Breeder Recipe](../recipes/breeder.md) for the resulting format and [Bee Jar Ingredient](../recipes/bee-jar-ingredient.md) for entity-specific parent matching.

This command is especially important for generated breeder recipes because their bee-jar item stacks contain bound data components that are not available early enough to safely synthesize during datapack discovery.

### Solidification chamber recipes

```text
/resourcefulbees generate recipe chamber
```

Writes recipes beneath:

```text
config/resourcefulbees/resources/data/resourcefulbees/recipe/solidification/
```

For each registered honey with a usable honey-block item, the generator creates a `resourcefulbees:solidification` recipe using:

- 1000 units of that honey's still fluid
- the honey block item as the result
- a processing time of `200`

The filename is `<honey>_honey_block.json`. Honeys whose block item resolves to `minecraft:air` are skipped. See [Solidification](../recipes/solidification.md) for the recipe format.

## Beekeeper trade generator

```text
/resourcefulbees generate trade beekeeper
```

Generates dynamic level-3 and level-5 Beekeeper villager trades plus the corresponding trade tags.

Level-3 generated trade files are written beneath:

```text
config/resourcefulbees/resources/data/resourcefulbees/villager_trade/beekeeper/3/
```

The command considers tradable custom honey bottles, honey buckets, honey blocks, and honeycomb items. Their configured `tradeData` controls result count, optional secondary cost, max trades, XP, and reputation discount. The primary cost is Gold Flowers with a uniform amount from 8 through 16.

The level-3 tag is written to:

```text
config/resourcefulbees/resources/data/resourcefulbees/tags/villager_trade/beekeeper/level_3.json
```

It also includes the four static Resourceful Bees trades for vanilla honeycomb, honey bottle, honey bucket, and honey block.

Level-5 generated trade files are written beneath:

```text
config/resourcefulbees/resources/data/resourcefulbees/villager_trade/beekeeper/5/
```

Each tradable custom bee produces a bee-jar result containing that bee. The primary Gold Flower cost uses a uniform amount from 32 through 64, while the bee's `tradeData` supplies the other trade settings. This runtime generation is needed because the result jar carries bee-specific item-stack data components.

The level-5 tag is written to:

```text
config/resourcefulbees/resources/data/resourcefulbees/tags/villager_trade/beekeeper/level_5.json
```

and includes the static `resourcefulbees:beekeeper/5/queen_bee_banner` trade in addition to generated bee trades.

Only entries whose trade data is marked tradable are generated. Honey products resolving to `minecraft:air` are also skipped.

## Language generator

```text
/resourcefulbees generate lang
```

Generates an English `en_us.json` from the currently registered bees, honeys, honeycombs, traits, and generated Resourceful Bees registry objects. Identifier paths are converted from underscore-separated names to title-cased display strings.

Unlike the recipe and trade generators, this command uses the mod's resource path and writes under:

```text
assets/resourcefulbees/lang/en_us.json
```

It is primarily a development/content-authoring convenience rather than a datapack data generator.