# Bee Core Serializer

Serializer ID: `resourcefulbees:core/v1`

The core serializer controls a bee's produced honeycomb variation, pollination targets, hive timing, and lore.

## Fields

| Field | Type | Required | Default | Range / accepted forms |
| --- | --- | --- | --- | --- |
| `honeycombVariation` | string | No | `""` | Honeycomb variation identifier/name. Empty means no variation. |
| `flower` | registry predicate of blocks | No | `minecraft:poppy` | A block ID, `#tag`, or list of block IDs. |
| `entityFlower` | registry predicate of entity types | No | empty predicate (`[]`) | An entity ID, `#tag`, or list of entity IDs. |
| `maxTimeInHive` | integer | No | `2400` | `600` through `2147483647`. |
| `lore` | array of Minecraft Components | No | `[]` | Each entry may be a string, non-empty component list, or component object. |

## Example

```json
{
  "resourcefulbees:core/v1": {
    "honeycombVariation": "ruby",
    "flower": "#minecraft:flowers",
    "entityFlower": [],
    "maxTimeInHive": 2400,
    "lore": [
      "A warm, gem-like bee."
    ]
  }
}
```

## `honeycombVariation`

This value selects the output variation used when the bee produces honeycombs. The codec default is an empty string.

## `flower` and `entityFlower`

Both fields use Resourceful Bees' registry-predicate codec. Accepted compact forms are:

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

`flower` targets blocks. `entityFlower` uses the same syntax for entity types.

## `maxTimeInHive`

This is the base hive residence time before tier modifiers are applied. Values lower than `600` are rejected by the codec.

## `lore`

Lore is a list of Minecraft chat components. Plain strings are valid, so simple lore does not need the expanded component-object syntax.

```json
"lore": [
  "First line",
  {
    "text": "Second line",
    "italic": false
  }
]
```

See [Common JSON Types](../../common-types.md) for shared identifier and compact-collection conventions.
