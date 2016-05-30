# Cloning a Repository
Part of what makes git such a well-loved VCS is that it easily lets everyone on the team have their own local working repository. It's expected that everyone will work on their own computer, and sync changes they've made with each other only when they need to.

But first, we have to make a local copy of your repository. To do this, we have to "clone" the repository that you have hosted on GitHub.

When you clone a GitHub repository you are creating a copy of everything in that repository, including its history. This is one of the benefits of a distributed VCS like git—rather than being required to query a slow centralized server to review the commit history, queries are run locally and are lightning fast.

![Clone a repository](https://raw.githubusercontent.com/wheelhouseio/curriculum-github/master/images/clone-diagram.png)

# Cloning a Repository: Recap

* Start a new branch on GitHub to work on.
* Copy the clone URL on GitHub.
* Using the command line, cd to the directory that you want to put your local repo in.
* Type git clone <clone_url>.
You might be prompted for your password. You should enter your GitHub password at this point.
* cd into the new cloned repo and type git status.
* git branch will show you the available branches. Only master appears.
* git branch -a will show all the remote branches.
* git checkout <branchname> will create a local branch that matches the remote branch. All edits you make locally * with be applied to that branch until you checkout another one.


# Cloning a Repository

Type the Git command you would use to clone the repository located at the following remote address 
[https://github.com/githubteacher/sample-repo.git]

 git clone https://github.com/githubteacher/sample-repo.git
 


# Checking Out a Branch
QUESTION
Type the Git command you would use to switch to a branch named more-bio-changes that you created on GitHub before cloning the repository.

YOUR ANSWER
git checkout more-bio-changes

Correct!

Good job! You included the appropriate git command and the URL. You are ready to work locally.

Thanks for your response. You may continue to the next screen.


# The Two Stage Commit
When you work locally, your files exist in one of four states. They are either untracked, modified, staged, or committed.

An untracked file is one that is not currently part of the version controlled directory—such as any new files or files whose names have been changed.

Modified files are any files that you have edited and saved since the last time you committed.

Untracked and modified files exist in your working directory.
![untracked to staging](https://raw.githubusercontent.com/wheelhouseio/curriculum-github/master/images/two-stage-commit-c.png)
![staging to committed](https://raw.githubusercontent.com/wheelhouseio/curriculum-github/master/images/two-stage-commit-d.png)

# The Two Stage Commit: Recap
- git status lets you see which files have been changed since the last commit.
- git add <filename> adds that file to the staging area.
- git add . adds all the changed and untracked files to staging.
- git commit will submit all those file changes under one unit of work.
This also opens your default text editor (as set earlier in this lesson) for you to add a commit message.
This commit will happen locally, and only on the checked out branch. If you check out another branch, the changes will no longer show in that file.


# Pushing Changes
Now that you've committed files locally, it's time to make sure that your remote repository also reflects those changes. So we'll push the files and version history up to GitHub.

![Push to GitHub](https://raw.githubusercontent.com/wheelhouseio/curriculum-github/master/images/push.png)
