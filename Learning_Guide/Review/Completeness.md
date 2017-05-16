# Goal Completeness Review

When you are reviewing a project for completeness, you are holding the project team accountable to the specs.

## How to Review a Project's Completeness


- Go to https://game.learnersguild.org to get the artifact for the project
- If there is no artifact, the completeness score should be 0
  - If you think this is an error, feel free to DM the team and ask them to set it
- Ensure they committed their specs on Monday
- Ensure those specs did not change mid-week
- Ensure they made multiple commits each day throughout the week
- Verify each spec is complete one by one
  - __Be rigorous & do not give people the benefit of the doubt__. If a spec is incomplete or unfulfilled __DO NOT__ count it as complete and __DO NOT__ give them partial credit
  - Ask clarifying questions of the author(s) if you're unsure about something
- If applicable
  - clone and run project locally to verify all specs are met
  - run the test suite locally
- If the specs aren't clear, and it's difficult to determine completeness from them, [write a PR against the spec](/Learning_Guide/Goals/Improvement.md) asking a goal librarian to clarify the specs.
  - Feel free to suggest the changes you think would make the specs more clear
- Determining the completeness score:
  - Go to the jsdev link for the goal and check each spec as you confirm them
  - Once you have confirmed all the specs are or are not met, counting completeness:
    - Take a screenshot to send in a DM to the team members
    - Stretch specs are **NOT** counted toward completeness. **DO NOT** count them.
    - If the specs are weighted:
      - completeness score = (the sum of the weights for each spec they met / the sum of all specs) * 100
    - If the specs are not weighted:
      - completeness score = (number of checked specs / number of specs) * 100
- Report your score in slack by using the this command: `/review [team-name] [score]`
- Also send the final score and a screenshot of the specs to the team members in a group DM
- If they argue that a spec you did not check should in fact be checked, it is okay to have a conversation and change the score you've given *IF* you missed something. But remember __Be rigorous & do not give people the benefit of the doubt__.
