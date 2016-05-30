Modifying Local Files: Recap
========
There is only one working and one staging area, so you can create a branch after you've changed or added a file, and still commit that file to the new branch.
git checkout -b "<new_branchname>" is a quick way to both create a new branch and check it out.
If you edit a file after git adding it, then when you commit only the changes made before the git add will actually be commited. You must git add it again in order to commit all the changes.

Modifying Local Files
========
1. Open your file and make a few changes.
2. Save the changes and add them to the staging area. Do not commit the changes yet.
3. Open the same file and make a few more changes.
4. Save the changes.
5. Run git status.

Comparing Local File States
========
In the last section, we made several changes to a local file, causing the file to appear in different stages of the commit process. The git diff command allows us to see what has changed in these different versions of our files. Let's explore some of these options now.

Viewing Local Diffs: Recap
========
git diff allows you to compare different versions of a file against each other.
On its own, git diff compares the working directory to the staged version of the file.
git diff --staged compares the staged version to the most recent commited version.
git diff HEAD combines the changes in your working and staged versions of the file, and compares them to the version of the file designated as HEAD (most often, the most recent commit).
git diff --color-words displays a word-by-word comparision rather than a line-by-line comparison, helpful for small changes.

Merging Local Changes: Recap
========
When performing a merge, you need to have checked out the branch you are merging into.
git merge <branchname_to_merge> will merge the branch locally.
To send the merge to the remote, simply git push. If you already have a PR for that branch open on GitHub, this will automatically close that PR.
You must still delete the branch separately on GitHub (in the PR window) and locally (using git branch -d <branchname>).

Merging Local Changes
========
1. Merge your local branch into master.
2. Push your changes to the remote.
3. Delete the local copy of your branch.

Viewing Project History: Recap
========
git pull updates the local directory to include all the changes made to the remote directory, even those done by other people.
git log provides a list of all of the commits on the current branch, with the most recent commit first.
Up and down arrows navigate, enter cycles through log entries, and q quits log viewing screen.
git log --oneline shows a smaller version of the log.
git log --oneline --graph shows a graph of the changes along with the one-line log.
git log --oneline --graph --decorate includes information about the branches and the head.
git log --oneline --graph --decorate --all also includes unmerged branches.
git log --stat tells you which files were included in each commit.
git log --patch shows the actual changes that were made in each commit as diffs.

Viewing Project History
========
1. View git log on your copy of the repository.
2. View git log --oneline on your copy of the repository.
3. View git log --oneline --graph --decorate --all on your copy of the repository.
