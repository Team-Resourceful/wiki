# Combat Data

## Identifier

```
resourcefulbees:combat/v1
```

## Data Object

### Passive / <mark style="color:red;">`isPassive`</mark> / Boolean

Is passive determines if this will retaliate when hit. If true the bee will ignore being hit, if false the bee will attack the entity back.

{% hint style="info" %}
**Default:** false
{% endhint %}

### Remove Stinger / <mark style="color:red;">`removeStingerOnAttack`</mark> / Boolean

Determines if the bees stinger will be removed on attack. If a bees stinger is removed it has a chance of randomly dying a bit after the stinger was removed.

{% hint style="info" %}
**Default:** true
{% endhint %}

### Inflict Poison / <mark style="color:red;">`inflictsPoison`</mark> / Boolean

Determines if when the bee attacks an entity if it should give the entity the posion effect.

{% hint style="info" %}
**Default:** true
{% endhint %}

### Invulnerable / <mark style="color:red;">`isInvulnerable`</mark> / Boolean

Determines if the bee should not take any damage, if true the bee will no longer take damage.

{% hint style="info" %}
**Default:** false
{% endhint %}

### Attributes / <mark style="color:red;">`attributes`</mark> / Map\<Attribute, Double>

An object of attributes to their values, keys being the attribute id and the value being what the attribute should be set to.\
Minecrafts attributes can be found [here.](https://minecraft.fandom.com/wiki/Attribute#Attributes)

{% hint style="info" %}
**Default:** default bee attributes (todo link)
{% endhint %}
