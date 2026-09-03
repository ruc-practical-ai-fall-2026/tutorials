# Optional but Highly Recommended: VS Code

## Introduction

VS Code is a free integrated development environment (IDE) by Microsoft. An IDE is a collection of tools to develop software which are integrated into a convenient user interface so they are accessible through a single application. Modern IDEs can be augmented with various packages and extensions. You are encouraged to search for useful extensions to help you as you take on assignments. While you are welcome to use any IDE you like for this class, VS Code is highly recommended. VS Code is so popular currently that getting help from your classmates and the internet will be much easier if you are using it.

## Installation

VS Code can be installed from [here](https://code.visualstudio.com/download). Click the link for your OS and follow the instructions. You can use all default settings.

## Basics

A quick [7 minute introduction](https://www.youtube.com/watch?v=B-s71n0dHUk) to VS Code is recommended if you are completely new to it. A slightly longer [20 minute introduction](https://www.youtube.com/watch?v=ORrELERGIHs) is also helpful.

VS Code has many [keyboard shortcuts](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf). Learning them will help you work faster in it.

### Opening VS Code

Once you have VS Code installed, you should have a shortcut on your desktop or in your application menu to open it. You can also open VS Code by searching for it in your OS search bar as you would any other program.

Depending on your operating system and installation options, you may also be able to right click a folder and click "Open with Code".

To open VS Code in a particular folder from your shell, navigate to that folder and type:

```bash
code .
```

On MacOS, if the `code` command is not available, open the Command Palette in VS Code and run:

```text
Shell Command: Install 'code' command in PATH
```

### Buttons and Sections

The *activity bar* is on the left of VS Code's interface and has buttons for basic high level functions of VS Code.

These include the following.

* **Explorer**: explore files and navigate to where you need to develop code.
* **Search**: search the files in your project and perform find and replace tasks.
* **Source Control**: interact with Git through a UI instead of the command line.
* **Run and Debug**: run and debug the code you are writing.
* **Extensions**: install and manage extensions that add additional functionality to VS Code.

### Making New Files

You can make a new file by clicking the **New File** button inside the Explorer.

You can also type `Ctrl` + `N` (`Cmd` + `N` on MacOS) to open a new untitled file and then save it into your project folder.

### Opening a New Editor

Open an entirely new instance of VS Code with `Ctrl` + `Shift` + `N` (`Cmd` + `Shift` + `N` on MacOS).

### Selecting Your Python Interpreter

Many tools within VS Code need to know which Python environment you intend to use. For example, VS Code uses the selected Python environment when running Python code, debugging, providing autocomplete, and checking imports.

In this course, we will frequently create a Python virtual environment named `.venv` inside each project. Tools such as `uv` can create and manage this environment for us.

VS Code will normally detect these environments automatically.

To select the Python environment you want to use, press `Ctrl/Cmd` + `Shift` + `P` to open the Command Palette and type:

```text
Python: Select Interpreter
```

Select the Python interpreter associated with your project's `.venv`.

Depending on your operating system, the interpreter may have a path similar to:

```text
.venv/bin/python
```

on Linux or MacOS, or:

```text
.venv\Scripts\python.exe
```

on Windows.

You can see the currently selected Python environment in the VS Code status bar. If VS Code seems to be using the wrong Python version or cannot find a package that you know you installed, checking the selected interpreter should be one of your first troubleshooting steps.

Usually, you should not need to manually configure paths to packages inside `.venv`. Once the correct interpreter is selected, VS Code and its Python extensions will automatically locate the packages installed in that environment.

### Python Settings

You can customize Python behavior in VS Code through your settings.

Open your User Settings JSON file by pressing `Ctrl/Cmd` + `Shift` + `P` and typing:

```text
Preferences: Open User Settings (JSON)
```

For example, if you are using Ruff for formatting and organizing imports, you might have Python settings similar to:

```json
{
    "jupyter.askForKernelRestart": false,

    "[python]": {
        "editor.defaultFormatter": "charliermarsh.ruff",
        "editor.formatOnSave": true,
        "editor.codeActionsOnSave": {
            "source.fixAll.ruff": "explicit",
            "source.organizeImports.ruff": "explicit"
        }
    }
}
```

You generally do not need to hard-code the location of Python or manually add directories inside `.venv` to VS Code's autocomplete or analysis paths. Selecting the correct interpreter is usually sufficient.

### Making and Running a Python Script

To make a Python script, create a new file in VS Code with `Ctrl/Cmd` + `N`. Type the following line and save the file as `hello.py`.

```python
print("Hello World!")
```

Click the play button in the top right to run your script.

Before running Python code, make sure the correct Python interpreter is selected.

A tutorial on getting started with VS Code in Python can be found [here](https://code.visualstudio.com/docs/python/python-quick-start).

### Opening a Terminal

First, select your default terminal by pressing `F1` and then typing:

```text
Terminal: Select Default Profile
```

Select Git Bash or another preferred shell.

To open a terminal, press `Ctrl` + `Shift` + `` ` ``. On MacOS, use `Ctrl` + `` ` ``.

This should now open the shell you selected as your preferred shell.

The terminal will normally open inside the folder you currently have open in VS Code, which makes it convenient for running commands associated with your project.

### Running Commands

Above we pressed `F1` to open the Command Palette. The Command Palette can also be opened with `Ctrl` + `Shift` + `P` (`Cmd` + `Shift` + `P` on MacOS). Both of these are equivalent. Remember at least one! The Command Palette is used often.

### Picking a Theme

It is fun to customize VS Code with themes. Press `F1` and then type "Preferences: Color Theme" or just "Theme". Use the up and down arrows to select a theme you like!

### Helpful Extensions

VS Code is readily extensible and has an active community developing extensions for it. You are encouraged to try out new extensions during this class. Some that you will find helpful are listed here.

* **ms-python.python**: Python support
* **ms-python.vscode-pylance**: Python autocomplete, inline error checking, and code analysis
* **ms-python.vscode-python-envs**: Python environment management, including discovering and selecting virtual environments
* **ms-python.debugpy**: Python debugger extension
* **ms-toolsai.jupyter**: Jupyter Notebook support
* **charliermarsh.ruff**: Python formatting, linting, and import organization
* **streetsidesoftware.code-spell-checker**: spell checking inside your code

You can install extensions by clicking the **Extensions** button in the Activity Bar and searching for the extension name.

### Tip: Maximize your Terminal with a Keyboard Shortcut

If you like to work in the terminal and need a way to maximize the terminal without interrupting your workflow you can add a keyboard shortcut to VS Code for this.

Start with `Ctrl/Cmd` + `Shift` + `P` to open the Command Palette and then type:

```text
Preferences: Open Keyboard Shortcuts (JSON)
```

Add the following inside the square brackets in the `keybindings.json` file.

```json
{
    "key": "ctrl+shift+m",
    "command": "workbench.action.toggleMaximizedPanel"
}
```

### Tip: See a List of Keyboard Shortcuts

To see the list of keyboard shortcuts that VS Code has configured for you, use `Ctrl/Cmd` + `Shift` + `P` to open the Command Palette and type:

```text
Preferences: Open Default Keyboard Shortcuts (JSON)
```
