# Basic Gameplay

There are two objectives of the game: to learn, and to contribute to others' learning.

Focus on these two activities and you will succeed.

## Components

### Levels

All players advance through a sequence of levels in the game.

Learn more about levels in [Levels & Roles][levels-roles].

### Roles

There are four roles: Player, Technical Coach, Project Lead, and Moderator.

Learn more about roles in [Levels & Roles][levels-roles].

### Goals

Goals serve as templates for projects.

Goals live in a goal library which all learners contribute to.

### Projects

Projects are how the work of learning is organized and made meaningful.

Projects are defined by goals, but can be modified by the team working on them. They have clear outcomes and context, which helps learners know both _what success looks like_ as well as _how this project will help them learn their craft_.

### Cycles

The game moves forward through a series of 1-week cycles. Everything happens within a cycle; it is the primary game loop.

Every cycle, learners select learning goals, form projects from them, practice their craft in the context of the project, and finish the cycle by reflecting on both the process and the outcome.

Learners complete cycles on their journey to achieving dignified livelihood.

## Stages

### Goal Selection

The first stage of a cycle is called **goal selection**.

During this stage, learners vote on goals from the goal library for their particular craft. The goal library for your craft is located in the appropriate craft repo under the [GuildCrafts][guildcrafts] organization.

Any learner can add goals to the library, just follow the template and instructions in the goal repository.

Each learner chooses their top two goals from the list. It's best to choose goals that are both _relevant_ to the skills you wish to acquire and appropriately _challenging_ given your current skill level.

Use the `/vote` command to vote on goals.

After all learners have voted, the votes are tallied and the most popular goals become **projects** to which learners are then assigned.

#### Forming Project from Goals

Forming projects from votes is a relatively complex process. To ensure that project teams have the right number of learners with the right balance of experience levels, more than just votes have to be factored into the equation.

For example, to make **cognitive apprenticeship** work, every team needs one learner who has significantly more experience so that they can take on the most difficult tasks and share their skills and knowledge with the rest of the team. So if one advanced learner votes differently from four beginner learners, then the advanced learner may get assigned to the more popular project to ensure that their experience is put to best use.

To accomplish this, there is an automated process that will generate projects using many different parameters to try and achieve the best result. This means that voting on a goal is not a _guarantee_ that the goal will be chosen or that you will be assigned to the project.

### Project Kickoff

A **project** is formed from a goal and is assigned a **team** of learners.

The purpose of a project is for the team to achieve the goal through practicing their craft, learning through collaboration and engagement with relevant and challenging tasks.

#### Artifact and Project Outline

Once projects have been formed, the first thing the team needs to do is to create a container for the **artifact** and write a **project outline** document within it.

The artifact is the output of a project. It is the thing produced by a team to complete a project. All artifacts need a URL and a project outline document. In most cases, the artifact will be a GitHub repository in the account of a learner on the team.

The project outline document defines the specifications and quality criteria for the artifact to meet. To create a project outline, copy the text of the goal into a `README.md` file within your artifact.

#### Specifications and Quality Criteria

After creating the project outline, the team must edit the document to define the scope of features and quality criteria for their project.

The scope of features is determined by the set of specifications for the project. It is used to measure _completeness_.

The quality criteria are rules that govern how the artifact should be produced. They are used to measure _quality_.

To define the scope, add, edit, or remove specifications from the list. The team is accountable for producing an artifact that satisfies _all_ of the specifications, so be realistic.

Discuss the specs with your team, and adjust them as you see fit to get to a scope that will provide an appropriate level of difficulty and "stretch".

To set quality criteria, choose 2 or 3 rules or guidelines that, as a team, you agree to follow to ensure a quality artifact. Add these to the project outline.

For example, a quality criteria might be "Follow object-oriented principles in all program design" or "Write good commit messages using these rules: http://chris.beams.io/posts/git-commit/".

Once a proper project outline document has been written, it's time to **practice**.

### Practice

Most of the cycle is spent in the **practice** stage. This is the time for engaged collaboration, research, study, and experimentation.

What happens in practice is entirely up to the team and the project at hand. It is the learners prerogative to decide _how_ to spend their time to best achieve the goal.

The most important piece about practice is that learners should be appropriately challenged. Practice that isn't sufficiently challenging (or is overwhelmingly difficult) will not result in learning. Practice should stretch a learner just beyond the edge of their knowledge and skill, but not too far past it.

Seek advice from more experienced learners on how to engage in good, deliberate practice.

When practice is done, the cycle enters its final stage: **reflection**.

### Reflection

In the **reflection** stage, learners reflect on both the _process_ of their learning and team collaboration as well as on the _product_ of their own and others' projects.

There are two parts to this stage: a **retrospective**, for reflecting on and giving feedback about the team process and individual learning; and a **review**, for evaluating and critiquing the artifacts produced during the cycle.

The moderator will set aside time at the end of the cycle for reflection. During this time, learners reflect on their own. It is a quiet, contemplative time for harvesting the insights and learnings of the past cycle.

Once the reflection stage is over, the cycle is finished, and it is time to begin a new one!

#### Retrospective

The retrospective consists of a series of questions and prompts for learners to give feedback to themselves and their team.

Use the `/retro` command to view questions and log answers.

#### Review

The project review is a time for exploring an artifact and determining to what extent it satisfies the project's specifications and quality criteria.

Learners can review as many projects as they like. At the very least, learners should review their own projects and one other project completed during the cycle.

Use the `/review` command to capture a project review.

[guildcrafts]: http://github.com/GuildCrafts
[levels-roles]: ./Levels_and_Roles.md
