To install Githug, run
```
gem install githug
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
How many items are there in your todolist? 4
Congratulations, you have solved the level!

Name: rename_commit
Level: 44
Difficulty: ***

Correct the typo in the message of your first (non-root) commit.
Solution
```
 $ git log
commit 2565732673efd398d2f9fafd3458955d824d7e3a
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 14:46:01 2016 +0000

    Second commit

commit f4d27d6a3e46bad9c61cfd099a1210413149d3fd
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 14:46:01 2016 +0000

    First coommit

commit 46a72ae7833715af17733a52533a791a2244b2ab
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 14:46:01 2016 +0000

    Initial commit
midikang:~/workspace/git_hug (master) $ git rebase 46a72ae7 -i

pick f4d27d6 First coommit
pick 2565732 Second commit

# Rebase 46a72ae..2565732 onto 46a72ae (2 command(s))
#
# Commands:
# p, pick = use commit
r#, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
x#, exec = run command (the rest of the line) using shell
# d, drop = remove commit
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out

```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: grep
Level: 43
Difficulty: **

Your project's deadline approaches, you should evaluate how many TODOs are left in your code
Solution
```
midikang:~/workspace/git_hug (master) $ vim app.rb 
midikang:~/workspace/git_hug (master) $ git grep 'TODO' -- '*.rb'
app.rb:# TODO Make site url variable.
app.rb:# TODO Make API version variable.
app.rb:# TODO Redirecting queries could be useful.
config.rb:    # TODO Move password to a configuration file.
midikang:~/workspace/git_hug (master) $ git grep 'TODO'
app.rb:# TODO Make site url variable.
app.rb:# TODO Make API version variable.
app.rb:# TODO Redirecting queries could be useful.
config.rb:    # TODO Move password to a configuration file.
```


********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: cherry-pick
Level: 42
Difficulty: ***

Your new feature isn't worth the time and you're going to delete it. But it has one commit that fills in `README` file, and you want this commit to be on the master as well.
Solution
```
midikang:~/workspace/git_hug (master) $ git co new-feature 
Switched to branch 'new-feature'
midikang:~/workspace/git_hug (new-feature) $ git log
commit ea2a47c19b85fc321e2737ddc49db3deeba3a1b5
Author: Andrey <aslushnikov@gmail.com>
Date:   Wed Mar 28 02:28:35 2012 +0400

    some small fixes

commit 4a1961bce62840eaef9c4392fe5cc799e38c9b7b
Author: Andrey <aslushnikov@gmail.com>
Date:   Wed Mar 28 02:27:18 2012 +0400

    Fixed feature

commit ca32a6dac7b6f97975edbe19a4296c2ee7682f68
Author: Andrey <aslushnikov@gmail.com>
Date:   Wed Mar 28 02:25:51 2012 +0400

    Filled in README.md with proper input

commit 58a8c8edcfdd00c6d8cce9aada8f987a1677571f
Author: Andrey <aslushnikov@gmail.com>
Date:   Wed Mar 28 02:24:41 2012 +0400

    Added a stub for the feature

commit ea3dbcc5e2d2359698c3606b0ec44af9f76def54
Author: Andrey <aslushnikov@gmail.com>
Date:   Wed Mar 28 02:20:32 2012 +0400

    Initial commit
    
midikang:~/workspace/git_hug (new-feature) $ git co master 
Switched to branch 'master'


midikang:~/workspace/git_hug (master) $ git cherry-pick ca32a6dac7b6f9
[master 26a03a8] Filled in README.md with proper input
 Author: Andrey <aslushnikov@gmail.com>
 Date: Wed Mar 28 02:25:51 2012 +0400
 1 file changed, 1 insertion(+), 2 deletions(-)
midikang:~/workspace/git_hug (master) $ git log
commit 26a03a80fecda539fc291e63c45630506d05ebc6
Author: Andrey <aslushnikov@gmail.com>
Date:   Wed Mar 28 02:25:51 2012 +0400

    Filled in README.md with proper input

commit 6edea632d9540e060bca97dda0897df2b7da0ec0
Author: Andrey <aslushnikov@gmail.com>
Date:   Wed Mar 28 02:23:28 2012 +0400

    Added fancy branded output

commit 232d266a78d5ef7196f1ede14972ccf7ee19e587
Author: Andrey <aslushnikov@gmail.com>
Date:   Wed Mar 28 02:22:29 2012 +0400

    Renamed project.js -> herdcore-math.js

