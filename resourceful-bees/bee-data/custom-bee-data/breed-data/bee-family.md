# Bee Family

## Data Object

### Weight / <mark style="color:red;">`weight`</mark> / Double(≥0.0)

The weight that this bee pair will result is the child that this pair was added to.

{% hint style="info" %}
**Default:** 10
{% endhint %}

### Chance / <mark style="color:red;">`chance`</mark> / Double(0.0-1.0)

The chance that this pair will successfuly create a child.

{% hint style="info" %}
**Default:** 1
{% endhint %}

### Parent 1 / <mark style="color:red;">`parent1`</mark> / String

The id of the first parent.

{% hint style="danger" %}
**Required:** If not provided family will be ignored.
{% endhint %}

### Parent 2 / <mark style="color:red;">`parent2`</mark> / String

The id of the second parent.

{% hint style="danger" %}
**Required:** If not provided family will be ignored.
{% endhint %}
