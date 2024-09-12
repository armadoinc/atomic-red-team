## Description
This document provides ARMMADO employees with the necessary steps to keep their local master branch synchronized with the forked repository at https://github.com/armadoinc/atomic-red-team/. It ensures feature branches are created from an up-to-date master branch before submitting pull requests (PRs) to the upstream Red Canary repository.

## Objective
This process ensures that your master branch is synchronized with Red Canary's master branch before creating a feature branch. The objective is to keep the master branch in sync, allowing for the smooth creation of new feature branches.

## Instructions

Submitting a PR with the `git` command line tool for [Windows](https://git-scm.com/download/win), [Linux](https://git-scm.com/download/linux) and [macOS](https://www.atlassian.com/git/tutorials/install-git).

Use the following git commands to clone and set up your repository before submitting a PR to Red Camary's atomic-red-team repository.

```bash
# Clone your fork of the Red Canary Atomic Red Team™ Repository
git clone https://github.com/<your-github-username>/atomic-red-team.git
​
# Change directories into your cloned repository
cd atomic-red-team
​
# Set your origin (your fork) and your upstream (Red Canary's repo)
# You have to do this every time you re-clone your repo, which likely is not often
git remote set-url origin https://github.com/<your-github-username>/atomic-red-team.git
git remote add upstream https://github.com/redcanaryco/atomic-red-team.git
​
# Update your forked master branch to match Red Canary's repo
# Do this right before creating a feature branch and working on it
git checkout master
git fetch --all
git rebase upstream/master
git push origin master
​
# Create a new branch from master to work on your new feature and switch to it (replace <branch-name> with whatever name you would like to use for your branch)
git checkout -b <branch-name>

# Add and commit your new/modified files to your local branch (not on the web), use "git status" to see what is new/changed
git add /path/to/new/changed/file.yaml    # repeat for multiple files as needed
git commit -m "This should be a short message describing what changed."

# Push the changes out to your repository residing in GitHub on the web
# The output from this command will tell you where to go on the web to submit the PR
git push origin <branch-name>
```