commit b30c6a965415df6aef5f2903f9892fa5481152fc
Author: Andrey <aslushnikov@gmail.com>
Date:   Wed Mar 28 02:21:22 2012 +0400

    Added a hardcore math module

commit ea3dbcc5e2d2359698c3606b0ec44af9f76def54
Author: Andrey <aslushnikov@gmail.com>
Date:   Wed Mar 28 02:20:32 2012 +0400

    Initial commit
```


********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: repack
Level: 41
Difficulty: **

Optimise how your repository is packaged ensuring that redundant packs are removed.
Solution
```
midikang:~/workspace/git_hug (master) $ find .git/objects/ -type f
.git/objects/pack/pack-6157deddb6a1e22ef92fae4c4cb6fb85e5c36b1f.idx
.git/objects/pack/pack-6157deddb6a1e22ef92fae4c4cb6fb85e5c36b1f.pack
.git/objects/info/packs
.git/objects/e6/9de29bb2d1d6434b8b29ae775ad8c2e48c5391
.git/objects/7b/7b748d88ce20f54855747cc6844aeb28709e19
.git/objects/4d/5fcadc293a348e88f777dc0920f11e7d71441c

midikang:~/workspace/git_hug (master) $ git prune-packed

midikang:~/workspace/git_hug (master) $ find .git/objects/ -type f
.git/objects/pack/pack-6157deddb6a1e22ef92fae4c4cb6fb85e5c36b1f.idx
.git/objects/pack/pack-6157deddb6a1e22ef92fae4c4cb6fb85e5c36b1f.pack
.git/objects/info/packs
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: rebase
Level: 40
Difficulty: **

We are using a git rebase workflow and the feature branch is ready to go into master. Let's rebase the feature branch onto our master branch.
Solution
```
midikang:~/workspace/git_hug (master) $ git branch
  feature
* master
midikang:~/workspace/git_hug (master) $ git log
commit 98205e9faf10cf33d2ef7c0f66e402540c62613a
Author: ipmsteven <steven.lyl147@gmail.com>
Date:   Fri Dec 12 00:34:30 2014 -0800

    add content

commit a78bcab6232e9382a86436cdfcb2ed0391b1f0ac
Author: ipmsteven <steven.lyl147@gmail.com>
Date:   Fri Dec 12 00:33:05 2014 -0800

    init commit
    
midikang:~/workspace/git_hug (master) $ git checkout feature
Switched to branch 'feature'
midikang:~/workspace/git_hug (feature) $ git log
commit ed0fdcf366b21b8984fb37ea34106978a2e5c5ba
Author: ipmsteven <steven.lyl147@gmail.com>
Date:   Fri Dec 12 00:33:59 2014 -0800

    add feature

commit a78bcab6232e9382a86436cdfcb2ed0391b1f0ac
Author: ipmsteven <steven.lyl147@gmail.com>
Date:   Fri Dec 12 00:33:05 2014 -0800

    init commit
midikang:~/workspace/git_hug (feature) $ git rebase master
First, rewinding head to replay your work on top of it...
Applying: add feature
midikang:~/workspace/git_hug (feature) $ git log
commit fe0c7464c0d8bf7ec5c26ac0bfb39cde54ff5c92
Author: ipmsteven <steven.lyl147@gmail.com>
Date:   Fri Dec 12 00:33:59 2014 -0800

    add feature

commit 98205e9faf10cf33d2ef7c0f66e402540c62613a
Author: ipmsteven <steven.lyl147@gmail.com>
Date:   Fri Dec 12 00:34:30 2014 -0800

    add content

commit a78bcab6232e9382a86436cdfcb2ed0391b1f0ac
Author: ipmsteven <steven.lyl147@gmail.com>
Date:   Fri Dec 12 00:33:05 2014 -0800

    init commit
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: fetch
Level: 39
Difficulty: **

Looks like a new branch was pushed into our remote repository. Get the changes without merging them with the local repository 
Solution
```
midikang:~/workspace/git_hug (master) $ ls
master_file
midikang:~/workspace/git_hug (master) $ git log
commit 71e7b4061e0440a7f37776f88331a49911c442ca
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 08:40:34 2016 +0000

    Commits master_file
