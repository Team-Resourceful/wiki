# Holder Sets

Resourceful Bees biome modifiers use Minecraft/NeoForge holder-set codecs for biomes, structures, blocks, fluids, placed features, and—in recipe contexts—entities.

When `alwaysUseList` is false, the practical authoring forms are:

## Single registry entry

```json
"minecraft:plains"
```

## Registry tag

```json
"#minecraft:is_overworld"
```

## Compact list

```json
[
  "minecraft:plains",
  "minecraft:forest"
]
```

An empty list is codec-valid, though it generally matches nothing.

## NeoForge custom holder set

NeoForge may dispatch custom holder-set implementations through an object with a registered `type` plus type-specific fields:

```json
{
  "type": "namespace:custom_holder_set"
}
```

The Resourceful Bees schemas keep these custom objects extensible because their fields depend on the registered holder-set type.

## Important nesting distinction

`BeeBiomeModifier.whitelist` and `blacklist` are **lists of holder sets**, not just one holder set. Therefore:

```json
"whitelist": [
  "minecraft:plains",
  "minecraft:forest"
]
```

is two holder sets, each containing one biome, while:

```json
"whitelist": [
  ["minecraft:plains", "minecraft:forest"]
]
```

is one holder set containing two biomes.

For simple membership tests the runtime result may be equivalent, but the serialized structures are different.

`BeeNestBiomeModifier.biomes` and `features`, by contrast, are each a **single holder set**.
