---
layout: post
author: aaron
---
# Common Git Scenarios

For a comprehensive intro guide to Git commands, please refer to **[this guide (Introduction to Git)](https://www.notion.so/zarkom/Introduction-to-Git-ac396a0697704709a12b6a0e545db049#3f395b09dee24f738fea3ee6f14ed220)**. In the meantime, you can refer to some commonly used Git commands that you may encounter throughout your projects:

## Scenario: After making changes on a 'test branch', you now want to push to your team's Github repo:

- Before making any changes on your Git repository, you would want to check the state of the working directory and the 'staging area'. `git status` allows you to see what files are currently 'staged', 'unstaged', and 'untracked'.
```
git status
``` 

```
// On branch main
// Your branch is up to date with 'origin/main'.

// Changes not staged for commit:
//  (use "git add <file>..." to update what will be committed)
//  (use "git restore <file>..." to discard changes in working directory)
//	modified:   2022-08-25-git Commands.md

// no changes added to commit (use "git add" and/or "git commit -a")
```

- You see that there are some files that have been modified, but are not yet staged for the next commit. If so, you can add these updated files onto staging area by using `git add [directory or file name]`. Note that you can use `.` after `git add` if you want to simply add ALL files onto the staging area. This way, you do not need to specify the name of each file you want to add to the staging area. 
```
git add .
```

<img src="https://res.cloudinary.com/practicaldev/image/fetch/s--M_fHUEqA--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/128hsgntnsu9bww0y8sz.png"  width="500px" height="300px">


- As you can see from the Git flowchart above, you would now want to **'commit'** your staged changes back to the repository. You will also need to add a brief, but detailed comment about the changes that were made after the `-m` flag. These messages will better help you and your collaborators figure out what changes you made... especially a few months down the road, so keep them concise, but informative!
```
git commit -m “Fixed log-in button.”
```

- Now it is time to merge back to the remote repository (eg. on Github). But before doing this, we will need to ensure our current repo is up-to-date with the remote repo. For eg. During the time you were making changes, your teammates could have updated the remote repo before you had the chance to merge your changes! 

- Let's first navigate back to the **'main'** branch, which is our local representation of what the remote repo looked like at the time of the last **'pull'**. We navigate back with the `checkout` command, followed by the branch we want to go to, `main`.

```
git checkout main
```
```
// Switched to branch 'main'
// Your branch is up to date with 'origin/main'.
```
- Before we use the `pull` command, let's use `fetch` to see the differences between our local repo vs the remote repo, without overwriting any existing local code. (`fetch` downloads objects to the local machine without overwriting existing local code in the current branch.)

```
git fetch
```

- If the terminal does not return anything, it means we are good to go, and we can skip to the `git checkout test-branch` stage.

- If `git fetch` indicates there were changes, we need to do a `git pull` first to ensure our local repo is up-to-date with the remote repo.

```
git pull
```

- Now that our main branch is up-to-date, we can now navigate back to our 'test branch', so we can merge the changes back to our main branch (in our local repo).

```
git checkout test-branch
```

- `git merge` here will merge our changes from our 'test branch' to our 'main' branch.
```
git merge main
```

- Assuming there are no 'version conflicts' from the main branch (Eg. if updates were made in the recently pulled version), we can finally use `git push` to 'push' our changes to the remote repo on Github.
        
```
git push --set-upstream origin test-branch
```

Lastly, if there are any merge conflicts, we can go onto our Github repo, and click on **Create Pull Request → Merge Pull Request → Confirm Merge** to confirm the merge.

Congrats! You have completed your first Git push.