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

# Bee Family

A bee family consists of four key pieces of information necessary for breeding a bee:

* The first parent required
* The second parent required
* The weighting of how likely the child is to be selected among potential candidates
* The chance the child is created if selected

{% code title="Template:" %}
```json
"resourcefulbees:breeding/v1": {
  "parents": [
    {
      "parent1": "diamond",
      "parent2": "coal",
      "weight": 75.0,
      "chance": 0.67
    }
  ]
}
```
{% endcode %}



## Customization Options

***

### <mark style="color:orange;">`weight`</mark>

For all possible children these two parents can create how likely is it this one will be picked? Weight affects the result distribution among potential outcomes.&#x20;

<details>

<summary>Calculating Weight Distributions:</summary>

A pair of parents has five different child options.

The weights are as follows:

```
Child 1: 20
Child 2: 10
Child 3: 30
Child 4: 60    
Child 5: 80
```

The chances each child has of being selected are as follows:

```
Child 1: 10%
Child 2: 5%
Child 3: 15%
Child 4: 30%
Child 5: 40%
```

To calculate the chance:

1. Add up all the weights
2. Divide the weight you wish to check by the total in step 1

</details>

***

{% hint style="info" %}
**Name:** Weight

**Key:** <mark style="color:orange;">`weight`</mark>

**Type:** Double

**Range:** ≥0.0

**Default:** 10
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:breeding/v1": {
  "parents": [
    {
      "parent1": "diamond",
      "parent2": "coal",
      "weight": 75.0
    }
  ]
}
```

</details>



### <mark style="color:orange;">`chance`</mark>

Once this child has been chosen as the result type, what is the chance that it will be created?

{% hint style="success" %}
**Note:** The value has a range of 0.0 - 1.0.&#x20;

A value of 0.5 = a 50% chance of the child being created.
{% endhint %}

***

{% hint style="info" %}
**Name:** Chance

**Key:** <mark style="color:orange;">`chance`</mark>

**Type:** Double

**Range:** 0.0 - 1.0

**Default:** 1
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:breeding/v1": {
  "parents": [
    {
      "parent1": "diamond",
      "parent2": "coal",
      "chance": 0.67
    }
  ]
}
```

</details>



### <mark style="color:orange;">`parent1`</mark>

The ID of the first parent.

{% hint style="danger" %}
If not provided family will be ignored!
{% endhint %}

***

{% hint style="info" %}
**Name:** Parent 1

**Key:** <mark style="color:orange;">`parent1`</mark>

**Type:** String

**Default:** 1

**Required:** If not provided family will be ignored.
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:breeding/v1": {
  "parents": [
    {
      "parent1": "diamond",
      "parent2": "coal"
    }
  ]
}
```

</details>



### <mark style="color:orange;">`parent2`</mark>

The ID of the second parent.

{% hint style="danger" %}
If not provided family will be ignored!
{% endhint %}

***

{% hint style="info" %}
**Name:** Parent 2

**Key:** <mark style="color:orange;">`parent2`</mark>

**Type:** String

**Default:** 1

**Required:** If not provided family will be ignored.
{% endhint %}

<details>

<summary>Example</summary>

```json
"resourcefulbees:breeding/v1": {
  "parents": [
    {
      "parent1": "diamond",
      "parent2": "coal"
    }
  ]
}
```

</details>

