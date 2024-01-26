# Core Data

## Identifier

```
resourcefulbees:core/v1
```

## Data Object

### Honeycomb / <mark style="color:red;">`honeycombVariation`</mark> / String

Honeycomb variation represents the identifier of a honeycomb variation. More information about honeycomb variations can be found in the [Honeycomb Data](https://app.gitbook.com/o/GQdOlzzIqftgC5xMgxnG/s/S5sbJi5FdsoHIzK2cvL5/) section.

{% hint style="info" %}
**Default:** No Honeycomb
{% endhint %}

### Flower / <mark style="color:red;">`flower`</mark> / [HolderSet\<Block>](https://app.gitbook.com/s/uHMOruowjctiLyjG3esg/)

Flowers can be represented in many ways as a block holder such as a tag, a list of blocks, or a single block.

{% hint style="info" %}
**Default:** minecraft:poppy
{% endhint %}

### Entity Flower / <mark style="color:red;">`entityFlower`</mark> / [HolderSet\<Entity>](https://app.gitbook.com/s/uHMOruowjctiLyjG3esg/)

Entity flowers like block flowers can be represented in many ways too such as like a block holder a tag, a list of entities, or a single entity.

{% hint style="info" %}
**Default:** Empty Set
{% endhint %}

### Max Hive Time / <mark style="color:red;">`maxTimeInHive`</mark> / Integer (≥600)

Max Hive Time represents the max amount of a time a bee can spend in a hive at a time. This time will be adjusted depending on the hive or apiary but this is the base time.

{% hint style="info" %}
**Default:** 2400
{% endhint %}

### Lore / <mark style="color:red;">`lore`</mark> / [Component](https://minecraft.fandom.com/wiki/Raw\_JSON\_text\_format)\[]

Lore is used to show in JEI this is useful to let your players know if this bee is gotten another way than conventional means.

{% hint style="info" %}
**Default:** Empty List
{% endhint %}
