# Practical AI: AI Coding Guidance

This document briefly reviews practical tips in using AI for software development. We begin with overarching philosophical guidance, then provide tips on innovating with AI and using AI tools as an enabler for innovation, along with tips for managing the risks associated with this. Chat strategies, and tips on token and cost management are covered, along with development environment setup and security requirements.

## Overarching Guidance

### Take Responsibility for Your Work

Regardless of the tools used, you are responsible for your code and the relationship the products you create have with other humans on your team and in society. Remain accountable to your fellow humans and own the decisions made about your products that might affect others. Empathize with those impacted by your decisions and strive to make decisions that create beneficial software for the world.

### Maintain and Strengthen Your Agency

Control your tools. Do not allow them to control you. You are responsible for your work and you know how to empathize with those who depend on it. A tool might not.

While an AI tool is trained on billions of tokens, amassing to more text and data than you can ever process in a lifetime, you, your teammates, and your users are the product of billions of years of evolution, including the trials and failures of every life that ever lived and every ancestor you have all had since the dawn of life itself.

Shared intuition for the way the universe works is embedded in your DNA. Strive to stand on top of that history, and use your intuition to shape yourself and the products you create to be worthy of the trust your fellow humans place in you.

### Strengthen and Maintain your Own Self-awareness

Know what you know and what you do not.

**Beware** of prompting models to do things that *you do not know how to do*.

**Do not** prompt models to do things *you do not know how to test*.

### Honor Your Job's Charter and Scope

When using AI tools, stay within the charter of your job or educational responsibilities. There is a critical difference between an electrical engineer using AI to accelerate a circuit design task and a software engineer using AI to design a novel chemical.

In the former case, a trained electrical engineer will have the judgement to determine if the circuit is safe and appropriate for the application. In the latter case, there might not be a chemical engineer on the team to determine if the result is safe and appropriate for the application.

Similarly, if a junior electrical engineer uses AI to automate the work of a senior or principal electrical engineer, this could become problematic if the work is not reviewed by an engineer with sufficient training and certifications to assess if work of that degree of complexity is safe and appropriate for the application.

AI can enable individuals with little expertise in a domain to generate results and products that *look* like a plausible solution. However, domain expertise and thorough testing are required to determine the difference between results that *look* viable and results that *are* viable. Managers and technical leaders must ensure appropriate talent mix, senior review, talent pipelines to build reviewers, and sufficient schedule to enable review by the appropriate experts.

### Know What Your Time is Worth

Some tasks truly are not worth your time, and might not have a critical outcome but still must be done. Automate these tasks without guilt. A human mind is a precious and finite resource. Do not waste it in holding onto tasks to feed your ego.

Similarly, know what *is* worth your time. There is no shame in doing a task manually that others may want to automate. For some cuts, a chisel can be faster than a circular saw. Someone who wants to build intuition for how wood fibers are attached to each other to make more beautiful furniture, will build this intuition more readily through chisel work, even if a circular saw will ultimately be used in the shop.

### Implement the Simplest Version First

Occam's razor applies in math, AI, and software engineering. Avoid implementing an overly complicated solution through careless prompting or automation. Keep your solutions as simple as they must be but no simpler. Do not implement unnecessary features or layers of abstraction just because you have the tools to implement these faster. These design elements and features will still need to be tested and maintained, and the extra complexity, when not truly needed, will make the code more costly to maintain and change over time.

## Innovation

### Use the Model as a Novelty Gauge

When performance breaks down, you might be doing something out of distribution. Maintain self-awareness so you know when you know if performance is breaking down. If you are doing something truly novel, the model you are working with might be less prepared to reason about your task!

### Ensure Prompt Specificity is Proportional to Novelty

Novel tasks can be broken down into smaller tasks, which themselves are likely routine. When you see degraded performance due to novelty (e.g., asking a model for an algorithm that truly does not exist in the state of the art), break the problem down into smaller parts and prompt each part individually. You can likely one-shot prompt a web frontend.

You might not be able to one-shot prompt a cure for a disease! More powerful models have stronger abilities with less specific prompts, but do not have unlimited intelligence. Synthesis and analysis are the ingredients of innovation.

### Balance the Known and the Unknown

Strive to work at the edge of the known and the unknown where progress will be evident and there will be a foundation to build off of. You will likely not get far prompting AI for the cure to a disease or the meaning of life. You might get far prompting a model to help with designing an algorithm to detect a pattern in an MRI though! This might be a small step towards curing a disease.

## Risk Management and Review

### Leverage Redundancy for Risk Reduction

For critical tasks, on top of human review, use redundant strategies to support review and correct implementation:

* Ask multiple models for solutions and compare them.
* Ask a model to critique another model's solution.
* Use AI and human review together.

### Review the Diff

