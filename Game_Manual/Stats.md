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

##### Working more than normal hours on a project

If you do "overtime" and put in more hours on a project than is expected, it is likely that you will see a greater increase in XP.

Be aware that if you put in more hours but are _less effective_ (i.e. if your contribution per hour goes down), then it is likely that your Elo will not go up. Working long hours can feel like it is more productive, but if you are not getting enough sleep and the quality of your work suffers, then it can negatively impact your stats.

Similarly, if you end up doing a lot of work and don't keep your team informed and engaged, you will likely see a drop in your team play and culture stats. It's great to be enthusiastic, but be sure to bring your team with you.

##### One or more teammates don't submit a retrospective

As mentioned above, stats cannot be earned for a project until every team member has submitted a retrospective.

If one or more of your teammates is out sick or otherwise unable to submit a retro at the end of the work week, no stats can be generated for any players in that project. Remind any absent teammates to submit their retros when they are active again.

---

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

Unlike XP, Elo moves up and down depending on your project-to-project contribution stats and with whom you work on projects.

It can be a little difficult to understand how Elo works in a collaborative game like this one, since it is usually applied to competitive, zero-sum games like chess or beach volleyball or hot dog eating contests. So let's dive into an example.

Imagine that you're a professional jigsaw puzzle solver. You work with other puzzlers to collaboratively solve jigsaw puzzles. Your Elo rating in the Professional Jigsaw League is 1200.

Let's say that you solve a puzzle with three other puzzlers of the _exact same_ Elo rating (1200). If you solve 1/2 of the puzzle (by placing 1/2 of the pieces), then your Elo rating would _go up_ after the game because you performed _much better_ than you were expected based on your Elo. On a team of four puzzlers of the same skill (Elo), you'd be expected to solve 1/4 of the puzzle.

If, on the other hand, you only solved 1/5 of the puzzle, your Elo rating would _go down_, because you performed worse than was expected of you.

The interesting thing about Elo is that the ratings take into account the relative skill _before_ the game, so you can play more advanced players, perform worse, and _still go up_ in your Elo rating. It all depends on how much better or worse you performed relative to what is expected of you.

