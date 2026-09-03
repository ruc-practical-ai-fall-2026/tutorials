# Taking and Submitting Assignments

## Introduction

Assignments for this course are distributed using GitHub repositories.

Each assignment begins as a public template repository maintained by the instructors. You will create your own private repository from this template under your personal GitHub account, give the instructor access to your repository, clone it to your development environment, complete the assignment, and push your work back to GitHub.

The general process is:

1. Get assignment template from course organization.
2. Create your private repository.
3. Add the instructor (and any teammates for group work) as a collaborator.
4. Clone your repository.
5. Complete the assignment.
6. Commit and push your work.
7. Submit the assignment.

Your assignment repository belongs to you and will remain in your GitHub account after the course ends. For projects you would like to link to on your resume, they will persist in your GitHub account after the course ends.

## Creating a GitHub Account

If you already have a GitHub account, you may use your existing account for this course. If you do not already have one, go to:

```text
https://github.com/signup
```

Follow the prompts to create a personal GitHub account. You will need to:

1. Enter an email address.
2. Create a password.
3. Choose a GitHub username.
4. Complete GitHub's account verification process.
5. Verify the email address associated with your account.

Your GitHub username is important because it identifies your account throughout GitHub. For example, if your profile is:

```text
https://github.com/jsmith
```

then your GitHub username is:

```text
jsmith
```

You will use the same GitHub account throughout the course.

GitHub also strongly recommends enabling two-factor authentication for your account.

## A Note About the Course GitHub Organization

The instructor-maintained repositories for this course are hosted in:

```text
ruc-practical-ai-fall-2026
```

You do not need to join this organization to complete assignments. You may clone the instructor repositories and modify them locally if you like to, but pushing them back to the course organization is not the correct way to submit assignments.

The assignment templates are public, so you can access them using your normal personal GitHub account.

Your own assignment repositories will live under your account.

For example:

```text
Instructor repository:

ruc-practical-ai-fall-2026/assignment-01-python

Your repository:

jsmith/assignment-01-python
```

The first repository is maintained by the instructor. The second repository is your private copy of the assignment and is where you should do your work.

## Taking an Assignment

The instructor will provide a link to the GitHub repository containing the assignment. For example:

```text
ruc-practical-ai-fall-2026/assignment-01-python
```

Open the repository on GitHub. Near the top of the repository page, click:

**Use this template**

then:

**Create a new repository**

This creates a new repository containing the starting files for the assignment. Unlike a Git fork, your new repository is an independent repository that simply begins with the files provided by the instructor.

## Creating Your Assignment Repository

When GitHub asks where to create the repository, select your **personal GitHub account** as the owner. Use the same assignment name unless the assignment instructions specify otherwise.

For example:

```text
assignment-01-python
```

Select:

**Private**

for the repository visibility.

Your finished repository might therefore be:

```text
jsmith/assignment-01-python
```

Click **Create repository**.

GitHub will create the assignment repository under your account and take you to its repository page. After the course is over, you can change repositories to public if you would like to use them in a portfolio (e.g., for job applications).

## Adding the Instructor as a Collaborator

Your assignment repository is private, so the instructor cannot see it until you explicitly give them access.

You should do this immediately after creating the repository.

On your repository's GitHub page:

1. Click **Settings**.
2. Select **Collaborators** or **Collaborators and teams**.
3. Click **Add people**.
4. Search for the instructor's GitHub username provided in class.
5. Select the correct account.
6. Send the invitation.

The instructor must accept the invitation before they can access the repository. For assignments where group work is allowed, you can also add other students as collaborators.

You only need to give the instructor access to the assignment repository. You are not giving the instructor access to your GitHub account or to your other private repositories.

Do not wait until the assignment deadline to complete this step just in case something goes wrong!

## Cloning Your Assignment

You now need to clone *your repository*, not the original instructor repository.

Click the **Code** button on your repository's GitHub page and copy its Git URL.

Then open a terminal in the directory where you would like to store your coursework and run:

```bash
git clone <repository-url>
```

For example:

```bash
git clone git@github.com:jsmith/assignment-01-python.git
```

