# Bee Rendering Serializer

Serializer ID: `resourcefulbees:rendering/v1`

The rendering serializer controls the bee's model, base texture, animation, size, layered textures, and colors.

## Fields

| Field | Type | Required | Default | Range / accepted forms |
| --- | --- | --- | --- | --- |
| `layers` | array of layer objects | No | `[]` | Decoded as a linked set; each layer may define color, texture, effect, pollen behavior, pulse frequency, and a target bone. |
| `colors` | color-data object | No | all white | Spawn egg and jar colors. |
| `model` | resource identifier | No | `resourcefulbees:base` | Registered/model resource ID. |
| `texture` | layer texture string | No | missing texture | Short texture name expanded by Resourceful Bees. |
| `animation` | resource identifier | No | `resourcefulbees:bee` | Animation resource ID. |
| `sizeModifier` | float | No | `1.0` | `0.5` through `2.0`, inclusive. |

## Example

```json
{
  "resourcefulbees:rendering/v1": {
    "layers": [
      {
        "color": "#ffffff",
        "texture": "ruby_bee",
        "layerEffect": "GLOW",
        "isPollen": false,
        "pulseFrequency": 20.0,
        "bone": "body"
      },
      {
        "texture": "ruby_crystals",
        "layerEffect": "ENCHANTED",
        "bone": "crystals"
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

Each entry in `layers` uses the `LayerData` codec:

| Field | Type | Required | Default | Range / behavior |
| --- | --- | --- | --- | --- |
| `color` | ResourcefulLib color | No | white | Tint applied to the layer. |
| `texture` | layer texture string | No | missing texture | Texture used by the layer. |
| `layerEffect` | enum name or ordinal | No | `NONE` | `NONE`, `ENCHANTED`, or `GLOW`. |
| `isPollen` | boolean | No | `false` | Marks the layer as a pollen layer. |
| `pulseFrequency` | float | No | `0.0` | Explicit values must be `5.0` through `100.0`, inclusive. |
| `bone` | string | No | `"body"` | Bone targeted by effects that operate on a specific model bone. Currently used by `ENCHANTED`. |

`layerEffect` is backed by the `LayerEffect` enum. The current enum values are `NONE`, `ENCHANTED`, and `GLOW`. `EnumCodec` also accepts the enum's numeric representation.

### Enchanted bone targeting

For `ENCHANTED` layers, `bone` selects the model bone that receives the enchantment glint effect. It defaults to `"body"` when omitted.

This is useful when only part of a bee should glint. Crystal bees such as diamond, emerald, lapis, and redstone can target their `crystals` bone so the glint is applied to the crystals rather than the entire bee:

```json
{
  "texture": "diamond_crystals",
  "layerEffect": "ENCHANTED",
  "bone": "crystals"
}
```

The value is a model bone name, not a resource identifier. It therefore needs to match a bone defined by the selected model.

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

The `colors` object contains:

| Field | Type | Required | Default |
| --- | --- | --- | --- |
| `spawnEgg` | ResourcefulLib color | No | white |
| `jarColor` | ResourcefulLib color | No | white |

## `pulseFrequency` caveat

`pulseFrequency` belongs to each layer, not to the top-level rendering serializer. Omitting it resolves to `0.0`. Because an explicitly supplied value is decoded with `Codec.floatRange(5f, 100f)`, explicit values must be between `5.0` and `100.0`. Therefore `"pulseFrequency": 0` is rejected even though omission produces the default value `0.0`.
