---
layout: post
author: aaron
---
# Git Commands

For a comprehensive intro guide to Git commands, please refer to [this guide](https://www.notion.so/zarkom/Introduction-to-Git-ac396a0697704709a12b6a0e545db049#3f395b09dee24f738fea3ee6f14ed220) (Introduction to Git). In the meantime, you can refer to some commonly used Git commands that you may encounter throughout your projects:

#### Scenario: After making changes on a 'test-branch' and want to push to Github repo:

- `git status`: to check the status of your git
- `git add .`: ...
- `git commit -m “commit message”`: ...

- `git checkout masterbranch`:...
- `git fetch`: to see differences first...
- `git pull`: ....
- `git checkout test-branch`:...
- `git merge masterbranch`: (from Test branch)

- Resolve all conflicts locally first (in **VSCode** → **Source Control**) - sit with teammate to go over (include screenshot), if there are version conflicts.
        
- When everything is resolved: `git push`
- `git push --set-upstream origin test-branch-6`
Then go on github repo, and **Create Pull Request → Merge Pull Request → Confirm Merge**... (if there are merge conflicts)


#### Scenario: Installing MongoDB
- `git remote add origin [https://github.com/vasansr/pro-mern-stack-2.git](https://github.com/vasansr/pro-mern-stack-2.git)`
- `git fetch`
- `git checkout origin/06.06-writing-to-mongodb`
- `apt install gnupg`
- `curl -fsSL https://www.mongodb.org/static/pgp/server-4.4.asc | apt-key add -`
- `echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.4 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-4.4.list`
- `apt update`
- `apt install mongodb-org
- `mkdir -p /data/db`
- `screen mongod` to run mongodb in the background
- `ctr-a + d` : to detach
- `git branch`
- `git branch -r`: to view all branches
- `git checkout origin/06.06-writing-to-mongodb`
