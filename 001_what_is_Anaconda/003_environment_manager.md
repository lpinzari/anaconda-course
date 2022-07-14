# Environment Managers

![create virtual environment](../images/conda-create-env.png)
*Create virtual environment with Conda*

Along with managing packages, Conda is also a virtual **environment manager**. It's similar to [virtualenv](https://virtualenv.pypa.io/en/stable/) and [pyenv](https://github.com/pyenv/pyenv) or [venv](https://docs.python.org/3/library/venv.html) module to create lightweight virtual environment.

`Environments` allow you to **separate and isolate the packages you are using for different projects**.

Often you’ll be working with code that depends on different versions of some library. For example, you could have code that uses new features in `Numpy`, or code that uses old features that have been removed. It’s practically impossible to have two versions of `Numpy` installed at once. Instead, **you should make an environment for each version of** `Numpy` **then work in the appropriate environment for the project**.

This issue also happens a lot when dealing with `Python 2` and `Python 3`. You might be working with old code that doesn’t run in Python 3 and new code that doesn’t run in Python 2. Having both installed can lead to a lot of confusion and bugs. It’s much better to have separate environments.

You can also **export the list of packages in an environment to a file**, then include that file with your code. This allows other people to easily load all the dependencies for your code.

Pip has similar functionality with `pip freeze > requirements.txt`. Now anyone we share our project with will be able to run our project on their system by duplicating our environment using our `requirements.txt` file.

In summary, Virtual environments provide a simple solution to a [host of potential problems](https://packaging.python.org/tutorials/installing-packages/#creating-virtual-environments). In particular, they help you with:

- **Resolves dependency issues** by allowing you to use different versions of a package for different projects. For example, you could use Package A v2.7 for Project X and Package A v1.3 for Project Y.

- Make your project **self contained** and **reproducible** by capturing all package dependencies in a single file.

- Keep your global `site-packages/` directory tidy by removing the need to install packages system-wide which you might only need for one project.

## Why use Environment Manager ?

```console

    Machine Learning Project      Data Analysis Project
          Scikit-learn 0.21.3      Pandas 0.25.1
              |           |          |
  ScipY >= 0.17.0       NumPY >= 1.13.3
    | | |                   | | |
  .. .. ..                .. .. ..
```

Let's say we have a Machine Learning project, so we install `Scikit-learn` with all its dependencies and then we decide to stop for a while to start a Data Analysis project. Therefore, we need to install `Pandas` and since it depends on a higher version of `Numpy`, we upgrade from version (1.11.0) to version (1.13.3).

Once the Data Analysis project is finished we switch back to the Machine Learning Project. We try to run the code again but this time the code breaks and we get an error message because one of the `Scikit-learn` functions used in our code doesn't work anymore and after a lot of digging we finally find out that the problem occurred because of the upgraded version of `NumPY`.

For example, maybe a function in `NumPY` library was slightly changed which caused the `Scikit-learn` function that we used in our code to not work anymore. Thus, to solve the issue what you could do is either
- update our code to be able to work with the new number version of NumPY or
- we could downgrade NumPY version.

A better approach would be to simply `put all the dependencies that we need for a specific project` into an **isolated container** or **environment**.

```console
                         Environment Managers
  ----------------------------------------------------------------
      environment_1                 |         environment_2
  -----------------------------------------------------------------
    Machine Learning Project        |     Data Analysis Project   |
          Scikit-learn 0.21.3       |        Pandas 0.25.1        |
              |           |         |             |               |
ScipY >= 0.17.0     NumPY >= 1.11.0 |      NumPY >= 1.13.3        |
      | | |             | | |       |                             |
     .. .. ..         .. .. ..      |                             |
```

In this way we can easily install a new library or upgrade an existing library for a specific project without worrying about any side effect on the dependencies that we have installed in other environments. In this way we can simply activate the respective environment and then accordingly run the code again without running into any errors.

Another scenario where an Environment Manager is useful can be, for example, when you simply upgrade a library in a Project over time. Let's say you create a copy of your project in another environment and update the version of a library.


```console
                         Environment Managers
  ----------------------------------------------------------------
      environment_1                 |         environment_2
  -----------------------------------------------------------------
    Machine Learning Project 1      |   copy Machine Learning Project 1  |
          Scikit-learn 0.19.1       |        Scikit-learn 0.21.3         |
               |                    |             |                      |
```

In this way you **can easily switch between different versions of a specific library**.

Another great benefit that comes from using such environments is that your code is more **reproducible**.

For instance, if you want to share your project on gitHub, than **you can also share the specific environment that you used for that specific project**. In this way, other people can recreate your environment and run the code without getting any errors because they have different versions of a library or maybe they are missing one library.

### Where we go from here

Next, I'll get into the details of using Anaconda. First I'll cover installing it, then creating and managing environments, and finally using the package manager.

### Resources

The tutorial is the integration of different documents gathered on the web and the Udacity Anaconda tutorial.

- Set up a lean robust data science environment with Miniconda and Conda-forge
  [tutorial 1](https://medium.com/dunder-data/anaconda-is-bloated-set-up-a-lean-robust-data-science-environment-with-miniconda-and-conda-forge-b48e1ac11646)
- Getting started with Conda. [Official guide](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html)
- [The Definitive Guide to Conda Environments](https://towardsdatascience.com/a-guide-to-conda-environments-bc6180fc533)
- [A guide to Python's virtual environment](https://towardsdatascience.com/virtual-environments-104c62d48c54#1839)
- [Python's virtual environments](https://realpython.com/python-virtual-environments-a-primer/)
