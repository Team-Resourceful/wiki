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

# Layer Data

The layer customization component is responsible for defining key aspects of a specific render layer. There are several aspects of a layer that can be modified:

* Effect
* Pulse Frequency
* Color
* Texture
* Visibility when carrying pollen

{% code title="Template:" %}
```json
"resourcefulbees:rendering/v1": {
  "layers": [
    {
      "layerEffect": "GLOW",
      "pulseFrequency": 5.0,
      "color": 65535,
      "texture": "/example/pollen",
      "isPollen": false
    }
  ]
}
```
{% endcode %}



## Customization Options

***

### <mark style="color:orange;">`color`</mark>

The color that will be applied to the layers texture, this should not be set if your texture is not made to be colored.

***

{% hint style="info" %}
**Name:** Color

**Key:** <mark style="color:orange;">`color`</mark>

**Type:** Color

**Default:** Optional
{% endhint %}

{% tabs %}
{% tab title="Integer Color" %}
```json
"resourcefulbees:rendering/v1": {
  "layers": [
    {
      "color": 52020
    }
  ]
}
```
{% endtab %}

{% tab title="Named color" %}
```json
"resourcefulbees:rendering/v1": {
  "layers": [
    {
      "color": "blanchedalmond"
    }
  ]
}
```
{% endtab %}

{% tab title="Hex Color" %}
```json
"resourcefulbees:rendering/v1": {
  "layers": [
    {
      "color": "#442920"
    }
  ]
}
```
{% endtab %}
{% endtabs %}



### <mark style="color:orange;">`texture`</mark>

The texture for the layer. Each texture requires two versions to exist: <mark style="color:orange;">normal</mark> and <mark style="color:red;">angry</mark>. The angry texture should use the same name as the normal texture with the suffix `_angry` appended to it.&#x20;

{% tabs %}
{% tab title="Normal" %}
`creeper.png`
{% endtab %}

{% tab title="Angry" %}
`creeper_angry.png`
{% endtab %}
{% endtabs %}

***

{% hint style="info" %}
**Name:** Texture

**Key:** <mark style="color:orange;">`texture`</mark>

**Type:** String

**Default:** Missing Texture
{% endhint %}

<details>

<summary>Example:</summary>

```json
"resourcefulbees:rendering/v1": {
  "layers": [
    {
      "texture": "/example/pollen"
    }
  ]
}
```

</details>



### <mark style="color:orange;">`layerEffect`</mark>

The effect the layer will have. There are 3 options available:

{% tabs %}
{% tab title="NONE" %}
This effect does nothing. It is the default option and does not need to be set explicitly.
{% endtab %}

{% tab title="ENCHANTED" %}
This effect applies the enchantment glint effect to the layer.
{% endtab %}

{% tab title="GLOW" %}
This is used to apply a `fullbright` glow to the texture similar to the flash a creeper makes.\
This combined with the <mark style="color:orange;">`pulseFrequency`</mark> field will allow for the same effect as a creeper.
{% endtab %}
{% endtabs %}

***

{% hint style="info" %}
**Name:** Layer Effect

**Key:** <mark style="color:orange;">`layerEffect`</mark>

**Type:** Enum | LayerEffect

**Default:** `NONE`
{% endhint %}

{% tabs %}
{% tab title="NONE" %}
This does not have to be set explicitly. The two examples below do the same thing:

{% code title="Explicit:" %}
```json
"resourcefulbees:rendering/v1": {
  "layers": [
    {
      "layerEffect": "NONE"
    }
  ]
}
```
{% endcode %}

{% code title="Implicit:" %}
```json
"resourcefulbees:rendering/v1": {

}
```
{% endcode %}
{% endtab %}

{% tab title="ENCHANTED" %}
```json
"resourcefulbees:rendering/v1": {
  "layers": [
    {
      "layerEffect": "ENCHANTED"
    }
  ]
}
```
{% endtab %}

{% tab title="GLOW" %}
```json
"resourcefulbees:rendering/v1": {
  "layers": [
    {
      "layerEffect": "GLOW"
    }
  ]
}
```
{% endtab %}
{% endtabs %}



### <mark style="color:orange;">`isPollen`</mark>

When `true`, this layer will only be visible if the bee is carrying pollen.

***

{% hint style="info" %}
**Name:** Pollen Layer

**Key:** <mark style="color:orange;">`isPollen`</mark>

**Type:** Boolean

**Default:** `false`
{% endhint %}

<details>

<summary>Example:</summary>

```json
"resourcefulbees:rendering/v1": {
  "layers": [
    {
      "isPollen": true
    }
  ]
}
```

</details>



### <mark style="color:orange;">`pulseFrequency`</mark>

Used with the <mark style="color:orange;">`GLOW`</mark> <mark style="color:orange;">`layerEffect`</mark> to create a flashing effect.

***

{% hint style="info" %}
**Name:** Pulse Frequency

**Key:** <mark style="color:orange;">`pulsefrequency`</mark>

**Type:** Float

**Range:** 5.0 - 100.0

**Default:** 0
{% endhint %}

<details>

<summary>Example:</summary>

```json
"resourcefulbees:rendering/v1": {
  "layers": [
    {
      "layerEffect": "GLOW",
      "pulseFrequency": 5.0
    }
  ]
}
```

</details>

