# Stats

These statistics (stats) are meant to reflect your progress towards the [game objectives][game-objectives], as well as your overall "health" in the game.

### How to Earn Stats

At the end of every project, the data gathered in the reflection—that is, retrospectives and project reviews—is used to calculate and update your player stats.

In order to earn stats from a project, the following conditions must be met:

1. Every member of the team has completed the project retrospective
1. The project has been reviewed twice as many people as the size of the team

Once _both_ of these conditions are met for a project, stats will be calculated and awarded for all team members.

---

## XP

Your experience, aggregated and condensed to a number. XP always grows; the larger the number, the higher your experience.

XP is calculated and awarded in three steps for each project.

First, the gross project XP is calculated by adding all of the hours each team member contributed to the project. So a project where the players contributed 35, 30, and 35 hours would have a total of 100 hours.

Second, the net project XP is calculated by multiplying the gross project XP by the completeness and quality scores. So for a project with 95% completeness and 90% quality, the net project XP would be 85.5 (100 * .90 * .95).

Finally, the net project XP is divvied up to each player according to their actual contribution to the project. So if your actual contribution to the project is 40%, you would get 34.2 XP (85.5 * .40).

## Elo Rating

[Elo][elo-rating-wiki] is a system for determining the relative skill of players. It is used by many different games and sports for organizing play within a league. Represented as a positive integer, which shows your relative skill as compared to other players.

In the context of the LOS, your Elo rating is a representation of your ability to contribute to projects relative to other players. It is not an _absolute_ measure of your skill, but is only meaningful in reference to other players.

Unlike XP, Elo moves up and down depending on your project-to-project contribution stats and with whom you work on projects.

It can be a little difficult to understand how Elo works in a collaborative game like this one, since it is usually applied to competitive, zero-sum games like chess or beach volleyball or hot dog eating contests. So let's dive into an example.

Imagine that you're a professional jigsaw puzzle solver. You work with other puzzlers to collaboratively solve jigsaw puzzles. Your Elo rating in the Professional Jigsaw League is 1200.

Let's say that you solve a puzzle with three other puzzlers of the _exact same_ Elo rating (1200). If you solve 1/2 of the puzzle (by placing 1/2 of the pieces), then your Elo rating would _go up_ after the game because you performed _much better_ than you were expected based on your Elo. On a team of four puzzlers of the same skill (Elo), you'd be expected to solve 1/4 of the puzzle.

If, on the other hand, you only solved 1/5 of the puzzle, your Elo rating would _go down_, because you performed worse than was expected of you.

The interesting thing about Elo is that the ratings take into account the relative skill _before_ the game, so you can play more advanced players, perform worse, and _still go up_ in your Elo rating. It all depends on how much better or worse you performed relative to what is expected of you.

## Average Project Completeness

The average % completion of all projects you've worked on.

## Average Project Quality

The average % quality of all projects you've worked on.

## Learning Support

How much your team members felt that you supported them in their learning. This is a weighted average with more recent projects counting more than earlier ones. Represented as a percentage (0..100%).

## Culture Contribution

How much your team members felt you contributed positively to the team culture. This is a weighted average with more recent projects counting more than earlier ones. Represented as a percentage (0..100%).

## Team Play

How well your team members felt that you collaborated on team efforts, independent of your technical skill, mentorship, or cultural contribution. This is a weighted average with more recent projects counting more than earlier ones. Represented as a percentage (0..100%).

Some examples of good "team play" behavior: engaging fully with the problem, trying to figure out how to maximize your output to the team, compromising and standing firm when needed, speaking up and standing back appropriately.

## Project Reviews

The number of projects you've reviewed the completeness and quality of. Represented as an integer.

## Project Contribution

The amount that you contribute to a project determines a series of other stats, and also contains several sub-stats within.

Within a given project, you have **actual** and **expected** contributions, as well as a **contribution gap**.

To demonstrate how the various contribution stats are calculated, we'll use the following dataset in examples.

#### Example Project Contribution Estimations

| Project      | Team size | Self estimate | Team estimates | Your Hours | Total Hours |
|:-------------|:----------|:--------------|:---------------|:-----------|:------------|
| #big-bees    | 3         | 50%           | 42%, 48%       | 30         | 80          |
| #red-rabbits | 4         | 28%           | 27%, 35%, 28%  | 25         | 120         |
| #tiny-tigers | 2         | 20%           | 30%            | 40         | 75          |

