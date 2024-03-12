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

# Trade Data

The villager trade customization component is reused across several JSON files within Resourceful Bees. It is responsible for defining the costs and rewards of certain trade items depending on which file it is used in. Not including a villager trade customization component prevents the associated items from being added to the pool of trades.

Below are the JSON files which can have a villager trade customization component and the trades they create.

{% tabs %}
{% tab title="Custom Bee" %}
When the component is used in a custom bee JSON, a filled bee jar will be added to the Level 5 trade pool.
{% endtab %}

{% tab title="Custom Honeycombs" %}
When the component is used in a custom honeycomb JSON, the honeycomb and honeycomb block will be added to the Level 3 trade pool.
{% endtab %}

{% tab title="Custom Honey" %}
The component can be used in three different sections of a custom honey JSON:

* When used in the honey bottle section, a honey bottle will be added to the Level 3 trade pool.
* When used in the honey block section, a honey block will be added to the Level 3 trade pool.
* When used in the honey fluid section, a honey bucket will be added to the Level 3 trade pool.
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Adding an empty villager trade component will add the trade to the pool using all default values.

{% code title="Example" %}
```json
{
  "resourcefulbees:block/v1": {
    "color": "rainbow",
    "honeyBlockItem": "resourcefulbees:rainbow_honey_block",
    "honeyBlock": "resourcefulbees:rainbow_honey_block",
    "tradeData": {}
  }
}
```
{% endcode %}
{% endhint %}

{% code title="Template:" %}
```json
"resourcefulbees:trade/v1": {
  "amount": {
    "min": 1,
    "max": 1
  },
  "secondaryItem": "minecraft:coal_block",
  "secondaryItemCost": {
    "min": 4,
    "max": 8
  },
  "priceMultiplier": 0.4,
  "maxTrades": 2,
  "xp": 8
}
```
{% endcode %}



## Identifier

***

The root JSON of the villager trade customization component looks like this:

```json
"resourcefulbees:trade/v1": {
    ...
}
```

The identifier of the component is as such:

<pre><code><strong>resourcefulbees:trade/v1
</strong></code></pre>

{% hint style="danger" %}
In custom honeycomb and honey JSON's the identifier is `tradeData`:

{% code title="Example" %}
```json
{
  "resourcefulbees:block/v1": {
    "tradeData": {}    <---- Identifier
  }
}
```
{% endcode %}
{% endhint %}



## Customization Options

***

### <mark style="color:orange;">`amount`</mark>

The max amount of filled bee jars that can potentially be received in a single trade.

{% hint style="warning" %}
When trades are being populated, the amount actually used is a randomized value between the min and the max, therefore, not all trades will always have this amount.
{% endhint %}

***

{% hint style="info" %}
**Name:** Amount

**Key:** <mark style="color:orange;">`amount`</mark>

**Type:** UniformInt

**Default:** 1, 64
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:trade/v1": {
  "amount": {
    "min": 1,
    "max": 1
  }
}
```

</details>



### <mark style="color:orange;">`secondaryItem`</mark>

The item needed, when the trade requires a secondary item, in addition to golden flowers.

***

{% hint style="info" %}
**Name:** Secondary Item

**Key:** <mark style="color:orange;">`secondaryItem`</mark>

**Type:** ItemStack

**Default:** `ItemStack.EMPTY`
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:trade/v1": {
  "secondaryItem": "minecraft:coal_block"
}
```

</details>



### <mark style="color:orange;">`secondaryItemCost`</mark>

The max base cost for the secondary item.

{% hint style="warning" %}
When trades are being populated, the amount actually used is a randomized value between the min and the max, therefore, not all trades will always have this amount.
{% endhint %}

***

{% hint style="info" %}
**Name:** Secondary Item Cost

**Key:** <mark style="color:orange;">`secondaryItemCost`</mark>

**Type:** UniformInt

**Default:** 1, 4
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:trade/v1": {
  "secondaryItem": "minecraft:coal_block",
  "secondaryItemCost": {
    "min": 4,
    "max": 8
  }
}
```

</details>



### <mark style="color:orange;">`priceMultiplier`</mark>

When demand goes up, so does the price. Use this value to scale the price increase.

{% hint style="warning" %}
Most vanilla trades have a price multiplier of 0.05
{% endhint %}

***

{% hint style="info" %}
**Name:** Price Multiplier

**Key:** <mark style="color:orange;">`priceMultiplier`</mark>

**Type:** Float

**Range:** 0.00 - 1.00

**Default:** `0.05`
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:trade/v1": {
  "priceMultiplier": 0.4
}
```

</details>



### <mark style="color:orange;">`maxTrades`</mark>

The max number of trades that can be performed before a restock is needed.&#x20;

***

{% hint style="info" %}
**Name:** Max Trades

**Key:** <mark style="color:orange;">`maxTrades`</mark>

**Type:** Integer

**Range:** 1 - 64

**Default:** 8
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:trade/v1": {
  "maxTrades": 2
}
```

</details>



### <mark style="color:orange;">`xp`</mark>

The XP awarded each trade.

***

{% hint style="info" %}
**Name:** XP

**Key:** <mark style="color:orange;">`xp`</mark>

**Type:** Integer

**Range:** 1 - 64

**Default:** 3
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:trade/v1": {
  "xp": 8
}
```

</details>

