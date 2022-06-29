pyenv-register
==============
pyenv-register is a [pyenv](https://github.com/yyuu/pyenv) plugin
to use existing python installations

Installing versions of python with `pyenv install` usually takes longer than using system package management tools (like apt-get, yum, brew or spack); and there are other considerations.

`pyenv-register` imports already installed python to pyenv environment; it works by creating a virtual environment for that installation and pointing pyenv to it.

This fork will by default use the built-in `venv` python module unless told explicitly to use `virtualenv` by using the `-m virtualenv` option.

When directed to use `virtualenv`, it will use python's `pip` module to install it if it's not installed already.

Installation
------------

### Install as a pyenv plugin

    $ git clone https://github.com/hell-pl/pyenv-register.git $(pyenv root)/plugins/pyenv-register
    $ exec "$SHELL"

Usage
-----

### Register python of package management system

    $ sudo apt-get install -y python3.3  # install by package management system

    $ /usr/bin/python3.3 --version
    Python 3.3.2+

    $ pyenv register /usr/bin/python3.3

    $ pyenv versions
    * system (set by /home/xxxx/.pyenv/version)
      system-3.3.2

An environment named `system-x.x.x` will be created.
The environment contains system installed libraries.

    $ sudo apt-get install -y python3-lxml

    $ pyenv register /usr/bin/python3.3

    $ pyenv shell system-3.3.2

    $ pip freeze | grep lxml
    lxml==3.2.0

### Register non-default python of your brew installation

    $ pyenv register -m virtualenv \
        $(brew --prefix)/opt/python3.10/bin/python3.10 \
        python-brew@3.10

    Registering /home/linuxbrew/.linuxbrew/opt/python@3.10/bin/python3.10 =>
    /home/miroslaw/.pyenv/versions/python-brew@3.10
    created virtual environment CPython3.10.5.final.0-64 in 160ms

    [output abbreviated]

