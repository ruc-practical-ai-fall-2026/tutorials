# Practical AI: AI Coding Guidance

This document briefly reviews practical tips in using AI for software development.

## Overarching Guidance

### Take Responsibility for Your Work

Regardless of the tools you use, you are responsible for your code and the relationship the products you create have with other humans on your team, and in society. Remain accountable to your fellow humans and own the decisions made about your products that might affect others. Empathize with those impacted by your decisions and strive to make decisions that create beneficial software for the world.

### Maintain and Strengthen Your Agency

Control your tools. Do not allow them to control you. You are responsible for your work, and you know how to empathize with those who depend on it. A tool might not.

### Strengthen and Maintain your Own Self-awareness

Know what you know and what you do not. Beware of prompting models to do things that you do not know how to do. Do not prompt models to do things you do not know how to test.

### Know What Your Time is Worth

Some tasks truly are not worth your time, and might not have a critical outcome but still must be done. Automate these tasks without guilt. A human mind is a precious resource. Do not waste it in holding onto tasks to feed your ego. Similarly, know what is worth your time. There is no shame in doing a task manually that others may want to automate. For some cuts, a chisel can be faster than a circular saw.

### Implement the Simplest Version First

Occam's razor applies math, AI, and software engineering. Avoid implementing an overly complicated solution through careless prompting or automation.

## Innovation

### Use the Model as a Novelty Gauge

When performance breaks down, you might be doing something out of distribution. Maintain self-awareness so you know when you know if performance is breaking down. If you are doing something truly novel, the model you are working with might be less prepared to reason about your task!

### Ensure Prompt Specificity is Proportional to Novelty

Novel tasks can be broken down into smaller tasks, which themselves are likely routine. When you see degraded performance due to novelty (e.g., asking a model for an algorithm that truly does not exist in the state of the art), break the problem down into smaller parts and prompt each part individually. You can likely one-shot prompt a web frontend. You might not be able to one-shot prompt a cure for a disease! More powerful models have stronger abilities with less specific prompts, but do not have unlimited intelligence. Synthesis and analysis are the ingredients of innovation.

### Balance the Known and the Unknown

Strive to work at the edge of the known and the unknown where progress will be evident and there will be a foundation to build off of. You will likely not get far prompting AI for the cure to a disease or the meaning of life. You might get far prompting a model to help with designing an algorithm to detect a pattern in an MRI though!

## Risk Reduction

### Leverage Redundancy for Risk Reduction

For critical tasks, on top of human review, use redundant strategies to support review and correct implementation:

* Ask multiple models for solutions and compare them
* Ask a model to critique another model's solution
* Use both AI and human review together

### Test Early and Often

Automate tests and run tests often to make sure your code still works as you change it!

### Build a Little Test a Little Learn a Lot

This saying (from the famous RADM Wayne E. Meyer) has guided some of the biggest engineering projects in history. Let it guide your repository development. Do not develop large project features without testing.

### Use End-to-End and Unit Level Tests

Unit tests do not replace end-to-end tests. Systems that pass unit tests can still have emergent behaviors! Test your work, end-to-end, every time you ship!

### Avoid False Urgency

Just because AI is here and can expedite work does not mean deadlines need to move up artificially. Deliver when the customer needs it, do not move fast for speed's sake. Slow is smooth and smooth is fast.

## Chat Strategies

### Change Chats To Prevent Context-Rot

Use new chats for new tasks to create a logical break between tasks. Provide the model context for the task at hand and do not mix tasks if not needed.

## Token Saving

### Save Tokens

Despite what the hype tells you, tokens are a resource. You are not a bad scientist or engineer for using less of them. In fact, in engineering, using fewer resources within cost and schedule constraints is considered good practice, not bad practice. Do not design workflows to use excessive tokens. Do not implement token quotas. If management implements token quotas, run.

### Use the Smallest Model for the Job

While it is tempting to want to use larger models to tackle harder problems, strive to engineer harnesses and workflows that use tokens efficiently. Use smaller models when able. Tokens, and the costs associated, will often be the limiting factor in AI projects. Treat them like an engineering resource, not something with unlimited budget.

### Use Different Models for Different Jobs

While modern AI tools are truly multi-task, it is still possible to get better results using fewer resources with specialized models and tools. Some models are more efficient for some tasks than others. Use multiple models in your workflows and pick the best model for each job, where best is defined as the ratio of performance to cost, and cost is an engineering constraint.

## Harness Engineering

### Chain Steps Together

When making API calls, employ separate API call, to separate models and tools as needed, for different tasks in a workflow. For example, have one call to generate code, another call to sanitize it, another to use the code to make a plot, and another to put the plot in a report.