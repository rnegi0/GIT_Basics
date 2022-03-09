https://cloudxlab.com/assessment/create/slide?playlist_id=435&slide_id=4931

You can merge the changes you made in one branch into another branch. You also need to resolve any conflicts if they arise.

Consider this typical scenario.
You created a feature branch from the master branch, made a few changes in your feature branch, committed, and pushed to the git repo.
Meanwhile, some other changes have been pushed to the master branch by other developers.
Now, let's say you want those additional changes from master branch to be merged into your feature branch.
And eventually, you have to merge your feature branch into the master branch.

Initial Master - A -> B -> C
Initial Feature - A -> B -> C

After changes:
Current Master - A -> B -> C -> M1 -> M2
Current Feature - A -> B -> C -> F1 -> F2


You can do this in 3 ways:

1. Merge commits - it will keep all the commits history of the feature branch and move them into the master branch by adding an extra dummy commit (called as merge commit) at the end.

git checkout feature
git merge master

OR

git merge feature master

At this time, feature branch will look like:

A -> B -> C -> M1 -> M2
               F1 -> F2 -> (new dummy merge commit)
               
Create pull request from feature to master
Merge the pull request

git checkout master
git merge feature

At this time, master branch will look like:

A -> B -> C -> M1 -> M2 -> (new dummy merge commit)
               F1 -> F2

2. Rebase and merge - it will append all the new commits history of the master branch at the end of the feature branch without adding any extra dummy commit.

git checkout feature
git rebase master

At this time, feature branch will look like:

A -> B -> C -> M1 -> M2 -> F1 -> F2

Note - Interactive rebase also allows for squash

Now merge the feature into master by creating pull request or via commands.

git checkout master
git merge feature


3. Squash and merge - it will group all the commits of the feature branch into one commit and then add that at the end of the master branch by adding an extra dummy commit.

git checkout feature
git merge --squash master

At this time, feature branch will look like:

A -> B -> C -> F1 -> F2 -> (new squash merge commit)

But, note that you can still not merge feature to
