# Project Kickoff Guide

A **project** is formed from a goal and is assigned a **team** of learners.

The purpose of a project is for the team to achieve the goal through practicing their craft, learning through collaboration and engagement with relevant and challenging tasks.

The first couple of hours of a project are critical to the success of your learning for the week. Investing time and attention getting the kickoff right, can go a long way to maximizing your learning for the week.

**You should budget around 30 minutes for the project kickoff, and it shouldn't take you more than an hour.**

## First Commit

Once projects have been formed, the first thing the team needs to do is to create a container for the **artifact**. The artifact is the output of a project. It is the thing produced by a team to complete a project. All artifacts need a URL and a Learning Contract document in a `CONTRACT.md` file.

In most cases, the artifact will be a GitHub repository in the account of a learner on the team that is forked from the goal repository.

- Create a repo for your project by forking the goal repository\* and make a simple first commit. Your first commit should write or update the README.md file with your project's name, team members, a link to the goal and a LICENSE file (unless it already exists).
- Once you've done that, set the artifact for your project. For example: `/project set-artifact http://github.com/LearnersGuild/playbook`

Make your first commit to a master branch. You should aim to have this step done **within a few minutes** of finding your team.

\*Most goals should come with a goal repository, so the best way to get started is to fork that repository. In some cases, the goal won't have an associated repo, so you'll need to create a new one for your project. Some goals (like the OSS projects) have a different process for project kickoff. Read the goal for more information.

## Learning Contract

Once your first commit is in, it's time to review the scope of your project by reading the Learning Contract in the `CONTRACT.md` file. The Learning Contract document defines the specifications and quality criteria for the artifact to meet.

The goal of a Learning Contract is to guide your team's effort for the rest of the project. It is a **learning contract** that you make with yourselves and has many purposes:

1. It guides and focuses your efforts for the rest of the cycle.
2. It defines completeness and quality for your code reviewers during the reflection phase.
3. It is a means for you to practice **project estimation**, **spec'ing**, and **goal setting**. These are critical skill for any software developer to develop (and really difficult ones).
4. It challenges you and your team to stay in your Zone of Proximal Development (ZPD). Without a good challenge, your learning will not be optimized.

Review the Learning Contract included in the goal. You may need to improve it if the specs are unclear or the quality rubric is incomplete. If so, make changes in a pull request and then submit your PR to [prrr](http://prrr.apps.learnersguild.org/).

Checkout this [example of a model spec](https://github.com/GuildCrafts/model-project-specifications/blob/master/model_specs.md) and this [quality rubric library](https://github.com/GuildCrafts/model-project-specifications/blob/master/quality_rubric_library.md).

If you notice that the specs for the goal are too vague or incomplete, inform the goal author and request that they update them.

## Work Plan

Next up: time to checkin with your team and plan how you'll work together.

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

**You should plan 15 to 20 minutes for this conversation. Don't spend too much time on it, and don't skip it**

## Guidelines for OSS projects

If you are working on an OSS project, you should spend the project kickoff getting clear on which issues from the backlog you're committing to. Create a gist with links to the issues you will be working on and set it as your project artifact. No need to use Prrrr or get your issues reviewed since your Project Lead is making sure the specs are clear and they will be the ones doing the project review at the end of the cycle.


## FAQ

**Q: I am more technically advanced than my pair/team. I feel uncomfortable dragging them behind. Can we compromise on the specs so that they're not too far outside their ZPD?**

The more skilled partner should not sacrifice the work being delivered to slow down. They should also not leave their partner(s) in the dust and work on their own. The challenge is to move at the speed and skill of the more advanced pair **and stay in team**. How can you leave every project saying "We built as much as (or more) than I would have by myself". If one partner is way more advanced than the other, then they can spend the entire week in a [cognitive apprenticeship](/Game_Manual/Cognitive_Apprenticeship.md) (and should).

Fidelity should be shipping high quality, complete code, on time, based on agreed on specs on day one. There will always be a tension between "going fast alone, or going far together". Part of the art of software development is working on teams with varied skills, and figuring out ways to ship code, learn, and accommodate the difference in skill all at the same time.

**Q: What if a team is working on a project without a real deliverable, yet one teammate must add individual specs with a deliverable to be challenged?**

You should really avoid this scenario. this is why project planning on Monday is so important. Make sure specs are clear, and deliverable is clear, and there's a good, solid, learning contract, and then spend the rest of the week executing it. Don't get into the habit of changing the scope of your work as you go along.

**Q: I feel some frustration that these guidelines sometimes seem to be asking people to sacrifice their learning for project completion.**

Shipping quality code on time is the most important thing to learn. Completing projects, and meeting your specs is what software development is. The guild's pedagogy is based on *learn by doing* approach. You learn to ship quality software on time, by doing your best to ship quality software on time.

The assumption is that for every project, there will be at least one member of the team who didn't understand everything that happened. It is a [spiral approach](https://en.wikipedia.org/wiki/Spiral_approach) to learning. The idea is to trust that the details you didn't pick up for this project, you'll pick up on the next.

Learning to learn this way may be frustrating or difficult at first, but over time you'll get used to it. And, more importantly, it's critical for you to become adept at learning this way because **being dragged on a team of people more skilled than you, and learning in a context where you don't know all the details is what the first few years of your career are going to be like**.