Change into the newly created directory:

```bash
cd assignment-01-python
```

You can now open this directory in VS Code or whatever development environment you are using.

```bash
code .
```

## Setting Up the Assignment Environment

Read the assignment's `README.md` before beginning. Most assignments will include instructions for installing any required packages or configuring the development environment.

For projects using `uv`, this will commonly include:

```bash
uv sync
```

This creates or updates the project's virtual environment and installs the dependencies specified by the project. Assignment-specific instructions may differ, so always check the repository's `README.md`.

## Working on the Assignment

Work on the assignment normally in your cloned repository. You should commit your work periodically as you make meaningful progress.

Git status, i.e.,

```bash
git status
```

can be used to see which files you have changed.

You can stage your changes with

```bash
git add .
```

and commit them with a descriptive message.

```bash
git commit -m "Complete data preprocessing"
```

Then push the commit to GitHub.

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

Make commits often, at reasonable points where you have completed some meaningful piece of work. Every line of code is too much, but once per assignment is too little. Commits are intended to provide a log of your work for you and collaborators. You can go back to them like reverting to a checkpoint in a video game if needed!

## Checking Your Work on GitHub

After pushing, open your repository on GitHub. You should see your most recent files and commits there.

**NOTE:** Work that exists only on your computer has *not* automatically been submitted to GitHub. Be sure to check that you can view your work online!

Remember that you must run the full add, commit, and `git push` workflow for commits to appear on GitHub.

## Submitting Your Assignment

When you are finished with the assignment and are ready to submit it, first save all of your files. (Do not forget to save!)

Stage your final changes:

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

The complete submission sequence you will have memorized by the end of the class is as follows.

```bash
git add .
git commit -m "finish assignment"
git push
```

Your assignment is considered submitted when the `finish assignment` commit has been successfully pushed to GitHub.

## Verify Your Submission

After submitting, open your repository in the browser on GitHub.

Confirm that:

1. Your latest work appears in the repository.
2. The latest submission commit includes the message `finish assignment`.
3. The commit appears on GitHub before the assignment deadline.
4. The instructor has been added as a collaborator and can access the repository.

If the commit exists only on your computer and has not been pushed, the assignment has not been submitted. If the repository is private and the instructor does not have access to it, the assignment cannot be graded.

## Making Changes After Submission

Git does not prevent you from continuing to work after making a `finish assignment` commit. If you discover a problem before the deadline, you may continue working normally:

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

The most recent valid submission before the deadline will be treated as your submitted version.

## Common Mistake: Cloning the Instructor Repository

Make sure you clone *your assignment repository*, not the original assignment template. The instructor repository might be:

```text
ruc-practical-ai-fall-2026/assignment-01-python
```

while your repository might be:

```text
jsmith/assignment-01-python
```

You should do your work in the second (personal) repository.

If you clone the instructor repository, you will generally not have permission to push your changes to it.

## Common Mistake: Creating a Public Repository

Unless an assignment specifically says otherwise, your assignment repository should be **private**. Do not make graded assignment work public while the assignment is active.

If you accidentally create the repository as public, you can change its visibility from the repository settings or recreate it as a private repository.

You can and should make work you are proud of public after the course has ended!

## Common Mistake: Forgetting to Add the Instructor

Creating a private repository does not automatically give the instructor access. Make sure you add the instructor as a collaborator when you create the assignment repository. You can verify this from the repository's collaborator settings.

## Common Mistake: Forgetting to Push

A Git commit saves a version of your project in your **local Git repository**. For example:

```bash
git commit -m "finish assignment"
```

does not by itself send your work to GitHub. You must also run:

```bash
git push
```

The version that is pushed is the version that will be graded!

## Summary

For each assignment:

1. Open the instructor's public assignment repository.
2. Select "Use this template."
3. Create a private repository under your personal GitHub account.
4. Add the instructor as a collaborator.
5. Clone your repository.
6. Complete the assignment.
7. Commit and push your work regularly.
8. When finished, run the add, commit, and push workflow.
9. Verify the submission on GitHub.
10. Confirm that the instructor still has access to the repository.
