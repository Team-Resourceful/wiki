# Common JSON Types

These structures recur across Resourceful Bees data files.

## Resource locations

Minecraft registry identifiers use the familiar `namespace:path` form,
for example:

``` json
"minecraft:plains"
```

The schemas also accept an omitted namespace where the underlying
identifier codec permits it.

## Tags

Registry tags are written with a leading `#`:

``` json
"#minecraft:is_overworld"
```

## Holder sets

Minecraft/NeoForge holder sets used by the biome modifier schemas can be
authored as a single registry ID, a tag, a list of registry IDs, or a
NeoForge custom holder-set dispatch object.

``` json
"minecraft:plains"
```

``` json
"#minecraft:is_overworld"
```

``` json
[
  "minecraft:plains",
  "minecraft:forest"
]
```

Custom NeoForge holder-set objects are extensible and depend on the
registered holder-set type.

## Min/max bounds

Minecraft `MinMaxBounds` codecs accept either an exact number or an
object containing optional `min` and `max` values.

``` json
8
```

``` json
{
  "min": 8,
  "max": 15
}
```

The codec rejects a range where `min` is greater than `max`.

## Item stack templates

Where used by Resourceful Bees, item stack templates generally support a
compact item ID or an object containing an `id`, optional count, and
optional component patch. Consult the schema for the exact form and
range used by a particular data type.

## Schema conventions

The generated schemas use JSON Schema Draft 2020-12. Known Resourceful
Bees `MapCodec` objects are generally documented with
`additionalProperties: false`, while intentionally extensible
Minecraft/NeoForge structures remain permissive.
