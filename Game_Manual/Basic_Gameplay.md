# Basic Gameplay

There are two objectives of the game: to learn, and to contribute to others' learning.

Focus on these two activities and you will succeed.

### Roles

There are two roles: **Learner** and **Moderator**.

Learners play the game; the Moderator acts as a referee and game master.

### Cycles

The game moves forward through a series of 1-week cycles. Everything happens within a cycle; it is the primary game loop.

Every cycle, learners select learning goals, form projects from them, practice their craft in the context of the project, and finish the cycle by reflecting on both the process and the outcome.

Learners complete cycles on their journey to achieving dignified livelihood.

### Goal Selection

The first stage of a cycle is called **goal selection**.

During this stage, learners vote on goals from the goal library for their particular craft. The goal library for your craft is located in the appropriate craft repo under the [GuildCrafts][guildcrafts] organization.

Each learner chooses their top two goals from the list. It's best to choose goals that are both _relevant_ to the skills you wish to acquire and appropriately _challenging_ given your current skill level.

Use the `/vote` command to vote on goals.

After all learners have voted, the votes are tallied and the most popular goals become **projects** to which learners are then assigned.

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

Use the `/log --retro` command to view questions and log answers.

#### Review

The project review is a time for exploring an artifact and determining to what extent it satisfies the project's specifications and quality criteria.

Learners can review as many projects as they like. At the very least, learners should review their own projects and one other project completed during the cycle.

Use the `/review` command to capture a project review.

[guildcrafts]: http://github.com/GuildCrafts
