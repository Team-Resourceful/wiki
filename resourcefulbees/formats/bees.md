# Bees

Resourceful Bees bee definitions are flat maps keyed by versioned serializer IDs. The bee identifier itself is supplied externally by the registry/loader rather than by a root `id` property.

The schema-driven format is the authoritative reference for field names, defaults, ranges, and accepted JSON shapes. The older wiki also contained useful authoring guidance, which is preserved here where it remains compatible with the current codec-based format.

## Getting started

Creating a custom bee starts with a correctly structured JSON file. Most customization options are optional and have defaults, so authors can begin with a small definition and add behavior, rendering, breeding, mutations, traits, and trading as needed.

A bee definition alone may not provide every part of a finished pack experience. Depending on the bee, you may also want custom textures, translations, models or animations, traits, mutations, honey/honeycombs, recipes, and biome modifiers.

For config-based authoring, the legacy documentation used these Resourceful Bees folders:

- `config/resourcefulbees/bees` — custom bee JSON
- `config/resourcefulbees/bee_traits` — custom traits
- `config/resourcefulbees/honey` — custom honey
- `config/resourcefulbees/honeycombs` — custom honeycombs
- `config/resourcefulbees/resources` — resource-pack-style assets such as language files

These data types can also be provided through datapack/resource-pack mechanisms where supported by the mod and pack setup.

## Built-in serializer sections

| Section | Purpose |
| --- | --- |
| `resourcefulbees:core/v1` | Core bee properties, flower predicates, hive timing, and lore. |
| `resourcefulbees:combat/v1` | Passive/aggressive behavior and entity attributes. |
| `resourcefulbees:rendering/v1` | Layers, colors, texture/model/animation, and render sizing. |
| `resourcefulbees:mutation/v1` | Mutation count and mutation identifier. |
| `resourcefulbees:breeding/v1` | Parent families, feed items, feed return item, and breeding delays. |
| `resourcefulbees:trait/v1` | Aura range and trait identifiers. |
| `resourcefulbees:trade/v1` | Trade amount, costs, reputation discount, limits, and XP. |

The Draft 2020-12 schema models these known serializer keys while deliberately allowing additional root properties so third-party serializers remain possible.

## Core data

The core section controls the bee's honeycomb variation, pollination targets, hive timing, and lore.

```json
"resourcefulbees:core/v1": {
  "honeycombVariation": "diamond",
  "flower": "#minecraft:flowers",
  "entityFlower": [],
  "maxTimeInHive": 2400,
  "lore": []
}
```

`flower` and `entityFlower` accept registry-predicate forms: a single registry ID, a `#tag`, or a list of registry IDs. `maxTimeInHive` has a minimum of `600` and defaults to `2400`. Lore is a list of Minecraft text components and is useful for JEI/tooltips, hints, attribution, or flavor text.

## Language files

Custom content benefits from translations instead of exposing raw translation keys in-game. Under a config resource pack, language files can live under:

`config/resourcefulbees/resources/assets/resourcefulbees/lang`

For English (US), create `en_us.json`. A typical custom bee might use entries such as:

```json
{
  "block.resourcefulbees.blaze_honeycomb_block": "Blaze Honeycomb Block",
  "item.resourcefulbees.blaze_honeycomb": "Blaze Honeycomb",
  "item.resourcefulbees.blaze_spawn_egg": "Blaze Bee Spawn Egg",
  "entity.resourcefulbees.blaze_bee": "Blaze Bee"
}
```

Keep one language file per language and add new keys to it as more custom content is added. Asset reload (`F3+T`) or a restart can be used after changing resource-pack assets.

## Important codec behavior

`resourcefulbees:mutation/v1` requires a `mutation` identifier when that section is explicitly present, and its `count` uses a positive integer codec.

Rendering has a notable `pulseFrequency` behavior: omission produces the codec default `0`, while an explicitly supplied value must be within the codec's accepted `5` through `100` range.

Breeding family entries require `parent1` and `parent2`; the child bee is injected from the bee being loaded rather than encoded in each family entry.

## Machine-readable reference

The complete authoring template and JSON Schema live in the [`reference`](../reference/README.md) directory. Use the schema as the authoritative field/type reference and this page for authoring and runtime behavior that JSON Schema cannot fully express.
