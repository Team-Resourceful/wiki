# Holder Sets

Resourceful Bees uses Minecraft/NeoForge holder-set codecs anywhere a field needs to select entries from a registry. In the biome-modifier formats this includes biomes and placed features; the same holder-set concept may also appear with other registry types elsewhere in the mod.

This page is the shared reference for holder-set JSON shapes. Individual biome-modifier pages document which fields use holder sets and any field-specific runtime behavior rather than repeating these forms.

When `alwaysUseList` is false, the practical authoring forms are:

## Single registry entry

Use one registry identifier to select one entry:

```json
"minecraft:plains"
```

## Registry tag

Prefix a registry tag with `#` to select the entries in that tag:

```json
"#minecraft:is_overworld"
```

## Compact list

An array represents **one holder set containing multiple individual registry entries**:

```json
[
  "minecraft:plains",
  "minecraft:forest"
]
```

It is not a list of holder sets. An empty list is codec-valid, though it generally matches nothing.

## NeoForge custom holder set

NeoForge may dispatch custom holder-set implementations through an object with a registered `type` plus type-specific fields:

```json
{
  "type": "namespace:custom_holder_set"
}
```

The Resourceful Bees schemas keep these custom objects extensible because their fields depend on the registered holder-set type.

## Biome modifier fields

The current Resourceful Bees biome modifiers use these holder-set forms directly:

| Modifier | Field | Registry |
| --- | --- | --- |
| Bee Spawn | `whitelist` | Biome |
| Bee Spawn | `blacklist` | Biome |
| Bee Nest | `biomes` | Biome |
| Bee Nest | `features` | Placed Feature |

Each field in this table is **one holder set**. For example, a bee-spawn whitelist containing plains and forest is:

```json
"whitelist": [
  "minecraft:plains",
  "minecraft:forest"
]
```

See [Bee Spawns](bee-spawns.md) and [Bee Nests](bee-nests.md) for the required/default status and runtime semantics of those fields.
