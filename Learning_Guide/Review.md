# Review Guide

## Preparing your project for final review

**Step 1:** You first need to find out the commit hash for the first commit in the repository.

**If you are _NOT_ working on a forked repo**

```sh
$ git rev-list --all --author $(git config --get user.email) | tail -1
ec2287e5837386c54fbd082021530aa18c0dcf18
```

In the example above the hash is ```ec2287e5837386c54fbd082021530aa18c0dcf18```, but this will be different for you.

**If you are working from a forked repository**

1. In your forked repository
2. Click the number of commits in your repository
![Step 2 - Commits](/images/forked_repo_step2.png)
3. Look for the last commit made by the original repository owner
4. Click the commit number on the right
![Step 3 & 4](/images/forked_repo_step3and4.png)
5. Copy the commit number in the upper right hand corner
![Step 5](/images/forked_repo_step5.png)


**Step 2:** Create an empty branch containing only that commit:

```$ git branch empty ec2287e5837386c54fbd082021530aa18c0dcf18```

This will create, but not switch to, the empty branch.

**Step 3:** Push your empty branch to GitHub:

```$ git push origin empty```

**Step 4:** Go to your repository on GitHub and click on the 'Pull Request' button at the top right of the window:

![Pull Request](/images/pull_request_1.png)

Then set it up so that you are pulling the changes from master into empty, as follows:

![Pull Request](/images/pull_request_2.png)

**Step 5:** You can now enter a title and message for the pull request. Make sure to put your project team name, and goal number in the message. If you make changes to master, you can simply push the changes to GitHub as usual:

```$ git push origin master```

which should cause the new commits to appear in the pull request.

**Step 6:** Submit a link to your pull request to [prrr](http://prrr.apps.learnersguild.org)

**Step 7:** Repeat steps 2 through 6 **two more times**. Use two other branches ```empty2``` and ```empty3```. This sets up your project to reviewed by three different reviewers.

**Step 8:** Once someone has reviewed your code, be sure to go over their comments, engage in a discussion, and thank them!


## How to Review a Project

To begin reviewing a Project, got to [prrr](http://prrr.apps.learnersguild.org) and claim a PR.

Once you've claimed the PR, make sure that the project/code is within your technical level to usefully review. If it isn't, unclaim it, wait a couple of minutes and claim another one.

When you are reviewing a project, you are practicing reading, understanding and commenting on code that someone else wrote. This is a critical skill for a software developer to practice and master. Reading, reviewing and commenting on other developers' code is 30% to 50% of the job! Sometimes more. It's also a great way to learn.

There are a few steps that you should take to make sure that your review is useful and thorough.

- Project specs are clear, and completeness is well defined
- Quality rubric is clear, and quality is well defined
- Git ignore file
- README.MD file
- License file
- Clone, and run project locally and verify all features are complete
- Run test suite locally
- Find Pull Request from "Empty" branch and review code quality
- Log quality and completeness in Echo. 1. Be rigorous. Don't give people the benefit of the doubt. If a spec is incomplete or unfulfilled, don't count it as complete. Give honest feedback. It's the only way we learn.
- Once the review is complete, you can just close the pull request (without merging), and keep the empty branch for future reviews.
- Check [prrr](http://prrr.apps.learnersguild.org) for more pending reviews and claim them. **You should aim to claim and complete two thorough reviews per review period**

**You should aim to do a thorough review of 2 projects** individually, OR **pair on reviewing three projects**.

If there are no projects to review on prrr, then find [already done reviews](http://prrr.apps.learnersguild.org/all) and review them.

**Once your done with a project code review, use `/review #team -c -q` in echo to review completeness and quality.**

## Guidelines for OSS projects

If you worked on an OSS project, a gist with links to the issues you worked on should be your project artifact. Since every PR has been already reviewed by your project lead, you should just ping your project lead to do a /review in echo. No need to prepare review branches, and no need to use Prrrr, and you won't get two other reviews from two different coaches.



## Guidelines for Coaches

For the first half hour or so of the review period, there won't be any reviews to review, so:

- help people setup their projects for reviews
- if you have the bandwidth, claim a review off of [prrr](http://prrr.apps.learnersguild.org) and complete it (see checklist above).

For the rest of the review period **focus your efforts on reviewing the reviews:**

- Go through the list of project reviews and give the reviewers feedback on their comments.
- Make sure to add your completeness and quality review for the project, even if you're reviewing the review. **In the future, we'll use coach's review scores to give other reviewers feedback about their review accuracy.**
- Use echo (or a google spreadsheet) to co-ordinate with other coaches about which review you're reviewing, so that the effort is spread across as many reviews as possible and we don't end up in a situation where one review is reviewed by multiple coaches while others are ignored.
