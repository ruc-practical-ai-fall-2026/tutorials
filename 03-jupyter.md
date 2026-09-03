## Jupyter

### Introduction

Jupyter is a notebook environment for programming in Python. Unlike a normal Python script, which is typically stored in a `.py` file containing primarily source code, a Jupyter notebook is stored in an `.ipynb` file that can contain code, markdown, equations, and saved outputs such as plots and tables.

Jupyter provides two main advantages which make it a popular choice for data science and machine learning projects, especially in early stages of development. First, Jupyter displays data and visualizations of the data next to the code, alongside equations and typeset markdown documentation. In this way, Jupyter enables practicing one of the most important principles of data visualization (as given in the ubiquitous reference, *The Visual Display of Quantitative Information* by Tufte), which states that visualizations should be *embedded within the documents that describe them*.

Second, Jupyter allows executing code in cells, which means that code can be executed out of order. This is helpful for iterative development. You might want to write some code to load in data, run the code, adjust, and repeat until the data is loaded correctly. This type of nonlinear (out of order) execution is common in machine learning workflows, which often require significant iteration and adjustment to meet requirements. Developing the workflow in the early stages of the project directly next to associated visualizations before rushing to implement a full product aids proper requirements development for the full product and is often preferred over writing production code prematurely.

Behind each running notebook is a **kernel**, which is the Python process that actually executes your code and stores variables in memory. When you run one cell and define a variable, that variable remains available to later cells because the kernel remembers it. Restarting the kernel clears this state and starts a fresh Python session. This is also why it is important to make sure your notebook is using the correct Python environment and kernel.

We will go over Jupyter in detail and use it many times throughout this class.

### Installation

Jupyter Notebook can be installed in your project using `uv` as follows.

```bash
uv add notebook ipykernel
```

The `ipykernel` package allows a Python environment to be used as a Jupyter kernel.

JupyterLab is a more full-featured interface for working with Jupyter notebooks, terminals, files, and other tools. We will not use it directly in this course, but you are welcome to try it out for yourself!

```bash
uv add jupyterlab
```

### Basic Usage

Jupyter notebooks are comprised of **cells**. You can make a new cell and tell Jupyter whether you want this to be a code cell or a markdown cell. Use markdown cells to organize your notebooks by adding headers and documentation. Use code cells to add the code you want to run. You can add markdown and code cells with the `+ Markdown` and `+ Code` buttons respectively.

To run a Jupyter cell, press `Shift` + `Enter`. Note that unlike a Python script, where all lines will execute in the same order, it is easy to run Jupyter cells out of order. As noted above, this can be useful for prototyping and debugging (e.g., to run an interesting section of code multiple times before moving on to the next). However, if Jupyter cells are run out of order by accident, a program may not run as intended.

If you lose track of the order your Jupyter cells have been running in, you can use the `Restart` button to restart the kernel. You can clear all old outputs with the `Clear All Outputs` button. You can run all cells in order using the `Run All` button.

Before submitting a notebook or handing it over to a colleague, it is a good practice to restart the kernel and run all cells from top to bottom. This verifies that the notebook works from a fresh Python session and does not accidentally depend on variables or other state left over from cells you ran earlier.

One example of the usefulness of Jupyter cells' nonlinear execution flow is in training machine learning models. When training a machine learning model, you may wish to try to train it, look at some visualizations to see how well it fits the data, and then retrain it if it does not fit well before moving on to test it. You may implement this workflow in Jupyter by having a "train" cell, a "visualization" cell, and a "test" cell. Then you can run the train cell multiple times, checking the visualization cell after each (and potentially running that cell a few times to adjust your plots) before moving on to the test cell once you are satisfied.
