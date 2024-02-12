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

# Render Data

The render customization component is responsible for defining how the bee looks. The data is only used on the client. There are several visual aspects of a bee that can be modified:

* Size
* Model
* Animations
* Textures/Layers
* UI Colors

{% code title="Template:" %}
```json
"resourcefulbees:rendering/v1": {
  "layers": [
    {
      "pulseFrequency": 5.0,
      "color": 52020
    },
    {
      "layerEffect": "GLOW",
      "pulseFrequency": 5.0,
      "color": 65535
    }
  ],
  "model": "resourcefulbees:geo/base.geo.json"
  "texture": "/oreo/oreo_bee",
  "animation": "resourcefulbees:animations/bee.animation.json"
  "ColorData": {
    "spawnEggPrimaryColor": "#442920",
    "spawnEggSecondaryColor": "#e1d9b8",
    "jarColor": "#442920"
  },
  "sizeModifier": 1.25
}
```
{% endcode %}

## Identifier

***

The root JSON of the rendering customization component looks like this:

```json
"resourcefulbees:rendering/v1": {
    ...
}
```

The identifier of the component is as such:

```
resourcefulbees:rendering/v1
```



## Customization Options

***

### <mark style="color:orange;">`layers`</mark>

Layers are used to add custom textures on top of the base texture and allow them to have special effects or be enabled by special means.

{% hint style="warning" %}
**Warning:** Increasing the number of textures rendered on a bee will impact performance. It is recommended to use the least number of layers necessary!
{% endhint %}

***

{% hint style="info" %}
**Name:** Layers

**Key:** <mark style="color:orange;">`layers`</mark>

**Type:** [LayerData\[\]](layer-data.md)

**Default:** Empty List
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:rendering/v1": {
  "layers": [
    {
      "pulseFrequency": 5.0,
      "color": 52020
    },
    {
      "layerEffect": "GLOW",
      "pulseFrequency": 5.0,
      "color": 65535
    }
  ]
}
```

</details>



### <mark style="color:orange;">`ColorData`</mark>

Color data is used to set the colors for things like jars and spawn eggs.

***

{% hint style="info" %}
**Name:** Color Data

**Key:** <mark style="color:orange;">`ColorData`</mark>

**Type:** [ColorData](color-data.md)

**Default:** No Colors
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:rendering/v1": {
  "ColorData": {
    "spawnEggPrimaryColor": "#442920",
    "spawnEggSecondaryColor": "#e1d9b8",
    "jarColor": "#442920"
  }
}
```

</details>



### <mark style="color:orange;">`model`</mark>

The location where the [GeckoLib geo file](https://github.com/bernie-g/geckolib/wiki/Geo-Models-\(Geckolib3\)) is stored.

{% hint style="danger" %}
**Beware:** The more complex the model is, the more impact it will have on performance. It is **highly** recommended to keep custom models as simple as possible!
{% endhint %}

***

{% hint style="info" %}
**Name:** Model

**Key:** <mark style="color:orange;">`model`</mark>

**Type:** [ResourceLocation](https://minecraft.wiki/w/Resource\_location)

**Default:** `resourcefulbees:geo/base.geo.json`
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:rendering/v1": {
  "model": "resourcefulbees:geo/base.geo.json"
}
```

</details>



### <mark style="color:orange;">`texture`</mark>

The base texture for the bee. Each texture requires two versions to exist: <mark style="color:orange;">normal</mark> and <mark style="color:red;">angry</mark>. The angry texture should use the same name as the normal texture with the suffix `_angry` appended to it.&#x20;

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

<summary>Example</summary>

```json
"resourcefulbees:rendering/v1": {
  "texture": "/oreo/oreo_bee"
}
```

</details>



### <mark style="color:orange;">`animation`</mark>

The location where the [GeckoLib animation file](https://github.com/bernie-g/geckolib/wiki/Geo-Models-\(Geckolib3\)) is stored.

***

{% hint style="info" %}
**Name:** Texture

**Key:** <mark style="color:orange;">`texture`</mark>

**Type:** [ResourceLocation](https://minecraft.wiki/w/Resource\_location)

**Default:** `resourcefulbees:animations/bee.animation.json`
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:rendering/v1": {
  "animation": "resourcefulbees:animations/bee.animation.json"
}
```

</details>

{% hint style="warning" %}
**Note**: Only vanilla bee animations are currently supported!
{% endhint %}



### <mark style="color:orange;">`sizeModifier`</mark>

The scale of the bee when rendered in-game.

{% hint style="success" %}
**Note:** A value of 2.0 would double the size of the bee, while a value of 0.5 would shrink the bee to half its normal size.&#x20;
{% endhint %}

***

{% hint style="info" %}
**Name:** Size Modifier

**Key:** <mark style="color:orange;">`sizeModifier`</mark>

**Type:** Float

**Range:** 0.5 - 2.0

**Default: 1.0**
{% endhint %}

<details>

<summary>Example</summary>

```
"resourcefulbees:rendering/v1": {
  "sizeModifier": 1.25
}
```

</details>

