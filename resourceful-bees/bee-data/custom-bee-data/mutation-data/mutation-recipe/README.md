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

# Mutation Recipe

{% hint style="danger" %}
**todo: move this to a separate recipes category**
{% endhint %}

Mutations utilize the recipe system to make them more data pack friendly. One benefit of using the recipe system is that a mutation can be created once and shared among many different bees.

{% code title="Template:" %}
```json
{
  "type": "resourcefulbees:mutation",
  "mutations" : [
    {
      "input": {
        "type": "block",
        "block": {
          "id": "minecraft:stone"
        },
        "chance": 0.5
      },
      "outputs" : [
        {
          "type": "block",
          "block": {
            "id": "minecraft:end_stone"
          }
        }
      ]
    }
  ]
}
```
{% endcode %}



## Recipe Type

***

Every recipe JSON is required to have a type. For mutations the type is <mark style="color:orange;">`resourcefulbees:mutation`</mark>

```json
{
    "type": "resourcefulbees:mutation",
    ...
}
```



## Customization Options

***

### <mark style="color:orange;">`input`</mark>

The item/block/fluid/entity being transformed.

***

{% hint style="info" %}
**Name:** Mutation Input

**Key:** <mark style="color:orange;">`input`</mark>

**Type:** [MutationType](mutation-type.md)

**Default:** This value is required or the recipe won't load!
{% endhint %}

<details>

<summary>Example</summary>

```json
"input": {
  "type": "block",
  "block": {
    "id": "minecraft:stone"
  },
  "chance": 0.5
}
```

</details>



### <mark style="color:orange;">`outputs`</mark>

A list of possible transformation results, which can be an item, block, fluid, or entity.

***

{% hint style="info" %}
**Name:** Mutation Outputs

**Key:** <mark style="color:orange;">`outputs`</mark>

**Type:** [MutationType\[\]](mutation-type.md)

**Default:** This value is required or the recipe won't load!
{% endhint %}

<details>

<summary>Example</summary>

```json
"outputs" : [
  {
    "type": "block",
    "block": {
      "id": "minecraft:end_stone"
    }
  }
]
```

</details>

