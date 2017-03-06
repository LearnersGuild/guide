# Stats

These statistics (stats) are meant to reflect your progress towards the [game objectives][game-objectives], as well as your overall "health" in the game.

### How to Earn Stats

At the end of every project, the data gathered in the retrospectives are used to calculate and update your player stats, as well as the stats for the project itself.

In order to earn stats from a project, _every member of the team must have completed the project retrospective_. Stats can only be calculated and awarded from a project once all retros have been submitted.

Other stats, like average project completion and quality (both for projects and for players), will change over time as more reviews are submitted.

#### Example Situations that Impact Stats

To understand how stats work, it's helpful to know how certain scenarios will impact your stats. These are just a few examples - there are many more ways that stats can be impacted, and not enough room to cover them all here.

##### Missing project work time

If you are unable to work on your project during active hours and thus put in fewer hours than normal, there are a few consequences for your stats.

The most direct consequence is that you will log fewer hours for that project, which will in turn lower your XP.

Less direct consequences are that your contribution will likely be lower because you will have had less time than your teammates to contribute to the project.

If you are out of integrity with your team (for example, by not informing them of absences or not taking accountability for your tasks), then you may also see a drop in your culture & team play health.

##### Working more than expected hours on a project

Working long hours can feel like it is more productive, but if you are not getting enough sleep and the quality of your work suffers, then it can negatively impact your stats.

If you do "overtime" and put in more hours on a project than is expected, it shouldn't have a direct impact on your stats. It may, however, have an _indirect_ impact if those additional hours yield a higher perceived contribution on your part; in that case, you may see your Elo go up.

On the other hand, if you end up doing a lot of work and don't keep your team informed and engaged, you will likely see a drop in your team play and culture stats. It's great to be enthusiastic, but be sure to bring your team with you.

##### One or more teammates don't submit a retrospective

As mentioned above, stats cannot be earned for a project until every team member has submitted a retrospective.

If one or more of your teammates is out sick or otherwise unable to submit a retro at the end of the work week, no stats can be generated for any players in that project. Remind any absent teammates to submit their retros when they are active again.

---

## Hours Contributed

The number of hours you contributed is computed by taking the expected hours for a project (typically 38, but perhaps fewer if the week includes any holidays) and subtracting from that number the number of "personal time off" hours you took while working on that project.

Note that, within the context of the game, it's not possible for a player to contribute _more_ hours than the number of expected hours for the project. This is by design, since we don't want the game to be unfairly balanced toward people who have fewer outside obligations.

##### Formula

```
projectExpectedHours - yourPersonalTimeOffHours
```

## XP

Your experience, aggregated and condensed to a number. XP always grows; the larger the number, the higher your experience.

XP is calculated and awarded in three steps for each project.

First, the gross project XP is calculated by adding all of the hours each team member contributed to the project. So a project where the players contributed 35, 30, and 35 hours would have a total of 100 hours.

Then, the gross project XP is divvied up to each player according to their actual contribution to the project. So if your actual contribution to the project is 40%, you would get 40 XP (100 x 0.40).

##### Formula

```
sum(allTeamHours) * yourContributionPercentage
```

## Elo Rating

[Elo][elo-rating-wiki] is a system for determining the relative skill of players. It is used by many different games and sports for organizing play within a league. Represented as a positive integer, which shows your relative skill as compared to other players.

In the context of the LOS, your Elo rating is a representation of your ability to contribute to projects relative to other players. It is not an _absolute_ measure of your skill, but is only meaningful in reference to other players.

Unlike XP, Elo moves up and down depending on your Effectiveness at contributing to a project, and and with whom you work on projects. Effectiveness is measured as percentage contribution to the project divided by the number of hours contributed.

It can be a little difficult to understand how Elo works in a collaborative game like this one, since it is usually applied to competitive, zero-sum games like chess or beach volleyball or hot dog eating contests. So let's dive into an example.

Imagine that you're a professional jigsaw puzzle solver. You work with other puzzlers to collaboratively solve jigsaw puzzles. Your Elo rating in the Professional Jigsaw League is 1200.

Let's say that you solve a puzzle with three other puzzlers of the _exact same_ Elo rating (1200). If you solve 1/2 of the puzzle (by placing 1/2 of the pieces) *in the same time as the three remaining puzzlers*, then your Elo rating would _go up_ after the game because you performed _much better_ than you were expected based on your Elo. On a team of four puzzlers of the same skill (Elo), who all put in the same time, you'd be expected to solve 1/4 of the puzzle.

If, on the other hand, you only solved 1/5 of the puzzle, your Elo rating would _go down_, because you performed worse than was expected of you.

