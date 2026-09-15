# Template Commands

Template commands encode Resourceful Bees' built-in dummy/template data through the same codecs used by the corresponding JSON formats and print the resulting pretty-formatted JSON to the game/server log.

All template commands require gamemaster command permission.

## Bee template

```text
/resourcefulbees template bee
```

Encodes `DummyBeeData.DATA` through the bee dispatch codec and logs the resulting bee JSON template. A success message is sent to the command source after encoding succeeds.

Use this as a codec-generated starting point for a custom bee definition. The maintained field-by-field reference is under [Bee Formats](../formats/bees/index.md).

## Honeycomb template

```text
/resourcefulbees template honeycomb
```

Encodes the dummy `OutputVariation` through `OutputVariation.CODEC` and prints the resulting JSON. If encoding fails, the codec error is logged and the command returns failure instead of printing a template.

See [Honeycombs](../formats/honeycombs/index.md) for the maintained format reference.

## Honey template

```text
/resourcefulbees template honey
```

Encodes `DummyHoneyData.DATA` through the honey dispatch codec and prints the resulting JSON. Encoding errors are logged and cause the command to return failure.

See [Custom Honey](../formats/honey/index.md) for the maintained format reference.

## Trait template

```text
/resourcefulbees template trait
```

Encodes `DummyTraitData.DUMMY_TRAIT_DATA` through the trait codec and prints the resulting JSON. Encoding errors are logged and cause the command to return failure.

See [Traits](../formats/traits/index.md) for the maintained format reference.

## Where the template appears

These commands log the complete pretty-printed JSON through the Resourceful Bees logger. The in-game command response only confirms that the template was printed; copy the JSON from the game/server log.

The command output is useful for obtaining a codec-produced example, while the documentation schemas and templates remain the better reference for field requirements, defaults, accepted representations, and runtime caveats.