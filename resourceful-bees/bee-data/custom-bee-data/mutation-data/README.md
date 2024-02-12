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

# Mutation Data

Mutations are the repurposing of a vanilla mechanic: <mark style="color:orange;">pollination effect</mark>. When a bee pollinates a flower and is returning to a hive, any flower it flies over has a chance to be fertilized (have a growth tick applied to it). It can do this up to 10 times before it needs to visit a hive to reset the counter.&#x20;

Mutations reuse the vanilla mechanic by allowing bees to transform one object into another. The bee would simply fly over a target `item|block|fluid|entity` and the target would be transformed into different `item|block|fluid|entity`.

The mutation customization component simply contains the recipe ID for the mutations which the bee can perform and the mutation limit.

{% code title="Template:" %}
```json
"resourcefulbees:mutation/v1": {
  "count": 5,
  "mutation": "resourcefulbees:mutations/template"
}
```
{% endcode %}



## Identifier

***

The root JSON of the mutation customization component looks like this:

```json
"resourcefulbees:mutation/v1": {
    ...
}
```

The identifier of the component is as such:

```
resourcefulbees:mutation/v1
```

## Customization Options

***

### <mark style="color:orange;">`count`</mark>

The number of mutations that can be performed before the bee needs to visit a hive to reset the counter.

***

{% hint style="info" %}
**Name:** Mutation Count

**Key:** <mark style="color:orange;">`count`</mark>

**Type:** Integer

**Default:** `10`
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:mutation/v1": {
  "count": 5,
  "mutation": "resourcefulbees:mutations/template"
}
```

</details>



### <mark style="color:orange;">`mutation`</mark>

The ID for the mutation recipe. The format is that of a [ResourceLocation](https://minecraft.wiki/w/Resource\_location).

***

{% hint style="info" %}
**Name:** Mutation

**Key:** <mark style="color:orange;">`mutation`</mark>

**Type:** [ResourceLocation](https://minecraft.wiki/w/Resource\_location)

**Default:** `No Mutation`
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:mutation/v1": {
  "mutation": "resourcefulbees:mutations/template"
}
```

</details>

