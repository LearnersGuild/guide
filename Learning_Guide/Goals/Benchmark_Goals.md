# Benchmark Goals

## Overview

We are piloting a program around "benchmark" goals. The first of these goals, the ["initiation integration" benchmark][initiation-integration-benchmark], was designed as a way to measure how much was learned from the first 4 "init" goals. Assuming the pilot goes well, we will likely roll-out additional benchmark goals.

## The Process

When a learner wants to attempt one of the "benchmark" goals, they should not vote during that week and instead will be manually assigned to the "benchmark" goal of their choice. The lead coach for the project will be an SEP, and learners should have few or no meetings to attend.

Learners will have 4 days to work on the goal, and **the artifact _must_ be submitted by 9am Friday morning**.

### Getting Support

During the week, learners can, of course, ask their lead coach (who is an SEP) for support. For example, learners may have to ask clarifying questions about the goal or its specs, or may need help debugging strange environment or git issues.

They should _not_ expect, however, the same level of in-depth support that would ordinarily be avialable on non-benchmark goal projects. For example, it is unlikely that a learner's coach will "pair program" with them or do any kind of "cognitive apprenticeship". In most cases, the SEP will not even touch the learner's keyboard.

### Evaluation

Once the project artifact has been submitted, the two-phase evaluation begins:

- **Artifact Evaluation:** (private review, by an evaluator, of the code submitted)
- **Comprehension Evaluation:** (face-to-face review of the code submitted, between the evaluator and the learner)

#### Artifact Evaluation

During the artifact evaluation, an artifact evaluator will privately review the code that was submitted. They are primarily looking at two things:

##### Does the commit history "tell a story"?

On a typical project, code _evolves_ over time. Lines, modules, and functions are added over time, then later changed, or sometimes even removed. The commit history tells a story of _how_ the person who wrote the code went about figuring out and solving the particular problem.

As an extreme example, if there was only one commit, with all of the _final_ code included in _working form_, that would look suspicious.

If a learner follows good git hygiene (commit often, write clear commit messages, and push at least once daily), this part of the evaluation should be straight-forward and not raise any flags.

##### How complete is the project relative to the specifications?

When evaluating completeness, the evaluator will:

- only check off specs that are definitively met by the artifact
- count the number of "completed" specs
- divide the number of "completed" specs by the total number of specs
- convert this number to a percentage (0-100%)

#### Comprehension Evaluation

During the comprehension evaluation, a comprehension evaluator will meet (via video chat) with the learner, in a 1:1 setting. Together (for about 30 minutes), they will dig-in to various parts of the code that was submitted.

During this phase of the evaluation, the evaluator is trying to answer the following questions:

- Did the learner write this code themselves, or does it seem like it was blindly cut-and-pasted?
- Does the learner understand the code? Can they explain how it works?
- Is the learner aware of their own skill and knowledge boundaries?

To prepare for this assessment, consider the following questions. These may or may not be things the assessor will ask about. You should be prepared to answer any of them.

- How are the project files organized? What does each file do?
- What is the role of this function or subroutine?
- How will the computer read this code?
- Why did you make this design decision?
- What are the inputs and outputs?
- How did you arrive at your solution? Walk through your commit history to show how your solution grew.

[initiation-integration-benchmark]: http://jsdev.learnersguild.org/goals/312
