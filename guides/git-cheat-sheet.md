# Git cheat sheet

{% page-ref page="command-line-cheat-sheet.md" %}

## Create a repo

| Command | Description |
| :--- | :--- |
| `git clone SOME_GIT_URL` | Clone \(download a copy of\) the repo at SOME\_GIT\_URL to the current folder |
| `git clone https://github.com/YOUR_GITHUB_USERNAME/SOME_REPO.git` | Clone a repo from your github account |
| `git init` | Turn the current folder into a new empty git repo |

## Checking what's going on

| Command | Description |
| :--- | :--- |
| `git status` | List changed and staged files in the current repo |
| `git diff` | Show the **diff**erence between the last commit and the files in your repo right now |
| `git log` | See all the previous commits |

## Making a commit & syncing with a remote \(e.g. GitHub\)

| Command | Description |
| :--- | :--- |
| `git add file1.txt file2.txt` | Add the two files to the stage so they're ready to commit |
| `git add .` | Add the current folder \(and everything in it\) to the stage so it's ready to commit |
| `git commit -m 'describe the changes here'` | Commit the staged files - add a descriptive message of what changed and why! |
| `git push` | Send all the new commits from your local repo to the remote one - e.g. GitHub |
| `git pull` | Get all the new changes/commits from GitHub |