Do not judge work done by an AI coding agent only by whether the program appears to work at the end. Review what changed.

Use git diff, your IDE's source control view, or similar tools to inspect changes before accepting them. Look for unnecessary changes, deleted functionality, new dependencies, duplicated code, changes outside the requested scope, and code that you do not understand.

AI tools enable fast generation of code. This increases the need for disciplined review. A hundred lines of unnecessary code generated in seconds are still a hundred lines that must be tested and maintained in the future.

### Keep Changes Small and Reversible

Prefer small changes corresponding to a logical feature over large changes. Ask the agent to implement one feature, fix one bug, or perform one refactor at a time when practical.

Use version control. Commit working states before substantial changes and create commits as work progresses. If an experiment fails, undoing a small change is much easier than untangling a large collection of unrelated changes.

Small changes are also easier to review, test, understand, and explain. This principle is valuable whether the code is written by a human or an AI tool.

### Test Early and Often

Automate tests and run tests often to make sure your code still works as you change it!

### *"Build a Little Test a Little Learn a Lot"*

This saying (from the famous RADM Wayne E. Meyer) has guided some of the biggest engineering projects in history. Let it guide your repository development. Do not develop large project features without testing. Learn from each test you conduct and feed the lessons back into your next iteration. Keep iterations short and avoid making too many changes without frequent testing to ensure the changes are anchored to the practical reality of the domain of application.

### Use End-to-End and Unit Level Tests

Unit tests do not replace end-to-end tests. Systems that pass unit tests can still have emergent behaviors! Each component of a system can function correctly (all unit tests pass) but the components might still be connected incorrectly. Small defects can also compound and become amplified in large multi-component systems. Test your entire system, end-to-end, every time you ship!

### Avoid False Urgency

Just because AI tools are available and can expedite work does not mean deadlines need to move closer artificially. Deliver when the customer needs it. Do not move fast for speed's sake. Slow is smooth and smooth is fast.

## Chat Strategies

### Change Chats Often

Use new chats for new tasks to create a logical break between tasks. Provide the model context for the task at hand and do not mix tasks if not needed. When you finish a feature, reach a logical breakpoint, or notice Codex carrying irrelevant assumptions, change to a new chat. Do not use chats as the primary source of persistent project memory. Long-term project context should live in repository artifacts such as `AGENTS.md`, documentation, skills, tests, and other appropriate files.

### Give Each Chat One Clear Objective

Starting a chat with the intent of implementing a file loader and adding tests provides more manageable scope than mixing implementation, debugging, refactoring, documentation, and multiple features into a single chat. This can lead to less predictable behavior as context and assumptions across tasks mix together. Working on one clear objective at a time before moving onto the next is solid practice for human work as well as AI-enabled work!

### Provide Constraints and Context Early in a Chat

Avoid vague prompts like `"build a deep learning framework"` and `"fix all errors"`. Provide context on what you are trying to do. For example, the prompts,

```text
"I have an image dataset. I want to design a deep learning framework to classify the images.
It must be able to add new classes quickly. Use representation learning strategies to enable few-shot addition of new classes.
Recommend an approach before making changes."
```

```text
"There is an error in the loss function implementation in compute_loss.
Fix the equation so it correctly implements mean square error loss."
```

will provide more specification than the former prompts. The more unique your work is, the more specific your prompts must be and the more context will be required. You can likely "one-shot" prompt a web front-end. It is less likely that you can one-shot prompt a niche algorithm for tokenization of a novel data source.

### Inspect Before Changing

Codex can be just as valuable for inspecting code as it is for writing code. For unfamiliar code, start with prompts like

```text
"I need to implement a change to the normalization functions in this repository.
Read the relevant files and explain how they work before suggesting changes."
```

before making any changes. Understand your repository first, be confident you know how the code works, what the major modules are and what they do, and what you need to change, before you request changes. Having full context on the repository yourself also facilitates keeping subsequent prompts more specific, since you know what changes to ask for in which components.

### Provide a Definition of Done

Give the model a definition of done.

For a coding task, the "definition of done" might mean that the requested behavior is implemented, existing tests pass, new behavior has tests, ruff passes, no unrelated files were changed, and the resulting diff has been reviewed.

Without a definition of done, an agent can continue making changes simply because additional improvements are possible. Completion criteria reduce unnecessary work, simplify implementations and result in less unnecessary code to maintain.

## Cost and Token Management

### Save Tokens

Despite what the hype tells you, tokens are a resource to be used judiciously. You are not a bad scientist or engineer for using less of them. In fact, in engineering, using fewer resources within cost and schedule constraints is considered good practice rather than bad practice. Do not design workflows to use excessive tokens. Do not implement *minimum* token quotas. If management implements minimum token-use quotas, run!

### Use the Smallest Model for the Job

