# Spawn Predicate

Bee spawn biome modifiers may include an optional `spawnPredicate` using Minecraft's `LocationPredicate` codec.

All known top-level fields are optional.

| Field | Type | Required | Default | Notes |
| --- | --- | --- | --- | --- |
| `position` | Position predicate | No | — | Optional x/y/z bounds. |
| `biomes` | Biome holder set | No | — | Additional biome constraint. |
| `structures` | Structure holder set | No | — | Structure membership constraint. |
| `dimension` | dimension identifier | No | — | Example: `minecraft:overworld`. |
| `smokey` | boolean | No | — | Matches smokey locations. |
| `light` | Light predicate | No | — | Constrains light level. |
| `block` | Block predicate | No | — | Constrains block at the tested location. |
| `fluid` | Fluid predicate | No | — | Constrains fluid at the tested location. |
| `can_see_sky` | boolean | No | — | Constrains sky visibility. |

## Position predicate

`x`, `y`, and `z` each use `MinMaxBounds.Doubles` and are optional.

A bound can be an exact number:

```json
{
  "position": {
    "y": 64
  }
}
```

or an object:

```json
{
  "position": {
    "y": {
      "min": 60.0,
      "max": 128.0
    }
  }
}
```

The codec rejects `min > max`.

## Light predicate

`light.light` uses integer min/max bounds.

```json
{
  "light": {
    "light": {
      "min": 8,
      "max": 15
    }
  }
}
```

## Block predicate

Known fields include:

| Field | Type | Required |
| --- | --- | --- |
| `blocks` | Block holder set | No |
| `state` | block-state predicate object | No |
| `nbt` | NBT predicate | No |

Minecraft data-component matcher fields are flattened into the same block predicate object. Those internals remain intentionally permissive in the schema because their complete codec definitions were not supplied.

## Fluid predicate

Known fields are:

| Field | Type | Required |
| --- | --- | --- |
| `fluids` | Fluid holder set | No |
| `state` | fluid-state predicate object | No |

## Full example

```json
{
  "position": {
    "y": {"min": 60.0, "max": 128.0}
  },
  "biomes": "#minecraft:is_overworld",
  "dimension": "minecraft:overworld",
  "smokey": false,
  "light": {
    "light": {"min": 8}
  },
  "block": {
    "blocks": ["minecraft:grass_block", "minecraft:dirt"]
  },
  "fluid": {
    "fluids": "minecraft:water"
  },
  "can_see_sky": true
}
```
