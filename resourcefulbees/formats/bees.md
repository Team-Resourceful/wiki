# Bees

Resourceful Bees bee definitions are flat maps keyed by versioned serializer IDs. The bee identifier itself is supplied externally by the registry/loader rather than by a root `id` property.

The current machine-readable template confirms the built-in sections and their representative defaults, including core hive timing and lore, combat attributes, rendering data, mutation data, breeding, traits, and trades. fileciteturn3file0L2-L7

## Built-in serializer sections

| Section | Purpose |
| --- | --- |
| `resourcefulbees:core/v1` | Core bee properties, flower predicates, hive timing, and lore. |
| `resourcefulbees:combat/v1` | Passive/aggressive behavior and entity attributes. |
| `resourcefulbees:rendering/v1` | Layers, colors, texture/model/animation, and render sizing. |
| `resourcefulbees:mutation/v1` | Mutation count and mutation identifier. |
| `resourcefulbees:breeding/v1` | Parent families, feed items, feed return item, and breeding delays. |
| `resourcefulbees:trait/v1` | Aura range and trait identifiers. |
| `resourcefulbees:trade/v1` | Trade amount, costs, multiplier, limits, and XP. |

The Draft 2020-12 schema models these known serializer keys while deliberately allowing additional root properties so third-party serializers remain possible. fileciteturn3file1L2-L30

## Important codec behavior

`resourcefulbees:mutation/v1` requires a `mutation` identifier when that section is explicitly present, and its `count` uses a positive integer codec.

Rendering has a notable `pulseFrequency` behavior: omission produces the codec default `0`, while an explicitly supplied value must be within the codec's accepted `5` through `100` range.

Breeding family entries require `parent1` and `parent2`; the child bee is injected from the bee being loaded rather than encoded in each family entry.

## Machine-readable reference

The complete authoring template and JSON Schema live in the [`reference`](../reference/README.md) directory. Use the schema as the authoritative field/type reference and this page for the codec/runtime behavior that JSON Schema cannot express.
