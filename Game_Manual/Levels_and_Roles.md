# Levels and Roles

Players advance through various levels. Each level has specific requirements and confers new abilities to the player.

Roles delineate different ways of interacting with the game. Players at all levels have the "Player" role, and as players advance they gain access to new roles.

## Levels

Levels are cumulative, so more advanced levels also include privileges of previous levels.

Every level is a voting pool. In other words, players vote on goals that are in their level with other players in their level.

Advancement is not one-way: players can move backwards if they stay in the red for two weeks (same mechanic as current in-the-red piece).

### Level Abilities

- Level 0
  - Can access guild facilities
  - Can choose `foundational` and `practice` goals
  - Can use guild materials (e.g. borrow a laptop)
- Level 1
  - Can receive stipend
  - Can create `foundational` and `practice` goals
  - Can do cog app sessions with Technical Coaches
- Level 2
  - Can choose `apprentice` goals
  - Can do cog app sessions with Project Leads
- Level 3
  - Can choose `prototype` goals
  - Can create `apprentice` goals
  - Can take on Technical Coach role
  - Can earn Coaching stats (TBD)
- Level 4
  - Can choose `production` goals
  - Can create `prototype` goals
  - Can do mock technical interviews (TBD)
- Level 5
  - Can create `production` goals
  - Can take on Project Lead role
  - Can earn Leadership stats (TBD)

#### A note on goal types

There are 5 types of goals (only 3 of which are currently active). Eventually, there will be projects for each of the 5 types. Here's what each type means:

1. `foundational`: no "product" produced. Purely for focusing on fundamental skill building. Example: "Relational DB design"
1. `practice`: one-off, toy projects. For exploring and learning in a sandboxed environment, but with a defined (albeit contrived) "product". Example: "Bookstore App"
1. `apprentice`: a real-world, maintained project, but without any user base or production environment. No need to manage a deployed app. Example: "Trossello"
1. `prototype`: maintained projects with at least an "alpha-level" production environment and some user base. Will involve some dev ops. Example (hypothetical): a better goal library
1. `production`: professional-grade projects with a live product and active users. Example (hypothetical): the LOS

### Level Requirements

This table shows each level starting at 0 and advancing to 5 with the criteria for advancing to that level.

| Level | XP           | XP/Week   | Elo    | Cultural | Team Play | Technical | Bias        | Reviews | Other              |
|:------|:-------------|:----------|:-------|:---------|:----------|:----------|:------------|:--------|:-------------------|
| 0     | -            | -         | -      | -        | -         | -         | -           | -       | enrolled in LG     |
| 1     | >=0          | 18      | >=65   | >=65     | -         | -8<=bias<=8 | -       | joined a cohort    |
| 2     | >=150        | 22 | >=1000 | >=80     | >=80      | -         | -           | >=20    | -                  |
| 3     | >=500        | 27 | >=1040 | >=85     | >=85      | >=80      | -           | >=60    | -                  |
| 4     | >=750        | 33 | >=1080 | >=90     | >=90      | >=90      | -           | >=90    | ? coach stat (TBD) |
| 5     | >=1000       | 40 | >=1100 | >=90     | >=90      | >=95      | -           | >=120   | ? coach stat (TBD) |

#### Moving Up and Back through Levels

Moving up a level is simple: as soon as a player has met **all** of the requirements, they automatically advance.

Moving back a level is a longer process. In order for a player to move back a level, their stats have to drop below the requirement and _stay below_ for two consecutive active cycles. When a player in level N drops their stats below the level N requirement, they are "in the red" and they have 2 cycles to move their stats back into compliance with the level N requirements.

For example, say Dora is a player at level 2, with an Elo of 1008, cultural health at 89% and team play at 92%. Then, at the end of cycle 4, Dora's cultural health dips to 76%. She still in level 2, but she is now "in the red".

If Dora doesn't bring her cultural health back to 80% or above by the end of cycle 6, then she will move back to level 1. She will lose her level 2 abilities until her stats are once again good enough to advance to level 2.

### Why levels?

The LOS has levels for many reasons. Mostly, levels are useful to create a structure through which players can advance, giving direction and acknowledgement of real achievement.

Levels support two growth trajectories for learners:

- An arc from scaffolded structure towards informed agency
- An arc from personal development towards community leadership

When they start, players have few options. This limitation is actually a benefit, because it allows new players to focus intensely on their own development: establishing good learning habits, solidifying foundational technical and collaborative skills, developing a fluency with the language and norms of the learning collective.

Players advance by taking on more difficult and challenging work. They push themselves to learn beyond their comfort and capacity, integrate those learnings, and repeat. There will always be greater and more interesting relevant challenges for them to face.

As players advance, they earn more freedom to choose how to spend their time, what skills to focus on, and what work to pursue. With this status comes the accountability (and privilege) to mentor and aid others, to distribute and compound their learnings throughout the collective.

## Roles

There are 3 roles in the LOS.

By default, every learner has the "Player" role.

The other two roles must be earned by advancing to higher levels.

#### Player

Purpose:
- A learning collective that helps all members find a dignified livelihood

Accountabilities:

- Working on relevant & stretchy goals with other players
- Learning new skills and abilities
- Improving stats

Stats:
- Health
- Growth
- Estimation
- Review

#### Technical Coach

Purpose:
- Players are well supported in improving their technical skills & stats

Role Accountabilities:
- Providing technical guidance and advice to players
- Assisting players in their project work
- Conducting cognitive apprenticeship sessions with level 1 players
- Guiding players by authoring/curating/suggesting appropriate goals for their
- skill/knowledge level
- Authoring/Curating/Suggesting resources for technical growth
- Supporting teams in completing their projects

Stats: TBD

#### Project Lead (PL)

Purpose:
- Players have ongoing, maintained, well-managed, real-world projects to work on

Role Accountabilities:
- Maintaining backlog of work issues for project
- Reviewing/giving feedback on project work
- Defining and maintaining quality standards for project
- Conducting cognitive apprenticeship sessions with level 2 & level 3 players

Stats: TBD

#### Moderator

Purpose:
- LOS superbly moderated

Role Accountabilities:
- Moderating LOS
- Setting up and maintaining Craft Repo
- Defining, communicating, and enforcing game over conditions for players
- Defining game play hours
- Defining stats thresholds to optimize for learners who are a bad fit for the guild leaving as early as possible
- Administering Echo users and teams
- Selecting coaches / maintaining coach rotation schedule
