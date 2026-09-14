# Mutation Entry

Each entry in a `resourcefulbees:mutation` recipe maps one input mutation predicate to one or more possible output mutations.

## Fields

| Field | Type | Required | Default | Notes |
| --- | --- | --- | --- | --- |
| `input` | Mutation object | Yes | — | Uses the built-in mutation dispatch described below. |
| `outputs` | array of Mutation objects | Yes | — | Plain list of output mutation objects; there is no outer weight wrapper. |

An empty `outputs` array is structurally possible if accepted by the list codec, but is not useful for gameplay.

## Mutation dispatch

Mutation objects are dispatched by their required `type` field. Built-in values are:

- `item`
- `block`
- `fluid`
- `entity`

All built-in mutation objects also support the common fields below.

| Field | Type | Required | Default | Range |
| --- | --- | --- | --- | --- |
| `chance` | number | No | `1.0` | `0.0` through `1.0` |
| `weight` | number | No | `10.0` | `>= 0` |

`chance` determines whether the mutation succeeds when selected. `weight` participates in weighted selection where multiple candidates are available.

## Item mutation

```json
{
  "type": "item",
  "item": {
    "id": "minecraft:diamond"
  },
  "chance": 1.0,
  "weight": 10.0
}
```

| Field | Type | Required | Default |
| --- | --- | --- | --- |
| `type` | string | Yes | `item` |
| `item` | Restricted item predicate | Yes | — |
| `chance` | number | No | `1.0` |
| `weight` | number | No | `10.0` |

The item predicate requires `id` and may additionally contain `components`, `durability`, and `count` constraints.

## Block mutation

```json
{
  "type": "block",
  "block": {
    "id": "minecraft:diamond_block"
  }
}
```

| Field | Type | Required | Default |
| --- | --- | --- | --- |
| `type` | string | Yes | `block` |
| `block` | Restricted block predicate | Yes | — |
| `chance` | number | No | `1.0` |
| `weight` | number | No | `10.0` |

The block predicate requires `id` and may additionally constrain `components`, `location`, or block `properties`.

## Fluid mutation

```json
{
  "type": "fluid",
  "fluid": "minecraft:water"
}
```

| Field | Type | Required | Default |
| --- | --- | --- | --- |
| `type` | string | Yes | `fluid` |
| `fluid` | fluid identifier | Yes | — |
| `chance` | number | No | `1.0` |
| `weight` | number | No | `10.0` |

## Entity mutation

```json
{
  "type": "entity",
  "entity": {
    "type": "minecraft:cow"
  }
}
```

| Field | Type | Required | Default |
| --- | --- | --- | --- |
| `type` | string | Yes | `entity` |
| `entity` | Restricted entity predicate | Yes | — |
| `chance` | number | No | `1.0` |
| `weight` | number | No | `10.0` |

The entity predicate requires an entity `type` and may additionally include location, effects, NBT, flags, and target constraints.
