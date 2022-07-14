# Package Manager

As mentioned earlier, `conda` is a **package manager** and a **environment manager**. These two things are very useful in structuring any project.

## Package Manager

![install package](../images/conda-install.png)
*Installing Numpy with conda*

A package manager is a tool that **installs, updates, and removes computer programs**.

For us, these computer programs will be third-party Python packages. A **third-party Python package** is any package that is not part of the Python standard library. There are many thousands of third-party packages available to be installed onto your system.

You’re probably already familiar with `pip`, it’s the default package manager for Python libraries. `Conda` is similar to pip except that the available packages are **focused around data science** while pip is for general use. However, conda is not Python specific like pip is, **it can also install non-Python packages**.

<u>It is a package manager for any software stack</u>. In other words, `conda` is `language agnostic`. That being said, not all Python libraries are available from the Anaconda distribution and conda. You can (and will) still use pip alongside conda to install packages.

Whereas `pip` only installs Python packages from [PYPI](https://pypi.org/), `conda` can both:

- Install packages (written in any languages) from repositories like [Anaconda Repositories](https://repo.anaconda.com/) and [Anaconda Cloud](https://anaconda.org/).

- Install packages from [PYPI](https://pypi.org/) by using `pip` in active `conda` environment.

## Why use Package Managers ?

Let's say we want to do a machine learning project and therefore we want to install specific libraries such as `Scikit-learn 0.21.3`.

```console
              Package Manager

         Machine Learning Project
            Scikit-learn 0.21.3
              |           |
  ScipY >= 0.17.0       NumPY >= 1.11.0   
    | | |                | | |
  .. .. ..              .. .. ..
```

In that case we can just install the latest version of `Scikit-learn` and start coding on our project. We see that the installed library depends on other libraries, for example `ScipY` and `NumPY`, those libraries in turn depend on other libraries as well. Thus, to be able to use `Scikit-learn` we need to install first its dependencies and on top of that we have to install the right version. If we had to install all the dependent dependencies manually then this could become cumbersome and time-consuming.

So a better approach would be to **simply specify the library we want to use**, in this case `Scikit-learn` and then let the <u>program figure out all the right dependencies</u>. `That's exactly what a package manager does`.

Let's say we want to use several libraries. For example, we want to use `Scikit-learn` together with `Pandas`. The libraries may depend on the same library, for example `NumPY`, but they could depend on different versions. Thus, it could become quite complicated to figure out all the right dependencies to make them everything work.

```console

         Machine Learning Project
            Scikit-learn 0.21.3              Pandas 0.25.1
              |           |                       |
  ScipY >= 0.17.0       NumPY >= 1.11.0      NumPY >= 1.13.3
    | | |                | | |
  .. .. ..              .. .. ..
```
A package manager helps to `resolve the conflicts`.
```console
              Package Manager

        Machine Learning Project
            Scikit-learn 0.21.3         Pandas 0.25.1
              |             |           |
  ScipY >= 0.17.0           NumPY >= 1.13.3
     | | |                       | | |
   .. .. ..                     .. .. ..
```
It's clear that within the same project the functions we used for the two libraries must be compatible with NumPY 1.13.3.

`Conda` **installs precompiled packages**. For example, the Anaconda distribution comes with `Numpy`, `Scipy` and `Scikit-learn` compiled with the [MKL](https://docs.continuum.io/mkl-optimizations/) library, speeding up various math operations. 

The packages are maintained by contributors to the distribution which means they usually lag behind new releases. But because someone needed to build the packages for many systems, they tend to be more stable (and more convenient for you).
