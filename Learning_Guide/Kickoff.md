# Project Kickoff Guide

A **project** is formed from a goal and is assigned a **team** of learners.

The purpose of a project is for the team to achieve the goal through practicing their craft, learning through collaboration and engagement with relevant and challenging tasks.

The first couple of hours of a project are critical to the success of your learning for the week. Investing time and attention getting the kickoff right, can go a long way to maximizing your learning for the week.

## First Commit

Once projects have been formed, the first thing the team needs to do is to create a container for the **artifact**. The artifact is the output of a project. It is the thing produced by a team to complete a project. All artifacts need a URL and a project outline document. In most cases, the artifact will be a GitHub repository in the account of a learner on the team.

- Create a repo for your project, and make a simple first commit. Your first commit should contain a README.md file with your project's name, team members, a link to the goal and a LICENSE.MD file.
- Once you've done that, set the artifact for your project. For example: `/project set-artifact http://github.com/LearnersGuild/playbook`

Make your first commit to a master branch. You should aim to have this step done within a few minutes of finding your team.


## Project Outline


#### Overview

Once your first commit is in, it's time to scope your project by creating a project outline. The project outline document defines the specifications and quality criteria for the artifact to meet. The goal of a project outline is to guide your team's effort for the rest of the project. It is a **learning contract** that you make with yourselves and has many purposes:

1. It guides and focuses your efforts for the rest of the cycle.
2. It defines completeness and quality for your code reviewers during the reflection phase.
3. It is a means for you to practice **project estimation**, **specing**, and **goal setting**. These are critical skill for any software developer to develop (and really difficult ones)
4. It challenges you and your team to stay in your Zone of Proximal Development (ZPD). Without a good challenge, your learning will not be optimized.

#### Preparing for the outline

Before writing your project outline, it's good practice to checkin with your team about the following:

- How familiar are they with this goal? Have they done it before? What have they learned?
- How available are they for the week? Do they have any planned personal time off?
- How familiar are they with the technology stack suggested by the goal (if any)?
- Is this is a normal week, or are there any holidays / special events that will shorten it?

Once you've surveyed your teams' skill and availability, it's time to solidify the specs:

**You should aim to write specs that are clear, and detailed, and challenging. They should put the entire team in their for the rest of the week. The goal is to maximize quantity and quality of software shipped. NOT to make sure everyone is comfortable.**

To create a project outline, create a new `outline` branch:

```
git branch outline
git checkout outline
git push origin outline
```

Copy the text of the goal into the `README.md` file.


#### Specifications and Quality Criteria

After creating the project outline, the team must edit the document to define the scope of features and quality criteria for their project.

The scope of features is determined by the set of specifications for the project. It is used to measure _completeness_.

The quality criteria are rules that govern how the artifact should be produced. They are used to measure _quality_.

To define the scope, add, edit, or remove specifications from the list. The team is accountable for producing an artifact that satisfies _all_ of the specifications, so be realistic.

Discuss the specs with your team, and adjust them as you see fit to get to a scope that will provide an appropriate level of difficulty and "stretch".

To set quality criteria, choose 2 or 3 rules or guidelines that, as a team, you agree to follow to ensure a quality artifact. Add these to the project outline.

For example, a quality criteria might be "Follow object-oriented principles in all program design" or "Write good commit messages using these rules: http://chris.beams.io/posts/git-commit/".

#### Commitment and Review

Once a proper project outline document has been written and agreed on, it's good practice to go around your team and give a number from 1 to 10 that signals how much of a stretch they think it will be to accomplish this work:

Use the following values to calibrate:

    1 = Extremely bored
    4 = Confident and comfortable
    6 = Stretched but still capable
    7 = In flow and pushed just beyond capacity
    8 = Slightly more challenged than is fun
    10 = Completely overwhelmed

**If any team member is less than a seven, then you should take the time to increase the difficulty of the project by adding more specs, or raising the quality bar**

Once the project outline is set, push the outline branch to github:

```
git push origin outline
```

And create a pull request: Go to your repository on GitHub and click on the 'Pull Request' button at the top right of the window:

![Pull Request](/images/pull_request_1.png)

And finally, submit a link to your pull request to [prrr](http://prrr.apps.learnersguild.org). A coach will review it and give you feedback on the quality of your specs and rubrics.

#### Work Plan

While the spec is being reviewed, it's time to checkin with your team and plan how you'll work together.

Some of the things you might want to cover:

- What goal did you work on last week?
- What are you hoping to achieve from the goal this week?
- Have you worked on this goal before?
- What methodologies will we need for this goal?
- What do you think are your strengths and weaknesses that you bring to this goal?
- How can we offer mutual learning support around this goal? And both stay in our ZPD?
- How often do you want to pair? What pairing style should we use?
- At what point do you feel the need to ask for help (via coach-que, etc.)?
- How long does it take until you feel frustrated, tired, zoned out, etc., and need to take a break?
- What feedback did you get last project that you want to work on this week?
- Is there anything going on this week that will constrain on your time commitment to the guild and our team? (Note player support group times, appts., lunchtime activities, etc.)
- What time do you usually take lunch and for how long?
- What makes for good communication? Bad communication?
- How do you address any pinches or misunderstandings in communication?
- Exchange phone numbers if comfortable to do so for communication purposes.

#### Check on your outline review

Check on your PR,

- If it's been reviewed and merged, read the review comments and begin your work
- If it has been reviewed but not merged, incorporate the feedback to the outline, and submit it for another review

- Don't being your project unless your project outline PR has been reviewed **and merged**.

If you're waiting for a review, then jump on [prrr](http://prrr.apps.learnersguild.org) and claim a pending review for another project's outline and review it.

## Reviewing another Team's Project Outline

When reviewing another Team's project outline, make sure you cover the following:

- The README.MD has the project's name, team members, and a link to the goal
- There is a proper LICENSE.MD file
- The project specs are clear, detailed and unambiguous. They don't leave too much room for interpretation. You can imagine yourself using them to review the completeness of the project
- The quality rubric is clear and unambiguous. You can imagine yourself using it to review the quality of the project

Once you're confident the project outline passes the above criteria, **approve the pull request and merge it**. If the outline needs to be improved on before passing, make the suggestions and do not merge it. 
