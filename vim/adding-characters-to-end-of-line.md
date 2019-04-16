# Adding Characters To End Of Line


## Current Line:

```
:s/$/<character(s)>/
```

## All Lines:
```
:%s/$/<character(s)>/g
```

## Remove All New Lines:
```
:%s/\n//g
```

## Combine The Two Steps:
```
:%s/\n/, /g
```
