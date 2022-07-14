# Introduction

As I mentioned before, `conda` can be used to create environments to isolate your projects. Conda allows you to create separate environments containing files, packages, and their dependencies that will not interact with other environments. A nice tutorial on **virtual environment** can be found [here](https://realpython.com/python-virtual-environments-a-primer/).

By default, the `base` environment will always be active upon opening the terminal. Specifically, the `opt/anaconda3/bin` directory will be added to your path and allow you to start python and all the programs installed in the Anaconda distribution.

You do not want to put programs in your `base` environment, though. The `base` environment is usually used to test out some snippet code. Therefore, you **should create separate environments to keep your programs isolated from each other**.

In the following lesson we'll show some useful commands to create and manage separate environments using `conda`.
