# Development Environment Setup Tutorial

This tutorial shows how to install the tools that will be used during this course. When programming professionally on a team, this is often called "setting up your development environment". Getting a development environment set up is often the first task any software or data science professional will take on when joining a new team.

As is typical on a professional team, we will not mandate exactly what tools must be used to perform the exercises in this course. For each assignment and quiz, as long as the code works and meets the specified requirements, you will get full credit regardless of the tools you choose to use. You may attempt each any number of times and are encouraged to try out different tools as you do. The tools covered in this guide are only suggestions. You may find additional tools useful throughout the course and are welcome to use them. Some additional tools will be covered as we review special topics throughout the year.

## Tools for this Course

The following tools are required for this course. We will introduce all of them here and show how to install them.
* **Git**: distributed version control system
* **GitHub**: popular website for hosting Git repositories
* **Git Bash**: Linux-like command prompt for windows (comes with Git on Windows)
* **Python**: programming language ubiquitous in data science and machine learning (the latest version is 3.13 and is recommended)
* **Jupyter**: notebook environment for developing in Python
* **VS Code**: free IDE by Microsoft
* **uv**: tool for keeping track of Python dependencies
* **Docker**:

This guide also reviews Poetry, which, like uv, is a tool for keeping track of Python dependencies. While uv has rapidly become more popular in industry, Poetry is still used and it is worth knowing about. Understanding Poetry is optional in this course.

VS Code is technically optional (you may use another IDE). However, you may find that VS Code is so popular that it is far easier to follow online tutorials and get help from your classmates if you use VS Code.

It is helpful to practice installing these and other useful tools on your own so you can get comfortable searching the internet for the documentation on a new tool, reading the instructions, and learning how to use it on your own. This skill will help you in this course as you try new tools, and will help you professionally as you grow an ability to make independent contributions to software and data science teams.

## Git and GitHub

### Introduction

Git is a distributed version control system and exists to meet two needs that are ubiquitous in programming: (1) the need to track which *version* of a file we are working on (including any changes we may have made to it) and (2) the need to ensure that others we are working with can access that same version. If you have ever worked on a programming project (or even any other computer file, like an essay or assignment) and found yourself saving multiple copies titled `final.zip`, `final1.zip`, `final-final.zip`, `final-final-team-comments.zip`, etc. then Git can help. Git is especially important for programming on a team because as a distributed version control system, it not only tracks versions of our files, but also helps us store them in the cloud so anyone we are working with can access them.

### GitHub: collection of Git repositories

A collection of files version controlled in Git are called a *repository*. Repositories containing software also often contain other documentation files, including a `README.md` which explains the purpose of the repository and provides instructions to install it as a user or to contribute to it as a developer. This file (and the course syllabus along with other documentation we will use throughout the course) is a `README.md` file! Getting these files from the internet or a cloud environment to your local computer is called *cloning* the repository. Repositories are often called "repos" for short.

