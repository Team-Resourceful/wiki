# Bee Breeding Serializer

Serializer ID: `resourcefulbees:breeding/v1`

The breeding serializer controls valid parent combinations, breeding feed items, optional returned feed containers/items, and breeding/growth delays.

## Fields

| Field | Type | Required | Default | Range / accepted forms |
| --- | --- | --- | --- | --- |
| `families` | array of family objects | No | `[]` | Each family requires `parent1` and `parent2`. |
| `feedItems` | registry predicate of items | No | `minecraft:poppy` | Item ID, `#tag`, or list of item IDs. |
| `feedReturnItem` | item stack template | No | omitted | Compact item ID or expanded item object. |
| `feedAmount` | integer | No | `1` | Positive integer (`>= 1`). |
| `childGrowthDelay` | integer | No | `-24000` | Must be `<= 0`. |
| `breedDelay` | integer | No | `6000` | Must be `>= 0`. |

## Example

```json
{
  "resourcefulbees:breeding/v1": {
    "families": [
      {
        "weight": 10.0,
        "chance": 1.0,
        "parent1": "resourcefulbees:ruby_bee",
        "parent2": "minecraft:bee"
      }
    ],
    "feedItems": "minecraft:poppy",
    "feedReturnItem": {
      "id": "minecraft:bucket",
      "count": 1
    },
    "feedAmount": 1,
    "childGrowthDelay": -24000,
    "breedDelay": 6000
  }
}
```

## Family objects

| Field | Type | Required | Default | Range |
| --- | --- | --- | --- | --- |
| `weight` | number | No | `10.0` | `>= 0` |
| `chance` | number | No | `1.0` | `0.0` through `1.0` |
| `parent1` | resource identifier | **Yes** | none | Bee identifier |
| `parent2` | resource identifier | **Yes** | none | Bee identifier |

The child is **not** encoded in each family object. Resourceful Bees injects the child identifier from the bee file currently being loaded.

## Feed predicates

`feedItems` uses the same compact registry-predicate forms as other Resourceful Bees fields:

```json
"minecraft:poppy"
```

```json
"#minecraft:flowers"
```

```json
[
  "minecraft:poppy",
  "minecraft:dandelion"
]
```

## Item stack templates

An item stack template can be a compact item identifier:

```json
"minecraft:bucket"
```

or an expanded object:

```json
{
  "id": "minecraft:bucket",
  "count": 1,
  "components": {}
}
```

Expanded objects require `id`. `count` defaults to `1` and must be from `1` through `99`. `components` defaults to an empty component patch and remains registry-extensible.
