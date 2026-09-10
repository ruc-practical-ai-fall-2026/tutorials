# AI-Assisted Software Development with Codex

## Introduction

Large Language Models (LLMs), e.g., ChatGPT, and other AI technologies are powerful tools that are increasingly integrated into modern software development. AI coding tools can help explain unfamiliar code, generate code snippets, identify bugs, write tests, refactor programs, and answer questions about programming libraries and development tools.

Use of LLMs is encouraged in this course, and setup of AI coding tools is part of the course material. For this course, our preferred AI coding tool is OpenAI's Codex. As with all other course setup, you may use other tools if you wish and you are encouraged to explore multiple tools to see which ones you like. Keep in mind though that using the preferred course tools will make it easier to obtain help from your classmates and your instructor.

Codex is an AI coding agent that can work directly with the files in your project. Rather than copying code back and forth between an editor and a general-purpose chatbot, Codex can inspect your project, discuss the code with you, propose changes, edit files, and run commands such as tests and formatters. In professional software development for many fields, it is increasingly common to interact more with the AI coding agent(s) in your development environment than directly with your code.

The introduction of agents to modern software development is sometimes described as analogous to the introduction of compilers to software development in its early years, or object oriented programming in more recent decades. Like compilers and object oriented programming, using agents to write code enables us to think at higher levels of abstraction. As with any abstraction, the simplicity of the abstraction comes with the tradeoff that there are multiple potential specific solutions that can be implemented to satisfy the abstraction.

Just as there are multiple assembly language implementations of high level C++ code, there are multiple possible implementations in code that an agent might wright in response to a natural language prompt. It is therefore up to you as the software craftsperson to take responsibility for ensuring that the code implemented is correct for your application and requirements. In this course, **you are responsible for the work you turn in and the grade that it receives**. Similarly, in a professional development team, **you are responsible for your code and the impacts it has on your team, users, and society**. AI tools should be used to help you develop, understand, and review your work, not to replace reasoning and technical judgment. This is especially true in an academic setting, where the primary goal of your education is to develop your own reasoning and technical judgement. Using LLMs to automate all of your work for you in class would be analogous to attempting to learn to speak a new language by copy-pasting from a translator!

The following sections walk you through the complete setup process. Even if you have used ChatGPT, GitHub Copilot, Claude, or another AI coding tool before, work through the setup so that you have the same basic environment used in the course.

## Creating a ChatGPT Account

Codex can be accessed using a ChatGPT account.

If you already have a ChatGPT account, you can skip this section. Otherwise, do the following to make an account.

1. Go to the ChatGPT website.
2. Select **Sign up**.
3. Create an account using your preferred supported sign-in method.
4. Complete any account verification requested during signup.
5. Sign into ChatGPT at least once before continuing.

Codex is available with ChatGPT accounts, although different account types may have different usage limits.

## API Keys

You do not need to create an OpenAI API key for the normal Codex setup used in this course. We will develop more advanced applications later in this course that may require an API key. That will be covered in the instructions for those assignments.

## Installing Codex in VS Code

For most work in this course, the recommended way to use Codex is through OpenAI's official VS Code extension. To install the extension, open VS Code and select the **Extensions** icon from the Activity Bar on the left side of the window. You can also open the Extensions panel using the following shortcuts

Windows:

```text
Ctrl+Shift+X
```

MacOS:

```text
Cmd+Shift+X
```

Search the extension marketplace for:

```text
Codex
```

Install the official **Codex** extension published by **OpenAI**.

**NOTE**: Be careful when installing development tools from extension marketplaces. Check the publisher rather than installing another extension that happens to have a similar name. In some cases there might be multiple extensions with the same name, which might cause confusion. In rarer, but more serious cases, there might be malicious tools that share the same or similar names as common tools. Always verify the publisher of any software you install, whether through VS Code extension marketplace or other source!

After installation, you should see a Codex icon in the VS Code interface. If the icon does not appear, open the VS Code Command Palette with `Ctrl+Shift+P` (Windows) or `Cmd+Shift+P` (macOS). Search for `Codex: Open Codex Sidebar`.

## Signing Into Codex

To sign into Codex, first open the Codex sidebar. The first time you use Codex, you will be prompted to sign in. Choose the option to **Sign in with ChatGPT** and follow the authentication process in your browser. Use the ChatGPT account that you created earlier.

After authentication completes, return to VS Code. Codex should now be available directly from the editor.

## Opening a Project

Codex works best when you open the **entire project folder** rather than an individual Python file.

For example, if you cloned an assignment repository named `assignment-01`, you would select `File -> Open Folder` in VS Code and open the `assignment-01` folder.

