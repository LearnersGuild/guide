# Stats

These statistics (stats) are meant to reflect your progress towards the [game objectives][game-objectives], as well as your overall "health" in the game.

At the end of every project, the data gathered in the reflection phase is used to calculate and update your player stats.

## XP

Your experience, aggregated and condensed to a number. XP always grows; the larger the number, the higher your experience. XP is calculated by combining the following for each project worked on:

- Your percentage contribution to the project
- Total hours worked on the project by all team members
- Project quality
- Project completeness

## Average Project Completeness

The average % completion of all projects you've worked on.

## Average Project Quality

The average % quality of all projects you've worked on.

## Learning Support

How much your team members felt that you supported them in their learning. This is a weighted average with more recent projects counting more than earlier ones. Represented as a percentage (0..100%).

## Culture Contribution

How much your team members felt you contributed positively to the team culture. This is a weighted average with more recent projects counting more than earlier ones. Represented as a percentage (0..100%).

## Project Contribution

The amount that you contribute to a project determines a series of other stats, and also contains several sub-stats within.

Within a given project, you have **actual** and **expected** contributions, as well as a **contribution gap**.

To demonstrate how the various contribution stats are calculated, we'll use the following dataset in examples.

#### Example Project Contribution Estimations

| Project      | Team size | Self estimate | Team estimates |
|:-------------|:----------|:--------------|:---------------|
| #big-bees    | 3         | 50%           | 42%, 48%       |
| #red-rabbits | 4         | 28%           | 27%, 35%, 28%  |
| #tiny-tigers | 2         | 20%           | 30%            |

### Actual Contribution

Your actual contribution is the average of your team's estimates of what percentage of the project you contributed to. It includes your own estimate of your contribution. Represented as a percentage (0..100%).

In the above dataset, the player's actual contribution for the `#big-bees` project is the average of _all_ the estimates, so it would be equal to 46.67% ( (50% + 42% + 48%) / 3 ).

### Expected Contribution

Your expected contribution how much you are expected to contribute to the project based on the team size so that each player contributes equally. Represented as a percentage (0..100%).

In the above dataset, the player's expected contribution for the `#big-bees` project is equal to 33.33% ( 100% / 3 ) because their team has 3 players, so an equal contribution is 1/3 of the project.

### Contribution Gap

The contribution gap is the difference between actual and expected contribution. It demonstrates whether a player contributed _more_ or _less_ than is expected of them, based on the size of their team. Represented as a percentage (0..100%).

In the above dataset, the player's contribution gap for the `#big-bees` project is equal to 13.34% ( 46.67% - 33.33% ).

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

Zero is equal to perfect accuracy (i.e. you estimate your contribution the same as your peers do). The closer this stat is to zero, the more accurate your contribution estimates are.

Your estimation accuracy _per project_ is the difference between self- and team-estimated contribution for that project, using the [absolute value][absolute-values] of that difference. So the estimation accuracy stats for the above projects would be:

| Project      | Estimation Accuracy                  |
|:-------------|:-------------------------------------|
| #tiny-tigers | abs(20% - 30%) = abs(-10%) = **10%** |
| #big-bees    | abs(50% - 45%) = abs(5%) = **5%**    |
| #red-rabbits | abs(28% - 30%) = abs(-2%) = **2%**   |

Based on these projects, the _overall estimation accuracy stat_ is 5.67% (average of [10%, 5%, 2%]).

## Estimation Bias

Estimation bias reflects whether you tend to over- or under- estimate your contribution. Represented as a +/- percentage (-100%..100%).

If your estimation bias is _below zero_, that means that you tend to underestimate your contribution to the projects that you work on. Your fellow players see value that you don't recognize; you can learn to take more credit for your work!

If your estimation bias is _above zero_, that means that you tend to overestimate your contribution to the projects that you work on. Your fellow players don't think you deserve as much credit as you seem to want; you can learn to be more humble.

If your estimation bias is _exactly zero_, congratulations! You must be a mind-reader, and/or exceptionally self-aware.

Estimation bias is calculated the same as estimation accuracy, except that it does _not_ use the absolute values of the difference between self and team estimates.

Your estimation bias _per project_ is the difference between self- and team-estimated contribution for that project. So the estimation bias stats for the above projects would be:

| Project      | Estimation Bias  |
|:-------------|:-----------------|
| #tiny-tigers | 20% - 30% = -10% |
| #big-bees    | 50% - 45% = 5%   |
| #red-rabbits | 28% - 30% = -2%  |

Based on these projects, the _overall estimation bias stat_ is -2.33% (average of [-10%, 5%, -2%]).

## Time Dedication per Week

Average hours per week you spent contributing to team projects.

[game-objectives]: ./Boundaries.md#objectives
[absolute-values]: http://www.coolmath.com/algebra/18-absolute-value-equations-inequalities/01-absolute-values-01
