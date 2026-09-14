# Bee Trait Serializer

Serializer ID: `resourcefulbees:trait/v1`

The bee trait serializer assigns reusable trait definitions to a bee and controls the range used by aura-style behavior.

## Fields

| Field | Type | Required | Default | Range / accepted forms |
| --- | --- | --- | --- | --- |
| `auraRange` | integer | No | `10` | `3` through `20` |
| `traits` | array of strings | No | `[]` | Trait identifiers/names |

## Example

```json
{
  "resourcefulbees:trait/v1": {
    "auraRange": 10,
    "traits": [
      "resourcefulbees:fireproof"
    ]
  }
}
```

The standalone custom-trait JSON format is documented separately under [Traits](../traits.md). This serializer only assigns those traits to a bee.