The interesting thing about Elo is that the ratings take into account the relative skill _before_ the game, so you can play more advanced players, perform worse (in terms of efficiency), and _still go up_ in your Elo rating. It all depends on how much better or worse you performed relative to what is expected of you.

Checkout the [wikipedia](https://en.wikipedia.org/wiki/Elo_rating_system) article for background on Elo rating.

#### Formula

Elo is (currently) calculated using the [elo-rank][elo-rank-github] library with a K-Factor of 20 and an initial Elo for all players of 1000.

Below is a rough summary of what happens in our production codebase for the calculation, with all key components for calculating Elo (except for what's taken care of by the library).

```javascript
import elo from 'elo-rank'

function eloRatings([playerA, playerB]) {
  const {rating: ratingA, score: scoreA} = playerA
  const {rating: ratingB, score: scoreB} = playerB
  const kFactor = 20

  const eloA = elo(kFactor)
  const eloB = elo(kFactor)

  const expectedMarginA = eloA.getExpected(ratingA, ratingB)
  const expectedMarginB = eloB.getExpected(ratingB, ratingA)

  const [actualMarginA, actualMarginB] = scoreMargins([scoreA, scoreB])

  const newRatingA = eloA.updateRating(expectedMarginA, actualMarginA, ratingA)
  const newRatingB = eloB.updateRating(expectedMarginB, actualMarginB, ratingB)

  return [newRatingA, newRatingB]
}

function updateEloRatings(playerStats) {
  // playerStats is an object keyed on playerId
  // with a value of that player's stats
  const scoreboard = playerStats
    .reduce((result, {playerId, ...stats}) => {
      const {elo = {}} = stats
      result.set(playerId, {
        id: playerId,
        rating: elo.rating || INITIAL_RATINGS.DEFAULT,
        matches: elo.matches || 0,
        score: stats.relativeContributionPerHour, // a.k.a., "effectiveness"
      })
      return result
    }, new Map())

  // sorted by elo (descending) solely for the sake of being deterministic
  const sortedPlayerIds = Array.from(scoreboard.values())
                            .sort((a, b) => a.rating - b.rating)
                            .map(item => item.id)

  // pair every team player up to run "matches"
  const matches = toPairs(sortedPlayerIds)

  // for each team player pair, update ratings based on relative effectiveness
  matches.forEach(([playerIdA, playerIdB]) => {
    const playerA = scoreboard.get(playerIdA)
    const playerB = scoreboard.get(playerIdB)
    const [playerRatingA, playerRatingB] = eloRatings([playerA, playerB])

    playerA.rating = playerRatingA
    playerA.matches++
    playerA.kFactor = _kFactor(playerA.matches)

    playerB.rating = playerRatingB
    playerB.matches++
    playerB.kFactor = _kFactor(playerB.matches)
  })

  // ...
  // save updated scores to players' stats in database for each player in
  // scoreboard
  // ...
}
```

Checkout this pELO caclulator](http://www.3dkingdoms.com/chess/elo.htm) to model Elo Changes. Use a K-factor of 20.


## Average Project Completeness

The average % completeness of all reviews for the given project.

##### Formula

```
sum(allProjectCompletenessReviews) / count(reviews)
```

## Average Project Quality

The average % quality of all reviews for the given project.

##### Formula

```
sum(allProjectQualityReviews) / count(reviews)
```

## Weighted Average Stats

Each of the following stats are based on a weighted average of (up-to) 6 of your most recent projects for which the given stat was available, since not all stats are applicable for all projects. For example, if you work on a project by yourself, there won't be any team-related feedback collected in the retrospective, and as such, there won't be any team-related stats. In all of the formulas below, that's what is meant by `recentProjects`.

### Health - Culture

How much your team members felt you contributed positively to the team culture.
Not a part of your stats, but it is part of the retrospective and is used to help with the Project Formation Algorithm (PFA).

#### What Culture Contribution Means

Culture contribution can be a difficult thing to assess. It is important to understand what it means, both so that you can effectively evaluate your teammates and interpret your own stats.

Use the rubric below to build your sense of what "good culture contribution" is. These are mirrored by the [dynamic tensions][cos-dynam-tensions] in the COS.

| Value     | Evidence                                                                                                                                                                                                                                                               |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Belonging | They were authentic and real. They were being themselves which inspired us to be ourselves.<br> They were in relationship with me. They cared for the quality of our working relationship, and paid attention to it.                                                   |
| Efficacy  | They honored their own and others' autonomy. They practiced and supported free, creative work.<br> They acted in integrity. They helped to create and maintain clear accountabilities. They stood firm in their domain and power, and respected the domains of others. |
| Trust     | They told the truth. They said what was true for them, and chose truth over comfort.<br> They were safe to work with. They didn't judge, criticize, or stonewall. They supported our team culture to be free from standards, judgements, and personal attacks.         |
| Growth    | They challenged themselves and others. They sought out growth for themselves, and helped everyone extend their potential.<br> They were generous in their support. They were responsive to requests for help, and offered guidance and mentorship.                     |
| Flow      | They were engaged. Their focus, dedication and motivation supported our team in staying on task.<br> They enjoyed the work. They created more fun and enjoyment for us.                                                                                                |

### Health - Team Play

How well your team members felt that you collaborated on team efforts, independent of your technical skill, mentorship, or cultural contribution. Not a part of your stats, but it is part of the retrospective and is used to help with the Project Formation Algorithm (PFA).

#### What Team Play Means

It is important to understand what it means to be a good team player, both so that you can effectively evaluate your teammates and interpret your own stats.

Use the rubric below to build your sense of what "good team play" is.

| Value               | Evidence                                                                                                                                   |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| Receptiveness       | They were open to feedback, and received it gracefully without becoming defensive or dismissive. They separated their ego from their work. |
| Results Focus       | They focused on the best outcomes for the team. They were dedicated to and persevered in achieving shared goals.                           |
| Flexible Leadership | They stepped into leadership roles when needed, and supported others to step into leading roles.                                           |
| Friction Reduction  | They were constantly looking for ways to improve team process, and to help everyone play to their full potential.                          |

### Health - Technical

How well you are able to contribute to a project based on your technical skills, independent of your team play or cultural contribution. Not a part of your stats, but it is part of the retrospective and is used to help with the Project Formation Algorithm (PFA).

#### What Technical Skill Means

It is important to understand what it means to contribute technically, both so that you can effectively evaluate your teammates and interpret your own stats.

Use the rubric below to build your sense of what "good technical skill" is.

| Value                         | Evidence                                                                                                                                                         |
|:------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code Quality                  | They were committed to quality. They practiced good code organization, source control, naming, syntax, indentation, modularity...etc.                            |
| Code Completeness             | They were committed to completeness. They practiced good estimation, good time management, and drove us to shipping on time.                                     |
| Technical Communication       | They were able to professionally discuss, debate and relay technical ideas. They were succinct, precise, clear and proficient in their thinking & communication. |
| Technical Knowledge           | They had pre-existing technical knowledge and experience with the technologies we were working with.                                                             |
| Technical Confidence          | They were confident in facing the unknown. They stayed with the challenges, and faced them head on.                                                              |
| Research                      | They were skilled in asking the right questions, googling, spiking, reading docs, and pulling in existing resources/solutions/code bases.                        |
| Problem Decomposition/Solving | They were good at breaking down large problems into smaller pieces, and tackling them in the right order.                                                        |
| Debugging                     | They were adept at identifying, isolating, recreating, and fixing bugs.                                                                                          |
| Testing                       | They wrote good, solid tests, and used testing to drive a better product.                                                                                        |


### Challenge

The challenge stat is a reflection of how well you are able to find work that puts you into your zone of proximal development (ZPD). Represented as a number between 1 and 10, with 7 representing your ZPD. This mapping is used to give meaning to the other numbers:

- 1 = Extremely bored
- 4 = Confident and comfortable
- 6 = Stretched but still capable
- 7 = In flow and pushed just beyond capacity
- 8 = Slightly more challenged than is fun
- 10 = Completely overwhelmed

##### Formula

```
sum(recentChallengeStatsForProjects) / count(recentProjects)
```

Where `recentChallengeStatsForProjects` one project's challenge score (that gets summed with up-to 5 other projects), and `recentProjects` is up to 6 recent projects that contain a stat value for challenge.


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

The number of _other players'_ projects you've reviewed the completeness and quality of. Represented as an integer.

### Internal Project Review Count

The number of your own projects you've reviewed the completeness and quality of. Represented as an integer.

### Review Accuracy

Review accuracy is a measure of how good a player is at evaluating the completeness and quality of projects (both their own as well as others') as compared to players who have more review experience (higher RXP).

It is a composite stat that is impacted by:

* Delta between completeness score of my reviews (both internal and external) and other players with better RXP
* Delta between quality score of my reviews (both internal and external) and other players with better RXP

It expressed as a number between 0 and 100. With 100 meaning that review accuracy is flawless.

#### Formula

```
// per-project stats
for each project that a player reviewed (internal or external review)
  skip if player was the top reviewer (reviewer with the highest RXP)
  topCompletenessScore = (top reviewer's completeness assessment)
  absoluteCompletenessDelta = abs(topCompletenessScore - playerCompletenessScore)
  topQualityScore = (top reviewer's quality assessment)
  absoluteQualityDelta = abs(topQualityScore - playerQualityScore)
  reviewDelta = (absoluteCompletenessDelta + absoluteQualityDelta) / 2
  projectReviewAccuracy = 100 - reviewDelta

// overall stat
reviewAccuracy = projectReviewCount < 8 ? null : mean(20 most recent projectReviewAccuracy scores)
```

We don't start computing accuracy for a player until that player has passed a threshold of 8 reviews. With fewer reviews that that we really don't have enough information to judge their accuracy.

### Review Experience (RXP)

RXP is a function of Review Accuracy of a player combined with how much experience the player has. The higher the RXP, the better this player is at assessing completeness and quality scores of another player.

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

## Project Contribution

The amount that you contribute to a project determines a series of other stats, and also contains several sub-stats within.

It can be hard to determine what constitutes _contribution_. Quantity of work produced? What about ideas? Hours engaged?

Whenever you start working on a project, you should spend a little time with your team defining what contribution means and how you plan to measure it. Here are some guidelines to get you started:

**What contribution is:**

- Designing and planning project features
- Actively building a critical feature of the project
- Assisting other team members in completing project features
- Resolving bugs and conflicts in the code

**What contribution is NOT:**

- Exploring tangential topics and ideas
- Developing non-critical features of the project
- Passively pairing / being an observer

Within a given project, you have **actual** and **expected** contributions, as well as a **contribution gap**.

To demonstrate how the various contribution stats are calculated, we'll use the following dataset in examples.

#### Example Project Contribution Estimations

| Project      | Team size | Self estimate | Team estimates | Self accuracy | Team accuracies | Your Hours | Total Hours |
|:-------------|:----------|:--------------|:---------------|:--------------|:----------------|:-----------|:------------|
| #big-bees    | 3         | 50%           | 42%, 48%       | 88            | 88, 88          | 30         | 80          |
| #red-rabbits | 4         | 29%           | 27%, 35%, 28%  | 91            | 92, 89, 96      | 25         | 120         |
| #tiny-tigers | 2         | 20%           | 30%            | 96            | 94              | 40         | 75          |

### Actual Contribution

Your actual contribution is the determined by taking the contribution estimate from the player on your team who has the highest [estimation accuracy](#estimation-accuracy). Represented as a percentage (0..100%).

If it is not possible to determine which player has the highest estimation accuracy, then contribution is determined by taking the average of your team's estimates of what percentage of the project you contributed to. Such cases include:
- any or all players on the team have no estimation accuracy stat yet
- all players have the same estimation accuracy

When averaging the team estimates, your own actual contribution _does_ include your own estimate of your contribution.

In the above dataset, the player's actual contribution for the `#big-bees` project (since everyone on the team has the same estimation accuracy) is the average of _all_ the estimates, so it would be equal to 46.67% ( (50% + 42% + 48%) / 3 ).

However, the player's actual contribution for the `#red-rabbits` project would be 28%, because the player who reported 28% has the highest estimation accuracy (96%).

##### Formula

For a team where it is possible to determine which player has the highest estimation accuracy:

```
projectContribution  // (from player with highest estimation accuracy)
```

For a team where it is _not_ possible to determine which player has the highest estimation accuracy:

```
sum(projectContributionFeedbackFromTeam) / teamSize
```

### Expected Contribution

Your expected contribution is how much you are expected to contribute to the project based on how many hours you contribute relative to the total hours of all players. Represented as a percentage (0..100%).

In the above dataset, the player's expected contribution for the `#big-bees` project is equal to 37.5% ( 30 / 80 ) because they contributed 30 out of a total 80 hours that players spent on this project.

### Contribution Gap

The contribution gap is the difference between actual and expected contribution. It demonstrates whether a player contributed _more_ or _less_ than is expected of them, based on the size of their team. Represented as a +/- percentage (-100%..100%).

In the above dataset, the player's contribution gap for the `#big-bees` project is equal to 9.17% ( 46.67% - 37.5% ). In other words, they contributed +9.17% _more_ to the project than what is expected based on how many hours they worked on it.



[game-objectives]: ./Boundaries.md#objectives
[absolute-values]: http://www.coolmath.com/algebra/18-absolute-value-equations-inequalities/01-absolute-values-01
[elo-rating-wiki]: https://en.wikipedia.org/wiki/Elo_rating_system
[elo-rank-github]: https://github.com/dmamills/elo-rank
[cos-dynam-tensions]: http://cos.learnersguild.org/Dynamic_Tensions/
