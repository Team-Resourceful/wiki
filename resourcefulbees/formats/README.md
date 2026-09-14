# JSON Formats Overview

Resourceful Bees uses several top-level JSON formats for defining reusable game content. The four primary formats documented here are **Bees**, **Honeys**, **Traits**, and **Honeycombs**. Each format has its own loader behavior and nested data structure, but they are designed to work together: bees can reference honeycomb variations and traits, while honey and honeycomb definitions provide reusable outputs and content shared across multiple bees.

## Bees

[Bee definitions](bees/index.md) describe the behavior, appearance, breeding, mutation, traits, and trade configuration of a custom bee.

Bee JSON is a flat map of versioned serializer IDs rather than a single monolithic object. Built-in sections include:

- `resourcefulbees:core/v1` for pollination targets, hive timing, lore, and honeycomb variation
- `resourcefulbees:combat/v1` for aggression and entity attributes
- `resourcefulbees:rendering/v1` for layers, colors, models, textures, animation, and size
- `resourcefulbees:mutation/v1` for mutation output configuration
- `resourcefulbees:breeding/v1` for breeding families, feed items, and delays
- `resourcefulbees:trait/v1` for attaching standalone traits and configuring aura range
- `resourcefulbees:trade/v1` for beekeeper trade configuration

The bee identifier itself is supplied by the loader/file context rather than by a root JSON `id` field. Serializer sections are largely optional unless the specific serializer codec requires a field when that section is present.

## Honeys

[Honey definitions](honey/index.md) configure the block, fluid, and bottled forms associated with a custom honey.

Honey JSON is also a versioned serializer map. The built-in sections are:

- `resourcefulbees:block/v1` for honey-block properties such as color, movement factors, replacement block/item, and trade data
- `resourcefulbees:fluid/v1` for fluid rendering, physical attributes, sounds, rarity, and trade data
- `resourcefulbees:bottle/v1` for bottled-honey color, food behavior, potion effects, rarity, replacement item, and trade data

The bottle serializer is required by the current schema; block and fluid serializers are optional. The honey identifier/name comes from the file context rather than a root `name` field.

## Traits

[Standalone trait definitions](traits/index.md) describe reusable behavior that can be attached to bees through the bee trait serializer.

Trait JSON can configure:

- the display item
- potion-based damage effects
- damage immunities
- potion immunities
- custom damage-type entries
- special abilities
- particles
- one or more auras

Most top-level trait fields are optional and default to empty collections or codec-defined defaults. Trait files are reusable: multiple bees can reference the same trait identifier rather than duplicating the behavior in each bee definition.

## Honeycombs

[Honeycomb definitions](honeycombs/index.md) configure registered honeycomb content and the output variations used by bees and hive/apiary processing.

A honeycomb file can contain two major sections:

- `honeycomb` for registration properties such as name override, color, edible/block/enchanted flags, and trade data
- `variations` for reusable output mappings, including hive-tier outputs, apiary-tier outputs, a default comb, and a default comb block

Both sections are optional at the top-level codec, and `variations` defaults to an empty list. Honeycomb variation identifiers are what bee core data uses through `honeycombVariation`.

## How the formats relate

A typical custom-content setup may use all four formats together:

1. Define a **Honeycomb** and one or more output variations.
2. Optionally define a reusable **Honey** with block, fluid, and bottle behavior.
3. Define reusable **Traits** for special bee behavior.
4. Define the **Bee**, referencing the honeycomb variation and any traits it should use.

Recipes and biome modifiers are documented separately because they are datapack-style integration formats rather than primary content-registration files.

## Detailed reference

Use the child pages in this section for field-level documentation, including required/optional status, defaults, ranges, accepted compact forms, and runtime/codec caveats. Machine-readable templates and Draft 2020-12 schemas are available in the [JSON Schemas and Templates](../reference/README.md) section.
