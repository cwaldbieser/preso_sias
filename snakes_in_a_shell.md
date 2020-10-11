
---
title: Snakes in a Shell
author: Carl Waldbieser
date: 2020-10-11
---

# Python 2.x

* Please don't.
* Python 2.x has been discontinued.
* Moving on ...

---

Python 3 - Installing Scripts

Use `pip`:

```bash
$ pip install lookatme
...
$
```
---

# Python 3 - Dependencies

* Python has "batteries included".
* Some scripts want to use extra modules.
* Different scripts might require different versions or modules.
* Some scripts might use incompatible modules.
* How to manage dependencies?

---

# Python Virtualenv

* A virtual copy of a base Python environment.
* Includes an interpreter and standard library, but its own modules.
* Won't clobber your OS Python.
* How to use?

---

# venv - Python standard library

```bash
$ # Create a virtualenv using the standard lib.
$ python3 -m venv ./venv
$ # Activate the virtualenv in your shell.
$ . ./venv/bin/activate
(venv)$ # Install some modules ...
(venv)$ pip install requests
...
(venv)$ # Run a script.
(venv)$ python ./myscript.py
...
(venv)$ # Quit the environment
(venv)$ deactivate
$
```

**Q:** That's great for interactive use, but aren't the activate and deactivate
steps kind of clunky for scripted use?

**A:** You can just include the full path to the virtualenv executable(s) you want
to use.  For example:

```bash
$ /home/waldbiec/virtenvs/preso-env/bin/python ./myscript.py
```

---

# VirtualenvWrapper

[virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/) lets
you create, manage, and move between virtualenvs like a pro.

How do you install it without mucking about with the OS Python?  On Ubuntu
18.04+ it is in the package repositories:

```bash
$ sudo apt update && sudo apt install virtualenvwrapper
...
$ # Add this to your ~/.bashrc
$ . /usr/share/virtualenvwrapper/virtualenvwrapper.sh
```

For others, install in your *user local directory*:

```bash
$ pip install --user virtualenvwrapper
```

How to use:

```bash
$ mkvirtualenv -p /usr/bin/python3 presoenv
(presoenv)$ pip install lookatme
...
(presoenv)$ workon myotherenv
(myotherenv)$ python ./myotherscript.py
(myotherenv)$ deactivate
$
```

---

# Pipenv

[pipenv](https://github.com/pypa/pipenv) combines virtualenv management with
dependency management.

Basic usage:

```bash
$ cd myproj
$ ls
Pipfile Pipfile.lock ...
$ # Set up the virtualenv one time only.
$ pipenv install
...
$ # Run script with virtualenv.
$ pipenv run ./myapp.py
```

