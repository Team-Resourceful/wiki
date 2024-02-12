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

# Trait Data

A unique feature to Resourceful Bees. traits group together:

* Particle Effects
* Damage and Potion Immunities
* Damage Types and Potion Effects
* Special Abilities
* and Auras

Traits enable users to breathe life into infinite variations of bees that can be godly, pesky, helpful, or just downright evil.

{% code title="Template:" %}
```json
"resourcefulbees:trait/v1": {
  "auraRange": 20,
  "traits": ["nether", "wither"]
}
```
{% endcode %}



## Identifier

***

The root JSON of the trait customization component looks like this:

```json
"resourcefulbees:trait/v1": {
    ...
}
```

The identifier of the component is as such:

<pre><code><strong>resourcefulbees:trait/v1
</strong></code></pre>



## Customization Options

***

### <mark style="color:orange;">`auraRange`</mark>

The range within which players would be affected by the aura. This value is the number of blocks.

***

{% hint style="info" %}
**Name:** Aura Range

**Key:** <mark style="color:orange;">`auraRange`</mark>

**Type:** Integer

**Range:** 3 - 20

**Default:** `10`
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:trait/v1": {
  "auraRange": 20
}
```

</details>



### <mark style="color:orange;">`traits`</mark>

The list of traits given to the bee.

***

{% hint style="info" %}
**Name:** Traits List

**Key:** <mark style="color:orange;">`traits`</mark>

**Type:** String\[]

**Default:** `Optional/Empty`
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:trait/v1": {
  "traits": ["nether", "wither"]
}
```

</details>

###
