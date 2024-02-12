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

# Damage Type

## Customization Options

***

### <mark style="color:orange;">`damageType`</mark>

Currently, there are only two acceptable choices:

{% tabs %}
{% tab title="explosive" %}
When the bee attacks, the targeted entity explodes.
{% endtab %}

{% tab title="setOnFire" %}
When the bee attacks, the target entity is set on fire.
{% endtab %}
{% endtabs %}

***

{% hint style="info" %}
**Name:** Damage Type

**Key:** <mark style="color:orange;">`damageType`</mark>

**Type:** String

**Default:** Empty String
{% endhint %}

<details>

<summary>Example</summary>

<pre class="language-json"><code class="lang-json"><strong>{
</strong>  "damageTypes": [
    {
      "damageType": "explosive",
      "amplifier": 3
    },
    {
      "damageType": "setOnFire",
      "amplifier": 4
    }
  ]
}
</code></pre>

</details>



### <mark style="color:orange;">`amplifier`</mark>

The strength of the damage effect.

***

{% hint style="info" %}
**Name:** Amplifier

**Key:** <mark style="color:orange;">`amplifier`</mark>

**Type:** Integer

**Range:** ≥0

**Default:** 0
{% endhint %}

<details>

<summary>Example</summary>

```json
{
  "damageTypes": [
    {
      "damageType": "explosive",
      "amplifier": 3
    }
  ]
}
```

</details>

