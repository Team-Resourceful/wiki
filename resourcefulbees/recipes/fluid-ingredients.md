# Fluid Ingredients and Fluid Stack Templates

Several Resourceful Bees recipes use NeoForge fluid ingredient codecs or fluid stack templates. They are similar concepts but have different JSON shapes.

## Fluid Ingredient

A fluid ingredient selects acceptable input fluids. It accepts either a direct fluid ID, a fluid tag, or a custom NeoForge ingredient object.

### Direct fluid

```json
"minecraft:water"
```

### Fluid tag

```json
"#c:water"
```

### Custom NeoForge fluid ingredient

```json
{
  "neoforge:ingredient_type": "namespace:custom_type"
}
```

Custom objects require `neoforge:ingredient_type`; remaining fields depend on the registered ingredient type.

## Sized Fluid Ingredient

Used by solidification recipes.

| Field | Type | Required | Default | Range |
| --- | --- | --- | --- | --- |
| `ingredient` | Fluid Ingredient | Yes | — | — |
| `amount` | integer | No | `1000` | `>= 1` |

Example:

```json
{
  "ingredient": "minecraft:lava",
  "amount": 1000
}
```

## Fluid Stack Template

Used by flow hive recipes to describe produced fluid rather than matched input fluid.

Two forms are accepted.

### Compact form

```json
"resourcefulbees:ruby_honey_fluid_source"
```

This represents the named fluid with a bucket-volume amount (`1000`) and no component patch.

### Expanded form

| Field | Type | Required | Default | Range |
| --- | --- | --- | --- | --- |
| `id` | non-empty fluid identifier | Yes | — | — |
| `amount` | integer | Yes | — | `>= 1` |
| `components` | DataComponentPatch object | No | `{}` | — |

```json
{
  "id": "resourcefulbees:ruby_honey_fluid_source",
  "amount": 1000,
  "components": {}
}
```

`minecraft:empty` (and the shorthand `empty`) are rejected for fluid stack templates.
