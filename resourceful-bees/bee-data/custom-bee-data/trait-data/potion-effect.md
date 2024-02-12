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

# Potion Effect

## Customization Options

***

### <mark style="color:orange;">`effect`</mark>

The ResourceLocation for any registered MobEffect, including modded ones.

***

{% hint style="info" %}
**Name:** Effect

**Key:** <mark style="color:orange;">`effect`</mark>

**Type:** ResourceLocation

**Default:** `minecraft:luck`
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "auras": [
    {
      "aura": "POTION",
      "potionEffect": {
        "effect": "minecraft:blindness"
      }
    }
  ]
}
```

</details>

### <mark style="color:orange;">`strength`</mark>

The strength of the potion effect.

***

{% hint style="info" %}
**Name:** Strength

**Key:** <mark style="color:orange;">`strength`</mark>

**Type:** Integer

**Range:** 0 - 4

**Default:** 1
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "auras": [
    {
      "aura": "POTION",
      "potionEffect": {
        "effect": "minecraft:hunger",
        "strength": 2
      }
    }
  ]
}
```

</details>

