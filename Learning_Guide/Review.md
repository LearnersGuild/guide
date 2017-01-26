# Review Guide

## Preparing your project for final review

**Step 1:** You first need to find out the commit hash for the first commit in the repository, which you can do with:

```
$ git rev-list --all | tail -1
ec2287e5837386c54fbd082021530aa18c0dcf18
```

In the example above the hash is ```ec2287e5837386c54fbd082021530aa18c0dcf18```, but this will be different for you.

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

**Step 7:** Repeat steps 2 through 6 but use another branch ```empty2```. This sets up your project to reviewed by two different reviewers.

**Step 8:** Once someone has reviewed your code, be sure to go over their comments, engage in a discussion, and thank them!


## How to Review a Project

To begin reviewing a Project, got to [prrr](http://prrr.apps.learnersguild.org) and claim a PR.

Once you've claimed the PR, make sure that the project/code is within your technical level to usefully review. If it isn't, unclaim it, wait a couple of minutes and claim another one.

When you are reviewing a project, you are practicing reading, understanding and commenting on code that someone else wrote. This is a critical skill for a software developer to practice and master. Reading, reviewing and commenting on other developers' code is 30% to 50% of the job! Sometimes more. It's also a great way to learn. 

There are a few steps that you should take to make sure that your review is useful and thorough.

- [ ] Learning Contract is in place by day one
- [ ] Learning contract was reviewed in PR on day one
- [ ] Project specs are clear, and completeness is well defined
- [ ] Quality rubric is clear, and quality is well defined
- [ ] Git ignore file
- [ ] README.MD file
- [ ] License file
- [ ] Clone, and run project locally and verify all features are complete
- [ ] Run test suite locally
- [ ] Find Pull Request from "Empty" branch and review code quality
- [ ] Log quality and completeness in Echo. 1. Be rigorous. Don't give people the benefit of the doubt. If a spec is incomplete or unfulfilled, don't count it as complete. Give honest feedback. It's the only way we learn.
- [ ] Once the review is complete, you can just close the pull request (without merging), and keep the empty branch for future reviews.
