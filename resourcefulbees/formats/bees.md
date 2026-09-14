# Bees

Resourceful Bees bee definitions are flat maps keyed by versioned
serializer IDs. The bee identifier itself is supplied externally by the
registry/loader rather than by a root `id` property.

## Example structure

``` json
{
  "resourcefulbees:core/v1": {
    "honeycombVariation": "ruby",
    "flower": "#minecraft:flowers",
    "maxTimeInHive": 2400,
    "lore": []
  },
  "resourcefulbees:combat/v1": {},
  "resourcefulbees:rendering/v1": {},
  "resourcefulbees:breeding/v1": {},
  "resourcefulbees:trait/v1": {},
  "resourcefulbees:trade/v1": {}
}
```

## Built-in serializer sections

  -----------------------------------------------------------------------
  Section                             Purpose
  ----------------------------------- -----------------------------------
  `resourcefulbees:core/v1`           Core bee properties, flower
                                      predicates, hive timing, and lore.

  `resourcefulbees:combat/v1`         Passive/aggressive behavior and
                                      entity attributes.

  `resourcefulbees:rendering/v1`      Layers, colors,
                                      texture/model/animation, and render
                                      sizing.

  `resourcefulbees:mutation/v1`       Mutation count and mutation
                                      identifier.

  `resourcefulbees:breeding/v1`       Parent families, feed items, feed
                                      return item, and breeding delays.

  `resourcefulbees:trait/v1`          Aura range and trait identifiers.

  `resourcefulbees:trade/v1`          Trade amount, costs, multiplier,
                                      limits, and XP.
  -----------------------------------------------------------------------

## Important codec behavior

Serializer keys are extensible, so third-party serializers may add
additional root keys.

`resourcefulbees:mutation/v1` has a required `mutation` identifier when
the section is explicitly present. Its `count` uses a positive integer
codec.

Rendering has a notable `pulseFrequency` behavior: omission produces the
codec default `0`, while an explicitly supplied value must be within the
codec's accepted `5` through `100` range.

Breeding family entries require `parent1` and `parent2`; the child bee
is injected from the bee being loaded rather than encoded in each family
entry.

## Status of this page

This page captures the bee codec structure established during the
reverse-engineering work. A bee template/schema pair was not present
among the mounted generated files when this documentation bundle was
produced, so this page is intentionally a starting reference rather than
an automatically generated field-by-field schema page.
