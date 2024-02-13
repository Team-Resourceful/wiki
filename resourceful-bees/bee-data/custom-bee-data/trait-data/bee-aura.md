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

# Bee Aura

<details>

<summary>Resourceful Bees provides a set number of predefined Auras (with customizable values) out of the box:</summary>

<mark style="color:orange;">**Burning**</mark>

Players within the aura's range are set on fire.

<mark style="color:orange;">**Potion**</mark>

Players within the aura's range have a potion effect applied to them.

<mark style="color:orange;">**Healing**</mark>

Players within the aura's range are healed an amount equal to the modifier value.

<mark style="color:orange;">**Damaging**</mark>

Players within the aura's range are damaged using a defined damage source and strength.

<mark style="color:orange;">**Experience**</mark>

Players within the aura's range are given experience equal to the modifier value.

<mark style="color:orange;">**Experience Drain**</mark>

Players within the aura's range are drained of experience equal to the modifier value.

</details>

{% code title="Template:" %}
```json
{
  "auras": [
    {
      "potionEffect": {
        "effect": "minecraft:instant_health",
        "strength": 2
      },
      "modifier": 3,
      "calmingDisabled": true,
      "aura": "EXPERIENCE",
      "damageEffect": {
        "source": "minecraft:in_fire",
        "hasEntity": false,
        "strength": 0
      }
    }
  ]
}
```
{% endcode %}

## Customization Options

***

### <mark style="color:orange;">`aura`</mark>

The Aura Type determines the effect that the aura has on the player. It is a required value for the Aura to load properly.

***

{% hint style="info" %}
**Name:** Aura Type

**Key:** <mark style="color:orange;">`aura`</mark>

**Type:** AuraType | Enum

**Default:** Value is **required.**
{% endhint %}

{% tabs %}
{% tab title="BURNING" %}
{% hint style="info" %}
**Beneficial:** `false`

**Particle:** `ParticleTypes.FLAME`

**Effect:** Players within the aura's range are set on fire.
{% endhint %}

```json
{
  "auras": [
    {
      "aura": "BURNING"
    }
  ]
}
```
{% endtab %}

{% tab title="POTION" %}
{% hint style="info" %}
**Beneficial:** `false`

**Particle:** `ParticleTypes.WITCH`

**Effect:** Players within the aura's range have the defined <mark style="color:orange;">`potionEffect`</mark> applied to them.
{% endhint %}

```json
{
  "auras": [
    {
      "aura": "POTION"
    }
  ]
}
```
{% endtab %}

{% tab title="HEALING" %}
{% hint style="info" %}
**Beneficial:** `true`

**Particle:** `ParticleTypes.HAPPY_VILLAGER`

**Effect:** Players within the aura's range are healed using the <mark style="color:orange;">`modifier`</mark> amount.
{% endhint %}

```json
{
  "auras": [
    {
      "aura": "HEALING"
    }
  ]
}
```
{% endtab %}

{% tab title="DAMAGING" %}
{% hint style="info" %}
**Beneficial:** `false`

**Particle:** `ParticleTypes.CRIT`

**Effect:** Players within the aura's range are damaged using the damage source and strength values defined in <mark style="color:orange;">`damageEffect`</mark>.
{% endhint %}

```json
{
  "auras": [
    {
      "aura": "DAMAGING"
    }
  ]
}
```
{% endtab %}

{% tab title="EXPERIENCE" %}
{% hint style="info" %}
**Beneficial:** `true`

**Particle:** `ParticleTypes.ENCHANT`

**Effect:** Players within the aura's range are given experience equal to the <mark style="color:orange;">`modifier`</mark> value.
{% endhint %}

```json
{
  "auras": [
    {
      "aura": "EXPERIENCE"
    }
  ]
}
```
{% endtab %}

{% tab title="EXPERIENCE DRAIN" %}
{% hint style="info" %}
**Beneficial:** `false`

**Particle:** `ParticleTypes.POOF`

**Effect:** Players within the aura's range are drained of experience equal to the <mark style="color:orange;">`modifier`</mark> value.
{% endhint %}

```json
{
  "auras": [
    {
      "aura": "EXPERIENCE_DRAIN"
    }
  ]
}
```
{% endtab %}
{% endtabs %}



### <mark style="color:orange;">`damageEffect`</mark>

Used when the aura type is `DAMAGING` The damage source and strength values are defined in the [damage-effect.md](damage-effect.md "mention").

***

{% hint style="info" %}
**Name:** Damage Effect

**Key:** <mark style="color:orange;">`damageEffect`</mark>

**Type:** [DamageEffect](damage-effect.md)

**Default:** `DamageEffect.DEFAULT`
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "auras": [
    {
      "aura": "BURNING",
      "damageEffect": {
        "source": "minecraft:in_fire",
        "hasEntity": false,
        "strength": 0
      }
    }
  ]
}
```

</details>



### <mark style="color:orange;">`potionEffect`</mark>

Used when the aura type is `POTION` The effect and strength values are defined in the [potion-effect.md](potion-effect.md "mention").

***

{% hint style="info" %}
**Name:** Potion Effect

**Key:** <mark style="color:orange;">`potionEffect`</mark>

**Type:** [PotionEffect](potion-effect.md)

**Default:** PotionEffect`.DEFAULT`
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "auras": [
    {
      "aura": "BURNING",
      "potionEffect": {
        "effect": "minecraft:instant_health",
        "strength": 2
      }
    }
  ]
}
```

</details>



### <mark style="color:orange;">`modifier`</mark>

The modifier value is used with the `HEALING`, `EXPERIENCE`, and `EXPERIENCE_DRAIN` aura types.&#x20;

{% tabs %}
{% tab title="HEALING" %}
When used with the `HEALING` aura type, the value equals the amount healed.
{% endtab %}

{% tab title="EXPERIENCE" %}
When used with the `EXPERIENCE` aura type, the value equals the amount of experience received.
{% endtab %}

{% tab title="EXPERIENCE_DRAIN" %}
When used with the `EXPERIENCE_DRAIN` aura type, the value equals the amount of experience taken.
{% endtab %}
{% endtabs %}

***

{% hint style="info" %}
**Name:** Modifier

**Key:** <mark style="color:orange;">`modifier`</mark>

**Type:** Integer

**Range:** ≥0

**Default:** 0
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "auras": [
    {
      "aura": "BURNING",
      "modifier": 3
    }
  ]
}
```

</details>



### <mark style="color:orange;">`calmingDisabled`</mark>

The aura can be disabled by the "calming" status effect when this value is set to `true`.

***

{% hint style="info" %}
**Name:** Calming Disabled

**Key:** <mark style="color:orange;">`calmingDisabled`</mark>

**Type:** Boolean

**Default:** `false`
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "auras": [
    {
      "aura": "BURNING",
      "calmingDisabled": true
    }
  ]
}
```

</details>

