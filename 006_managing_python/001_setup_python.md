# Setup Python in a specific environment

One thing that’s helped me tremendously is having separate environments for Python 2 and Python 3.

Conda treats Python the same as any other package, so it is easy to manage and update multiple installations.

Anaconda supports Python 2.7, 3.6, and 3.7. The default is Python 2.7 or 3.7, depending on which installer you used:

- For the installers "Anaconda" and "Miniconda," the default is 2.7.

- For the installers "Anaconda3" or "Miniconda3," the default is 3.7.

To check the python version in the default environment type in the terminal:

```console
(base)~$ python --version
Python 3.7.4
```

To install a **different version of Python for anaconda** without overwriting the current version, create a new environment and install the second Python version into it:

1. Create the new environment:

  - To create the new anaconda environment for Python 3.6, in your terminal window, run:
  ```console
  (base)~$ conda create -n py36 python=3.6 anaconda  
  ```
  d **Note**: Replace `py36` with the name of the environment you want to create. `anaconda` is the metapackage that include all of the Python packages comprising the Anaconda distribution. `python=3.6` is the package and version you want to install in this new environment. This could be any package, such as `numpy=1.7`.
  - To create the new anaconda environment for Python 2.7, in your terminal window, run:
  ```console
  (base)~$ conda create -n py27 python=2.7 anaconda
  ```
2. Activate the new environment and verify that the current environment in your terminal is using the new Python version:
  ```console
  (base)~$ conda activate py36
  (py36)~$ python --version
  Python 3.6
  ```
To simply create a new environment with only python installed type:
```console
(base)~$ conda create -n py27 python=2.7
```

## Updating and upgrading Python

If you are in an environment with Python version 3.4.2, the following command updates Python to the latest version in the 3.4 branch:

```console
(py34)~$ conda update python
```

The following command upgrades Python to another version 3.6 by installing that version of Python:

```console
$ conda install python=3.6
```
