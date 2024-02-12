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

# Combat Data

The combat customization component is responsible for defining a bee's survival ability and hostility:

* Is the bee passive?
* Does it lose its stinger after attacking?
* Does it inflict poison?
* Can it take damage?
* General attributes of the entity such as:
  * Max health
  * Armor
  * Attack damage
  * Knockback
  * Any registered attribute vanilla or modded can be customized

{% code title="Template:" %}
```json
"resourcefulbees:combat/v1": {
  "removeStingerOnAttack": false,
  "inflictsPoison": false,
  "attributes": {
    "generic.attack_damage": 0,
    "generic.max_health": 2,
    "generic.armor": 5,
    "generic.armor_toughness": 10,
    "generic.attack_knockback": 3
  }
}
```
{% endcode %}



## Identifier

***

The root JSON of the combat customization component looks like this:

```json
"resourcefulbees:combat/v1": {
    ...
}
```

The identifier of the component is as such:

```
resourcefulbees:combat/v1
```



## Customization Options

***

### <mark style="color:orange;">`isPassive`</mark>

When `true`, the bee will not attack entities back.

***

{% hint style="info" %}
**Name:** Passive

**Key:** <mark style="color:orange;">`isPassive`</mark>

**Type:** Boolean

**Default:** `false`
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:combat/v1": {
  "isPassive": true
}
```

</details>



### <mark style="color:orange;">`removeStingerOnAttack`</mark>

When `true`, the bees stinger will be removed on attack. If a bees stinger is removed, it has a chance of randomly dying a bit after the stinger was removed.

***

{% hint style="info" %}
**Name:** Remove Stinger

**Key:** <mark style="color:orange;">`removeStingerOnAttack`</mark>

**Type:** Boolean

**Default:** `true`
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:combat/v1": {
  "removeStingerOnAttack": false
}
```

</details>



### <mark style="color:orange;">`inflictsPoison`</mark>

When `true`, the targeted entity will be inflicted with poison when attacked.

***

{% hint style="info" %}
**Name:** Inflict Poison

**Key:** <mark style="color:orange;">`inflictsPoison`</mark>

**Type:** Boolean

**Default:** `true`
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:combat/v1": {
  "inflictsPoison": false
}
```

</details>



### <mark style="color:orange;">`isInvulnerable`</mark>

When `true`, the bee will not take any damage.

***

{% hint style="info" %}
**Name:** Invulnerable

**Key:** <mark style="color:orange;">`isInvulnerable`</mark>

**Type:** Boolean

**Default:** `false`
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:combat/v1": {
  "attributes": {
    "generic.attack_damage": 0,
    "generic.max_health": 2,
    "generic.armor": 5,
    "generic.armor_toughness": 10,
    "generic.attack_knockback": 3
  }
}
```

</details>



### <mark style="color:orange;">`attributes`</mark>

A map of [attributes](https://minecraft.wiki/w/Attribute#Attributes) and their values. The keys are the Attribute ID's and the values are the attribute value.

***

{% hint style="info" %}
**Name:** Invulnerable

**Key:** <mark style="color:orange;">`attributes`</mark>

**Type:** Map<[Attribute](https://minecraft.wiki/w/Attribute#Attributes), Double>

**Default:**

```
"generic.max_health": 10,
"generic.flying_speed": 0.6,
"generic.movement_speed": 0.3,
"generic.attack_damage": 1,
"generic.follow_range": 48,
"generic.armor": 0,
"generic.armor_toughness": 0,
"generic.attack_knockback": 0
```
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:combat/v1": {
  "attributes": {
    "generic.attack_damage": 0,
    "generic.max_health": 2,
    "generic.armor": 5,
    "generic.armor_toughness": 10,
    "generic.attack_knockback": 3
  }
}
```

</details>

