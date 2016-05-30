9: FIXING COMMON ISSUES WITH GIT
========
 
Creating a Repository on the Command Line
========
You'll only be working locally for this section, so you won't need to interact with GitHub. Thus, it's a good chance to learn how to use Git on the command line to create a new local repo.

On the next slide you'll learn how to use git init to create a local repository, and then we'll use that repo in the rest of this lesson.

Creating a Repository on the Command Line: Recap
========
To create a project from scratch, type git init <directoryname>.
This creates the directory as a subdirectory of the current location, and initializes a repo there.
You will have to create your README.md file manually.

Creating a Repository on the Command Line
========
1. Initialize a new git repository.
2. Create a README.md file and commit it to the repository.
3. Create and commit a file called badname.md. You will use this later.
4. Create a branch in your new repository.

git init
========
TEMPLATE DIRECTORY

The template directory contains files and directories that will be copied to the $GIT_DIR after it is created.

The template directory used will (in order):

The argument given with the --template option.

The contents of the $GIT_TEMPLATE_DIR environment variable.

The init.templatedir configuration variable.

The default template directory: /usr/share/git-core/templates.



EXAMPLES
========
Start a new Git repository for an existing code base
$ cd /path/to/my/codebase
$ git init      <1>
$ git add .     <2>
prepare /path/to/my/codebase/.git directory

add all existing file to the index

My steps
====
- mkdir midi-local-github
- git init midi-local-github/
  
  Initialized empty Git repository in d:/GitMidi/midi-local-github/.git/
  
  (use "git rm --cached <file>..." to unstage)
-  git rm --cached README.md
  


Handling Merge Conflicts: Recap
========
When you have a merge conflict, type git status and look for "unmerged paths" to see which files are creating the merge conflict.
Open the file in your text editor. You will see some lines that look like the following:

<<<<<<<< HEAD
Some text here.
========
Different text here.
>>>>>>>> merge-me
The text above and below the equal signs are what is causing the merge conflict. They appear on the same line but are different text.

Decide how you want to resolve the conflict, and once that's completed delete the merge markers. Save and close your text editor.

git status will show that the files are no longer in conflict, but that you are in the middle of a merge. git add the file and then git commit it, and the merge will then automatically complete.


Handling a Merge Conflict
========
1
Clear your merge conflict.


Renaming and Moving Files: Recap
========
When moving files, use the command git mv rather than just the mv command.
The syntax for this is git mv <filename> <new_directory>/<filename>.
git mv automatically adds the file to the staging area after it is moved, so it can be commited right away.
Just as with mv, you can use git mv to rename a file like so: git mv <filename> <new_filename>.

Renaming Files
========
1. Rename the badname.md file you created earlier to goodname.md.
2. When you are finished, commit your file changes.

My Steps
========
- git mv badname.md goodname.md


 $ git status
 On branch merge-me
 Changes to be committed:
   (use "git reset HEAD <file>..." to unstage)
 
         renamed:    badname.md -> goodname.md
         
Making Commits
========
1
Open your goodname.md file and add some text.
2
When you are finished, commit your file changes.
3
Re-open your goodname.md file and make changes to the original text.
4
When you are finished, commit your file changes.


Reverting Commits: Recap
========
When reverting, you revert a specific commit.
Find that commit, and copy the first several characters of the SHA-1 hash.
git revert <commit_hash> will create a new commit that is the exact opposite of the commit you're reverting.

Reverting Your Commit

1
Revert the last commit you made on goodname.md.


My steps
========
Midi_Kang@midi /d/GitMidi/midi-local-github (merge-me)
$ git log --oneline --graph --decorate
* 810bdab (HEAD, merge-me) remove 'This is goodname.md file now'
* 2f4b466 add 'This is goodname.md file now'
* fe1c9e6 change badname.md to goodname.md
* 1b23972 Add conflict.md
* 61ba1b9 (midikang-branch, master) Add badname.md
* a80d98c Initial project

Midi_Kang@midi /d/GitMidi/midi-local-github (merge-me)
$ git revert 2f4b466
error: could not revert 2f4b466... add 'This is goodname.md file now'
hint: after resolving the conflicts, mark the corrected paths
hint: with 'git add <paths>' or 'git rm <paths>'
hint: and commit the result with 'git commit'

Midi_Kang@midi /d/GitMidi/midi-local-github (merge-me|REVERTING)
$ git status
On branch merge-me
You are currently reverting commit 2f4b466.
  (fix conflicts and run "git revert --continue")
  (use "git revert --abort" to cancel the revert operation)