midikang:~/workspace/git_hug (master) $ git branch
* master
midikang:~/workspace/git_hug (master) $ git fetch origin
remote: Counting objects: 2, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 2 (delta 0), reused 0 (delta 0)
Unpacking objects: 100% (2/2), done.
From /tmp/d20160527-11167-ve5hob/
 * [new branch]      new_branch -> origin/new_branch
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: merge
Level: 38
Difficulty: **

We have a file in the branch 'feature'; Let's merge it to the master branch.
Solution
```
midikang:~/workspace/git_hug (master) $ git branch
  feature
* master
midikang:~/workspace/git_hug (master) $ ls
file1
midikang:~/workspace/git_hug (master) $ git merge feature 
Updating e12277f..cc8ea5a
Fast-forward
 file2 | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file2
midikang:~/workspace/git_hug (master) $ git log
commit cc8ea5a233df119d025eb240b9470e1ca76a151c
Author: Dustin Rodrigues <dust.rod@gmail.com>
Date:   Fri Mar 16 01:01:41 2012 -0700

    added file2

commit e12277fe88657a072f1c4eb7d9320e4e6a74ba95
Author: Dustin Rodrigues <dust.rod@gmail.com>
Date:   Fri Mar 16 01:01:07 2012 -0700

    added file1
midikang:~/workspace/git_hug (master) $ ls
file1  file2
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: push_branch
Level: 37
Difficulty: **

You've made some changes to a local branch and want to share it, but aren't yet ready to merge it with the 'master' branch.  Push only 'test_branch' to the remote repository
Solution
```
midikang:~/workspace/git_hug (master) $ git log
commit 3dc784c587cceaadf2527b97866ca13dc4ea1824
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 08:34:33 2016 +0000

    If this commit gets pushed to repo, then you have lost the level :(

commit bc651928fb646d9fd4cea318b8e63808235e7529
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 08:34:33 2016 +0000

    committed changes on master
midikang:~/workspace/git_hug (master) $ git branch
* master
  other_branch
  test_branch
midikang:~/workspace/git_hug (master) $ git push origin test_branch 
Counting objects: 6, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 652 bytes | 0 bytes/s, done.
Total 6 (delta 2), reused 0 (delta 0)
To /tmp/d20160527-10969-12t2hif/.git
 * [new branch]      test_branch -> test_branch
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: delete_branch
Level: 36
Difficulty: **

You have created too many branches for your project. There is an old branch in your repo called 'delete_me', you should delete it.
Solution
```
$ git branch
  delete_me
* master

$ git branch -d delete_me 
Deleted branch delete_me (was b60afe2).
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: branch_at
Level: 35
Difficulty: ***

You forgot to branch at the previous commit and made a commit on top of it. Create branch test_branch at the commit before the last.
Solution

```
git branch test_branch HEAD~1
```

```
 $ git log
commit c32f2612fd551f03abc2a240700241ea553cabf1
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 08:18:26 2016 +0000

    Updating file1 again

commit 4163697114cfa15061dfc7b0caa8e4cea4eaa129
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 08:18:26 2016 +0000

    Updating file1

commit 015a51df79b78b72ce7d67ce06e0e0181db67d1d
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 08:18:26 2016 +0000

    Adding file1

$ git checkout 4163697114
Note: checking out '4163697114'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 4163697... Updating file1

$ git checkout -b test_branch
Switched to a new branch 'test_branch'

$ git log
commit 4163697114cfa15061dfc7b0caa8e4cea4eaa129
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 08:18:26 2016 +0000

    Updating file1

commit 015a51df79b78b72ce7d67ce06e0e0181db67d1d
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 08:18:26 2016 +0000

    Adding file1
    
```


********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: checkout_tag_over_branch
Level: 34
Difficulty: **

You need to fix a bug in the version 1.2 of your app. Checkout the tag `v1.2` (Note: There is also a branch named `v1.2`).
Solution
```
midikang:~/workspace/git_hug (master) $ git tag
v1.0
v1.2
v1.5
midikang:~/workspace/git_hug (master) $ git branch
* master
  v1.2
  
$ git checkout tags/v1.2
Note: checking out 'tags/v1.2'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 24a60f5... Some more changes  
  
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: checkout_tag
Level: 33
Difficulty: **

You need to fix a bug in the version 1.2 of your app. Checkout the tag `v1.2`.
Solution
```
$ git tag
v1.0
v1.2
v1.5
$ git checkout v1.2
Note: checking out 'v1.2'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at bd0a231... Some more changes
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: checkout
Level: 32
Difficulty: **

Create and switch to a new branch called my_branch.  You will need to create a branch like you did in the previous level.
Solution
```
$ git branch my_branch
$ git checkout my_branch
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Who made the commit with the password? Spider Man
Congratulations, you have solved the level!

Name: branch
Level: 31
Difficulty: *

You want to work on a piece of code that has the potential to break things, create the branch test_code.
Solution
```
midikang:~/workspace/git_hug (master) $ git branch test_code
midikang:~/workspace/git_hug (master) $ git branch
* master
  test_code
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
What is the number of the line which has changed? 26
Congratulations, you have solved the level!

Name: blame
Level: 30
Difficulty: **

Someone has put a password inside the file `config.rb` find out who it was.
Solution
```
$ git blame config.rb
^5e8863d (Gary Rennie       2012-03-08 23:05:24 +0000  1) class Config
70d00535 (Bruce Banner      2012-03-08 23:07:41 +0000  2)   attr_accessor :name, :password
97bdd0cc (Spider Man        2012-03-08 23:08:15 +0000  3)   def initialize(name, password = nil, options = {})
^5e8863d (Gary Rennie       2012-03-08 23:05:24 +0000  4)     @name = name
97bdd0cc (Spider Man        2012-03-08 23:08:15 +0000  5)     @password = password || "i<3evil"
00000000 (Not Committed Yet 2016-05-27 07:40:59 +0000  6) 
09409480 (Spider Man        2012-03-08 23:06:18 +0000  7)     if options[:downcase]
09409480 (Spider Man        2012-03-08 23:06:18 +0000  8)       @name.downcase!
09409480 (Spider Man        2012-03-08 23:06:18 +0000  9)     end
70d00535 (Bruce Banner      2012-03-08 23:07:41 +0000 10) 
ffd39c2d (Gary Rennie       2012-03-08 23:08:58 +0000 11)     if options[:upcase]
ffd39c2d (Gary Rennie       2012-03-08 23:08:58 +0000 12)       @name.upcase!
ffd39c2d (Gary Rennie       2012-03-08 23:08:58 +0000 13)     end
ffd39c2d (Gary Rennie       2012-03-08 23:08:58 +0000 14) 
^5e8863d (Gary Rennie       2012-03-08 23:05:24 +0000 15)   end
^5e8863d (Gary Rennie       2012-03-08 23:05:24 +0000 16) end

Who made the commit with the password? Spider Man
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: diff
Level: 29
Difficulty: **

There have been modifications to the `app.rb` file since your last commit.  Find out which line has changed.
Solution
```
midikang:~/workspace/git_hug (master) $ git diff app.rb
diff --git a/app.rb b/app.rb
index 4f703ca..3bfa839 100644
--- a/app.rb
+++ b/app.rb
@@ -23,7 +23,7 @@ get '/yet_another' do
   erb :success
 end
 get '/another_page' do
-  @message = get_response('data.json')
+  @message = get_response('server.json')
   erb :another
 end
 
 What is the number of the line which has changed? 26
 
```
the number **-23** is the code line number for code "erb :success"



********************************************************************************
*                                    Githug                                    *
********************************************************************************
resetting level
warning: no common commits
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0)
Unpacking objects: 100% (3/3), done.
From /tmp/d20160527-8709-5r7j0l/
 * [new branch]      master     -> origin/master

