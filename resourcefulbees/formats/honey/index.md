# Custom Honey JSON Reference

Custom honey data is a flat serializer map. The honey name and registered content identifiers are derived from the filename rather than root or serializer-level item/block identifier fields.

## Built-in serializers

| Serializer | Required | Page | Purpose |
| --- | --- | --- | --- |
| `resourcefulbees:block/v1` | No | [Block](block.md) | Honey block behavior, color, and trades; block and block-item registrations are filename-derived |
| `resourcefulbees:fluid/v1` | No | [Fluid](fluid.md) | Fluid rendering, attributes, trades |
| `resourcefulbees:bottle/v1` | **Yes** | [Bottle](bottle.md) | Bottle color, food properties, rarity, and trades; bottle-item registration is filename-derived |

The root remains extensible so additional serializers can be registered.

## Minimal valid file

```json
{
  "resourcefulbees:bottle/v1": {}
}
```

## Generated registry names

For a honey named `ruby`, Resourceful Bees derives registrations such as:

- `ruby_honey_block`
- `ruby_honey_bottle`
- `ruby_honey`
- `ruby_honey_fluid_source`
- `ruby_honey_fluid_flowing`
- `ruby_honey_bucket`
- `ruby_honey_fluid_block`

Because these registrations are derived from the filename, the block serializer does not accept separate block/block-item identifiers and the bottle serializer does not accept a separate bottle-item identifier.

Use [`resourcefulbees-honey-template.json`](../../reference/resourcefulbees-honey-template.json) and [`resourcefulbees-honey.schema.json`](../../reference/resourcefulbees-honey.schema.json) for the complete machine-readable reference.
