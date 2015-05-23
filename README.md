isnumb - a statistical approach to Python's isnumeric
===

Is ``"$100,000,001"`` a number? 

I say ``True``, Python says...

```python
>>> "$100,000,001".isnumeric()
False
```

Approach to implementation
---

I imagine two ways are possible: 

1. supervised learning by training

2. model by heuristics

### By training

You have a training (.txt) file of what humans consider to be "numbers" :

```text
$100,000,001
185774
123,456,789
1.01
%99.991
$9.11
100,000.00
%10
```

If classification resolution is desired, we could create multiple training
files where each file has numbers of specific classes: 


```text
# comma separated (with decimals)
123,456,789
100,000.00
```

```text
# currencies
$100,000,001
$9.11
```

```text
# percentages
%99.991
%10
```


### By heuristics

With heuristics, the task changes from having to create training files to 
having to describe rules that classify numbers.

For comma separated values, simply replacing commas with empty strings can
suffice. 

For currencies, we can conditionally check for currency symbols (ie. $, €, etc.). 
The same principle can be applied for percentages. 

