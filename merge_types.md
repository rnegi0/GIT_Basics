### Merge types

You can merge the changes you made in one branch into another branch in many. You also need to resolve any conflicts if they arise.

Consider this typical scenario.

You created a feature branch from the main branch, made a few changes in your feature branch, committed, and pushed to the git repo.
Meanwhile, some other changes have been pushed to the main branch by other developers.
Now, you want those additional changes from main branch to be merged into your feature branch.
And eventually, you have to merge your feature branch into the main branch either locally or on Github by creating a pull request.

Let's assume that below are initial commits.

Initial main - A -> B -> C

Initial Feature - A -> B -> C

After changes:

Current Main - A -> B -> C -> M1 -> M2

Current Feature - A -> B -> C -> F1 -> F2


You can do the merge using one of the three ways mentioned below. But, there may be other ways too.

#### 1. Merge commits - it will keep all the commits history of the feature branch and move them into the main branch by adding an extra dummy commit (called as merge commit) at the end.
```
git checkout feature
git merge main
```
OR
```
git merge feature main
```
At this time, feature branch will look like:

A -> B -> C -> M1 -> M2
               F1 -> F2 -> (new dummy merge commit)
               
Create pull request from feature to main
Merge the pull request
```
git checkout main
git merge feature
```
At this time, main branch will look like:

A -> B -> C -> M1 -> M2 -> (new dummy merge commit)
               F1 -> F2

#### 2. Rebase and merge - it will append all the new commits history of the main branch at the end of the feature branch without adding any extra dummy commit.
```
git checkout feature
git rebase main
```
At this time, feature branch will look like:

A -> B -> C -> M1 -> M2 -> F1 -> F2

Note - Interactive rebase also allows for squash

Now merge the feature into main by creating pull request or via commands.
```
git checkout main
git merge feature
```

#### 3. Squash and merge - it will group all the commits of the feature branch into one commit and then add that at the end of the main branch by adding an extra dummy commit.
```
git checkout feature
git merge --squash main
```
At this time, feature branch will look like:

A -> B -> C -> F1 -> F2 -> (new squash merge commit having changes of M1 and M2)

But, note that you can still not merge feature to main because your feature branch doesn't have main branch commits. So, squash merge is primarily useful when you are merging your feature branch into main as show below and you plan to delete the feature branch after that.
```
git checkout main
git merge --squash feature
```
At this time, main branch will look like:

A -> B -> C -> M1 -> M2 -> (new squash merge commit having changes of F1 and F2)

