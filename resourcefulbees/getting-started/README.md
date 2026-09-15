# Getting Started

Resourceful Bees is designed around data-driven content. A custom bee is not one giant JSON object that must define everything at once; instead, the mod separates reusable content into several formats and lets those pieces work together.

This site documents those formats, the supporting recipes and biome modifiers, and the machine-readable schemas/templates you can use while authoring custom content.

## Start here

If you are creating your first custom bee, a good workflow is:

1. **Create the bee definition first.** Start small and rely on defaults where they fit your design.
2. **Add a honeycomb variation** if the bee should produce custom comb output.
3. **Add reusable traits** if the bee needs special effects, immunities, particles, auras, or other trait behavior.
4. **Add custom honey** if you want a reusable block, fluid, or bottled-honey definition.
5. **Add recipes** for machine processing or other datapack-driven integrations.
6. **Add biome modifiers** if the bee or its nest should participate in world generation or natural spawning.
7. **Validate against the schemas/templates** and then test the content in-game.

Most customization is optional. The codecs provide defaults for many fields, so it is usually easier to begin with the smallest definition that expresses your idea and add complexity incrementally.

## How Resourceful Bees content is structured

The four primary top-level content formats are independent but designed to reference one another.

### Bees

Bee definitions control the bee itself: pollination targets, hive behavior, combat attributes, rendering, breeding, mutation behavior, attached traits, and trades.

Bee JSON is a flat map of versioned serializer sections such as:

- `resourcefulbees:core/v1`
- `resourcefulbees:combat/v1`
- `resourcefulbees:rendering/v1`
- `resourcefulbees:mutation/v1`
- `resourcefulbees:breeding/v1`
- `resourcefulbees:trait/v1`
- `resourcefulbees:trade/v1`

The bee identifier comes from the file/loader context rather than a root `id` field.

### Honeycombs

Honeycomb definitions describe registered honeycomb content and output variations. A variation can define hive-tier and apiary-tier outputs plus default comb/block fallbacks.

The important relationship for bee authors is that a bee's core serializer can reference a honeycomb variation through `honeycombVariation`.

### Traits

Standalone traits are reusable behavior definitions. They can contain potion or damage effects, immunities, custom damage entries, special abilities, particles, and auras.

A bee attaches these reusable definitions through its trait serializer, so the same trait can be shared by multiple bees.

### Honeys

Honey definitions configure reusable block, fluid, and bottled forms. Like bees, honey uses versioned serializer sections. The built-in serializers cover block behavior, fluid rendering/physical attributes, and bottled-honey behavior.

## Site map

The site is divided into four reference areas after this landing section:

- **Formats** — field-level documentation for Bees, Honeycombs, Honeys, and Traits.
- **Recipes** — mutation, solidification, hive, flow-hive, and honey-generator recipes, plus shared nested recipe types.
- **Biome Modifiers** — bee spawning, nest placement, holder sets, and spawn predicates.
- **JSON Schemas and Templates** — machine-readable Draft 2020-12 schemas and starter JSON templates.

Use the human-readable pages to understand intent and runtime behavior. Use the schema/template section when you need exact field names, types, required fields, ranges, and accepted JSON shapes.

## Authoring directory structure

For pack authors using the Resourceful Bees config-folder workflow, the custom-content layout is organized by content type:

```text
<instance>/
└── config/
    └── resourcefulbees/
        ├── bees/
        │   └── <bee>.json
        ├── honeycombs/
        │   └── <honeycomb>.json
        ├── honey/
        │   └── <honey>.json
        ├── bee_traits/
        │   └── <trait>.json
        └── resources/
            └── assets/
                └── resourcefulbees/
                    └── lang/
                        └── en_us.json
```

The `resources` directory behaves like resource-pack content and is where supporting client assets such as language files can be placed. Textures, models, and animations can also be used to customize a bee's appearance when the corresponding rendering data references them.

Resourceful Bees content can also participate in datapacks. Recipes and biome modifiers are datapack-style integrations, while the primary bee/honey/honeycomb/trait definitions are documented separately because their loaders and registration behavior are distinct. Exact datapack directory conventions can depend on the Minecraft/NeoForge version, so this reference focuses on the JSON contracts rather than guessing version-specific pack paths.

## A practical custom-bee development loop

A reliable way to build custom bees is to treat each change as a small, testable layer:

### 1. Pick stable identifiers

Choose a short, consistent name for the bee and for related content. Keep those identifiers consistent across bee definitions, honeycomb variations, traits, recipes, textures, and translations.

### 2. Build the minimum bee

Start from the Bee template/schema and add only the serializer sections you actually need. Many fields have useful defaults; omitting a field is often better than copying a value you do not intend to customize.

### 3. Add production output

If the bee should produce a custom comb, define the honeycomb/variation and reference that variation from the bee's core serializer. Keep hive/apiary output mapping separate from the bee itself so it can be reused or changed independently.

### 4. Add appearance

Use the rendering serializer for layers, colors, textures, models, animations, and size. Add resource-pack assets only when you need something beyond the provided/default resources.

### 5. Add behavior in layers

Use the dedicated serializer for the concern you are changing:

- combat for aggression and attributes
- breeding for parents, feed items, and delays
- mutation for bee mutation configuration
- traits for reusable special behavior
- trade for beekeeper trade configuration

Keeping concerns in their own serializer sections makes definitions easier to debug and maintain.

### 6. Add integration content last

Once the bee itself works, add machine recipes, spawning rules, or nest placement. This makes it easier to tell whether a problem comes from the bee definition or from the integration layer.

### 7. Validate, reload, test

Before launching or reloading the pack, compare the JSON with the corresponding schema/template. Pay particular attention to:

- required fields inside serializer sections
- numeric ranges
- compact string forms versus expanded object forms
- registry identifiers and tags
- fields whose omitted value behaves differently from an explicitly empty object

Then test one behavior at a time in-game.

## Important authoring concepts

### Omitted fields are meaningful

Many codecs provide defaults. If the default is what you want, leaving a field out is usually clearer than specifying it redundantly. Some nested objects also have a meaningful distinction between being omitted and being explicitly present as `{}`; the detailed pages call these cases out.

### Reuse definitions instead of copying them

Honeycombs, honeys, and traits are intentionally reusable. If several bees share an effect or output, prefer one reusable definition referenced by multiple bees rather than duplicating the same data everywhere.

### Registry IDs and tags are different tools

Many fields accept registry identifiers, tags, holder sets, or other compact codec forms. A tag such as `#minecraft:is_overworld` represents a registry tag rather than one specific entry. Check the relevant field page before assuming a list accepts tags, IDs, or both.

### Codec-valid does not always mean gameplay-useful

The documentation distinguishes between what a codec can deserialize and what makes sense at runtime. For example, an empty list may sometimes be structurally valid even when it produces no useful gameplay behavior. Runtime caveats are documented separately from schema constraints where necessary.

## Where to go next

- Open **Formats** to begin defining Bees, Honeycombs, Honeys, or Traits.
- Open **Recipes** after the core content is working and you want machine/process integration.
- Open **Biome Modifiers** for natural bee spawning or nest world generation.
- Open **JSON Schemas and Templates** whenever you want a copyable starting point or machine-readable validation reference.

For a first custom bee, start with the **Bee** format and keep the initial definition small. Add honeycomb output, rendering, traits, recipes, and spawning only as your design needs them.
