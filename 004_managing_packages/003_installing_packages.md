# Installing Packages

## Installing Packages

We are finally ready to install packages into our new environment.
There are two ways to install packages with `conda`:

1. From inside an active environment.
2. From your default shell.

The latter requires you to point to the environment you want to install packages in using the same flag (`--name` and `--prefix`) that you used to create your environment. All the examples in this guide will consider an environment named `my_env`. You can replace `my_env` with the name of your environment.

In the following, we will show how to install packages from the **default Anaconda repository, other conda repositories and PyPI (using pip)**. But, before we do that, it's important to list the basic commands to manage packages in **conda**.

- **conda install**:
To install a package, type `conda install package_name` in your terminal. For example, to install `numpy` type: `conda install numpy`. You can install multiple packages at the same time. Something like `conda install numpy scipy pandas` will install all those packages simultaneously. Conda attemps to install the newest versions of the requested packages. To accomplish this, it may update some packages that are already installed, or install additional packages. It's also possible to specify which version of a package you want by adding the version number such as `conda install numpy=1.10`.
Conda will automatically installs dependencies for you. For example `scipy` depends on `numpy`, it uses and requires `numpy`. If you install just `scipy` (`conda install scipy`), Conda will also install `numpy` if it isn't already installed.

- **conda remove**:
To uninstall a package, type `conda remove package_name` in your terminal. For example, to remove `numpy` type: `conda remove numpy`. Note that this command will also remove any package that depends on any of the specified packages as well-- unless a replacement can be found without that dependency. For example `scipy` and `pandas` depend on `numpy`, they use and require `numpy`. If you uninstall `numpy`, Conda will also uninstall `scipy` and `pandas`. Thus, it's recommended to use this command to uninstall high-level packages. For example, if you uninstall `scipy`, then `numpy` and `pandas` will not be uninstall.

- **conda update**:
To update a package, type `conda update package_name` in your terminal. This command accepts a list of package names and updates them to the latest versions that are compatible with all other packages in the environment. Note that Conda attempts to install the newest versions of the requested packages. To accomplish this, it may update some packages that are already installed, or install additional packages. If you want to update all packages in an environment, which is often useful, use `conda update --all`.

- **conda list**:
To list the packages installed in a given environment, type `conda list`, which you have seen before.

- **conda search**:
To find a package you haven't already installed in your environment, you can check if the package is available from the anaconda Repositories (you must be connected to internet) by typing: `conda search package_name`. This lists all packages whose names contain the text `package_name`. To list only the packages whose full name is exactly `package_name`, add the `--full-name` option. For example, I know I want to install [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/), but I'm not sure of the exact package name. So, I try `conda search *beautifulsoup*`. Note that your shell might expand the wildcard `*` before running the conda command. To fix this, wrap the search string in single or double quote like this:
`conda search '*beautifulsoup*'`. We can also try `conda search beautifulsoup` or for an exact matching `conda search --full-name beautifulsoup`.

**Note**: To update conda please use the following command:
```console
(base)~$ conda update -n base -c defaults conda  
```

### From the Anaconda repository

By default, `conda` install packages from the Anaconda Repository. Once you have created an environment, you can **install** additional packages in two ways:

1. From inside an active environment:
  ```console
  (my_env)~$ conda install scipy pandas
  ```

2. From your default shell:
  ```console
  (base)~$ conda install -n my_env scipy pandas
  ```
  Similarly we can specify the absolute path of the environment
  ```console
  (base)~$ conda install -p /opt/anaconda3/envs/my_env scipy pandas
  ```
Likewise, you can remove, update and list environments:

- From inside an active environment:
  ```console
  (my_env)~$ conda remove scipy pandas
  (my_env)~$ conda update scipy
  (my_env)~$ conda list
  ```

- From your default shell:
  ```console
  (base)~$ conda remove -n my_env scipy pandas
  (base)~$ conda update -n my_env scipy
  (base)~$ conda list -n my_env
  ```
  Similarly we can specify the absolute path of the environment.

### From other conda repositories

As discussed, if a package isn't available from the default Anaconda Repository, you can try searching for it on [Anaconda Cloud](https://anaconda.org/). To install a package from Anaconda Cloud, you will need the `--channel` or `-c` flag to specify the repository you want to install from. For example, if you wanted to install `opencv` from **conda-forge**, you'd run:

```console
(my_env)~$ conda install -c conda-forge opencv
```

Thankfully, `conda` keeps track of where a package was installed from:

```console
(my_env)~$ conda list
#packages in environment at /opt/anaconda3/envs/my_env
#
#Name    version   Build            channel

numpy    1.16.1    py37h92613e_0    
opencv   4.10      py37h0cb0d9f_3   conda-forge
pandas   0.24.2    py37h0a44026_0
```

For brevity, we listed only a section of packages above. The blank channel entries for `numpy` and `pandas` represent the `defaults` channel. You can also permanently add a channel as a package source: `conda config --append channels conda-forge`. This will modify your `.condarc` file to look something like this:

```console
channels:       # Lists package sources to install from
 - defaults     # Default Anaconda Repository
 - conda-forge
```

**Caution**: The order of your channels matters. If a package is available from multiple channels, conda will install it from the channel listed highest in your .condarc file. For more on managing channels, see [docs](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html).

### From PyPI

If a package isn’t available from Anaconda Repository or Anaconda Cloud, you can try installing it with `pip`, which `conda` installs by default in any environment created with Python.

For example, to install `requests` with `pip` you'd run:

```console
(base)~$ pip install requests
```

Note that `conda` correctly lists PyPI as the channel for `requests`, making it easy to identify packages installed with `pip`.

```console
(my_env)~$ conda list
#packages in environment at /opt/anaconda3/envs/my_env
#
#Name    version   Build            channel

numpy    1.16.1     py37h92613e_0    
opencv   4.10      py37h0cb0d9f_3   conda-forge
pandas   0.24.2    py37h0a44026_0
requests 2.21.0            pypi_0   pypi        
```

**Caution**: As pip packages do not possess all the features of conda packages, it’s strongly recommended to install packages with conda whenever possible. For more on conda vs. pip packages, click [here](https://conda.io/projects/conda/en/latest/commands.html#conda-vs-pip-vs-virtualenv-commands).
