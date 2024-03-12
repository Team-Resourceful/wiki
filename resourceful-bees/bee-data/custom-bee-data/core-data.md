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

# Core Data

The core customization component is responsible for defining **four** key aspects of nearly every bee imaginable:

* the flower(s) which a bee uses for pollination
* the base amount of time the bee spends in the hive
* associated lore
* the honeycombs produced, if any

{% code title="Template:" %}
```json
"resourcefulbees:core/v1": {
  "entityFlower": [
    "minecraft:cow",
    "minecraft:sheep"
  ],
  "maxTimeInHive": 4000,
  "lore": [
    {
      "text": "This bee is a dummy and does not exist"
    },
    {
      "text": "Bee happy...--``-..-``---."
    }
  ],
  "honeycombVariation": "dummy_honeycomb",
  "flower": [
    "minecraft:diamond_block",
    "minecraft:emerald_block"
  ]
}
```
{% endcode %}

## Identifier

***

The root JSON of the core customization component looks like this:

```json
"resourcefulbees:core/v1": {
    ...
}
```

The identifier of the component is as such:

```
resourcefulbees:core/v1
```

## Customization Options

***

### <mark style="color:orange;">`honeycombVariation`</mark>

The identifier of the honeycomb variation produced by the bee. More information about honeycomb variation can be found in the [Custom Honeycombs](https://app.gitbook.com/o/GQdOlzzIqftgC5xMgxnG/s/S5sbJi5FdsoHIzK2cvL5/ "mention") section.

***

{% hint style="info" %}
**Name:** Honeycomb Variation

**Key:** <mark style="color:orange;">`honeycombVariation`</mark>

**Type:** String

**Default:** No Honeycomb
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:core/v1": {
    "honeycombVariation": "diamond"
}
```

</details>

### <mark style="color:orange;">`flower`</mark>

Specifies what flower(s) the bee can pollinate. With the use of [Miscellaneous](https://app.gitbook.com/o/GQdOlzzIqftgC5xMgxnG/s/uHMOruowjctiLyjG3esg/ "mention"), the syntax will vary based on the definition. The flower can be defined as a tag, a list of blocks, or a single block. See the examples below for further understanding.

***

{% hint style="info" %}
**Name:** Flower

**Key:** <mark style="color:orange;">`flower`</mark>

**Type:** [HolderSet\<Block>](https://app.gitbook.com/o/GQdOlzzIqftgC5xMgxnG/s/uHMOruowjctiLyjG3esg/)

**Default:** `minecraft:poppy`
{% endhint %}

{% tabs %}
{% tab title="Tag" %}
```json
"resourcefulbees:core/v1": {
  "flower": "#minecraft:flowers"
}
```
{% endtab %}

{% tab title="List of Blocks" %}
```json
"resourcefulbees:core/v1": {
  "flower": [
    "minecraft:diamond_block",
    "minecraft:emerald_block"
  ]
}
```
{% endtab %}

{% tab title="Single Block" %}
```json
"resourcefulbees:core/v1": {
  "flower": "minecraft:diamond_block"
}
```
{% endtab %}
{% endtabs %}

### <mark style="color:orange;">`entityFlower`</mark>

When the flower a bee can pollinate is an entity, <mark style="color:orange;">`entityflower`</mark> must be used instead. The syntax used remains the same as blocks. See the examples below for further understanding.

***

{% hint style="info" %}
**Name:** Entity Flower

**Key:** <mark style="color:orange;">`entityFlower`</mark>

**Type:** [HolderSet\<Entity>](https://app.gitbook.com/o/GQdOlzzIqftgC5xMgxnG/s/uHMOruowjctiLyjG3esg/)

**Default:** Empty Set
{% endhint %}

{% tabs %}
{% tab title="Tag" %}
```json
"resourcefulbees:core/v1": {
  "entityFlower": "#minecraft:raiders"
}
```
{% endtab %}

{% tab title="List of Entities" %}
```json
"resourcefulbees:core/v1": {
  "entityFlower": [
    "minecraft:pig",
    "minecraft:cow"
  ]
}
```
{% endtab %}

{% tab title="Single Entity" %}
```json
"resourcefulbees:core/v1": {
  "entityFlower": "minecraft:cow"
}
```
{% endtab %}
{% endtabs %}

### <mark style="color:orange;">`maxTimeInHive`</mark>

The base amount of time a bee spends in a hive. This value is modified based on the hive tier.

***

{% hint style="info" %}
**Name:** Max Time in Hive

**Key:** <mark style="color:orange;">`maxTimeInHive`</mark>

**Type:** Integer

**Range:** ≥600

**Default:** 2400
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:core/v1": {
  "maxTimeInHive": 1200
}
```

</details>

### <mark style="color:orange;">`lore`</mark>

Lore is cosmetic text displayed in JEI tooltips when hovering over the bee with the cursor. It can be extremely useful for providing players with hints on how to obtain the bee or it can be useful for memes and credits.

***

{% hint style="info" %}
**Name:** Lore

**Key:** <mark style="color:orange;">`lore`</mark>

**Type:** [Component\[\]](https://minecraft.fandom.com/wiki/Raw\_JSON\_text\_format)

**Default:** Empty List
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:core/v1": {
    "lore": [
      {
        "text":"A Delicious Bee.",
        "color": "aqua"
      },
      {
        "translate":"tooltip.resourcefulbees.bee.creator",
        "with": ["§6Epic_Oreo"]
      }
    ]
  }
```

</details>

