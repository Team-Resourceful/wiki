# Beepedia Commands

The Beepedia command tree is registered for gamemaster-level command users and accepts a target player plus either a specific Resourceful Bees bee or `*`.

## Syntax

```text
/resourcefulbees beepedia <player> add <bee>
/resourcefulbees beepedia <player> add *
/resourcefulbees beepedia <player> remove <bee>
/resourcefulbees beepedia <player> remove *
```

`<player>` uses Minecraft's single-player entity argument. `<bee>` uses Resourceful Bees' custom bee argument and resolves against the registered Resourceful Bees bees.

## Current implementation status

The command tree and arguments are registered, but the actual Beepedia saved-data mutations are currently commented out in `BeepediaCommand`.

As a result, the current `add` and `remove` executions return success without changing Beepedia progression. This applies to both specific-bee and `*` forms.

The intended operations visible in the implementation are to add/unlock bees, remove individual bees, and clear or operate on all bees, but those saved-data calls are not active in the current 26.2 source. Treat these commands as unfinished/debug scaffolding until the mutation calls are restored.