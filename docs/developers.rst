Developer documentation
=======================

Welcome to the developer documentation of qcPy. Unlike the :doc:`API documentation <api/index>`, this part gives some general background information for developers who want to actively contribute to the project.


Virtual environment
-------------------

The whole development should take place inside a virtual python environment that should be located *outside* the project directory.

To create a new virtual python environment, open a terminal and change to a a directory where the virtual environment should reside. Then type something like::

  virtualenv qcpy

This will create a virtual environment in the directory "qcpy". To activate this virtual environment, use::

  source qcpy/bin/activate

To deactivate, the command would simply be::

  deactivate


Autoincrementing version numbers
--------------------------------

The version number is contained in the file ``VERSION`` in the project root directory. To automatically increment the version number with every commit, use a git hook that calls the file ``bin/incrementVersion.sh``. Git hooks reside in the directory ``.git/hooks``. The simplest would be to create a new file ``pre-commit`` in this directory with the following content::

  #!/bin/sh
  bash bin/incrementVersion.sh


Make sure to set it to executable and have a line break (aka: new or empty line) at the end of the file. Otherwise, you man run into trouble, i.e., not having your version number updated automatically with each commit.


Directory layout
----------------

The qcPy package follows good practice of the Python community regarding directory layout. As there will be several subpackages available, these reside each in a separate directory containing its own ``__init__.py`` file. All packages/modules reside below the ``qcpy`` directory of the project root. The ``tests`` directory follows the same structure and contains all the module tests. Generally, the qcPy package should be developed test-driven (test-first) as much as possible.

(This) documentation resides inside the ``docs`` directory of the project root. The auto-generated :doc:`API documentation <api/index>` is in its own directory.

A general overview of the overall package structure::

  bin/
  docs/
      api/
  qcpy/
  tests/


As you can see, currently three subpackages, namely "datasafe", "loi", and "eln", are supposed to be created. For details of the qcPy project as such, consult its `Homepage <https://www.qcpy.de/>`_.


Docstring format
----------------

The Docstring format used within the code of the qcPy package is "NumPy". For convenience, set your IDE accordingly.

For PyCharm, the settings can be found in ``Preferences`` > ``Tools`` > ``Python Integrated Tools``. Here, you find a section "Docstrings" where you can select the Docstring format from a number of different formats.


Unittests and test driven development
-------------------------------------

Developing the qcPy code should be done test-driven wherever possible. The tests reside in the ``tests`` directory in the respective subpackage directory (see above).

Tests should be written using the Python :mod:`unittest` framework. Make sure that tests are independent of the respective local environment and clean up afterwards (using appropriate ``teardown`` methods).

