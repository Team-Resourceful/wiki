# Breed Data

## Identifier

```
resourcefulbees:breeding/v1
```

## Data Object

### Parents / <mark style="color:red;">`parents`</mark> / [BeeFamily](bee-family.md)\[]

Parents is used to signify the pair of bees what will make this bee.

{% hint style="info" %}
**Default:** Empty List
{% endhint %}

### Feed Item / <mark style="color:red;">`feedItem`</mark> / [HolderSet\<Item>](https://app.gitbook.com/s/uHMOruowjctiLyjG3esg/)

Feed Items are the items that you need to use on a bee to breed it.

{% hint style="info" %}
**Default:** minecraft:poppy
{% endhint %}

### Feed Return Item / <mark style="color:red;">`feedReturnItem`</mark> / ItemStack

Layer data

{% hint style="success" %}
Optional
{% endhint %}

### Feed Amount / <mark style="color:red;">`feedAmount`</mark> / Integer(≥1)

The amount of feed items that are needed to be feed to the bee for it to be able to breed.

{% hint style="info" %}
**Default:** 1
{% endhint %}

### Child Growth Delay / <mark style="color:red;">`childGrowthDelay`</mark> / Integer(≤0)

The time in ticks that a baby bee will stay a baby bee.

{% hint style="info" %}
**Default:** -24000
{% endhint %}

### Breed Delay / <mark style="color:red;">`breedDelay`</mark> / Integer(≥0)

The time in ticks until bees can breed again.

{% hint style="info" %}
**Default:** 6000
{% endhint %}
