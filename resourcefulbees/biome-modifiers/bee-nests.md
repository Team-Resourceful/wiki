# Bee Nest Biome Modifier

Schema reconstructed from BeeNestBiomeModifier, Biome.LIST_CODEC,
PlacedFeature.LIST_CODEC, RegistryCodecs, and HolderSetCodec.

## Example

```json
{
  "type": "resourcefulbees:nests",
  "biomes": "#minecraft:is_overworld",
  "features": [
    "resourcefulbees:oak_bee_nest",
    "resourcefulbees:birch_bee_nest"
  ]
}
```

## Fields

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `type` | string | Yes | `resourcefulbees:nests` | Biome modifier serializer identifier. |
| `biomes` | biomeHolderSet | Yes | — | Required biome holder set. May be a single biome ID, biome tag, list of biome IDs, or NeoForge custom holder-set object. |
| `features` | placedFeatureHolderSet | Yes | — | Required placed-feature holder set. May be a single placed-feature ID, placed-feature tag, list of placed-feature IDs, or NeoForge custom holder-set object. |

## Runtime notes

The modifier runs during the biome modifier `ADD` phase. Features are
only added when the current biome matches `biomes` **and** the biome
already has at least one Resourceful Bees bee spawn. Matching features
are added at the `VEGETAL_DECORATION` generation step.

## Schema and template

The source files used for this page are included in the `reference/`
directory:

-   `resourcefulbees-nest-biome-modifier-template.json`
-   `resourcefulbees-nest-biome-modifier.schema.json`

> The schema is the machine-readable reference. Runtime notes document
> codec or game behavior that JSON Schema cannot fully express.
