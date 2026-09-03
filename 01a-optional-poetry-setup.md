# Poetry

Poetry was previously the primary Python dependency-management tool used in this course. You may still encounter Poetry in existing projects, tutorials, and professional development environments, particularly in legacy codebases that were created before newer tools such as `uv` became common. For this course, `uv` has replaced Poetry as the primary tool for managing Python environments and dependencies. The Poetry instructions below are retained for reference in case you need to work with an older project that still uses it.

## Introduction

When working on complex projects in Python, it can be difficult to keep track of what modules (e.g., `numpy`, `pandas`) and what versions of those modules your program depends on. Poetry is a useful tool for doing this.

Poetry helps with Python dependency management by completely automating the creation of a `pyproject.toml` file, which is a file used by Python build systems to define the dependencies needed by a Python package (collection of Python modules, themselves being `*.py` files, organized into an installable tool) in a folder. Poetry can then use a `pyproject.toml` file to automatically create a virtual environment for that specific project, which is self contained in a folder inside that project's directory (or in another location of your choosing).

This is a lighter weight method of managing the project's dependencies in a self-contained manner using a container and requires much less setup time compared to a container as long as we are familiar with the basic Poetry commends. For example, if we realize we forgot a dependency, we can simply add it with `poetry add <dependency>`. Poetry will then take care of updating our `pyproject.toml`, ensuring the versions of each package specified in the `pyproject.toml` do not conflict with each other. This automated management of version conflicts is one of the most powerful features of Poetry.

## Installation

