# Bee Rendering Serializer

Serializer ID: `resourcefulbees:rendering/v1`

The rendering serializer controls the bee's model, base texture, animation, size, layered textures, colors, and pulse behavior.

## Fields

| Field | Type | Required | Default | Range / accepted forms |
| --- | --- | --- | --- | --- |
| `layers` | array of layer objects | No | `[]` | Each layer may define color, texture, effect, and pollen behavior. |
| `colors` | color-data object | No | all white | Spawn egg and jar colors. |
| `model` | resource identifier | No | `resourcefulbees:base` | Registered/model resource ID. |
| `texture` | layer texture string | No | omitted | Short texture name expanded by Resourceful Bees. |
| `animation` | resource identifier | No | `resourcefulbees:bee` | Animation resource ID. |
| `sizeModifier` | number | No | `1.0` | `0.5` through `2.0`. |
| `pulseFrequency` | number | No | special omitted default `0.0` | If explicitly present: `5.0` through `100.0`. |

## Example

```json
{
  "resourcefulbees:rendering/v1": {
    "layers": [
      {
        "color": "#ffffff",
        "texture": "ruby_bee",
        "layerEffect": "GLOW",
        "isPollen": false
      }
    ],
    "colors": {
      "spawnEgg": "#c62828",
      "jarColor": "#e53935"
    },
    "model": "resourcefulbees:base",
    "texture": "ruby_bee",
    "animation": "resourcefulbees:bee",
    "sizeModifier": 1.0
  }
}
```

## Layer objects

Each layer accepts:

| Field | Type | Required | Default |
| --- | --- | --- | --- |
| `color` | ResourcefulLib color | No | `#ffffff` |
| `texture` | short texture string | No | omitted |
| `layerEffect` | enum name or ordinal | No | `NONE` |
| `isPollen` | boolean | No | `false` |

`layerEffect` accepts the names `NONE`, `ENCHANTED`, `GLOW`, and `TRANSLUCENT` case-insensitively. Numeric ordinals `0` through `3` are also accepted by the enum codec.

## Texture strings

A layer texture is not a full texture resource path. Resourceful Bees expands a short name under its bee entity texture directory and derives both normal and angry texture paths. For example:

```json
"texture": "ruby_bee"
```

or a nested short path such as:

```json
"texture": "bees/ruby_bee"
```

## Colors

ResourcefulLib colors accept numbers, strings such as `#ffffff`, registered special color names such as `rainbow`, or RGBA objects.

```json
{
  "r": 255,
  "g": 0,
  "b": 0,
  "a": 255
}
```

The color-data object controls spawn-egg and jar coloring. Use the JSON Schema in `reference/bee.schema.json` as the authoritative shape for the current version.

## `pulseFrequency` caveat

This field has intentionally unusual codec behavior. Omitting it produces the codec's special default value `0.0`. If it is explicitly present, the accepted range is `5.0` to `100.0`. Therefore `"pulseFrequency": 0` is not equivalent to omitting the field and is rejected by the explicit-value codec.
