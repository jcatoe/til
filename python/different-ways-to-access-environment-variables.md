# Different Ways To Access Environment Variables

## Options:
* `os.environ['VARIABLE', 'Wompwomp']`
* `os.environ.get(key='VARIABLE', default='Wompwomp')`
* `os.getenv(key='VARIABLE', default='Wompwomp')`

All three options tend to do the same thing. You must specify the environment variable name (`'VARIABLE'`) and you have the option of including what to return if the variable does not exist (`'Wompwomp'`)

The main difference is what happens if the variable does not exist and you didn't set a default. The first two options will return an error whereas the third option will return `None` by default. 

A "minor" difference is that the first two options are automatically imported when you `import os` while the third option is just a wrapper around `os.environ.get()`.

So the third option saves a few keystrokes if you just want `None` as the default.

I think I prefer the second option as it's easier to read and you should be explicit about the default value you expect.
