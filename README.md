pyenv-register
==============
pyenv-register is a [pyenv](https://github.com/yyuu/pyenv) plugin
to use existing python installations

Installing versions of python with `pyenv install` usually takes longer than using system package management tools (like apt-get, yum, brew or spack); and there are other considerations.

`pyenv-register` imports already installed python to pyenv environment; it works by creating a virtual environment for that installation and pointing pyenv to it.

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

