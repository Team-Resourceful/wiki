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

# Damage Effect

## Customization Options

***

### <mark style="color:orange;">`source`</mark>

The ResourceLocation for any registered MobEffect, including modded ones.

***

{% hint style="info" %}
**Name:** Damage Source

**Key:** <mark style="color:orange;">`source`</mark>

**Type:** ResourceLocation

**Default:** `minecraft:cactus`
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "auras": [
    {
      "aura": "DAMAGING",
      "damageEffect": {
        "source": "minecraft:in_fire"
      }
    }
  ]
}
```

</details>

### <mark style="color:orange;">`hasEntity`</mark>

If the damage source is sourced from an entity, this should be marked as `true`. This allows for the death messages to be displayed correctly in the event the target entity dies.

***

{% hint style="info" %}
**Name:** Has Entity Source

**Key:** <mark style="color:orange;">`hasEntity`</mark>

**Type:** Boolean

**Default:** `false`
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "auras": [
    {
      "aura": "DAMAGING",
      "damageEffect": {
        "source": "minecraft:thorns",
        "hasEntity": true
      }
    }
  ]
}
```

</details>



### <mark style="color:orange;">`strength`</mark>

The strength of the damage effect.

***

{% hint style="info" %}
**Name:** Strength

**Key:** <mark style="color:orange;">`strength`</mark>

**Type:** Integer

**Range:** 0 - 20

**Default:** 0
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "auras": [
    {
      "aura": "DAMAGING",
      "potionEffect": {
        "effect": "minecraft:wither",
        "strength": 5
      }
    }
  ]
}
```

</details>