### Actual Contribution

Your actual contribution is the average of your team's estimates of what percentage of the project you contributed to. It includes your own estimate of your contribution. Represented as a percentage (0..100%).

In the above dataset, the player's actual contribution for the `#big-bees` project is the average of _all_ the estimates, so it would be equal to 46.67% ( (50% + 42% + 48%) / 3 ).

### Expected Contribution

Your expected contribution how much you are expected to contribute to the project based on how many hours you contribute relative to the total hours of all players. Represented as a percentage (0..100%).

In the above dataset, the player's expected contribution for the `#big-bees` project is equal to 37.5% ( 30 / 80 ) because they contributed 30 out of a total 80 hours that players spent on this project.

### Contribution Gap

The contribution gap is the difference between actual and expected contribution. It demonstrates whether a player contributed _more_ or _less_ than is expected of them, based on the size of their team. Represented as a +/- percentage (-100%..100%).

In the above dataset, the player's contribution gap for the `#big-bees` project is equal to 9.17% ( 46.67% - 37.5% ). In other words, they contributed +9.17% _more_ to the project than what is expected based on how many hours they worked on it.

## Estimation Accuracy and Bias

Estimation accuracy and bias reflect how well you estimate your contribution to projects.

To demonstrate how these stats apply, we'll use a modified version of the above dataset, aggregating the team estimates into their average (mean):

| Project      | Self estimate | Team estimate (avg) |
|:-------------|:--------------|:--------------------|
| #big-bees    | 50%           | 45%                 |
| #red-rabbits | 28%           | 30%                 |
| #tiny-tigers | 20%           | 30%                 |

### Estimation Accuracy

Estimation accuracy reflects how accurate your estimations are relative to the consensus. Represented as a percentage (0..100%).

One hundred percent is perfect accuracy: you estimate your contribution the same as your peers do. The closer this stat is to 100%, the more accurate your contribution estimates are.

Your estimation accuracy _per project_ is computed by first finding difference between self- and team-estimated contribution for that project, and then using the [absolute value][absolute-values] of that difference. Finally, this number is subtracted from 100% (so that a perfect score would be 100%, not 0%). So the estimation accuracy stats for the above projects would be:

| Project      | Estimation Accuracy                          |
|:-------------|:---------------------------------------------|
| #tiny-tigers | 100% - abs(20% - 30%) = 100% - 10% = **90%** |
| #big-bees    | 100% - abs(50% - 45%) = 100% - 5% = **95%**  |
| #red-rabbits | 100% - abs(28% - 30%) = 100% - 2% = **98%**  |

Based on these projects, the _overall estimation accuracy stat_ is 94.33% (average of [90%, 95%, 98%]).

## Estimation Bias

Estimation bias reflects whether you tend to over- or under- estimate your contribution. Represented as a +/- percentage (-100%..100%).

If your estimation bias is _below zero_, that means that you tend to underestimate your contribution to the projects that you work on. Your fellow players see value that you don't recognize; you can learn to take more credit for your work!

If your estimation bias is _above zero_, that means that you tend to overestimate your contribution to the projects that you work on. Your fellow players don't think you deserve as much credit as you seem to want; you can learn to be more humble.

If your estimation bias is _exactly zero_, congratulations! You must be a mind-reader, and/or exceptionally self-aware.

Your estimation bias _per project_ is the difference between self- and team-estimated contribution for that project. So the estimation bias stats for the above projects would be:

| Project      | Estimation Bias      |
|:-------------|:---------------------|
| #tiny-tigers | 20% - 30% = **-10%** |
| #big-bees    | 50% - 45% = **5%**   |
| #red-rabbits | 28% - 30% = **-2%**  |

Based on these projects, the _overall estimation bias stat_ is -2.33% (average of [-10%, 5%, -2%]).

## Time Dedication per Week

Average hours per week you spent contributing to team projects. Think of these as "billable" hours.

[game-objectives]: ./Boundaries.md#objectives
[absolute-values]: http://www.coolmath.com/algebra/18-absolute-value-equations-inequalities/01-absolute-values-01
[elo-rating-wiki]: https://en.wikipedia.org/wiki/Elo_rating_system
