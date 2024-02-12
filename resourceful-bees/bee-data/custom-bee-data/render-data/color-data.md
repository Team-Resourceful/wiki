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

# Color Data

The color customization component handles the Bee Jar and Spawn Egg colors.&#x20;

{% code title="Template:" %}
```json
"resourcefulbees:rendering/v1": {
  "ColorData": {
    "spawnEggPrimaryColor": 16444375,
    "spawnEggSecondaryColor": 13789470,
    "jarColor": 6266528
  }
}
```
{% endcode %}



## Customization Options

***

### <mark style="color:orange;">`spawnEggPrimaryColor`</mark>

Sets the primary color used on the spawn egg item.

***

{% hint style="info" %}
**Name:** Primary Spawn Egg Color

**Key:** <mark style="color:orange;">`spawnEggPrimaryColor`</mark>

**Type:** Color

**Default:** No Color
{% endhint %}

{% tabs %}
{% tab title="Integer Color" %}
```json
"resourcefulbees:rendering/v1": {
  "ColorData": {
    "spawnEggPrimaryColor": 16444375
  }
}
```
{% endtab %}

{% tab title="Named Color" %}
```json
"resourcefulbees:rendering/v1": {
  "ColorData": {
    "spawnEggPrimaryColor": "red"
  }
}
```
{% endtab %}

{% tab title="Hex Color" %}
```json
"resourcefulbees:rendering/v1": {
  "ColorData": {
    "spawnEggPrimaryColor": "#FF0000"
  }
}
```
{% endtab %}
{% endtabs %}



### <mark style="color:orange;">`spawnEggSecondaryColor`</mark>

Sets the secondary color used on the spawn egg item.

***

{% hint style="info" %}
**Name:** Secondary Spawn Egg Color

**Key:** <mark style="color:orange;">`spawnEggSecondaryColor`</mark>

**Type:** Color

**Default:** No Color
{% endhint %}

{% tabs %}
{% tab title="Integer Color" %}
```json
"resourcefulbees:rendering/v1": {
  "ColorData": {
    "spawnEggSecondaryColor": 16444375
  }
}
```
{% endtab %}

{% tab title="Named Color" %}
```json
"resourcefulbees:rendering/v1": {
  "ColorData": {
    "spawnEggSecondaryColor": "red"
  }
}
```
{% endtab %}

{% tab title="Hex Color" %}
```json
"resourcefulbees:rendering/v1": {
  "ColorData": {
    "spawnEggSecondaryColor": "#FF0000"
  }
}
```
{% endtab %}
{% endtabs %}



### <mark style="color:orange;">`jarColor`</mark>

The color used on the jar when the bee is in the bee jar.

***

{% hint style="info" %}
**Name:** Bee Jar Color

**Key:** <mark style="color:orange;">`jarColor`</mark>

**Type:** Color

**Default:** No Color
{% endhint %}

{% tabs %}
{% tab title="Integer Color" %}
```json
"resourcefulbees:rendering/v1": {
  "ColorData": {
    "jarColor": 16444375
  }
}
```
{% endtab %}

{% tab title="Named Color" %}
```json
"resourcefulbees:rendering/v1": {
  "ColorData": {
    "jarColor": "red"
  }
}
```
{% endtab %}

{% tab title="Hex Color" %}
```json
"resourcefulbees:rendering/v1": {
  "ColorData": {
    "jarColor": "#FF0000"
  }
}
```
{% endtab %}
{% endtabs %}