Your VS Code Explorer might then look something like:

```text
assignment-01/
├── README.md
├── pyproject.toml
├── src/
│   └── solution.py
└── tests/
    └── test_solution.py
```

When Codex is working inside this folder, it can inspect the files in the repository and use them as context when answering your questions. This is one of the major advantages of using a coding agent inside your development environment instead of copying isolated pieces of code into a web browser. The project context, including any documentation, folder structure, files, etc. will inform the agent, helping to define the implementations the agent will develop in response to the prompts that you give.

## Your First Conversation with Codex

Before asking Codex to write anything, it is helpful to ask it to explain the project. This can be a useful way to explore a new repository, and identify which parts of the repository you need to modify and pay attention to so that you can accomplish a task.

For example:

```text
Explain the structure of this repository and what each file is used for.
Do not change any files.
```

Codex can inspect the repository and give you an overview. You can then "zoom in" to areas you are most interested in for the task at hand by asking increasingly specific questions, e.g.,

```text
Explain what solution.py currently does.
```
```text
Explain the purpose of the tests in tests/test_solution.py.
```
```text
Where in this project should I implement the function described in the README?
```

Using Codex to understand a project before changing it is a good practice to help ensure that you understand the code you will be changing. For large projects, AI-assisted review is common in professional software development.

## Modifying Code via Codex

Codex can also make changes directly to your files.

For example:

```text
Implement the normalize function described in the README.
Keep the implementation simple and do not modify the tests.
```

In response to the prompts, Codex may inspect the relevant files, propose or make changes, and explain what it changed. Review the code Codex generates. Make sure that it belongs in the correct file, follows the coding practices discussed in class, and actually solves the problem you intended to solve.

Remember that **direct copy and paste of LLM output without human editing or review is not considered professional use of AI in this course**. You must review and understand the output of your prompts, and make any changes required (either through additional prompting or manual edits as needed) since ultimately you are responsible for your work and the grade it receives. Do not leave your grade up to any other intelligence but you!

A useful follow-up question is:

```text
Explain the changes you just made and why you made them.
```

If the implementation is more complicated than you expected, you can ask:

```text
Can this be implemented more simply?
```

Iteration and refinement like this is often more effective than trying to write a single "one-shot" prompt containing every requirement. Iteration allows check-pointing frequently via Git commits, and testing frequently, both of which are also good professional practice. You do not need to commit after every prompt, but should commit habitually when you have reached a logical checkpoint that you would like to be able to return to if a subsequent prompt breaks previous code.

In professional software development, you will also frequently run automated unit tests or other tests. Iterative refinement when prompting enables you to run tests frequently, so that when something does break you have a better idea of exactly what step caused the issue, and can debug more readily. While not every assignment in this course will have unit tests, some will, and all will have some means that you can and should use frequently to "sanity check" your outputs. Do not prompt for lengthy sessions without checking if your code works!

## Reviewing Changes

Work produced with AI will be held to the same professional standards as any other work submitted in this course, including proper architecture, use of Git, testing, and review. Professional software development practice evolved to make life easier for your teammates and for your future self, by ensuring that code is not only working now, but easily understood and maintained well into the future. By extension, professional software practice also ensures that agents can be used most effectively on a project, now and in the project's future.

Codex integrates with Git and VS Code so that you can inspect the differences between your original files and the files modified by Codex. Before allowing an AI agent to make substantial changes, it is good practice to make a Git commit containing your current working version.

For example:

```bash
git status
git add .
git commit -m "add checkpoint with working normalizer before codex changes"
```

You can then allow Codex to work on the project. Afterward, you can inspect what changed using Git.

```bash
git diff
```

Pay attention not only to whether the code runs, but also to whether the changes are appropriate and professional. Common problems with poorly reviewed or carelessly prompted AI-generated work include:

* code being placed in the wrong file,
* unnecessarily complicated implementations,
* inconsistent solutions across similar problems,
* incorrect documentation,
* outdated coding practices,
* incorrect expansion of acronyms,
* and confident but inaccurate technical statements.

Just as Git facilitates human collaboration, it gives you a safe way to experiment while still being able to return to a prior version, and makes it easier to identify exactly what an AI tool changed.

## Installing the Codex Command-Line Interface

If you prefer a terminal environment, Codex can also be used directly from a terminal through the **Codex CLI**.

Many students find the VS Code extension the easiest interface for many tasks in this course, but you are welcome to use either the extension or the CLI. The CLI is particularly useful when working in remote systems, DevContainers, GitHub Codespaces, or other environments where it is already common to work in a terminal. Try both the extension and the CLI out and see what you like best!

