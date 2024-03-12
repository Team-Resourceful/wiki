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

# Mutation Type

## Customization Options

***

### <mark style="color:orange;">`type`</mark>

A mutation can be **one** of **four** different types:

```
Item | Block | Fluid | Entity
```

The type object is used for defining the Mutation Type, associated data, and the likelihood of obtaining, when used as an output option.

***

{% hint style="info" %}
**Name:** Mutation Type

**Key:** <mark style="color:orange;">`type`</mark>

**Type:** String

**Default:** This value is required or the recipe won't load!
{% endhint %}

{% tabs %}
{% tab title="Item" %}
#### <mark style="color:orange;">`item`</mark>

The item being transformed or resulted.

***

{% hint style="info" %}
**Name:** Item

**Key:** <mark style="color:orange;">`item`</mark>

**Type:** RestrictedItemPredicate

**Default:** This value is required or the recipe won't load!
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "type": "item",
  "item": {
    "id": "minecraft:nether_star"
  }
}
```

</details>

#### <mark style="color:orange;">`chance`</mark>

The chance of actually resulting the item when selected as the output from the pool of items.

***

{% hint style="info" %}
**Name:** Chance

**Key:** <mark style="color:orange;">`chance`</mark>

**Type:** Double

**Range:** 0.0 - 1.0

**Default:** 1.0
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "type": "item",
  "item": {
    "id": "minecraft:nether_star"
  },
  "chance": 0.5
}
```

</details>

#### <mark style="color:orange;">`weight`</mark>

How likely the item is to be selected among a pool of items.

<details>

<summary>Calculating Weight Distributions:</summary>

A mutation recipe has five different output options.

The weights are as follows:

```
Output 1: 20
Output 2: 10
Output 3: 30
Output 4: 60    
Output 5: 80
```

The chances each output has of being selected are as follows:

```
Output 1: 10%
Output 2: 5%
Output 3: 15%
Output 4: 30%
Output 5: 40%
```

To calculate the chance:

1. Add up all the weights
2. Divide the weight you wish to check by the total in step 1

</details>

***

{% hint style="info" %}
**Name:** Weight

**Key:** <mark style="color:orange;">`weight`</mark>

**Type:** Double

**Range:** ≥0.0

**Default:** 10
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "type": "item",
  "item": {
    "id": "minecraft:nether_star"
  },
  "weight": 69
}
```

</details>
{% endtab %}

{% tab title="Block" %}
#### <mark style="color:orange;">`block`</mark>

The block being transformed or resulted.

***

{% hint style="info" %}
**Name:** Block

**Key:** <mark style="color:orange;">`block`</mark>

**Type:** RestrictedBlockPredicate

**Default:** This value is required or the recipe won't load!
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "type": "block",
  "block": {
    "id": "minecraft:diamond_block"
  }
}
```

</details>

#### <mark style="color:orange;">`chance`</mark>

The chance of actually resulting the block, if selected as the output from the pool of blocks.

***

{% hint style="info" %}
**Name:** Chance

**Key:** <mark style="color:orange;">`chance`</mark>

**Type:** Double

**Range:** 0.0 - 1.0

**Default:** 1.0
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "type": "block",
  "block": {
    "id": "minecraft:diamond_block"
  },
  "chance": 0.5
}
```

</details>

#### <mark style="color:orange;">`weight`</mark>

How likely the block is to be selected among a pool of blocks.

<details>

<summary>Calculating Weight Distributions:</summary>

A mutation recipe has five different output options.

The weights are as follows:

```
Output 1: 20
Output 2: 10
Output 3: 30
Output 4: 60    
Output 5: 80
```

The chances each output has of being selected are as follows:

```
Output 1: 10%
Output 2: 5%
Output 3: 15%
Output 4: 30%
Output 5: 40%
```

To calculate the chance:

1. Add up all the weights
2. Divide the weight you wish to check by the total in step 1

</details>

***

{% hint style="info" %}
**Name:** Weight

**Key:** <mark style="color:orange;">`weight`</mark>

**Type:** Double

**Range:** ≥0.0

**Default:** 10
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "type": "block",
  "block": {
    "id": "minecraft:diamond_block"
  },
  "weight": 69
}
```

