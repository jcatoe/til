# List Comparisons

## Compare Two Lists And Return Matches:

```
a = ['apple', 'banana', 'carrot']
b = ['sandwich', 'apple', 'chips']

list(set(a).intersection(set(b)))

> ['apple']
```

## Compare Two Lists And Return Differences:
```
a = ['apple', 'banana', 'carrot']
b = ['sandwich', 'apple', 'carrot']

list(set(a) - set(b))

> ['banana']
```