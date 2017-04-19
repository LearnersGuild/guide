# Stats

These statistics (stats) are meant to reflect your progress towards the [game objectives][game-objectives], as well as your overall "health" in the game.

<!-- TOC depthFrom:2 depthTo:3 withLinks:1 updateOnSave:0 orderedList:0 -->

- [How to Earn Stats](#how-to-earn-stats)
- [XP](#xp)
- [Weighted Average Stats](#weighted-average-stats)
  - [Estimation Accuracy and Bias](#estimation-accuracy-and-bias)
- [Project Review Stats](#project-review-stats)
  - [External Project Review Count](#external-project-review-count)
  - [Internal Project Review Count](#internal-project-review-count)
  - [Review Accuracy](#review-accuracy)
  - [Review Experience (RXP)](#review-experience-rxp)
- [Project Contribution](#project-contribution)
  - [Actual Contribution](#actual-contribution)
  - [Expected Contribution](#expected-contribution)
  - [Contribution Gap](#contribution-gap)

<!-- /TOC -->

## How to Earn Stats

At the end of every project, the data gathered in the retrospectives are used to calculate and update your player stats, as well as the stats for the project itself.

In order to earn stats from a project, _every member of the team must have completed the project retrospective_. Stats can only be calculated and awarded from a project once all retros have been submitted.

Other stats, like average project completion, will change over time as more reviews are submitted.


## Hours Contributed

The number of hours you contributed is computed by taking the expected hours for a project (typically 38, but perhaps fewer if the week includes any holidays) and subtracting from that number the number of "personal time off" hours you took while working on that project.

Note that, within the context of the game, it's not possible for a player to contribute _more_ hours than the number of expected hours for the project. This is by design, since we don't want the game to be unfairly balanced toward people who have fewer outside obligations.


## Project Contribution

The amount that you contribute to a project determines a series of other stats, and also contains several sub-stats within.

It can be hard to determine what constitutes _contribution_. If you are unclear, review the section on [Technical Contribution](../Learning_Guide/Retrospectives.md#technical-contribution)


## Weighted Average Stats

Each of the following stats are based on a weighted average of (up-to) 6 of your most recent projects for which the given stat was available, since not all stats are applicable for all projects. For example, if you work on a project by yourself, there won't be any team-related feedback collected in the retrospective, and as such, there won't be any team-related stats. In all of the formulas below, that's what is meant by `recentProjects`.


### XP/Week

Your accomplishments, aggregated and condensed to a number.

Each goal you and your team attempt to complete, has XP attached to it.

**The base XP related to a goal gets divided** based on how much of the goal you've completed, and what your personal contribution is to the project:

```
goalBaseXP * projectCompleteness * yourContributionPercentage
```

Next, if you and your team complete more than 70% of the project, **each member of the team gets the same amount of bonus XP**. The bonus XP depends on how much over 70% your team accomplished.

```
goalBonusXP * min((projectCompleteness - 70),0)
```

The moving average of the XP you gained for your last 6 projects is the XP/Week

If you want to dig deeper into how this all works, check out [these examples](https://docs.google.com/spreadsheets/d/10g9F9XKmHodyyQ5AxLmrSAibehTrS7wdi-h4tj3Rfa0/edit#gid=0)


### Estimation Accuracy and Bias

Estimation accuracy and bias reflect how well you estimate your contribution to projects.

To demonstrate how these stats apply, we'll use a modified version of the above dataset, aggregating the team estimates into their average (mean):

| Project      | Self estimate | Team estimate (avg) |
|:-------------|:--------------|:--------------------|
| #big-bees    | 50%           | 45%                 |
| #red-rabbits | 28%           | 30%                 |
| #tiny-tigers | 20%           | 30%                 |

#### Estimation Accuracy

Estimation accuracy reflects how accurate your estimations are relative to the consensus. Represented as a percentage (0..100%).

One hundred percent is perfect accuracy: you estimate your contribution the same as your peers do. The closer this stat is to 100%, the more accurate your contribution estimates are.

Your estimation accuracy _per project_ is computed by first finding difference between self- and team-estimated contribution for that project, and then using the [absolute value][absolute-values] of that difference. Finally, this number is subtracted from 100% (so that a perfect score would be 100%, not 0%). So the estimation accuracy stats for the above projects would be:

| Project      | Estimation Accuracy                          |
|:-------------|:---------------------------------------------|
| #tiny-tigers | 100% - abs(20% - 30%) = 100% - 10% = **90%** |
| #big-bees    | 100% - abs(50% - 45%) = 100% - 5% = **95%**  |
| #red-rabbits | 100% - abs(28% - 30%) = 100% - 2% = **98%**  |

Based on these projects, the _overall estimation accuracy stat_ is 94.33% (average of [90%, 95%, 98%]).

##### Formula (for project)

```
100 - absolute(selfEstimatedContribution - teamEstimatedContribution)
```

##### Formula (for overall stat)

```
sum(recentEstimationAccuracy) / count(recentProjects)
```

Where `recentEstimationAccuracy` is one project's worth of estimation accuracy (that gets summed with up-to 5 other projects), and `recentProjects` is up to 6 recent projects that contain a stat value for estimation accuracy.


#### Estimation Bias

Estimation bias reflects whether you tend to over- or under-estimate your contribution. Represented as a +/- percentage (-100%..100%).

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

##### Formula (for project)

```
selfEstimatedContribution - teamEstimatedContribution
```

##### Formula (for overall stat)

```
sum(recentEstimationBias) / count(recentProjects)
```

Where `recentEstimationBias` is one project's worth of estimation bias (that gets summed with up-to 5 other projects), and `recentProjects` is up to 6 recent projects that contain a stat value for estimation bias.


## Project Review Stats

The following stats all relate to the activity of reviewing projects after they have been completed.

### External Project Review Count

The number of _other players'_ projects you've reviewed the completeness of. Represented as an integer.

### Internal Project Review Count

The number of your own projects you've reviewed the completeness of. Represented as an integer.

### Review Accuracy

Review accuracy is a measure of how good a player is at evaluating the completeness of projects (both their own as well as others') as compared to players who have more review experience (higher RXP).

It is impacted by the Delta between the completeness score of the player's reviews (both internal and external) and reviews by other players with better RXP.

It expressed as a number between 0 and 100. With 100 meaning that review accuracy is flawless.

#### Formula

```
// per-project stats
for each project that a player reviewed (internal or external review)
  skip if player was the top reviewer (reviewer with the highest RXP)
  topCompletenessScore = (top reviewer's completeness assessment)
  reviewDelta = abs(topCompletenessScore - playerCompletenessScore)
  projectReviewAccuracy = 100 - reviewDelta

// overall stat
reviewAccuracy = projectReviewCount < 8 ? null : mean(20 most recent projectReviewAccuracy scores)
```

We don't start computing accuracy for a player until that player has passed a threshold of 8 reviews. With fewer reviews that that we really don't have enough information to judge their accuracy.

### Review Experience (RXP)

RXP is a function of Review Accuracy of a player combined with how much experience the player has. The higher the RXP, the better this player is at assessing completeness scores of another player.

It is a composite stat that is impacted by:

* Review Accuracy
* External Project Review Count

For example:

Two players with the same review accuracy, but Player A has done twice as many reviews as Player B. This means Player A has a higher RXP.
Two players who have done the same number of reviews, but Player A has more review accuracy. This means that Player A has a higher RXP.

#### Formula

```
(externalProjectReviewCount / 20)  + reviewAccuracy
```


[game-objectives]: ./Basic_Gameplay.md#objectives
[absolute-values]: http://www.coolmath.com/algebra/18-absolute-value-equations-inequalities/01-absolute-values-01
[elo-rating-wiki]: https://en.wikipedia.org/wiki/Elo_rating_system
[elo-rank-github]: https://github.com/dmamills/elo-rank
[cos-dynam-tensions]: http://cos.learnersguild.org/Dynamic_Tensions/
