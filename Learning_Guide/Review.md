# Review Guide

## Preparing your project for final review

You first need to find out the commit hash for the first commit in the repository, which you can do with:

```
$ git rev-list --all | tail -1
ec2287e5837386c54fbd082021530aa18c0dcf18
```

In the example above the hash is ```ec2287e5837386c54fbd082021530aa18c0dcf18```, but this will be different for you. Now, create an empty branch containing only that commit:

```$ git branch empty ec2287e5837386c54fbd082021530aa18c0dcf18```

This will create, but not switch to, the empty branch. Next push your empty branch to GitHub:

```$ git push origin empty```

Go to your repository on GitHub and click on the 'Pull Request' button at the top right of the window:

![Pull Request](/images/pull_request_1.png)

Then set it up so that you are pulling the changes from master into empty, as follows:

![Pull Request](/images/pull_request_2.png)

You can now enter a title and message for the pull request. Make sure to put your project team name, and goal number in the message. If you make changes to master, you can simply push the changes to GitHub as usual:

```$ git push origin master```

which should cause the new commits to appear in the pull request.

## Review Checklist

- [ ] Learning Contract is in place
- [ ] Timing of learning Contract
- [ ] Learning contract was reviewed on day one
- [ ] Specs are clear
- [ ] Quality rubric is clear
- [ ] Git ignore file
- [ ] README.MD file
- [ ] License file
- [ ] Clone, and run project locally and verify all features are complete
- [ ] Run test suite locally
- [ ] Find Pull Request from "Empty" branch and review code quality
- [ ] Log quality and completeness in Echo
- [ ] Once the review is complete, you can just close the pull request (without merging), and keep the empty branch for future reviews.