### Linux and macOS

Open a terminal and run:

```bash
curl -fsSL https://chatgpt.com/codex/install.sh | sh
```

After installation, confirm that the command is available:

```bash
codex --version
```

### Windows

In VS Code, open the terminal. Click the dropdown arrow next to the `+` icon and select PowerShell to spawn a new shell. From PowerShell, the standalone Codex installer can be run with:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 | iex"
```

After installation, open a new terminal and check:

```powershell
codex --version
```

If you are using **WSL**, install Codex from inside your WSL Linux environment using the Linux installation command instead.

If you are using GitBash on Windows, install Codex via PowerShell and then use via GitBash. Note that you might need to restart your shell or restart VS Code after you install Codex.


### Installing ChatGPT for Desktop

Though it is not required, you might also wish to install ChatGPT for Desktop with Codex. Note that installing ChatGPT for Desktop is *not* the same as installing the VS Code Codex extension and is not the same as installing the Codex CLI. These are all different interfaces that provide different ways to use and interact with the GPT family of models. As always, try out different tools and workflows to see what you like.

You can install ChatGPT Desktop with Codex following the instructions here: [https://chatgpt.com/codex/](https://chatgpt.com/codex/).

### Starting Codex from the Terminal


Navigate to one of your project directories:

```bash
cd path/to/your/project
```

Then start Codex:

```bash
codex
```

The first time you run it, follow the instructions to sign in with your ChatGPT account. Once Codex starts, you can communicate with it directly from the terminal. For example:

```text
Explain this repository to me. Do not change anything yet.
```

Because you launched Codex from the project directory, it can inspect files in that project.

## Using Codex Inside a DevContainer

Some of the development work in this course may take place inside a VS Code DevContainer.

Remember that a DevContainer is effectively a separate Linux computer that will feel as if it has its own file system and operating system. Programs installed on your host operating system are not automatically installed inside the container!

The VS Code Codex extension can still provide an integrated interface to your development workflow. If you also want the `codex` command available **inside the container's terminal**, install the CLI from that terminal:

```bash
curl -fsSL https://chatgpt.com/codex/install.sh | sh
```

Then check:

```bash
codex --version
```

This will be automated for you when using standard Development Containers in this course. You can automate it yourself if setting up your own Development Container. Development Container setup will be covered later in the course.


Whenever you are unsure where a command is installed, remember the distinction between your:

* host operating system,
* DevContainer or Codespace,
* and Python virtual environment.

These are different layers of your development stack. Know where you are operating and understand what layer your commands are affecting.

## Codex Workflow and Use Cases in this Course

A simple workflow for using Codex on course assignments is as follows.

1. Open the complete repository in VS Code. Read and understand the assignment yourself.
2. Run the existing code and tests yourself (if applicable).
3. Make a Git checkpoint.
4. Use Codex to ask questions, explore ideas, or help generate specific pieces of code.
5. Review and edit the generated code. Check documentation or other authoritative sources when needed to confirm that generated code or technical claims are correct.
6. Run the program and tests yourself. Make sure you can explain your solution and the major decisions behind it.
7. Commit the final version with Git.

This reflects a key tenet of the ethical use of AI in this course: **understanding core material before applying AI to help expedite generation of tools and results**.

The aim of the course is to develop students who are capable of directing AI tools and other human teammates. That goal is not met if LLMs are used to complete entire assignments without human oversight.

### Appropriate Uses of Codex in this Course

Examples of appropriate uses of Codex in this course include:

* using Codex to write code snippets, then checking documentation to confirm that the code is correct and editing it to fit the problem at hand,
* using Codex directly from your command line or IDE to help develop code,
* using Codex to draft documentation, then checking that the documentation is correct and editing it accordingly,
* using Codex as a companion to bounce ideas off of before implementing those ideas yourself,
* using Codex to help identify concepts or documentation related to a topic, then reading the source material yourself,
* and using Codex to summarize or explain technical material, then checking the explanation against the original material.

The common thread is **human oversight, review, and technical judgment**.

### Inappropriate Uses of Codex in this Course

Use of Codex that prevents you from learning or understanding the underlying material is not appropriate for this course. Examples include:

* asking Codex to perform an entire assignment for you,
* accepting generated code without reading or understanding it,
* copying generated output directly into submitted work without editing or review,
* leaving generated code in files where it does not belong,
* submitting inconsistent answers that show no reasoning was applied across the work,
* retaining confident but incorrect AI-generated statements,
* and using outdated or inappropriate coding practices because an AI model suggested them.

Students who attempt to complete assignments entirely with LLMs often find that AI tools applied without thought and judgment result in low scores, even on seemingly simple problems.

## Tips and Warnings

### Tip: Iterate and Ask for Explanations or Refinements

One of the most valuable uses of Codex in this course is as an interactive companion for learning. If you encounter unfamiliar code, you can ask about it:
```text
Explain this function line by line.
```
```text
What does this syntax mean? Show me a simpler example before explaining how it is used here.
```
You can also challenge its suggestions:
```text
Why did you choose this implementation instead of using a for loop?
```
or:
```text
What are the disadvantages of this approach?
```

These kinds of interactions use AI to strengthen your understanding of the course material, while still building the foundations that you need to hone your ability to review important algorithms and apply good scientific and engineering judgement.

### Warning: AI Tools Can Be Confidently Wrong

LLMs can make statements that sound professional and convincing while still being incorrect. (Note that some humans can do this too - use caution when working with these individuals!) An AI agent might do any of the following, all while making documentation, comments, etc. appear correct and professional.

* misunderstand an assignment requirement,
* use a library incorrectly,
* reference a function that does not exist,
* introduce unnecessary complexity,
* accidentally break previously working code,
* modify files that did not need to change,
* use outdated coding practices,
* or produce code that works for one example but fails for others.

Do not assume that confidence in an AI-generated explanation implies correctness. When appropriate, frequently verify generated code using:
* official documentation,
* tests,
* small experiments,
* course material,
* and other authoritative sources.

If uncertainty remains, discuss with your instructor, classmates or other collaborators as appropriate!

### Warning: AI Does Not Replace Debugging

When your program fails, resist the temptation to immediately ask Codex to fix everything, e.g.,

```text
Not working - pls fix
```

First look at the error yourself. Try to identify:

* which line failed,
* what type of error occurred,
* what values were involved,
* and what you expected the program to do instead.

Then use Codex to help investigate, e.g.,

```text
I am getting this error when I run the program:

