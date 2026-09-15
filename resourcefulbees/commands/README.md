# Commands

Resourceful Bees provides server commands for generating supplemental data, printing JSON format templates, and managing development/debug features.

The command root is:

```text
/resourcefulbees
```

Most subcommands require Minecraft's gamemaster command permission.

## Why generation commands exist

Some Resourceful Bees data depends on fully registered runtime objects. In particular, generated breeder recipes and beekeeper trades contain item stacks with data components. Those components are not bound early enough during datapack discovery to safely generate the files and inject them into the in-memory datapack.

The `generate` commands therefore run after the game has loaded its registries and write ordinary JSON resources to the Resourceful Bees generated-resource directory. They supplement the normal JSON/datapack workflow rather than replacing it.

Generated data is written beneath:

```text
config/resourcefulbees/resources/data/resourcefulbees/
```

The language generator is different: it writes `en_us.json` through the mod's resources path rather than through the generated data path.

## Command groups

| Command | Purpose |
| --- | --- |
| [`/resourcefulbees generate ...`](generate.md) | Generate recipes, beekeeper trades, and English language data from the currently loaded Resourceful Bees registries. |
| [`/resourcefulbees template ...`](template.md) | Encode and print example JSON for bee, honeycomb, honey, and trait formats. |
| [`/resourcefulbees beepedia ...`](beepedia.md) | Beepedia progression/debug command tree. The current add/remove implementations are stubbed out. |

For generated recipes and trades, review the generated files before packaging or distributing them with a datapack/resource setup. Re-running a generator writes its known output paths again, so generated files at the same paths are replaced.