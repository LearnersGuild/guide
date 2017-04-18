# Goal Completeness Review

When you are reviewing a project for completeness, you are holding the project team accountable to the specs.

## How to Review a Project's Completeness


- Go to https://game.learnersguild.org to get the artifact for the project
- If there is no artifact, the completeness score should be 0
  - If you think this is an error, feel free to DM the team and ask them to set it
- Verify each spec is complete one by one
  - __Be rigorous & do not give people the benefit of the doubt__. If a spec is incomplete or unfulfilled __DO NOT__ count it as complete and __DO NOT__ give them partial credit
  - Ask clarifying questions of the author(s) if you're unsure about something
- If applicable
  - clone and run project locally to verify all specs are met
  - run the test suite locally
- If the specs aren't clear, and it's difficult to determine completeness from them, [write a PR against the spec](/Learning_Guide/Goals/Improvement.md) asking a goal librarian to clarify the specs.
  - Feel free to suggest the changes you think would the specs more clear next time.
- Determining the completeness score:
  - If the specs are weighted:
    - completeness score = the sum of the weights for each spec they met
  - If the specs are not weighted:
    - completeness score = (number of checked specs / number of specs) * 100
- Report your score in slack by using the this command: `/review [team-name] [score]`
