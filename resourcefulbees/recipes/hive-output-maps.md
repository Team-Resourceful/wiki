# Hive and Apiary Output Maps

Hive recipes and honeycomb output variations use maps keyed by registered hive or apiary tier identifiers.

## Tier keys

Built-in Resourceful Bees tiers use identifiers such as:

```text
resourcefulbees:t1
resourcefulbees:t2
resourcefulbees:t3
resourcefulbees:t4
```

The tier registries are extensible, so add-ons may register additional identifiers. The JSON schemas therefore validate tier keys as resource identifiers rather than limiting them to the four built-ins.

## Map values

Each value is an Item Stack Template. Compact and expanded forms are accepted.

```json
{
  "resourcefulbees:t1": "resourcefulbees:ruby_honeycomb",
  "resourcefulbees:t2": {
    "id": "resourcefulbees:ruby_honeycomb",
    "count": 2
  }
}
```

## Hive recipe behavior

In `resourcefulbees:hive` recipes, both `hiveCombs` and `apiaryCombs` are optional and default to `{}`.

## Honeycomb variation behavior

Honeycomb output variations also use tier maps, but they additionally support `defaultComb` and `defaultCombBlock`. Runtime normalization can fill missing hive tiers from prior/default values. Apiary fallback behavior may depend on configuration, so the static schema intentionally does not claim a stronger requirement than the codec provides.
