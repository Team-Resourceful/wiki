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

# Breed Data

The breeding customization component is responsible for defining relationships between bees. Bees can have many different breeding relationships.

{% code title="Template:" %}
```json
"resourcefulbees:breeding/v1": {
  "feedAmount": 2,
  "childGrowthDelay": -45000,
  "breedDelay": 2400,
  "parents": [
    {
      "parent1": "diamond",
      "parent2": "coal",
      "weight": 75.0,
      "chance": 0.67
    },
    {
      "parent1": "diamond",
      "parent2": "diamond",
      "weight": 24.0,
      "chance": 0.67
    }
  ],
  "feedItem": [
    "minecraft:poppy",
    "minecraft:carrot"
  ],
  "feedReturnItem": {
    "id": "minecraft:bucket",
    "count": 1,
    "nbt": {
      "this_is": "an_nbt_tag"
    }
  }
}
```
{% endcode %}



## Identifier

***

The root JSON of the breeding customization component looks like this:

```json
"resourcefulbees:breeding/v1": {
    ...
}
```

The identifier of the component is as such:

```
resourcefulbees:breeding/v1
```



## Customization Options

***

### <mark style="color:orange;">`parents`</mark>

A list of bee pairs that can be used to breed this bee.

***

{% hint style="info" %}
**Name:** Parents

**Key:** <mark style="color:orange;">`parents`</mark>

**Type:** [BeeFamily\[\]](bee-family.md)

**Default:** Empty List
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:breeding/v1": {
  "parents": [
    {
      "parent1": "diamond",
      "parent2": "coal",
      "weight": 75.0,
      "chance": 0.67
    }
  ]
}
```

</details>



### <mark style="color:orange;">`feedItem`</mark>

The item(s) which can be fed to the bee to trigger its love state.

{% hint style="warning" %}
**Note:** This value only applies when this bee is being used to breed another bee
{% endhint %}

***

{% hint style="info" %}
**Name:** Feed Item

**Key:** <mark style="color:orange;">`feedItem`</mark>

**Type:** [HolderSet\<Item>](https://app.gitbook.com/s/uHMOruowjctiLyjG3esg/)

**Default:** `minecraft:poppy`
{% endhint %}

{% tabs %}
{% tab title="Tag" %}
```json
"resourcefulbees:breeding/v1": {
  "feedItem": "#minecraft:candles"
}
```
{% endtab %}

{% tab title="List of Items" %}
```json
"resourcefulbees:breeding/v1": {
  "feedItem": [
    "minecraft:poppy",
    "minecraft:carrot"
  ]
}
```
{% endtab %}

{% tab title="Single Item" %}
```json
"resourcefulbees:breeding/v1": {
  "feedItem": "minecraft:carrot"
}
```
{% endtab %}
{% endtabs %}



### <mark style="color:orange;">`feedReturnItem`</mark>

Item returned to the player after the feed item has been consumed. Useful for returning container-like items after consuming the contents.

{% hint style="warning" %}
**Note:** This value only applies when this bee is being used to breed another bee
{% endhint %}

***

{% hint style="info" %}
**Name:** Feed Return Item

**Key:** <mark style="color:orange;">`feedReturnItem`</mark>

**Type:** ItemStack

**Default:** Optional
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:breeding/v1": {
  "feedReturnItem": {
    "id": "minecraft:bucket",
    "count": 1,
    "nbt": {
      "this_is": "an_nbt_tag"
    }
  }
}
```

</details>



### <mark style="color:orange;">`feedAmount`</mark>

The amount of feed items required to be given to the bee to trigger its love state.&#x20;

{% hint style="warning" %}
**Note:** This value only applies when this bee is being used to breed another bee
{% endhint %}

***

{% hint style="info" %}
**Name:** Feed Return Item

**Key:** <mark style="color:orange;">`feedAmount`</mark>

**Type:** Integer

**Range:** ≥1

**Default:** 1
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:breeding/v1": {
  "feedAmount": 2
}
```

</details>



### <mark style="color:orange;">`childGrowthDelay`</mark>

The time in ticks that a baby bee will stay a baby bee.

***

{% hint style="info" %}
**Name:** Child Growth Delay

**Key:** <mark style="color:orange;">`childGrowthDelay`</mark>

**Type:** Integer

**Range:** ≤0

**Default:** -24000
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:breeding/v1": {
  "childGrowthDelay": -45000
}
```

</details>



### <mark style="color:orange;">`breedDelay`</mark>

The time in ticks until the bee's love state can be triggered again.

***

{% hint style="info" %}
**Name:** Breed Delay

**Key:** <mark style="color:orange;">`breedDelay`</mark>

**Type:** Integer

**Range:** ≥1

**Default:** 6000
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:breeding/v1": {
  "breedDelay": 2400
}
```

</details>