[paste error]

Explain what the error means first. Do not change the code yet.
```

Once you understand the problem, you can ask Codex to fix it. You can likely provide better context to Codex as well. For example::

```text
The normalize_inputs function is throwing an error. The expected behavior is [fill in expected behavior]. Change the input arguments to reflect this expectation.
```

This enables you to debug quickly without introducing other changes (which may break other parts of your code in fixing the part that was originally broken), while continuing in building your own understanding of the debugging process.

### Tip: Display Professionalism Code and Documentation

AI-generated output frequently has recognizable stylistic habits. This is is not necessarily a problem, depending on the prompting approach, some of these idioms may appear unprofessional or distracting.

Examples of AI-idioms include:

* unnecessary bolding in documentation,
* excessive use of dashes in writing,
* repetitive phrases such as "Here's why,"
* constructions such as "It's not X. It's Y.",
* emojis in contexts where they are inappropriate,
* excessive sectioning,
* and overly-polished language that obscures uncertainty or technical nuance.

Edit generated material so that it matches the context and your own technical writing style and the tone required for your application. For example, while emojis might introduce a fun style to a readme for a personal project, it would be a grave stylistic error to have emojis in a technical report about a safety mishap on a critical system.

Software and documentation best practices will be covered later in this course, as will strategies for reviewing and iterating on prompts to ensure that the correct practices for the application are adhered to.

### Warning: Protect Sensitive Information

**Do not give an AI coding tool passwords, authentication tokens, private keys, or other sensitive credentials.**

Be particularly careful with files such as:

```text
.env
```

or files containing API keys and login credentials.

Similarly, secrets and sensitive information should generally not be committed to Git repositories.

If you accidentally expose a real credential, assume that credential has been compromised and replace it!

## Summary of Course Expectations

Use of LLMs and AI coding tools is encouraged in this course. However, you are responsible for the work that you submit and the grade that it receives. On a longer time scale, you are responsible for shaping yourself into an individual worthy of holding the responsibility of writing code that will be used beneficially in society, perhaps for many years to come. Be kind to your teammates, be kind to your future self, and be kind to your community by shaping yourself into an individual worthy of this responsibility.

In support of this goal, you should always be able to:
* explain the parts and subparts of your solution,
* describe why the approach works,
* modify the code when requirements change,
* interpret errors produced by the program,
* evaluate whether an AI-generated suggestion is reasonable,
* identify when generated material is incorrect or unprofessional,
* locate authoritative sources when further verification is required,
* have a meaningful and enriching discussion with peers and collaborators to resolve issues,
* feel that you are on a path toward becoming a better practitioner of your craft and able to use the full software stack to build applications that benefit society!