In this class, our repositories will be hosted on the internet via [GitHub](https://github.com/) which is an online tool for hosting Git repositories. The course repositories can be found [here](https://github.com/ruc-practical-ai). This [tutorial](https://github.com/ruc-practical-ai/development-environment-setup) is a Git repository. The [course syllabus](https://github.com/ruc-practical-ai/syllabus) and other instructional materials which will be provided throughout the semester are also Git repositories.

### Installation

Git's [website](https://git-scm.com/download/) has straightforward instructions on installation. There are links for Mac, Windows, and Linux / Unix. Follow the link for the operating system you use and download the installer. Once downloaded, run the installer, using administrator privileges if necessary, and keep all default settings.

### Setting Up a GitHub Account

Click here to [join GitHub](https://github.com/join) and create an account online if you do not already have one. Having a GitHub account is required to complete assignments in this course.

### Helpful Videos

A helpful 15 minute video on Git is available [here](https://www.youtube.com/watch?v=USjZcfj8yxE). A helpful 20 minute video on GitHub is available [here](https://www.youtube.com/watch?v=nhNq2kIvi9s).

### Useful Commands

We interact with Git through a command line interface (CLI) in a shell or through an integrated development environment (IDE). Some of the most basic Git commands are provided here for reference. If you do not yet have a shell or an IDE set up, CLIs and IDEs will be introduced further on in this tutorial. If you are new to Git and development environment set up it may help to skip this section and return after completing the rest of the tutorial, including cloning your first repository and making your first repository.

#### Cloning

Using Git to download a version controlled repository from the internet (in this class) or a cloud environment (in many professional settings) is called *cloning* the repository.

The following command shows how to clone the syllabus.

```bash
git clone git@github.com:ruc-practical-ai/syllabus.git
```

If you go to a Git repository on GitHub and click the green `code` button you will see the command you need to clone that repository. There are multiple commands you can use. We will cover those later in this tutorial.

#### Status

When you are inside a Git repository you can check the status of the repository (e.g., check if any files have changed) using the following command. Be sure to remember this command since it is used often!

```bash
git status
```

#### Adding Files

After we edit files in a repository, we must *add* them so git knows these are the files we want to commit and push from our local computer to the distributed repository where others will be able to clone them. Adding files is the first step to committing them, and is analogous to putting them in a box before we ship them (commit them).

The following command will add all files we have changed in the current repository.

```bash
git add .
```

The following command will add just `file.txt`.

```bash
git add file.txt
```

#### Committing Files

Once files are added, we can commit them into version control using `git commit`. The following command shows the most common way to do this and specifies a message with the `-m` flag.

```bash
git commit -m "Add a file"
```

Adding a message will help us track our changes later. A good commit message should always read as *"When applied, this change will...{your message here}"*.

For example, "Add visualization source files" is a good commit message (grammatically speaking) since it would make sense to read the sentence "when applied, this change will add the visualization source files."

In practice (outside the context of this tutorial) commit messages should be both grammatically correct and descriptive. This is considered good manners and good professional practice so when your teammates inspect a log of commit messages to find the version of a file they need, that log will be easily read and understood. Do not use simple generic commit messages like "fixed" or "stuff". This is considered unprofessional and can make finding contributions by members of a team difficult.

#### Pushing Files

Once you have committed files, you can use `git push` to send the changes from your local computer to a remote repository. In our class, the remote repository will be hosted on GitHub. All assignments and quizzes will be submitted using `git push`!

```bash
git push
```

#### Seeing a List of Changes

Git logs all commits made. The log contains the message you or another author wrote when the commit was made, along with a unique *hash* (signature) of the files in the repository.

A hash is a number which will be different if any of the files in the repository have changed. The hash is designed such that the difference between two hashes will be extreme, even if the changes made to the files tracked were small. The hash is also designed such that there is an (extremely!) low probability any two different repository commits will have the same hash.

Hashes are often used to track differences between files or records in computer science, and are used to create one way (i.e., non-reversible) functions in computer security (e.g., for storing a password without revealing the password). Hashes are notably used in blockchain technology to track changes in financial records, in a manner similar to the way Git has used them for decades.

You can see all commits and their corresponding hashes with the following command. When viewing the log of commits, it is clear why it is important to have descriptive and grammatically correct commit messages so the log is legible.

```bash
git log
```

An obvious question to ask is what happens in the extremely unlikely event that two different versions of your repository have the same hash? There are more possible files than there are hashes so this is technically possible. Linus Torvalds, creator of Linux and Git, answered this question himself in an [archived post](http://web.archive.org/web/20120701221418/http://kerneltrap.org/mailarchive/git/2006/8/28/211065). The short answer is that Git will keep the older version (as if no changes have been made). In practice, this can only happen in the case of a maliciously designed cyber-attack, which would be expensive to execute (to search for file with the same hash) and ultimately have no impact (since Git keeps the older files)! Such issues are outside the scope of this course but fun history nonetheless.

#### Seeing a Shorter Git Log

The git log command provides detailed information about each commit. Sometimes it is easier to view a compact version of the repository history using:

```bash
git log --oneline
```

This displays each commit on a single line with a shortened version of its hash and its commit message.

For example, the output may look something like:

```text
93ac014 Add visualization example
48bc871 Fix typo in README
7ad0210 Initial commit
```

#### Reverting to Previous Versions

To revert to a previous version, use `git checkout`. Replace `hash` with the unique signature of the commit you want to revert to. You can find the hash using `git log`. (If you have used descriptive commit messages, it should be easy to associate the hash to the version you want to return to!)

```bash
git checkout hash
```

To checkout the `main` branch (i.e., the primary branch for the project) use the following command.

```bash
git checkout main
```

The ability to revert to an old version is useful when working on assignments, e.g., when you realize your previous work was closer to what you wanted to submit. To help provide plenty of opportunity to revert changes, be sure to commit often! Committing often is a critical best practice both academically and professionally. You should not spend multiple days on a software project without making any commits.

#### Pulling Changes

When working with a repository that is shared with other people, the version stored on GitHub may change after you originally cloned it. The `git pull` command downloads changes from the remote repository and incorporates them into your local copy.

```bash
git pull
```

#### Viewing Remote Repositories

A local Git repository can be connected to one or more remote repositories. A remote is simply another copy of the Git repository stored somewhere else, such as GitHub.

You can see the remote repositories associated with your current repository using:

```bash
git remote -v
```

When you clone a repository from GitHub, Git normally creates a remote named origin automatically. You will therefore commonly see output similar to:

```text
origin  git@github.com:username/repository.git (fetch)
origin  git@github.com:username/repository.git (push)
```

Understanding the remote is helpful when troubleshooting problems with `git pull` or `git push`, since these commands communicate with the remote repository.

#### Seeing What Branch is Active

Use the following command to see a list of current branches available to change to. The branch you are currently on will have an asterisk next to it.

```bash
git branch
```

#### Making a New Branch

Use the following command to make a new branch. Replace `name` with the desired name of your new branch. There are conventions and best practices for using branches when developing on a professional team that are outside the scope of this tutorial and outside the scope of the course in general. In this class, use branches to try new ideas when working on assignments. If you have two ideas that you cannot implement simultaneously, make two separate branches for them and try them both out. Merge the one that works best into main.

```bash
git branch name
```

#### Merging a Branch into Current Branch

To merge a branch into another, first switch to the branch which is receiving the changes and then merge the branch from which the changes are merging. For example, use the following commands to merge `branch-b` into `branch-a`.

```bash
git checkout branch-a # Switch to branch a
git merge branch-b    # Merge branch b into branch a
```

#### Switching Between Branches

Earlier we saw that `git branch` can be used to see available branches and that `git checkout` can be used to move between them. Newer versions of Git provide the `git switch` command specifically for changing branches.

For example, to switch to the main branch:

```bash
git switch main
```

Both `git checkout` and `git switch` are commonly encountered in documentation and existing projects, so it is helpful to recognize both commands.

Instead of first creating a branch with git branch and then switching to it, you can perform both operations at once with the newer `git switch` command.

```bash
git switch -c experiment
```

This is equivalent to the older command:

```bash
git checkout -b experiment
```

#### Deleting a Branch

Once a branch has been merged and is no longer needed, it can be deleted using:

```bash
git branch -d branch-name
```

For example:

```bash
git branch -d experiment
```

Git will normally warn you if you attempt to delete a branch containing work that has not yet been merged. This helps prevent accidentally deleting work.

nce an experiment or change is finished, deleting unused branches can make a repository easier to navigate.

#### Seeing Differences Between Files

The git diff command shows the changes you have made to files since your last commit.

```bash
git diff
```

This is useful before committing because it lets you review exactly what has changed.

If you have already added files using git add, you can see the changes that are currently staged for the next commit using:

```bash
git diff --staged
```

Reviewing your changes before committing is a good professional habit and can help prevent accidentally committing debugging code, temporary files, or other changes you did not intend to include.

#### Removing a File From the Staging Area

Sometimes you may accidentally add a file that you do not want included in your next commit.

For example, suppose you run:

```bash
git add .
```

and then realize that one of the files should not be committed. You can remove that file from the staging area using:

```bash
git restore --staged file.txt
```

This does not delete the file or undo the changes you made to it. It tells Git not to include the file in the next commit unless you add it again.

Use `git status` to confirm which files are staged for the next commit.

```bash
git status
```

#### Discarding Changes to a File

If you have changed a file but decide that you want to discard those changes and return to the version from your most recent commit, you can use:

```bash
git restore file.txt
```

**IMPORTANT:** Unlike removing a file from the staging area, git restore file.txt will discard the changes you have made to that file. Be careful not to delete your work!

Before using it, you may want to inspect your changes with:

```bash
git diff file.txt
```

Git makes it relatively difficult to permanently lose work that has already been committed, but uncommitted changes can be lost. This is another reason to commit your work frequently.

#### Temporarily Saving Uncommitted Changes

Sometimes you may be in the middle of working on something but need to temporarily switch branches or update your repository. Git provides the stash tool for temporarily saving changes that you are not ready to commit.

To save your current changes:

```bash
git stash
```

You can then switch branches, pull changes, or perform other Git operations.

When you are ready to restore the changes:

```bash
git stash pop
```

The stash is useful for temporary work, but it should not replace making commits. If you have reached a meaningful point in your work, making a commit is usually preferable because commits become part of the permanent version history of the repository.

#### Fetching Changes Without Applying Them

The git fetch command downloads information about changes in a remote repository without immediately incorporating those changes into the files you are working on.

```bash
git fetch
```

This is different from:

```bash
git pull
```

A `git pull` downloads remote changes and attempts to incorporate them into your current branch. A `git fetch` only downloads information about those changes. The `git pull` workflow is sufficient for this course, but you may need to use `git fetch`, for example, to review changes before merging them (and risking needing to spend time resolving merge conflicts), review someone else's work, or even working offline (e.g., using `git fetch` to ensure you have remote files available locally).

#### Resolving Merge Conflicts

Git is designed to combine changes made by different people or on different branches. Often it can do this automatically. Sometimes, however, two versions of a repository change the same portion of the same file in incompatible ways. Git cannot determine which version you want to keep. This is called a merge conflict.

When this happens, `git status` is usually the first command you should run. Git will identify the files containing conflicts. Inside those files, Git will add markers similar to:

```text
    <<<<<<< HEAD
    your version
    =======
    other version
    >>>>>>> branch-name
```

You must edit the file yourself, decide which content should remain, and remove the conflict markers.

Once the file contains the code or text you want, add and commit it normally:

```bash
git add file.txt
git commit -m "Resolve merge conflict"
```

Merge conflicts can initially look intimidating, but they are a normal part of using version control on a team. Git is simply asking you to make a decision about which change to keep that it cannot safely make automatically!

#### IMPORTANT: Ignoring Files

Not every file in a development environment should be tracked by Git. For example, temporary files, generated files, Python virtual environments, large datasets, large images, and files containing passwords or API keys generally should not be committed.

Git repositories can contain a special file named `.gitignore` which specifies which files will *not* be tracked by Git. Each line in this file describes files or directories that Git should ignore.

For example:

```bash
.venv/
__pycache__/
*.pyc
```

would tell Git to ignore a Python virtual environment, Python cache directories, and compiled Python files.

Many repositories used in this course will already contain an appropriate .gitignore file. However, understanding its purpose is important when creating your own repositories.

**IMPORTANT SECURITY NOTE:** Never commit passwords, API keys, access tokens, or other secrets to a Git repository, even if the repository is private. These files should only be kept locally.

## Terminal Environment

### What is a Command Line Shell?

In computing, a shell is a means through which users interact with the computer. While we often interact with modern computers through graphic user interfaces (GUIs), it is important in software and data science to be able to interact with computers through command line interfaces (CLIs) since many repetitive tasks can be easily automated through a CLI. This is done through a command line shell. Popular command line shells include Bash (Linux), Zsh (Mac), and PowerShell (Windows).

A shell is, at the most basic level, an infinite loop. It provides an opportunity for a the user to provide input, then provides a response or takes some action and repeats the loop by asking the user for more inputs. This happens until the user exits the shell, often using an exit command. In the case of a command line shell, all of this interaction happens through text. Note that the text used to interact with the shell must be exactly correct to bring about the intended result. Even a single missed character can change the meaning of a command!

The shells we will use in this class are based on Bash. You can learn about Bash in great detail from its [user manual](https://www.gnu.org/software/bash/manual/).

### Mac or Linux/Unix: Bash or Other Command Line Shells

#### Introduction

Command line shells are popular among many Linux / Unix users. Linux / Unix provide a standard *terminal* environment for interfacing through a shell. Mac, which is a descendent of Unix, provides a similar terminal environment. `Ctrl` + `Alt` + `T` opens a terminal in Ubuntu. Pressing `Command` + `Space`, typing "terminal", and pressing enter opens a terminal on Mac.

#### Installation

If you are using any variety of Unix, Linux, or MacOS you should not need to install any additional shells. Linux, for example, should come with Bash and MacOS, for example, should come with Zsh. You are welcome to try other shells if you like. Keep in mind that using a popular shell like Bash will make it easier to find support from the internet and your classmates. Some shells, like Bash and Zsh, have similar commands. Other shells, like PowerShell, have different commands. Changing shells can feel like changing dialects when speaking a language if they are similar shells, or even feel like learning a new language if switching to a very different shell!

### Windows: Git Bash

#### Introduction

Modern Windows provides CLIs through both Command Prompt and PowerShell. You can open Command Prompt by using `Windows` + `R` to open the run window, typing "cmd" and pressing enter. You can open PowerShell by opening the run window with `Windows` + `R` and typing "powershell". Both are useful for some tasks but many online tutorials for data science tools are written for users of Linux who would use Bash or a similar shell. To make sure you will be able to easily follow these tutorials, using Git Bash instead of Command Prompt and PowerShell is highly recommended! A common cause of errors in this class is attempting to use a command for Git Bash in Command Prompt or PowerShell.

#### Installation

Luckily, Git Bash should have installed when you installed Git! If you do not have Git Bash installed, you might need to restart (if you just installed Git) or might need to try to [reinstall Git](https://git-scm.com/downloads). If you reinstall Git, be sure to note if there is an option to include Git Bash. To use Git Bash, right click on a folder in Windows explorer and use the menu option to `Open Git Bash Here`. If you do not have a desktop shortcut for Git Bash already, you can find where it is installed by searching for Git Bash in the search bar, right clicking it in the results, and clicking "Go to file location". Then you can copy the Git Bash program from that location and paste it on your desktop as a shortcut.

### Useful Commands

Assuming you are using Bash, Zsh, or Git Bash, these commands should all work the same. Note that they might be different in other shells! Commands for any shell are easily searchable online if you get stuck or want to learn more. For example, if you are using Git Bash and forget how to change directories, just Google search "how to change directories in Bash". Yes, it is that easy! (And yes, you are allowed and encouraged to Google search for commands during any assignment, quiz, or exam in this class!)

**Warning**: when searching for commands online, be sure to consult authoritative sources (like the tool's official documentation) to confirm what you need to run. Never blindly copy-paste code from untrusted sources (e.g., Reddit or other forums). In many cases, code posted on forums is helpful but in rare cases malicious users may attempt to get unsuspecting beginners to run dangerous code by pasting it to forums.

#### Seeing Where You Are

It is important to know what folder you are in when working on the command line. Do this with the `pwd`, i.e., the "print working directory" command.

```bash
pwd
```

A common mistake, especially in Windows, is to open a shell in a folder you do not have permission to write data to or perform other operations in (e.g., your root folder or a protected system area). Be sure to check where you are in your shell. It is recommended to use the commands in this tutorial to create a folder for this course in an area like your desktop or another user folder.

#### Seeing Who You Are

It is important to know what user you are operating as on the command line. Find this out using the `whoami` command.

```bash
whoami
```

Usually, this will print your user name. This means you are operating as yourself! Sometimes, you might want to open your shell as an administrator or with other privileges. In this case, you can confirm you have done so by running the `whoami` command. It should then print `root`, `admin` or something similar. Do not run a shell as a root or administrative user unless you absolutely need to! Elevated privilege accounts will enable you to run commands that may harm system files your computer needs to run properly. The operating system assumes you know what you are doing if you are using an account with elevated privileges.

#### Moving Between Directories

The basic way to move around your file system in the terminal is using the `cd`, i.e., "change directories" command.

```bash
cd DIRECTORY
```

Here we replace `DIRECTORY` with the name of the folder or path we want to navigate to. For example, the following command will `cd` to the `my_folder` directory.

```bash
cd my_folder
```

The `cd` command provides useful shorthands for moving to common directories.

The tilde, `~`, is shorthand for your home directory and the following command will take you home.

```bash
cd ~
```

A shorthand that is useful when working on a shared system (e.g., a team server) is `cd ~USERNAME` where you can replace `USERNAME` with the name of the user who's home area you want to navigate to. You will use this command often if working on a server with teammates in a professional setting (and will likely have your teammates' user names memorized).

The dash, `-`, is shorthand for the last directory you were in. The following command takes you back to the last directory you were in.

```bash
cd -
```

Two dots, `..` is shorthand for moving up one directory.

```bash
cd ..       # Move up one directory
cd ../..    # Move up two directories
cd ../../.. # Move up three directories
```

#### Tip: Understanding the Single Dot, `.`, and Relative vs. Absolute Paths

Many commands will use a single dot, i.e., `.`. This is shorthand for the current directory (the directory the command is being run from). For example, the command

```bash
git add .
```

Means add any files that have changes under the *current* directory. You will see a single dot sometimes in paths, such as the following.

```bash
./venv/bin
./venv/lib
```

In this case, the first dot means that the paths are specified relevant to the current directory. Using this notation is convenient since some paths or commands can be specified in a way that will not break if they need to be run again from a different directory. A path specifying the locations of folders or files relative to the current directory is called a *relative path*. Conversely, a path specifying the locations of folders or files relative to the root of the file system (`/`) is called an *absolute path*.

An example of a relative path is:

```bash
./path/to/my_script.py
```

An example of an absolute path is:

```bash
/c/Users/username/my_scripts/path/to/my_script.py
```

When using a relative path, remember that the current working directory of the process that is referencing the relative path will be used to access the file being referenced. You can find out the current working directory of the process that is using the reference by having the process call the `pwd` command. Note that the working directory of the process might not be the same as the working directory you are current in or the directory that you opened your terminal from!

To see how this works, make a quick script (shell scripting will be explained later on in this tutorial):

```bash
echo 'cd .. && pwd' > example.sh
```

Then run the following commands:

```bash
pwd # Run pwd directly from the terminal
/bin/bash example.sh # Run pwd from inside a script
```

Observe how the pwd command run directly from the terminal (the first command) returns a different result than the one run from inside the script. This is because a new terminal (without a user interface) was spawned under the hood as a new process (i.e., a *subprocess*) to run the script.

That new terminal now has a working directory of its own, independent of the working directory of the process that spawned it (i.e., the *parent* process). The `cd` command in the subprocess changed its working directory to be different than the parent directory.

In practice, we do not normally make scripts by echoing the commands we want to run from the command line, but it is good practice for using the command line here.

#### Making Directories

Use the `mkdir` command to make new directories.

```bash
mkdir DIRECTORY
```

Here we replace `DIRECTORY` with the name of the folder we want to create. The following command will create a new directory called `my_folder`.

```bash
cd my_folder
```

#### Making Files

You can quickly make new files using the `touch` command. The following command will create a Python script file `script.py` if it does not already exist.

```bash
touch script.py
```

If the file already exists, its last modified timestamp will be updated to the moment the touch command was invoked but the file contents will not be changed.

#### Printing File Contents to the Screen

The `cat` command is used to print the contents of a file to the screen. In this command, `cat` is short for `concatenate` since we are concatenating the contents of the file to the buffer which is displayed on the screen.

The following commands create a file, add some text to it, and display this text to the screen.

```bash
echo "hello world" > file.txt
cat file.txt # Should print hello world
```

#### Listing Files in a Directory

Files in a directory can be listed using the `ls` command. This is important and will be used often.

```bash
ls
```

The `ls` command provides many useful options.

```bash
ls -l     # Provides a long format list which shows dates and file permissions
ls -a     # Lists all files, including hidden files (hidden files begin with a dot)
ls -lat   # Combination of options listing all files in long format, newest first
ls -latr  # Combination of options listing all files in long format, oldest first
```

#### Finding Patterns in Files

The `grep` command can be used to find files in a directory. It is used like `grep pattern file`. The following example creates three files and then uses grep to search for a pattern between them.

```bash
echo "alpha" > file1.txt
echo "beta" > file2.txt
echo "gamma" > file3.txt
grep beta file*.txt  # Should output that pattern beta was found in file2.txt
```

Note that this example uses `>` to direct the output of the `echo` command into each file, and will create these files if they do not exist.

#### Redirecting Output and Chaining Commands

The CLI is most useful for automating tasks by chaining multiple commands together. Bash provides several ways to do this.

To simply run multiple commands on one line, separate them by a semi-colon. For example, do the following to move up one directory and then print the working directory.

```bash
cd ..; pwd
```

To execute the second command only if the first is successful, use `&&` to chain them together.

```bash
cd .. && pwd
```

To direct the output of one command into another Bash provides the ability to create *pipelines*.

The following command will list all files in the current directory, but will only show those with the pattern "2024" in their name. This command "pipes" the output of `ls` into `grep` to search through it.

```bash
touch file1_2023.txt
touch file2_2023.txt
touch file3_2023.txt
touch file1_2024.txt
ls | grep 2024
```

Note that this will only redirect standard output (known as STDOUT). Error messages (known as STDERR) will still be printed to the screen instead of being directed to the next command in the pipeline. To redirect both STDOUT and STDERR in a pipeline, use `|&` instead of `|`.

To redirect output to a file, use the `>` operator. This is what we did in the `grep` example above. As another example, the following command will output the list of files produced by `ls` to the file `my_file_list.txt`.

```bash
ls > my_file_list.txt # Overwrites my_file_list.txt with the output of ls
```

Note depending on how your system is configured, this will overwrite `my_file_list.txt`! To append the output to `my_file_list.txt` instead, use the `>>` operator.

```bash
ls >> my_file_list.txt # Appends the output of ls to my_file_list.txt
```

See the Bash manual pages on [pipelines](https://www.gnu.org/software/bash/manual/html_node/Pipelines.html) and [redirecting output](https://www.gnu.org/software/bash/manual/html_node/Redirections.html#Redirecting-Output) to learn more.

#### Shell Scripting

When using a shell to automate actions, commands are written in a *shell script*, i.e., a file with shell commands. The shell is then used to run the script which invokes the commands therein as if you were typing them in the shell. Shell scripting is outside the scope of this tutorial, but a basic example is shown here.

```bash
echo '#!/bin/bash' > hello.sh          # Make a file called hello.sh
echo 'echo "Hello World!"' >> hello.sh # Append a command to this file
cat hello.sh       # Inspect hello.sh to see what we wrote to it
chmod 755 hello.sh # Ensure we have permission to execute hello.sh
./hello.sh         # Runs the script to print Hello World!
```

Shell scripting is not part of this course, but it is useful to know in case you want to automate simple tasks. Normally, you would write a shell script in a file editor, but the above commands provide some examples of techniques learned here.

#### Comments

You may have noticed that we are providing helpful hints as to what our commands do after a `#` character. These are called comments. Comments are ignored by the shell and are useful for adding helpful documentation inside shell scripts. Remember that a good comment (outside the context of a tutorial) explains *why* a line of code is being written rather than explaining *what* the line of code does. Professionally, it is important to always write code which is understandable to you and your peers, ideally *without* needing to rely on comments to explain what you are doing. If you need to write a comment to explain what a line of code does, think of a simpler way to write that line so it is self-explanatory, and try using more descriptive variable and function names so your code reads like plain english.

#### Changing Permissions of a File or Folder

To ensure that only authorized users can access files and folders, operating systems maintain a *file permission system*. The file permission system indexes which users are allowed to access which files. Unix and unix-derived operating systems provide the `chmod` (short for "change mode") command to change permissions of a file or folder. For Windows users, Git Bash or other terminal emulators can emulate the the `chmod` command.

To understand how `chmod` works, it is necessary to know some basic binary code (i.e., strings of ones and zeros). To read binary code, we check where each one is and for each one we see, add $2^N$ to a sum, where $N$ is the place in the list of characters that the one occurred. For example, the string $101$ in binary corresponds to the number 5 in decimal since there is a one in the zeroth (right most) position and second (left most) position, and

$$
\begin{align*}
101_{\mathrm{BASE}\ 2} &= [(1 \times 2^2) + (0 \times 2^1) + (1 \times 2^0)]_{\mathrm{BASE}\ 10} \\
&= 4 + 0 + 1 \\
&= 5.
\end{align*}
$$

With that background in mind, the permissions of any file are defined for `chmod` by three binary numbers. The first number defines the permissions that the user who owns the file has, called the `user` permissions. The second number defines the permissions that the group (collection of users) owning the file has, called the `group` permissions. The third number defines the positions everyone else has, called the `other` or `world` permissions.

The first bit (one or zero) of each number specifies whether that user or group of users can *read* (open and view) the file or folder. The second bit of each number specifies whether the corresponding user or group of users can *write* (modify and save modifications) the file or folder. The third bit specifies whether that user or group of users can *execute* (run the file if it is a program or script) the file.

With this in mind, the `chmod` command uses three numbers (0-7) to specify read, write, and execute permissions for users, groups, and the world. When converted to binary, these numbers have ones in the locations where permissions are to be granted, and zeros in the locations where permissions are not to be granted.

For example, the command

```bash
chmod 754 script.sh
```

will do the following:

* Give the *user* owning the script *all* permissions, since

$$7 = [111]_{\mathrm{BASE}\ 2} = (\mathrm{READ\ ON,\ WRITE\ ON,\ EXECUTE\ ON})$$

* Give the *group* owning the script *read* and *execute* permissions, since

$$
5 = [101]_{\mathrm{BASE}\ 2} = (\mathrm{READ\ ON,\ WRITE\ OFF,\ EXECUTE\ ON})
$$

* Give the *world* *read-only* permissions, since

$$
4 = [100]_{\mathrm{BASE}\ 2} = (\mathrm{READ\ ON,\ WRITE\ OFF,\ EXECUTE\ OFF})
$$

#### Folders are Files!

When working with folders, it is helpful to know that Unix-derived operating systems treat them as files, and emulations of Unix tools emulate this behavior. To a Unix system, a folder is just a file that keeps track of which files human users expect to be in a particular location and which users have permissions to access them. With this in mind, it is easy to understand that changing the permissions of a folder simply changes the permissions of the file that indexes the contents of that folder. For example, making a folder writeable by a user does not by default make all folders beneath it writeable, it only means that user can add other folders to it.

#### Common `chmod` Examples

The follow are common uses of the `chmod` command.

Provide all permissions to the user and group, make the file readable and executable (but not writeable) to everyone else:

```bash
chmod 775 script.sh
```

Provide all permissions to the user, read and execute permissions to the group, and read-only permissions to everyone else:

```bash
chmod 754 script.sh
```

Provide all permissions to everyone (use this with caution):

```bash
chmod 777 script.sh
```

Recursively traverse all sub-folders, sub-sub-folders, etc. and open all permissions to the user, and read and execute (but not write) permissions to everyone else (group and world):

```bash
chmod 755 /path/to/folder
```

Use this command with caution. Think if you really want *all* files beneath a folder (including all sub-folders) to have the permissions you are specifying before applying this command.

#### Scope of Permission Changes and Differences between Operating System Permissions vs. Git Hub Visibility

Remember that the permission changes you apply will only apply to the computer network that you are applying them on. If you make a file world-readable on your local computer, it is still subject to any protections provided by your firewall, network router, etc. and therefore not truly readable by "the world." However, if you are working on a shared network (such as a shared university high performance computing cluster) making a file world readable *will* make it accessible to other students on that same network. Be very careful making files group-writable or world-writeable on shared computers since your teammates can accidentally modify them if you do that!

Also remember that Git Hub has its own permission management system and the permissions that you apply on the computer you develop on (whether a local or remote machine) are not related to whether or not someone can access your code via Git Hub in the cloud. Git Hub provides users the ability to make repositories public (truly viewable by the world on the internet) or private (only viewable to the user). These permissions must be configured in Git Hub itself and do not inherit from anything specified via `chmod`.

In class, all lecture notes and educational resources written by your instructor are made public by default to facilitate ease of access. All student work is made private and accessible only to the student, except in the case of group work, where it is made accessible only to members of the same group. These permissions will be configured via Git Hub classroom on a per project basis. Students are not responsible for configuring these themselves. If you wish to make your work from this course public (e.g., to link to it in your resume), you must re-push your work to a repository on a personal Git Hub account, make it public there, and link to that repository. Do not attempt to provide links to your work to others outside class since they will show up as inaccessible to them.

#### Tip: Up Arrow!

Most shells will allow you to access the last commands you typed using the up arrow. This will prevent you from having to retype commands and can also be useful when you realize your last command generated an error. Simply use the up arrow to access that command, change what

#### Tip: Seeing Command History

You can see all the commands you have previously used by typing `history`.

```bash
history
```

This is particularly useful in a pipeline with `grep`.

```bash
history | grep "cd" # Finds all the commands previously executed with the pattern "cd"
```

#### Tip: --help and Other Standard Arguments

Many shell commands provide standard arguments. The two most ubiquitous are `--help` and `--version`. You can learn more about standards for shell commands in the [GNU Standards](https://www.gnu.org/prep/standards/html_node/Command_002dLine-Interfaces.html).

For example, you can get help with the `ls` command by typing the following.

```bash
ls --help
```

#### Tip: Google it!

As noted before, all of these commands are thoroughly documented online. You are always allowed to Google them and to Google errors you get in this course. Finding documentation online and using it to solve problems independently is a critical skill to learn academically and professionally. You can also use AI tools to generate these commands, as long as you are reviewing the output. Reviewing LLM output is especially important for critical commands that move or delete files!


