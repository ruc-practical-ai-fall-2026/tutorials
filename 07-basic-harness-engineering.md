# Repository Guidance for AI Coding Agents

## Introduction

AI coding agents work best when they are given structured context about how a repository is organized, how code should be written, and how common tasks should be performed. Codex, and many other AI tools, support two useful mechanisms for providing this information:
* `AGENTS.md` files provide **persistent instructions and repository context**.
* Skills provide **reusable workflows for specific tasks**.

OpenAI recommends using `AGENTS.md` to supply persistent context that Codex may not be able to infer from the code itself, such as naming conventions, dependencies, project-specific rules, and validation requirements. [OpenAI: How OpenAI Uses Codex](https://openai.com/business/guides-and-resources/how-openai-uses-codex/)

Meanwhile, a skill packages instructions for performing a repeatable task. OpenAI describes skills as reusable workflows that may include instructions, examples, scripts, templates, and other supporting resources. [OpenAI: Using Skills](https://openai.com/academy/skills/) A useful way to remember the difference is to think about what question each file is answering.

```text
AGENTS.md
    How should the agent behave in this repository?

SKILL.md
    How should the agent perform this particular task?
```

This is part of the broader subject of *harness engineering*, i.e., the practice of designing the surrounding system that helps an AI agent work reliably, including its instructions, tools, repository context, tests, validation steps, permissions, and workflows. While deep discussion of harness engineering is outside the scope of this tutorial, basic harness engineering practices like using `AGENTS.md` can significantly improve the quality of AI-generated code and help to expedite AI-enabled software development workflows. You can read more about harness engineering here: [OpenAI: Harness Engineering](https://openai.com/index/harness-engineering/).

## AGENTS.md

An `AGENTS.md` file contains instructions that the agent should follow while working in a repository. For a small project, place it in the root of the repository:

```text
project/
├── AGENTS.md
├── README.md
├── pyproject.toml
├── src/
└── tests/
```

Codex automatically includes applicable `AGENTS.md` instructions in its working context. Instructions can also be placed deeper in the directory structure when different parts of a large repository require different rules. More specific files take precedence within their directory tree. For most course projects, **one short `AGENTS.md` at the repository root is sufficient**. For many course projects, a started `AGENTS.md` will be provided for you. A simple example `AGENTS.md` is as follows.

```markdown
# AGENTS.md

## Core Philosophy

- Prefer the simplest working solution.
- Do not add unnecessary steps.
- Favor readability over cleverness.
- Avoid unnecessary abstraction and over-engineering.
- Write code that is instructive and easy to understand.

## Python Style

- Use idiomatic Python.
- Target Python 3.12.
- Use clear, descriptive names.
- Prefer the standard library when practical.
- Ensure code passes Ruff checks.

## Modifying Existing Code

- Make the smallest change necessary.
- Do not refactor unrelated code.
- Preserve the existing repository structure.
- Do not modify tests unless explicitly requested.

## Validation

Before considering a change complete:

- Run the relevant tests.
- Run Ruff if configured.
- Review the final diff for unnecessary changes.
```

A slightly longer AGENTS.md example is in this directory. The goal is not to describe every possible programming rule. Keep the file focused on information that is important for this repository or course.

OpenAI similarly recommends keeping `AGENTS.md` useful as persistent context rather than treating it as a complete encyclopedia of the project.

## Skills

A **skill** describes how an AI agent should perform a particular repeatable task.

Each skill normally lives in its own directory and contains a file named `SKILL.md`. The filename is singular: `SKILL.md`. A skill may also contain supporting files such as scripts, templates, examples, or reference material. For example:

```text
check-project/
├── SKILL.md
├── templates/
└── scripts/
```

OpenAI describes a `SKILL.md` file as a Markdown playbook that typically specifies:

* what the skill does,
* what inputs it requires,
* what steps should be followed,
* what output should be produced,
* and what checks should be performed before completion.

You can read more here: [OpenAI: Using Skills](https://openai.com/academy/skills/).

## A Simple SKILL.md

Suppose a software project requires running a manual process to check that a change is ready before it is committed or submitted. Suppose some parts of that process can be scripted, but some require manual steps such as summarization, review, and reporting. A simple skill to expedite this workflow might be:

```markdown
# Check Project

Use this skill when asked to verify that the current project is ready
for submission or commit.

## Procedure

1. Inspect the current Git diff.
2. Run the relevant test suite.
3. Run Ruff checks if Ruff is configured.
4. Check for obvious debugging artifacts such as temporary print statements.
5. Confirm that no unrelated files were modified.

## Validation

Before finishing:

- Report any failing tests or linting errors.
- Identify files that appear to contain unrelated changes.
- Do not modify code unless explicitly asked.
- Summarize whether the project appears ready for commit or submission.
```

Instead of explaining this process again in every prompt, the workflow can be stored once as a skill. Codex can use skills explicitly when requested or select an appropriate skill based on the task.

You can read more on using skills and other Codex features here: [OpenAI: Introducing the Codex App](https://openai.com/index/introducing-the-codex-app/).

## Repository Skills with `.agents/skills`

For larger projects where a single `SKILL.md` file is insufficient, skills can be stored under `.agents/skills/`. Each skill receives its own directory containing a `SKILL.md`. An example folder structure might look as follows:

```text
project/
├── AGENTS.md
├── README.md
├── pyproject.toml
│
├── .agents/
│   └── skills/
│       ├── check-project/
│       │   └── SKILL.md
│       │
│       └── add-feature/
│           └── SKILL.md
│
├── src/
└── tests/
```

This structure keeps reusable agent workflows inside the repository so that they can be versioned with Git and shared with everyone working on the project. A more advanced skill might also include supporting resources:

```text
.agents/
└── skills/
    └── generate-report/
        ├── SKILL.md
        ├── template.md
        └── scripts/
            └── make_figures.py
```

OpenAI describes skills as folder-based bundles containing a `SKILL.md` plus optional supporting resources such as scripts, schemas, examples, or templates.

## What Goes Where?

For most projects, use the following guidance:

```text
README.md
    Information primarily intended for humans.

AGENTS.md
    Persistent repository instructions for coding agents.

.agents/skills/<skill-name>/SKILL.md
    Instructions for a specific repeatable workflow.
```

For example:

```text
README.md
    "This repository does XYZ. You can install it by doing ABC."

AGENTS.md
    "Use Python 3.12, prefer simple implementations, use Ruff,
     and do not modify the tests."

.agents/skills/check-project/SKILL.md
    "When checking the project, inspect the diff, run tests,
     run Ruff, and report any problems before submission."
```

## Tip: Keep Agent Instructions Simple

Keep instructions in harnesses clear and concise. This will both save tokens and avoid giving conflicting or unintentionally incorrect guidance to the agent.

For most course repositories:

* keep `AGENTS.md` short (if not provided for you),
* include only meaningful project conventions,
* create a skill only when a workflow is likely to be reused,
* prefer explicit and testable instructions,
* and avoid filling agent files with information that is already obvious from the code.

The same principles we use for software design apply in harness engineering, specifically, Occam's razor, i.e., **prefer the simplest approach that solves the problem first.**