Name: push
Level: 28
Difficulty: ***

Your local master branch has diverged from the remote origin/master branch. Rebase your commit onto origin/master and push it to remote.
Solution
```
 $ git rebase origin/master
First, rewinding head to replay your work on top of it...
Applying: First commit
Applying: Second commit
Applying: Third commit
$ git log
commit 052ea7b35eae54fa8839ecfa4a02fbe18c39ce4d
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 07:22:20 2016 +0000

    Third commit

commit 29b7aad2917e0cbc2687ab14fe61d6e6deb8f138
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 07:22:20 2016 +0000

    Second commit

commit aa41a2812840e3526c29fdfc0fbea181a1ec94eb
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 07:22:20 2016 +0000

    First commit

commit 3a4dbfdeccd5d2e5f030077f55a9ca8b9fe656dc
Author: Midi Kang <midi13@163.com>
Date:   Fri May 27 07:22:20 2016 +0000

    Fourth commit

$ git push origin master
Counting objects: 6, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 582 bytes | 0 bytes/s, done.
Total 6 (delta 2), reused 0 (delta 0)
To /tmp/d20160527-8709-5r7j0l/.git
   3a4dbfd..052ea7b  master -> master    

$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean

$ git remote -v
origin  /tmp/d20160527-8709-5r7j0l/.git (fetch)
origin  /tmp/d20160527-8709-5r7j0l/.git (push)
```