While it is tempting to want to use larger models to tackle harder problems, strive to engineer harnesses and workflows that use tokens efficiently. Use smaller models when able. Tokens, and the costs associated, will often be the limiting factor in AI projects. Treat them like an engineering resource, not as an unlimited supply.

### Use Different Models for Different Jobs

While modern AI tools are truly multi-task, it is still possible to get better results using fewer resources with specialized models and tools. Some models are more efficient for some tasks than others. Use multiple models in your workflows and pick the best model for each job, where best is defined as the ratio of performance to cost, and cost is an engineering constraint.

## Harness Engineering

### Use `AGENTS.md` for Project Context

Use `AGENTS.md` to provide persistent instructions that should apply whenever an AI coding agent works in your repository. Good candidates include repository structure, coding conventions, preferred tools, build and test commands, architectural constraints, and important rules that might not be obvious from reading the code alone.

Keep `AGENTS.md` concise! Do not try to explain your entire project in one file. If your project has architecture documentation, testing instructions, design documents, or development procedures, keep these in appropriate files and reference them from `AGENTS.md`.

Remember that every instruction added consumes context and creates another instruction that must remain correct as the repository evolves. As with code, more natural language instructions are not necessarily better instructions. Prefer a small number of rules that will remain stable over the long-term life of the project over more complex that might change more frequently.

### Use SKILL.md or .agents/skills to Define Repeatable Tasks

Use skills for workflows that cannot be readily scripted (e.g., involve natural language processing, summarization, or other tasks appropriate for AI) that you expect an agent to perform repeatedly. If you frequently ask an agent to perform the same multi-step task, consider defining the procedure once as a skill to save time.

For example, a project might contain a skill for creating a new Python module. The skill could instruct the agent to create the module in the correct directory, follow the project's naming conventions, add unit tests, run ruff, run the relevant tests, and report the files that changed.

Keep skills focused. A skill that describes one repeatable task is easier to understand, test, maintain, and reuse than an unnecessarily large skill that attempts to describe every possible development process. As with code, compose simple skills into larger modular workflows when needed.

### Chain Steps Together

When making API calls, employ separate API calls, to separate models and tools as needed, for different tasks in a workflow. For example, have one call to generate code, another call to sanitize it, another to use the code to make a plot, and another to put the plot in a report.

Do not assume that the best model for one step is the best model for every step. Breaking workflows into explicit stages also creates natural places to test intermediate outputs. If one stage produces an incorrect result, it is much easier to identify and repair the failure than when one prompt attempts to perform the entire workflow at once.

Where practical, make the interface between stages explicit. Files, structured data, tests, schemas, and clearly defined inputs and outputs make agentic workflows easier to inspect and less dependent on ambiguous conversational context.

### Keep Important Knowledge Outside the Chat

Use chats to convey working context rather than to document a project. Do not use chats as a long-term source of documentation. Important decisions, requirements, architecture, procedures, and conventions should live in the repository where both humans and AI tools can find them.

Do not employ chats as if they will be available to all project contributors forever. If a chat reveals something noteworthy, move that knowledge into the appropriate README, design document, `AGENTS.md`, skill, test, comment, or other artifact rather than leave it in the chat.

A healthy repository should become *easier* for both humans and AI agents to understand as work progresses.

## Development Environment

### Make the Development Environment Reproducible

AI coding agents are significantly more useful when they can build, run, test, lint, and inspect the project themselves. Maintain a development environment that makes these operations straightforward and repeatable.

Document the commands required to install dependencies, run the application, execute tests, lint the code, and perform other common development operations in the appropriate repository documentation, `AGENTS.md`, or skills. Where appropriate, use files, tools, and conventions such as `pyproject.toml`, lock files, and development containers to ensure the development environment can be reproduced.

Remember that agent (and people) cannot reliably verify work if the repository cannot be reliably built or tested.

### .ignore Files

Do not rely on `.gitignore` or a tool-specific `.ignore` file as a security mechanism. `.gitignore` controls what Git tracks rather than what an agent can necessarily access. While some AI coding tools have dedicated `.ignore` files, Codex does not officially honor them. For non-security sensitive project context and instructions about which files matter for which tasks, use `AGENTS.md`. For security sensitive files, see below.

## Security

### Never Commit Secrets

Do not place passwords, API keys, access tokens, SSH private keys, database credentials, certificates, or other secrets directly in source code or committed configuration files.

Use environment variables or an appropriate secrets management system instead. For local development, it is common to keep secrets in an untracked `.env` file and commit a `.env.example` file containing only the names of required variables.

For example,

```text
OPENAI_API_KEY=
DATABASE_URL=
```

documents which values the application expects without exposing the values themselves.

