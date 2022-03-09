### Creating pull requests
You can create the pull requests from Github portal or you can install gh cli on local machine and then create and merge the pull requests from local machine itself. But, this level of privilege may not be provided to individual developers.

https://cli.github.com/

Install the gh cli
```
gh auth login
```
Follow the instructions to set up cli.

Create the pull request
```
git checkout feature1
gh pr create
#or
gh pr create --base main --title "My first cli PR" --body "Raising a new PR"
```

#### Other examples
```
gh pr create --title "The bug is fixed" --body "Everything works again"
gh pr create --reviewer monalisa,hubot  --reviewer myorg/team-name
gh pr create --project "Roadmap"
gh pr create --base develop --head monalisa:feature
gh pr create --draft
gh pr create --web
```

#### More examples
```
gh issue list
gh issue view 10
gh issue create
gh repo create some-org/another-repo
gh repo clone some-org/some-other-repo
```

#### Review the PRs
```
gh pr status
gh pr list
```

#### Switch to the PR’s branch based on PR number
```
gh pr checkout 123
gh pr view 123 --web
```

#### Approve the pull request of the current branch
```
gh pr review --approve
```

#### Leave a review comment for the current branch
```
gh pr review --comment -b "interesting"
```

#### Add a review for a specific pull request
```
gh pr review 123
```

#### Request changes on a specific pull request
```
gh pr review 123 -r -b "needs more work"
```

