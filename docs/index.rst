=======
HSMfile
=======
A Python package to expedite access to files on a slow network volume
---------------------------------------------------------------------

.. This is a version of the HSMfile documentation front page prepared by 
   Mark Hadfield (mark.hadf@gmail.com) 2019-11-06.

Synopsis
--------

This package addresses the common case where there are large data files on a supercomputer and these are to be processed, maybe on the
supercomputer or maybe on local machines that can mount the supercomputer file system. HSMfile exposes one Python module, hsmfile, which provides functions to

  * Specify the file locations and operate on files in a platform-independent
    way, given some platform-specific configuration data;
  * Copy files automatically from the supercomputer to the local machines.

It is based on a set of IDL functions with a similar purpose with the prefix
mgh_san_.

.. _mgh_san: https://github.com/hadfieldnz/idl-roms/tree/master/san

Installation
------------
Install from Conda-Forge_ with the Conda package manager::

    conda install -c conda-forge hsmfile

.. _Conda-Forge: https://conda-forge.org/

Install from PyPI_ with PIP::

    pip install hsmfile

.. _PYPI: https://pypi.org/

Clone the GitHub_ repository and install with PIP in developer mode::

  git clone https://github.com/hadfieldnz/hsmfile.github
  pip install -e hsmfile

.. _GitHub: https://github.com/

User customisation
------------------

The hsmfile module exposes a dictionary named volume, with each entry
defining an hsmfile volume as described below. During initialisation, the dictionary is created with one entry, pointing to the user's home directory.
However at the end of the initialisation
process, the module attempts to read and execute Python code from a configuration
file, ~/.hsmfilerc.py. This provides an opportunity for defining further volumes.

TODO
----

The present user customization mechanism is insecure, as it involves executing arbitrary Python code. It will shortly be changed to one that reads volume definitions from a
configuration file using the configparser module.
