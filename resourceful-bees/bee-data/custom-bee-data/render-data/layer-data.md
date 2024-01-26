# Layer Data

## Data Object

### Color / <mark style="color:red;">`color`</mark> / Color

The color that will be applied to the layers texture, this should not be set if your texture is not made to be colored.

{% hint style="success" %}
Optional
{% endhint %}

### Texture / <mark style="color:red;">`texture`</mark> / String

The texture applied to this layer, this is a simple string that is used to lead to the texture.

For example if the texture is "creeper" it will use `resourcefulbees:textures/entity/creeper.png` for the normal texture and suffix `_angry` for the angry texture.

{% hint style="info" %}
**Default:** Missing Textures
{% endhint %}

### Layer Effect / <mark style="color:red;">`layerEffect`</mark> / LayerEffect

The effect that the layer will have, there are 3 options available.

{% tabs %}
{% tab title="NONE" %}
This effect is to not do anything special, its for the default and should never be manually set to.
{% endtab %}

{% tab title="ENCHANTED" %}
This effect applies the enchantment glint effect to the layer.
{% endtab %}

{% tab title="GLOW" %}
This is used to apply a fullbright glow to the texture similar to the flash a creeper makes.\
This combined with the pulseFrequency field will allow for the same effect as a creeper.
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Default:** NONE
{% endhint %}

### Pollen Layer / <mark style="color:red;">`isPollen`</mark> / Boolean

This determines if the layer should only show when the bee has pollen.

{% hint style="info" %}
**Default:** false
{% endhint %}

### Pulse Frequency / <mark style="color:red;">`pulseFrequency`</mark> / Float (5.0-100.0)

Pulse frequency is used with the GLOW LayerEffect to allow for a flashing glow.

{% hint style="info" %}
**Default:** 0
{% endhint %}