********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: remote_add
Level: 27
Difficulty: **

Add a remote repository called `origin` with the url https://github.com/githug/githug
Solution
```
$ git remote add origin https://github.com/githug/githug
midikang:~/workspace/git_hug (master) $ git remote -v
origin  https://github.com/githug/githug (fetch)
origin  https://github.com/githug/githug (push)
```


********************************************************************************
*                                    Githug                                    *
********************************************************************************
What is the url of the remote repository? https://github.com/githug/not_a_repo
Congratulations, you have solved the level!

Name: pull
Level: 26
Difficulty: **

You need to pull changes from your origin repository.
Solution
```
git remote -v
origin  https://github.com/pull-this/thing-to-pull (fetch)
origin  https://github.com/pull-this/thing-to-pull (push)
git pull origin master
From https://github.com/pull-this/thing-to-pull
 * branch            master     -> FETCH_HEAD
    
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
What is the name of the remote repository? my_remote_repo
Congratulations, you have solved the level!

Name: remote_url
Level: 25
Difficulty: **

The remote repositories have a url associated to them.  Please enter the url of remote_location.
Solution
```
git remote -v
my_remote_repo  https://github.com/Gazler/githug (fetch)
my_remote_repo  https://github.com/Gazler/githug (push)
remote_location https://github.com/githug/not_a_repo (fetch)
remote_location https://github.com/githug/not_a_repo (push)

```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: remote
Level: 24
Difficulty: **

This project has a remote repository.  Identify it.
Solution
```
git remote -v
my_remote_repo  https://github.com/Gazler/githug (fetch)
my_remote_repo  https://github.com/Gazler/githug (push)
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: checkout_file
Level: 23
Difficulty: ***

A file has been modified, but you don't want to keep the modification.  Checkout the `config.rb` file from the last commit.
Solution
```
git checkout config.rb
```


********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: reset_soft
Level: 22
Difficulty: **

You committed too soon. Now you want to undo the last commit, while keeping the index.
Solution
```
git reset --soft HEAD~1
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

Name: reset
Level: 21
Difficulty: **

There are two files to be committed.  The goal was to add each file as a separate commit, however both were added by accident.  Unstage the file `to_commit_second.rb` using the reset command (don't commit anything).

Solution
```
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   to_commit_first.rb
        new file:   to_commit_second.rb
$ git reset HEAD to_commit_second.rb        
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Name: commit_in_future
Level: 20
Difficulty: **

Commit your changes with the future date (e.g. tomorrow).
Solution
```
git commit --date=2016-05-31 -m "commit in the futrue date"
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Name: commit_amend
Level: 19
Difficulty: **

The `README` file has been committed, but it looks like the file `forgotten_file.rb` was missing from the commit.  Add the file and amend your previous commit to include it.
Solution
```
git add forgotten_file.rb
git commit --amend -m "amend and add forgotten_file.rb" 
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Name: push_tags
Level: 18
Difficulty: **

There are tags in the repository that aren't pushed into remote repository. Push them now.


From /tmp/d20160527-5992-151hs9n/
 * [new branch]      master     -> origin/master

Solution
```
There's a bug. I didn't run command 'git push ',but solved.
```

********************************************************************************
*                                    Githug                                    *
******************************************************************************** 
Name: tag
Level: 17
Difficulty: **

We have a git repo and we want to tag the current commit with `new_tag`.

Solution
```
git tag new_tag
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Name: log
Level: 16
Difficulty: **

You will be asked for the hash of most recent commit.  You will need to investigate the logs of the repository for this.

Solution
```
git log
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Name: restructure
Level: 15
Difficulty: ***

You added some files to your repository, but now realize that your project needs to be restructured.  Make a new folder named `src` and using Git move all of the .html files into this folder.
Solution
```
git mv *.html src/
```

********************************************************************************
*                                    Githug                                    *
********************************************************************************
Name: rename
Level: 14
Difficulty: ***

We have a file called `oldfile.txt`. We want to rename it to `newfile.txt` and stage this change.
```
git mv oldfile.txt newfile.txt
```
