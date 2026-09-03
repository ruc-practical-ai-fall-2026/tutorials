# Taking and Submitting Assignments

## Introduction

Assignments for this course are distributed using GitHub repositories.

Each assignment begins as a template repository maintained by the instructor. You will create your own repository from this template, clone your repository to your development environment, complete the assignment, and push your work back to GitHub.

The general process is:

```text
Assignment Template
        ↓
Create Your Repository
        ↓
Clone Your Repository
        ↓
Complete the Assignment
        ↓
Commit and Push Your Work
        ↓
Submit the Assignment
```

This is intentionally very similar to how you might begin working on an existing software project outside of a classroom environment.

## Taking an Assignment

The instructor will provide a link to the GitHub repository containing the assignment. For example, an assignment repository might be named:

```text
assignment-01-python
```

Open the repository on GitHub. Near the top of the repository page, click:

**Use this template**

and then:

**Create a new repository**

This creates a new repository containing the starting files for the assignment.

Unlike a Git fork, your new repository is an independent repository that simply begins with the files provided by the instructor.

## Naming Your Repository

Name your repository using the assignment name followed by your GitHub username. For example, if the assignment is:

```text
assignment-01-python
```

and your GitHub username is:

```text
jsmith
```

your repository should be named:

```text
assignment-01-python-jsmith
```

Create the repository inside the course GitHub organization:

```text
ruc-practical-ai-fall-2026
```

Your assignment repository should be **private** unless the assignment instructions specifically tell you otherwise.

After creating the repository, GitHub will take you to the page for your new repository.

## Cloning Your Assignment

You now need to clone **your repository**, not the original instructor repository.

Click the **Code** button on your repository's GitHub page and copy its Git URL.

Then open a terminal in the directory where you would like to store your coursework and run:

```bash
git clone <repository-url>
```

For example:

```bash
git clone git@github.com:ruc-practical-ai-fall-2026/assignment-01-python-jsmith.git
```

Change into the newly created directory:

```bash
cd assignment-01-python-jsmith
```

You can now open this directory in VS Code or whatever development environment you are using.

For example:

```bash
code .
```

## Setting Up the Assignment Environment

Read the assignment's `README.md` before beginning.

Most assignments will include instructions for installing any required packages or configuring the development environment.

For projects using `uv`, this will commonly include:

```bash
uv sync
```

This creates or updates the project's virtual environment and installs the dependencies specified by the project.

Assignment-specific instructions may differ, so always check the repository's `README.md`.

## Working on the Assignment

Work on the assignment normally in your cloned repository.

You should commit your work periodically as you make meaningful progress.

For example:

```bash
git status
```

can be used to see which files you have changed.

You can stage your changes with:

```bash
git add .
```

and commit them with a descriptive message:

```bash
git commit -m "Complete data preprocessing"
```

Then push the commit to GitHub:

```bash
git push
```

You should do this throughout the assignment rather than waiting until the very end.

For example, an assignment might accumulate commits such as:

```text
Set up data loading
Add preprocessing
Implement baseline model
Add evaluation plots
Finish discussion
```

Make commits often at reasonable points where you have completed some meaningful piece of work.

## Checking Your Work on GitHub

After pushing, open your repository on GitHub. You should see your most recent files and commits there.

This is an important check. Work that exists only on your computer has **not** been submitted to GitHub.

You can also run:

```bash
git status
```

before submitting.

Ideally, you should see something similar to:

```text
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

This indicates that your changes have been committed.

Remember that you must also have run:

```bash
git push
```

for those commits to appear on GitHub.

## Submitting Your Assignment

When you are finished with the assignment and are ready to submit it, first save all of your files.

Then stage your final changes:

```bash
git add .
```

Create a commit with the message:

```bash
git commit -m "finish assignment"
```

Finally, push the commit:

```bash
git push
```

The complete submission sequence is therefore:

```bash
git add .
git commit -m "finish assignment"
git push
```

Your assignment is considered submitted when the `finish assignment` commit has been successfully pushed to GitHub.

## Verify Your Submission

After submitting, open your repository on GitHub one final time.

Confirm that:

1. Your latest work appears in the repository.
2. The most recent commit includes the message `finish assignment`.
3. The commit appears on GitHub before the assignment deadline.

If the commit exists only on your computer and has not been pushed, the assignment has not been submitted.

## Making Changes After Submission

Git does not prevent you from continuing to work after making a `finish assignment` commit.

If you discover a problem before the deadline, you may continue working normally:

```bash
git add .
git commit -m "Fix evaluation plot"
git push
```

When you are ready to submit the corrected version, make another:

```bash
git add .
git commit -m "finish assignment"
git push
```

Unless the assignment instructions state otherwise, the most recent valid submission before the deadline should be treated as your submitted version.

## Common Mistake: Cloning the Instructor Repository

Make sure you clone **your assignment repository**, not the original assignment template.

The instructor repository might be:

```text
ruc-practical-ai-fall-2026/assignment-01-python
```

while your repository might be:

```text
ruc-practical-ai-fall-2026/assignment-01-python-jsmith
```

You should do your work in the second repository.

If you clone the instructor repository, you generally will not have permission to push your changes to it.

## Common Mistake: Forgetting to Push

A Git commit saves a version of your project in your **local Git repository**.

For example:

```bash
git commit -m "finish assignment"
```

does not by itself send your work to GitHub.

You must also run:

```bash
git push
```

A useful distinction to remember is:

```text
git commit
    ↓
saves your work to your local Git repository

git push
    ↓
sends those commits to GitHub
```

For submission purposes, the version on **GitHub** is the version the instructors can grade.

## Summary

For each assignment:

```text
1. Open the instructor's assignment repository.

2. Select "Use this template."

3. Create a private repository in:
   ruc-practical-ai-fall-2026

4. Name it:
   <assignment-name>-<your-github-username>

5. Clone your repository.

6. Complete the assignment.

7. Commit and push your work regularly.

8. When finished:

   git add .
   git commit -m "finish assignment"
   git push

9. Verify the submission on GitHub.
```

If you understand this workflow, you understand nearly everything you need to use Git for assignments in this course.