If a secret is accidentally committed it must now be assumed to be exposed and compromised. Removing it from the latest version of the file is not sufficient because it might remain in Git history, logs, caches, forks, backups, or other copies. Revoke or rotate the credential immediately.

### Apply the Principle of Least Privilege

Credentials should have only the permissions required for the task they support. For example, an application that only needs to read data should not use credentials with permission to modify or delete that data. A development API key should not have administrative access to production systems.

In professional environments, separate development, testing, and production credentials when possible. This limits the consequences of a mistake and makes it less likely that experimental code, an AI-generated command, or a local development environment can affect a production system.

Prefer short-lived credentials, scoped tokens, and automatically-rotated credentials when the infrastructure you are using supports them. A credential that expires quickly and has limited permissions creates a smaller security risk than a permanent credential with broad access.

### Do Not Share Secrets with AI Tools

**Do not paste passwords, API keys, authentication headers, private keys, `.env` files, production connection strings, or any other credentials into prompts**. An AI coding agent does not need to know the value of a secret. It only needs to know how the application accesses it.

For example, tell the agent,

```text
"The application reads the OpenAI API key from the OPENAI_API_KEY environment variable."
```

rather than providing the API key itself!

Be equally careful when providing logs, configuration files, screenshots, notebooks, database exports, or error messages to AI tools. These artifacts can contain sensitive information even when the secret is not obvious. Before providing data to an AI tool, understand what information you are providing and whether you are authorized to provide it (e.g., by your university or workplace intellectual property and privacy polices).

### Protect Secrets in Logs and Debugging Output

Secrets can be exposed even when they are not stored in source code. Be careful with `print` statements, logging calls, exception messages, stack traces, notebooks, screenshots, CI/CD output, generated reports, and debugging tools. Avoid printing authentication headers, tokens, connection strings, or environment variables.

For example, debugging code like

```python
print(os.environ)
```

might expose credentials available to the process. Redact sensitive values when they must appear in diagnostic output.  Remember that logs often persist much longer than the process that created them and might be accessible to more people than the original application, violating the principle of least privilege if information leaks across security borders through the logs.

### (In This Class) Use Environment Variables for Secrets

For projects in this class, environment variables are sufficient for storing API keys, access tokens, passwords, and other secrets. **Do not place deployment credentials directly in shell scripts, Dockerfiles, workflow files, or other committed infrastructure configuration.**

When convenient, store local values in an untracked `.env` file and load them into your application at runtime. Add `.env` to `.gitignore` and, when useful, include a `.env.example` file containing the names of the required variables but no real secret values.

For example,

```text
OPENAI_API_KEY=
DATABASE_URL=
```

**Do not** hard-code secrets in source code, notebooks, `AGENTS.md`, skills, prompts, configuration files that are committed to Git, or other repository files.

**Do not** print secrets in logs, screenshots, debugging output, or assignment submissions.

Avoid passing secrets through command-line arguments because command histories, process inspection tools, or logs might expose them.

**If you accidentally commit, publish, or otherwise expose a credential, treat it as compromised and follow the response procedure below.**

You are not required to use a dedicated secrets management platform such as AWS Secrets Manager, Azure Key Vault, Google Cloud Secret Manager, or HashiCorp Vault for normal class projects. However, you should be aware that these systems become more important in production environments where applications are deployed, automated through CI/CD, shared across teams, or given access to sensitive resources.

### (In Production) Use Secure Secret Storage in Deployment and CI/CD

CI/CD systems and cloud platforms generally provide mechanisms for securely storing secrets and injecting them into a process at runtime. Examples include GitHub Actions Secrets, AWS Secrets Manager, Azure Key Vault, Google Cloud Secret Manager, and HashiCorp Vault. Use these mechanisms rather than placing credential values directly in repository files. Production systems should generally use an appropriate secrets management capability approved by the business rather than copying credentials into configuration files manually.

### (In Production) Scan for Secrets and Respond Quickly to Exposure

Repository hosting platforms, pre-commit tools, and security scanners can identify many common credential formats before or after they are pushed. These tools are particularly valuable in AI-assisted workflows because coding agents can create and modify many files quickly.

Use automated scanning to augment, rather than replace, human review for security best practices. A scanner might fail to recognize a custom credential, proprietary token, or sensitive piece of configuration information.

### Responding to An Exposed Credential Incident

If a credential is exposed:

1. Revoke or rotate the credential.
2. Determine what permissions the credential had.
3. Review whether it was used unexpectedly. Even if it did not appear to be used, assume it was compromised.
4. Remove the credential from the repository and other accessible locations.
5. Replace it with an appropriate environment variable or secrets management mechanism.
6. Determine how the exposure occurred and modify the workflow to prevent recurrence.

Once a credential has entered a public repository, shared chat, public log, or other uncontrolled location, treat it as compromised information.