</details>
{% endtab %}

{% tab title="Fluid" %}
#### <mark style="color:orange;">`fluid`</mark>

The block being transformed or resulted.

***

{% hint style="info" %}
**Name:** Fluid

**Key:** <mark style="color:orange;">`fluid`</mark>

**Type:** Fluid

**Default:** This value is required or the recipe won't load!
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "type": "fluid",
  "fluid": {
    "id": "minecraft:water"
  }
}
```

</details>

#### <mark style="color:orange;">`chance`</mark>

The chance of actually resulting the fluid, if selected as the output from the pool of fluids.

***

{% hint style="info" %}
**Name:** Chance

**Key:** <mark style="color:orange;">`chance`</mark>

**Type:** Double

**Range:** 0.0 - 1.0

**Default:** 1.0
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "type": "fluid",
  "fluid": {
    "id": "minecraft:water"
  },
  "chance": 0.5
}
```

</details>

#### <mark style="color:orange;">`weight`</mark>

How likely the fluid is to be selected among a pool of fluids.

<details>

<summary>Calculating Weight Distributions:</summary>

A mutation recipe has five different output options.

The weights are as follows:

```
Output 1: 20
Output 2: 10
Output 3: 30
Output 4: 60    
Output 5: 80
```

The chances each output has of being selected are as follows:

```
Output 1: 10%
Output 2: 5%
Output 3: 15%
Output 4: 30%
Output 5: 40%
```

To calculate the chance:

1. Add up all the weights
2. Divide the weight you wish to check by the total in step 1

</details>

***

{% hint style="info" %}
**Name:** Weight

**Key:** <mark style="color:orange;">`weight`</mark>

**Type:** Double

**Range:** ≥0.0

**Default:** 10
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "type": "fluid",
  "fluid": {
    "id": "minecraft:water"
  },
  "weight": 69
}
```

</details>
{% endtab %}

{% tab title="Entity" %}
#### <mark style="color:orange;">`entity`</mark>

The block being transformed or resulted.

***

{% hint style="info" %}
**Name:** Entity

**Key:** <mark style="color:orange;">`entity`</mark>

**Type:** RestrictedEntityPredicate

**Default:** This value is required or the recipe won't load!
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "type": "entity",
  "entity": {
    "id": "minecraft:cow"
  }
}
```

</details>

#### <mark style="color:orange;">`chance`</mark>

The chance of actually resulting the entity, if selected as the output from the pool of entities.

***

{% hint style="info" %}
**Name:** Chance

**Key:** <mark style="color:orange;">`chance`</mark>

**Type:** Double

**Range:** 0.0 - 1.0

**Default:** 1.0
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "type": "entity",
  "entity": {
    "id": "minecraft:cow"
  },
  "chance": 0.5
}
```

</details>

#### <mark style="color:orange;">`weight`</mark>

How likely the entity is to be selected among a pool of entities.

<details>

<summary>Calculating Weight Distributions:</summary>

A mutation recipe has five different output options.

The weights are as follows:

```
Output 1: 20
Output 2: 10
Output 3: 30
Output 4: 60    
Output 5: 80
```

The chances each output has of being selected are as follows:

```
Output 1: 10%
Output 2: 5%
Output 3: 15%
Output 4: 30%
Output 5: 40%
```

To calculate the chance:

1. Add up all the weights
2. Divide the weight you wish to check by the total in step 1

</details>

***

{% hint style="info" %}
**Name:** Weight

**Key:** <mark style="color:orange;">`weight`</mark>

**Type:** Double

**Range:** ≥0.0

**Default:** 10
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "type": "entity",
  "entity": {
    "id": "minecraft:cow"
  },
  "weight": 69
}
```

</details>
{% endtab %}
{% endtabs %}