Unmerged paths:
  (use "git reset HEAD <file>..." to unstage)
  (use "git add <file>..." to mark resolution)

        both modified:   goodname.md

no changes added to commit (use "git add" and/or "git commit -a")

Midi_Kang@midi /d/GitMidi/midi-local-github (merge-me|REVERTING)



Making Commits
=======
1. Create a file called onefile.md. Stage this file.
2. Create a file called twofile.md. Stage this file.
3. Commit the two files.
4. 

Fixing Bad Commits: Recap
========
The command git commit --amend will add whatever is in your staging area to your last commit, and allow you to edit that commit message.

Using Commit Amend
========
1. Create a new file called threefile.md.
2. Add threefile.md to your previous commit.
3. 

Unstaging Files: Recap
========
git reset HEAD <filename> will remove a file from the staging area, putting it back in your working directory.


Git Reset
========
Sometimes we are working on a branch and we decide things aren't going quite like we had planned. We want to reset some, or even all, of our files to look like what they were at a different point in history. We can do that with git reset.

Remember that there are three different snapshots of our project at any given time. The first is the most recent commit. The second is the staging area (also called the index). The third is the working directory (i.e. whatever you currently have saved on disk). The git reset command has three modes, and they allow us to change some or all of these three snapshots.

It also helps to know what branches technically are: each is a pointer, or reference, to the latest commit in a line of work. As we add new commits, the currently checked-out branch "moves forward," so that it always points to the most recent commit.


Git Reset Modes
========
The three modes for git reset are: --soft, --mixed, and --hard. For these examples, assume that we have a "clean" working directory, i.e. there are no uncommited changes.

git reset --soft <my-branch> <other-commit> moves <my-branch> to point at <other-commit>. However, the working directory and staging area remain untouched. Since the snapshot that <my-branch> points to now differs from the index's snapshot, this command effectively stages all differences between those snapshots. This is a good command to use when you have made a large number of small commits and you would like to regroup them into a single commit.

With the --mixed option, Git makes <my-branch> and the staging area look like the <other-commit> snapshot. This is the default mode: if you don't include a mode flag, Git will assume you want --mixed. --mixed is useful if you want to keep all of your changes in the working directory, but change whether and how you commit those changes.

--hard is the most drastic option. With this, Git will now make all 3 snapshots -- , the staging area, and your working directory -- look like they did at <other-commit>. This can be dangerous! We've assumed so far that our working directory is clean. If it is not, and you have uncommited changes, git reset --hard will delete all of those changes. Even with a clean working directory, use --hard only if you're sure you want to completely undo earlier changes.

Let's take a look at each of these options in action.

![git reset modes](https://raw.githubusercontent.com/wheelhouseio/curriculum-github/master/images/reset-modes.png)



Git Reset Options: Recap
========
git revert reverts a specific commit. git reset resets git to a specific commit.
git reset --soft <to_commit> resets git to a specific commit, and puts the commits you're resetting into the staging area where they can be easily re-committed.
git reset --mixed <to_commit> resets git to a specific commit, and puts the commits you're resetting into the working directory so you can edit them directly.
git reset --hard <to_commit> resets git to a specific commit, and deletes the commits you're resetting.
Just like with git revert you can use the commit ID, or you can use the syntax HEAD~<number>. The number you put will be the number of commits backwards from the current HEAD that git will move the new HEAD to.
You can always use git log to see all your previous history to know where to reset to.


Discarding Changes in Modified Files: Recap
========
You can remove changes in the working directory using git checkout.
This is destructive! You will throw away the changes and not be able to get them back.
git checkout --<filename> is the syntax. The -- lets Git know you're talking about a file. This will revert the file to the version found in the last commit.
This only works for files in the working directory. Files in the staging area or already commited won't be reverted.

Discarding Changes in Modified Files: Recap
========
You can remove changes in the working directory using git checkout.
This is destructive! You will throw away the changes and not be able to get them back.
git checkout --<filename> is the syntax. The -- lets Git know you're talking about a file. This will revert the file to the version found in the last commit.
This only works for files in the working directory. Files in the staging area or already commited won't be reverted.

Discarding Changes in Modified Files
========
1
Edit the file threefile.md.
2
Use git checkout to discard your changes.


Removing Tracked Files: Recap
========
Just as git mv exists to move or rename a file and instantly add the change to the staging area, git rm exists to remove a file.
git rm <filename> will remove the file and add the change to the staging area.


Removing Tracked Files
========
1
Remove the tracked file onefile.md