Checkout the [wikipedia](https://en.wikipedia.org/wiki/Elo_rating_system) article for background on Elo rating.

#### Formula

Elo is (currently) calculated with a Ruby script that uses the [elo](https://github.com/iain/elo) library with a K-Factor of 20 and an initial Elo for all players of 1000.

Below is a condensed version of the calculation, with all key components for calculating Elo except for what's taken care of by the library. Each player is an instance of the `Elo::Player` class.

```ruby
def play(player_one, player_two, project)
  game = player_one.versus(player_two)

  p1_effectiveness = effectiveness(player_one, project)
  p2_effectiveness = effectiveness(player_two, project)

  pre_scaled_result = p1_effectiveness / (p1_effectiveness + p2_effectiveness).to_f

  scaled_result = ((pre_scaled_result - 0.5) * 3) + 0.5

  if (scaled_result > 1)
    scaled_result = 1
  elsif scaled_result < 0
    scaled_result = 0
  end

  game.result = scaled_result
end

def effectiveness(player, project)
  return (projectContribution(player, project) / projectHours(player, project).to_f).round(2)
end

1.upto(current_cycle) do |cycle_no|
  projects(cycle_no).sort.each do |proj_name|
    players = players(proj_name) # all players except pro players

    team_players.combination(2).each do |players|
      play(players[0], players[1], proj_name)
    end
  end
end
```

## Average Project Completeness

The average % completion of all projects you've worked on.

##### Formula

```
sum(allProjectCompletenessReviews) / count(projects)
```

## Average Project Quality

The average % quality of all projects you've worked on.

##### Formula

```
sum(allProjectQualityReviews) / count(projects)
```

## Health - Culture

How much your team members felt you contributed positively to the team culture. This is a weighted average that only uses retrospective data from the previous 6 cycles. Represented as a percentage (0..100%).

Culture contribution is calculated by taking the results of culture contribution question from the retrospective ("Based on X's culture contribution..."), and converting the Likert-scale values (0-6) to a percent (0-100%). A "strongly agree" answer is equal to 6 Likert points. So if you received two "agrees" and a "strongly agree", your average Likert score would be 5.33 ((5 + 5 + 6) / 3), which is then converted to a percentage score of 88.88% (5.33 / 6).

##### Formula

```
sum(recentCultureFeedback) / count(recentProjects)
```

Where `recentCultureFeedback` = average of culture feedback for each project in last 6 cycles and `recentProjects` = your projects in the last 6 cycles.

### What Culture Contribution Means

Culture contribution can be a difficult thing to assess. It is important to understand what it means, both so that you can effectively evaluate your teammates and interpret your own stats.

Use the rubric below to build your sense of what "good culture contribution" is. These are mirrored by the [dynamic tensions][cos-dynam-tensions] in the COS.

| Value     | Evidence                                                                                                                                                                                                                                                               |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Belonging | They were authentic and real. They were being themselves which inspired us to be ourselves.<br> They were in relationship with me. They cared for the quality of our working relationship, and paid attention to it.                                                   |
| Efficacy  | They honored their own and others' autonomy. They practiced and supported free, creative work.<br> They acted in integrity. They helped to create and maintain clear accountabilities. They stood firm in their domain and power, and respected the domains of others. |
| Trust     | They told the truth. They said what was true for them, and chose truth over comfort.<br> They were safe to work with. They didn't judge, criticize, or stonewall. They supported our team culture to be free from standards, judgements, and personal attacks.         |
| Growth    | They challenged themselves and others. They sought out growth for themselves, and helped everyone extend their potential.<br> They were generous in their support. They were responsive to requests for help, and offered guidance and mentorship.                     |
| Flow      | They were engaged. Their focus, dedication and motivation supported our team in staying on task.<br> They enjoyed the work. They created more fun and enjoyment for us.                                                                                                |

## Health - Team Play

How well your team members felt that you collaborated on team efforts, independent of your technical skill, mentorship, or cultural contribution. This is a weighted average that only uses retrospective data from the previous 6 cycles. Represented as a percentage (0..100%).

Team play scores are calculated the same as culture contribution scores, but using the team play answers from the retrospective.

##### Formula

```
sum(recentTeamPlayFeedback) / count(recentProjects)
```

Where `recentTeamPlayFeedback` = average of team play feedback for each project in last 6 cycles and `recentProjects` = your projects in the last 6 cycles.

### What Team Play Means

It is important to understand what it means to be a good team player, both so that you can effectively evaluate your teammates and interpret your own stats.

Use the rubric below to build your sense of what "good team play" is.

| Value               | Evidence                                                                                                                                   |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| Receptiveness       | They were open to feedback, and received it gracefully without becoming defensive or dismissive. They separated their ego from their work. |
| Results Focus       | They focused on the best outcomes for the team. They were dedicated to and persevered in achieving shared goals.                           |
| Flexible Leadership | They stepped into leadership roles when needed, and supported others to step into leading roles.                                           |
| Friction Reduction  | They were constantly looking for ways to improve team process, and to help everyone play to their full potential.                          |

## Health - Technical

How well you are able to contribute to a project based on your technical skills, independent of your team play or cultural contribution. This is a weighted average that only uses retrospective data from the previous 6 cycles. Represented as a percentage (0..100%).

Technical health scores are calculated the same as culture contribution scores, but using the technical health answers from the retrospective.

##### Formula

```
sum(recentTechnicalFeedback) / count(recentProjects)
```

Where `recentTechnicalFeedback` = average of technical feedback for each project in last 6 cycles and `recentProjects` = your projects in the last 6 cycles.

### What Technical Skill Means

It is important to understand what it means to contribute technically, both so that you can effectively evaluate your teammates and interpret your own stats.

Use the rubric below to build your sense of what "good technical skill" is.

| Value               | Evidence                                                                                                                                   |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| Code Quality            | They were committed to quality. They practiced good code organization, source control, naming, syntax, indentation, modularity...etc. |
| Code Completeness       | They were committed to completeness. They practiced good estimation, good time management, and drove us to shipping on time. |
| Technical Communication | They were able to professionally discuss, debate and relay technical ideas. They were succinct, precise, clear and proficient in their thinking & communication. |
| Technical Knowledge     | They had pre-existing technical knowledge with the technologies we were working with. |
| Technical Confidence    | They were confident in facing the unknown. They stayed with the challenges, and faced them head on. |
| Research                | They were skilled in asking the right questions, googling, spiking, reading docs, and pulling in existing resources/solutions/code bases. |
| Problem Decomposition/Solving | They were good at breaking down large problems into smaller pieces, and tackling them in the right order. |
| Debugging               | They were adept at identifying, isolating, recreating, and fixing bugs. |
| Testing                 | They wrote good, solid tests, and used testing to drive a better product. |



## Challenge

The challenge stat is a reflection of how well you are able to find work that puts you into your zone of proximal development (ZPD).

This is a weighted average that only uses retrospective data from the previous 6 cycles. Represented as a number between 1 and 10, with 7 representing your ZPD. This mapping is used to give meaning to the other numbers:

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

Where `recentChallengeStatsForProjects` = average of scores given for the challenge each project in last 6 cycles and `recentProjects` = your projects in the last 6 cycles.


## Project Reviews

The number of projects you've reviewed the completeness and quality of. Represented as an integer.

##### Formula

```
count(projectReviewsCompleted)
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

| Project      | Team size | Self estimate | Team estimates | Your Hours | Total Hours |
|:-------------|:----------|:--------------|:---------------|:-----------|:------------|
| #big-bees    | 3         | 50%           | 42%, 48%       | 30         | 80          |
| #red-rabbits | 4         | 28%           | 27%, 35%, 28%  | 25         | 120         |
| #tiny-tigers | 2         | 20%           | 30%            | 40         | 75          |

### Actual Contribution

Your actual contribution is the average of your team's estimates of what percentage of the project you contributed to. It includes your own estimate of your contribution. Represented as a percentage (0..100%).

In the above dataset, the player's actual contribution for the `#big-bees` project is the average of _all_ the estimates, so it would be equal to 46.67% ( (50% + 42% + 48%) / 3 ).

##### Formula

```
sum(projectContributionFeedbackFromTeam) / teamSize
```

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

Estimation accuracy reflects how accurate your estimations are relative to the consensus. This is a weighted average that only uses retrospective data from the previous 6 cycles. Represented as a percentage (0..100%).

One hundred percent is perfect accuracy: you estimate your contribution the same as your peers do. The closer this stat is to 100%, the more accurate your contribution estimates are.

Your estimation accuracy _per project_ is computed by first finding difference between self- and team-estimated contribution for that project, and then using the [absolute value][absolute-values] of that difference. Finally, this number is subtracted from 100% (so that a perfect score would be 100%, not 0%). So the estimation accuracy stats for the above projects would be:

| Project      | Estimation Accuracy                          |
|:-------------|:---------------------------------------------|
| #tiny-tigers | 100% - abs(20% - 30%) = 100% - 10% = **90%** |
| #big-bees    | 100% - abs(50% - 45%) = 100% - 5% = **95%**  |
| #red-rabbits | 100% - abs(28% - 30%) = 100% - 2% = **98%**  |

Based on these projects, the _overall estimation accuracy stat_ is 94.33% (average of [90%, 95%, 98%]).

##### Formula

```
100 - absolute(selfEstimatedContribution - teamEstimatedContribution)
```

## Estimation Bias

Estimation bias reflects whether you tend to over- or under-estimate your contribution. This is a weighted average that only uses retrospective data from the previous 6 cycles. Represented as a +/- percentage (-100%..100%).

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

##### Formula

```
selfEstimatedContribution - teamEstimatedContribution
```

## Time Dedication per Cycle

Average hours per week you spent contributing to team projects. Think of these as "billable" hours.

##### Formula

```
sum(cycleHoursLogged) / count(cyclesCompleted)
```

Where `cycleHoursLogged` = the set of hours you worked in each cycle and `cyclesCompleted` = the cycles during which you worked on a project.

[game-objectives]: ./Boundaries.md#objectives
[absolute-values]: http://www.coolmath.com/algebra/18-absolute-value-equations-inequalities/01-absolute-values-01
[elo-rating-wiki]: https://en.wikipedia.org/wiki/Elo_rating_system
[cos-dynam-tensions]: http://cos.learnersguild.org/Dynamic_Tensions/
