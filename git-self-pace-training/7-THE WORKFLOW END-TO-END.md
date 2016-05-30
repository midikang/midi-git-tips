Updating Our Workflow
========
So far you've learned the most-used Git commands.

In this section, we'll show you how to do certain things locally instead of on GitHub, as well as some shortcuts to make you even faster when using the command line.

Options for Creating a Repository
========
All of the work we do in Git and GitHub happens inside of a repository. There are two ways to get started working with a new repository. You can:

Clone the repository from a remote.
- Initialize Git in an existing local directory.
- Since this class is designed to teach you how to use Git and GitHub effectively, we will focus on how to structure our work to support collaboration.

If I want to collaborate with you on a project then I will start a repository on GitHub. Let's discuss some best practices for GitHub repositories now.

Create and Clone the Repository
========
1. Create a new repository on GitHub.
2. Add a README.md file to the repo.
3. Clone the new repo to your desktop.

Creating Branches Locally: Recap
===========
git branch shows which branch you're on locally, and which other local branches exist.
git branch <new_branchname> creates a new local branch.
You still must check out this new branch to edit it. git checkout <new_branchname>

Create a Local Branch
====

Create a local branch using your username as follows: githubusername-branch.


Workflow Review: Recap
========
- git add . adds all modified or new files to be committed, so you don't have to write out each file.
- You can write your commit message along with your commit command using the syntax: git commit -m "<commit_message>".
- You should then push your changes up to GitHub. git push -u origin <branch_name> will push your local branch changes to a branch with the same name on GitHub, as well as set a setting such that in the future, git push alone will complete the same command.
- Once this is finished, you must create a pull request on GitHub, and merge it on GitHub once it's completed.

Workflow Review
========
1. Create a new file on your branch.
2. Add the file to staging and commit it locally.
3. Push your file to the remote.
4. Create a pull request on GitHub.
5. Merge your changes into Master.

Pulling Changes: Recap
========
- When the remote repository has been changed (such as after someone else's pull request is merged), your local repository will not be updated until you choose for it to be.
- The command git pull will make your local working branch up to date with the remote version of that same branch.
- This will not delete local branches that have been deleted on the remote repo.
- To delete local branches that do not have a remote counterpart, use the git branch --merged command to list all such local branches, and then git branch -d <branchname> to delete specific local branches.
