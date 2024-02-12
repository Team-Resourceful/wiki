---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Custom Bee Data

Custom Bee Data is the main JSON object and is comprised of several customization objects which are defined using a `"key": { value }` syntax.&#x20;

```json
{
  "resourcefulbees:core/v1": {
    ...
  },
  "resourcefulbees:rendering/v1": {
    ...
  },
  "resourcefulbees:mutation/v1": {
    ...
  },
  "resourcefulbees:breeding/v1": {
    ...
  },
  "resourcefulbees:trade/v1": {
    ...
  }
}
```

The "key" names act as identifiers under which the data is registered and used and follow the `namespace:path` format. The path generally follows a `type/version` format.

```
"resourcefulbees:trade/v1"
```

This syntax allows for the customizable options to evolve over time with minimal upkeep required since data mappers can be written to upgrade older API versions to newer ones.



## Key Components

***

Below is a list of the key customization components provided by the mod. Additional components can be created by other mods via our API.

<table data-view="cards" data-full-width="false"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-type="files"></th><th data-hidden data-card-cover data-type="files"></th><th data-hidden></th></tr></thead><tbody><tr><td>Core Data</td><td><em>Key Bee Info</em></td><td><a href="custom-bee-data/core-data.md">core-data.md</a></td><td><a href="broken-reference">Broken file</a></td><td><a href=".gitbook/assets/core-data-card.png">core-data-card.png</a></td><td></td></tr><tr><td>Render Data</td><td><em>What it looks like</em></td><td><a href="custom-bee-data/render-data/">render-data</a></td><td></td><td><a href=".gitbook/assets/render-data-card.png">render-data-card.png</a></td><td></td></tr><tr><td>Breed Data</td><td><em>How to breed</em></td><td><a href="custom-bee-data/breed-data/">breed-data</a></td><td></td><td><a href=".gitbook/assets/breed-data-card.png">breed-data-card.png</a></td><td></td></tr><tr><td>Combat Data</td><td><em>Friend or foe?</em></td><td><a href="custom-bee-data/combat-data.md">combat-data.md</a></td><td></td><td><a href=".gitbook/assets/combat-data-card.png">combat-data-card.png</a></td><td></td></tr><tr><td>Mutation Data</td><td><em>Pollination effects</em></td><td><a href="custom-bee-data/mutation-data/">mutation-data</a></td><td></td><td><a href=".gitbook/assets/mutation-data-card.png">mutation-data-card.png</a></td><td></td></tr><tr><td>Trait Data</td><td><em>Uniqueness</em></td><td><a href="https://app.gitbook.com/o/GQdOlzzIqftgC5xMgxnG/s/gnHuwBi9dpB112fYP5nw/">Trait Data</a></td><td></td><td><a href=".gitbook/assets/trait-data-card.png">trait-data-card.png</a></td><td></td></tr><tr><td>Trade Data</td><td><em>Beekeeper trades</em></td><td><a href="custom-bee-data/trade-data.md">trade-data.md</a></td><td></td><td><a href=".gitbook/assets/trade-data-card.png">trade-data-card.png</a></td><td></td></tr></tbody></table>
