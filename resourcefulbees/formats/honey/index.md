# Custom Honey JSON Reference

Custom honey data is a flat serializer map. The honey name is derived from the filename rather than a root `name` property.

## Built-in serializers

| Serializer | Required | Page | Purpose |
| --- | --- | --- | --- |
| `resourcefulbees:block/v1` | No | [Block](block.md) | Honey block behavior, color, backing item/block, trades |
| `resourcefulbees:fluid/v1` | No | [Fluid](fluid.md) | Fluid rendering, attributes, trades |
| `resourcefulbees:bottle/v1` | **Yes** | [Bottle](bottle.md) | Bottle color, food properties, rarity, item, trades |

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

Use [`resourcefulbees-honey-template.json`](../../reference/resourcefulbees-honey-template.json) and [`resourcefulbees-honey.schema.json`](../../reference/resourcefulbees-honey.schema.json) for the complete machine-readable reference.
