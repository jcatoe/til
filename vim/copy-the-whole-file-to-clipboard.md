# Option 1: the shortest way
```
:%y+
```

If you receive `E850: Invalid register name` then vim was probably not compiled with the `+clipboard` option. To test this, you can type `:version` and see if `+clipboard` shows up in the ouptut.

To fix this problem, you need to `brew install vim`. If you don't have [brew](https://brew.sh/) already installed, run:

```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

followed by

```
$ brew install vim
```

It will take a few minutes to install everything.

# Option 2: probably won't work if Option 1 didn't work

If you didn't see `+xterm_clipboard` in the `:version` output, this won't work either.

```
:gg"*yG
```

# Option 3: a lot more to type

```
:%w !pbcopy
```

