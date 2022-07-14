# Setup Jupyter Notebook for specific environment

Anaconda conveniently installs the Jupyter Notebook in your default environment. However, the creation of a new environment does not include the Jupyter Notebook installation automatically. Therefore, in the creation of a new project it is common practice to include the `notebook` package.

For example, let's create a new environment with `numpy` and `notebook` packages.

```console
(base)~$ conda create -n my_env numpy notebook  
```

### Verify the Jupyter Notebook execute in the correct environment

Although we have created our new environment with the ability to create Jupyter Notebooks, we are not guaranteed that they will execute Python in the same environment that they where launched.

For instance, if we activate the environment we just created and run the following command:

```console
(base)~$ conda activate my_env
(my_env)~$ python
    >>> import sys
    >>> sys.executable
    '/opt/anaconda3/envs/my_env/bin/python'
```

The result returns a path to the environment python (`/opt/anaconda3/envs/my_env/bin/python`).
Similarly, we need to verify that executing notebooks launched from the activated environment (my_env) execute python from the same path and not from anywhere else.

With the `my_env` environment activated, run `jupyter notebook` and start a new `Python 3` notebook from the Jupyter interface in your browser, for more on how to launch and create a notebook click on the following [link](https://github.com/lpinzari/udacity-dsa-nand/tree/master/Jupyter_notebooks). In the first cell of the notebook, execute the following two lines of code:

```
import sys
sys.executable
```

The result should return in the Output: `/opt/anaconda3/envs/my_env/bin/python`. If it returns the location for the base environment `/opt/anaconda3/bin/python` or another path then you aren't executing python from the `my_env` environment.

The cause of this is a `User` kernel that is masking the environment kernel. For more information on how to fix this problem, please refer to the following [link](https://medium.com/dunder-data/anaconda-is-bloated-set-up-a-lean-robust-data-science-environment-with-miniconda-and-conda-forge-b48e1ac11646).

### Notebook conda to manage environments

As discussed earlier, we can launch a Notebook from an active environment and manage the notebooks within that environment. However, it is often useful to access multiple environments and their packages from within Jupyter Notebook Server User interface in your browser.

Anaconda provides a package named `nb_conda` to manage and switch environments from within Jupyter notebooks. Open your terminal and install the package `nb_conda` in your base environment:
```console
(base)~$ conda install nb_conda
```
Further information about environment management using Jupyter Notebooks can be found in the following links:
 - [nb_conda](https://docs.anaconda.com/anaconda/user-guide/tasks/use-jupyter-notebook-extensions/)
 - [jupyter conda](https://docs.anaconda.com/ae-notebooks/user-guide/adv-tasks/work-with-environments/)  
 - [here](https://github.com/lpinzari/udacity-dsa-nand/blob/master/Jupyter_notebooks/003_Launching_Jupyter_nb.md).
