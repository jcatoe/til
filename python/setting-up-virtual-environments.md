# venv

`venv` is a built-in package (Python 3.3+) for handling python environments and is very similar to the commonly used package `virtualenv`. The main difference between the two packages is that `venv` does not need to install the Python binaries (_except on Windows_) and it does not have Python 2 support.

There's a fancy package called `pipenv` that supposedly handles most of your package installs and virtual environment needs, but frequently working on different machines, local and cloud-based, leads to a lot of confusion so I'd rather stick to what's default and learn those commands well.

However, `pyenv` is not for package management, but rather Python version management. It is useful for running tests to see if your code works in all of the different versions.

**Ignore:** `pipenv`, `pyvenv`, `pyenv-virtualenv`, `pyenv-virtualenvwrapper`, `virtualenv`, `virtualenvwrapper`

Unless you're using a Python version older than 3.3, in which case, use `virtualenv`.

There is a handy [Stack Overflow question](https://stackoverflow.com/questions/41573587/what-is-the-difference-between-venv-pyvenv-pyenv-virtualenv-virtualenvwrappe) that received a lot of really good answers and discussion in the comments about all of the different virtual environment-related packages.

## Create a virtual environment:

I like to store all of my virtual environments in a hidden folder to reduce clutter, but it isn't necessary; use whichever filepath you prefer.
```
$ python -m venv ~/.virtualenvs/<environment-name>
```

## Activate a virtual environment:

```
$ source ~/.virtualenvs/<environment-name>/bin/activate
```

Unless you're on Windows:
```
$ source ~/.virtualenvs/<environment-name>/Scripts/activate
```

## Deactivate a virtual environment:

```
$ deactivate
```

## Delete a virtual environment:

```
$ rm -r ~/.virtualenvs/<environment-name>
```

## List all virtual environments:

```
$ ls ~/.virtualenvs/
```

## Install package requirements for project:

Activate the correct virtual environment for your project. If there is a `requirements.txt` file, then:
```
$ pip install -r requirements.txt
```

If there is not a `requirements.txt` file, then you will have pip install each package manually. After that, you can run:
 ```
 $ pip freeze > requirements.txt
 ```

There is some speculation as to how "safe" doing a pip freeze is, a concise article on the topic can be found [here](https://medium.com/@tomagee/pip-freeze-requirements-txt-considered-harmful-f0bce66cf895)