See the official installation instructions for Poetry [here](https://python-poetry.org/docs/#installing-with-the-official-installer).

For Windows users, the PowerShell method is recommended and summarized below.

Open PowerShell and run the following command.
```PowerShell
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
```

If you have installed Python through the Microsoft Store, replace py with python in the command above.

For Poetry to work properly, it will need to be on your path so that your shell knows where to find it. To do this, you will first need to know where Poetry was installed to. The best way to do this is to note where the installer placed it. If you did not note where the installer placed it, you might need to look around your system. Try searching to see where Poetry is typically installed for your OS. For Windows, Poetry is usually placed in a subfolder under `$APPDATA`. You can find our where `$APPDATA` is by opening Git Bash and doing:

```bash
echo "$APPDATA"
```

A common Poetry install location for Windows is `$APPDATA/pypoetry/venv/Scripts/`. Confirm that Poetry exists at this (or another) location by running it and checking its version using the following command.

```bash
$APPDATA/pypoetry/venv/Scripts/poetry.exe --version
```

If your system has Poetry at a different path, be sure find out where and edit the above command to use the actual path to Poetry on your system. Once you can get the `poetry.exe` file to print its version and confirm this is the version of Poetry that you actually installed, then you can add the folder in which this file resides to your `$PATH`. For example, if you found poetry at `$APPDATA/pypoetry/venv/Scripts/poetry.exe` then you will need to add `$APPDATA/pypoetry/venv/Scripts` to your `$PATH`. The preferred way to do this is by editing your `.bash_profile` to add the following lines:

```bash
# Poetry paths
POETRY_PATH="$APPDATA/pypoetry/venv/Scripts"
export PATH="$POETRY_PATH:$PATH"
```

After you add these lines, source your `.bash_profile` via

```bash
source .bash_profile
```

or restart your terminal so the updates take effect. Check your path with

```bash
echo $PATH | tr ':' '\n' | grep poetry
```

to see if Poetry is on your path. If successful, you should see something like `/system/specific/path/pypoetry/venv/Scripts` (where `/system/specific/path` is replaced by some path specific to your setup).

Finally, confirm Poetry is working by checking its version and confirming this is indeed the Poetry that you installed.

```bash
poetry --version
```

## Configuration

In this class, we will use Poetry to create virtual environments inside our project's current directory. This means that each project we build will have its own version of Python, nested inside the project's main folder, with *all* dependencies needed to run. This is useful since we will try out many different tools across projects. By using Poetry in this way, we will not have to worry about tool compatibility between projects.

Note that the tradeoff in configuring Poetry to create its own virtual environment in each project is overall system memory usage. We will need enough hard drive space to hold multiple installations of Python. However, for a modern computer with hundreds of GB of storage, this is no problem, even for large Python libraries.

To tell Poetry you want it to create virtual environments in your current directory (so you can have different virtual environments per project), use the following command.

```bash
poetry config virtualenvs.in-project true
```

Add this line to your `.bashrc` or `.bash_profile` so you do not have to type it every time you start your shell!

## Pointing Poetry to the Correct Python Version

Like most tools, Poetry needs to be pointed to the correct Python version to work correctly. A common source of errors is Poetry using an unexpected Python version. For example, if you have an older version of Python on your system and Poetry attempts to use this as your base Python, this may cause compatibility issues with more recently updated packages.

By now, we should know how to find where the version of Python we want to work with is installed on our system (see earlier sections of this guide for a reminder). Find this path and note it.

To check which version of Python poetry is currently configured to use, run the following. Note you must do this inside a poetry project. This tutorial provides a `poetry_demo` folder for this.

```bash
cd poetry_demo
poetry env info
```

If this is not your preferred version, tell Poetry which Python to use with the following.

```bash
poetry env use /path/to/your/preferred/python.exe
```

Be sure to type the exact path, including the extension `.exe` on windows. On windows, this will look something like:

```bash
poetry env use ~/AppData/Local/Programs/Python/Python312/python.exe
```

## Using Poetry with VS Code

When using Poetry with VS Code, we need to tell VS Code where to find the virtual environments that Poetry maintains for us. There are several ways we can do this. This repository contains a `poetry_demo` folder that can be used to follow these steps for practice.

### Launching VS Code from Poetry's Shell

Poetry comes with its own shell that you can start at any time from bash using the following command.

```bash
cd poetry_demo
poetry shell
```

Note we must type this command from inside Poetry's directory. Once inside Poetry's shell (if this command worked it will print a message telling you that you are in poetry's shell) we can install the project.

```bash
poetry install
```

we can launch VS Code.

```bash
code .
```

This will start VS Code and we should be able to see the Poetry environment when running Python scripts or executing cells in notebooks. Navigate to the `poetry_demo/hello.py` file and open it.

Now you will need to tell VS Code which of the potentially many Python versions you have on your system to use to run this file.

Use `Ctrl` + `Shift` + `P` to open the command pallette and enter `Python: Select Interpreter`. Select the interpreter in `.venv/Scripts/python.exe`. This may be made easier by selecting the option to browse system files for the right Python interpreter. Remember that you need to use the Python interpreter in the `.venv` folder! This is the project-specific Python installation that Poetry has created for you in the current folder.

Once you have selected the interpreter, click the play button (right facing triangle) to run the `hello.py` Python script. If you prefer command line usage, you can type

```bash
.venv/Scripts/python hello.py
```

### Pointing VS Code to Poetry's Location for Storing Virtual Environments

Launching VS Code from Poetry's shell is sometimes convenient, but what if we want to launch VS Code in a directory that sits outside a specific Poetry project and then migrate to a Poetry project within VS Code and use the Poetry environment? Instead, we can launch code directly.

```bash
code .
```

Once in VS Code, we can use the side-panel to navigate to the project we want to use. Then we can open a terminal with `Ctrl` + `Shift` + `` ` ``.

Assuming we are already in the Poetry project directory (i.e., the directory that contains the `pyproject.toml`) and have performed the steps above to 1) configure virtual environments inside the project and 2) set the Python environment, we can then run the following command to see the list of Poetry environments available.

```bash
poetry env list
```

To see the path to these environments we do the following.

```bash
poetry env info --path
```

We can open the command pallette with `Ctrl` + `Shift` + `P` and type `Python: Select Interpreter`.

Now specify that VS Code should use the that interpreter (the one in `./.venv/Scripts/python.exe` is the one we want here since we are using virtual environments inside our projects). Once you specify this, Python scripts should use the project's interpreter.

Jupyter notebooks will show the project's interpreter as an option when you click the `kernel` icon or the small icon showing the current version of python (e.g., `Python 3.12.1`) and then click `Select Another Kernel`, and finally click `Python Environments...`. A `hello.ipynb` notebook is provided as an example to try selecting the right interpreter for a Jupyter notebook.

## Basic Poetry Commands Review

Poetry basics can be found [here](https://python-poetry.org/docs/basic-usage/). Information about managing poetry environments can be found [here](https://python-poetry.org/docs/managing-environments/). We have used some of these already in this tutorial.

### Creating a New Project

This command is used to create a new Poetry project from scratch.

```bash
poetry new project-name
```

### Initializing a Poetry Project in a Pre-existing Directory

This command is used to take an existing project that is not a Poetry project and make it a Poetry project.

```bash
cd project_directory
poetry init
```

### Adding a New Dependency

If you need to add a package to an existing Poetry project, use `add`.

```bash
poetry add matplotlib
```

### Installing a Poetry Project

Use this command to install a Poetry project and all its dependencies into your virtual environment.

```bash
poetry install
```

Use this command to install the dependencies in the `pyproject.toml` only (but not the project itself).

```bash
poetry install --no-root
```
