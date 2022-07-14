# Summary steps

This section summarises the main commands to create a basic environment for data analysis or data science. We'll refer to the following [article](https://medium.com/dunder-data/anaconda-is-bloated-set-up-a-lean-robust-data-science-environment-with-miniconda-and-conda-forge-b48e1ac11646).

1. Let's create an environment named `minimal_da` that has no packages in it, not even python itself.
```
(base)~$ conda create -n minimal_da
```
2. Confirm its creation by listing all the environments:
```
(base)~$ conda env list  
```
3. Activate the environment with:
```
(base)~$ conda activate minimal_da
(minimal_da)~$
```
4. Let's add the conda-forge channel as an option for just this environment.
```
(minimal_da)~$ conda config --env --add channels conda-forge  
```
5. Confirm that the channel has been added:
```
(minimal_da)~$ conda config --show channels  
```
6. Ensure that conda-forge is used if the package is available.
```
(minimal_da)~$ conda config --env --set channel_priority strict
```
7. Install packages:
```
(minimal_da)~$ conda install pandas scikit-learn matplotlib notebook  
```

## More to Learn

- To learn more about conda and how it fits in the Python ecosystem, check out this article by Jake Vanderplas: [conda miths and misconceptions](https://jakevdp.github.io/blog/2016/08/25/conda-myths-and-misconceptions/).
- [conda documentation](https://docs.conda.io/projects/conda/en/latest/)
- [conda cheetsheet](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html).
