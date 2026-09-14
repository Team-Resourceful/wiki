# Bee JSON Reference

Bee definitions are flat maps keyed by versioned serializer IDs. The bee identifier itself comes from the loader/file context rather than a root `id` field.

## Built-in serializers

| Serializer | Page | Purpose |
| --- | --- | --- |
| `resourcefulbees:core/v1` | [Core](core.md) | Pollination, honeycomb variation, hive timing, lore |
| `resourcefulbees:combat/v1` | [Combat](combat.md) | Combat behavior and attributes |
| `resourcefulbees:rendering/v1` | [Rendering](rendering.md) | Model, texture, animation, layers, colors, size |
| `resourcefulbees:mutation/v1` | [Mutation](mutation.md) | Mutation identifier and count |
| `resourcefulbees:breeding/v1` | [Breeding](breeding.md) | Parent families, feed items, delays |
| `resourcefulbees:trait/v1` | [Traits](traits.md) | Assigned traits and aura range |
| `resourcefulbees:trade/v1` | [Trade](trade.md) | Beekeeper trade configuration |

The root object allows additional properties so third-party serializers can extend bee data.

## Minimal structure

Because serializer sections may have defaults, a bee file can be very small. Add only the serializer sections needed for the bee's behavior.

```json
{
  "resourcefulbees:core/v1": {
    "flower": "minecraft:poppy"
  }
}
```

## Complete authoring example

See [`bee_template.json`](../../reference/bee_template.json) for a representative file containing all built-in serializer sections, and [`bee.schema.json`](../../reference/bee.schema.json) for the machine-readable constraints.
