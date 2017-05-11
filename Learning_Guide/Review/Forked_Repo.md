# Preparing your Forked Repo for review

If did not fork a repo [click here](/Learning_Guide/Review/initial-repo.md)

**Step 1**: Make a pull request back to the original repository

1. Go to your repository on GitHub
2. Click `New pull request`
3. Ensure that the `base fork` is pointed to the original repo
   - which is probably a GuildCrafts repo
4. Ensure the base is `master`
5. Ensure the `head fork` is your fork
6. Ensure that you compare the branch with all of your work \(hopefully master\)
  - if you did your work in a non-master branch, use that branch
7. Click  `Create pull request`
8. **Look at the `Files changed` for your PR** and ensure it shows all of and only your code

**Step 2**: Set your artifact url in echo

```
/project set-artifact hedonistic-badger https://github.com/pllearns/core-algorithms/pull/12
```
