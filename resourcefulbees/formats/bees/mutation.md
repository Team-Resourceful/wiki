# Bee Mutation Serializer

Serializer ID: `resourcefulbees:mutation/v1`

This serializer connects a bee to a registered mutation definition and controls how many mutation rolls/uses are associated with that bee data.

## Fields

| Field | Type | Required | Default | Range / accepted forms |
| --- | --- | --- | --- | --- |
| `count` | integer | No | `10` | Positive integer (`>= 1`) when explicitly present. |
| `mutation` | resource identifier | **Yes** | none | Registered mutation identifier. |

## Example

```json
{
  "resourcefulbees:mutation/v1": {
    "count": 10,
    "mutation": "resourcefulbees:ruby_mutation"
  }
}
```

## Required-section behavior

The serializer itself has an internal default object used when the entire serializer section is absent, but that does **not** make `mutation` optional inside an explicitly written `resourcefulbees:mutation/v1` object. If you include the section, `mutation` must be present.

Likewise, the serializer-level default may contain zero-like values internally, while the explicit JSON codec for `count` is positive. Therefore `"count": 0` is invalid in an authored mutation section.
