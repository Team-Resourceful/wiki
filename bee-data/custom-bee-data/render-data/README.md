# Render Data

## Identifier

```
resourcefulbees:rendering/v1
```

## Data Object

### Layers / <mark style="color:red;">`layers`</mark> / [LayerData](layer-data.md)\[]

Layers are used to add custom textures on top of the base model and allow them to have special effects or be enabled by special means.

{% hint style="info" %}
**Default:** Empty List
{% endhint %}

### Color Data / <mark style="color:red;">`ColorData`</mark> / [ColorData](color-data.md)

Color data is used to set the colors for things like jars and spawn eggs.

{% hint style="info" %}
**Default:** No Colors
{% endhint %}

### Model / <mark style="color:red;">`model`</mark> / [ResourceLocation](https://minecraft.fandom.com/wiki/Resource\_location)

Model is a reference to the location where the GeckoLib JSON geo model is stored.

{% hint style="info" %}
**Default:** <mark style="color:blue;">resourcefulbees</mark>:<mark style="color:green;">geo/base.geo.json</mark>
{% endhint %}

### Texture / <mark style="color:red;">`texture`</mark> / String

Texture is used as the base texture for the model and will always be displayed on the bee no matter what.\
For example if the texture is "creeper" it will use `resourcefulbees:textures/entity/creeper.png` for the normal texture and suffix `_angry` for the angry texture.

{% hint style="info" %}
**Default:** Missing Textures
{% endhint %}

### Animation / <mark style="color:red;">`animation`</mark> / [ResourceLocation](https://minecraft.fandom.com/wiki/Resource\_location)

Animation is a reference to the location where the GeckoLib JSON animation is stored.

{% hint style="info" %}
**Default:** <mark style="color:blue;">resourcefulbees:</mark><mark style="color:blue;"><mark style="color:green;">animations/bee.animation.json<mark style="color:green;"></mark>
{% endhint %}

### Size Modifier / <mark style="color:red;">`sizeModifier`</mark> / Float (0.5-2.0)

Size modifier determines the scale of the bee when rendered in-game.

{% hint style="info" %}
**Default:** 1.0
{% endhint %}

