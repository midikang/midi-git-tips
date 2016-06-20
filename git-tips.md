# git tips

# Everyday Git in twenty commands or so
```
git help everyday
```
# git tutorial
```
git help toturial
```
# check git config
```
git config --global -l
```

# config your user name and email for git
git config --global user.name "Your Name"
git config --global user.email "your_email@whatever.com"

# How to set http proxy for git command
To set http proxy without authentication
```
git config --global http://proxyserver:port
```
To set http proxy with user and password
```
git config --global http.proxy http://user:password@proxyserver:port
```
To check http proxy settings
```
git config --get --global http.proxy
```
To remove http proxy settings
```
git config --system --unset http.proxy
```

# config alias
let you type git lol instead of the entire log command with all its options.
```
git config --global alias.lol "log --oneline --graph --decorate --all" 
```
let you write git co "Commit Message" to quickly commit with a message attached.
```
git config --global alias.co "commit -m" 
```
# unset alias
```
git config --global --unset alias.cm
```

# commit all stage files but new files
```
git commit -a
```
-a, --all
 Tell the command to automatically stage files that have been modified and
 deleted, but new files you have not told Git about are not affected.


# check out tag 'v1.2'
(Note: If there is also a branch named `v1.2`, we should use tags/v1.2).

```
git checkout v1.2
```

```
git checkout tags/v1.2
```

# create and checkout a new branch
```
git checkout -b ch09-updating-users
Switched to a new branch 'ch09-updating-users'
```

# list local branches
git branch --list # but didn't list all the branches,some branches are hidden.Why?

# list remote branches
git branch --remotes

# to check who change the file with line details.
git blame [filename] 


# extract patches from your branch, relative to master,
```
git format-patch master
```

# Remove a file from staging area
```
git rm --cached deleteme.rb 
```

# add file to be ignoreed in .gitignore
We want git to ignore all but the 'lib.a' file.
```
*.a
!lib.a
```

# Make a local clone that borrows from the current directory, without checking things out:
```
  $ git clone -l -s -n . ../copy
  $ cd ../copy
  $ git show-branch
```

# git-stash
Stash the changes in a dirty working directory away
 Pulling into a dirty tree
 When you are in the middle of something, you learn that there are upstream changes that are possibly relevant to what you are doing. When your local changes do not conflict with the changes in the upstream, a simple git pull will let you move forward.

 However, there are cases in which your local changes do conflict with the upstream changes, and git pull refuses to overwrite your changes. In such a case, you can stash your changes away, perform a pull, and then unstash, like this:
```
 $ git pull
  ...
 file foobar not up to date, cannot merge.
 $ git stash
 $ git pull
 $ git stash pop
``` 

# remove TopSecret.md from master branch
```
git filter-branch --tree-filter 'rm -f TopSecret.md' HEAD
```

# amendment previous commit
```
git add app/views/users/edit.html.erb
git commit --amend -m "ch09 edit user"
```

## Reword the previous commit message
```sh
git commit -v --amend
```



## push unmerged into master branch to remote 
```
git push origin ch09-updating-users
Counting objects: 25, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (25/25), done.
Writing objects: 100% (25/25), 2.73 KiB | 0 bytes/s, done.
Total 25 (delta 18), reused 0 (delta 0)
remote: 
remote: Create pull request for ch09-updating-users:
remote:   https://bitbucket.org/midikang/rails_sample_app_03/pull-requests/new?source=ch09-updating-users&t=1
remote: 
To git@bitbucket.org:midikang/rails_sample_app_03.git
 * [new branch]      ch09-updating-users -> ch09-updating-users
```

## Often the overview of the change is useful to get a feel of each step
```
git log --stat --summary
```

## peek remote changes before merge into local
This operation is safe even if you have uncommitted local changes
FETCH_HEAD, remote changes
```
git fetch
git log -p HEAD..FETCH_HEAD
```

   If Alice wants to visualize what Bob did since their histories forked she can issue the following command:

       $ gitk HEAD..FETCH_HEAD


   This uses the same two-dot range notation we saw earlier with git log.

   Alice may want to view what both of them did since they forked. She can use three-dot form instead of the
   two-dot form:

       $ gitk HEAD...FETCH_HEAD
   This means "show everything that is reachable from either one, but exclude anything that is reachable from
   both of them".

   Please note that these range notation can be used with both gitk and "git log".
   
## stash change of current working directy

```
touch mystash.txt # create file
git add .
git stash
Saved working directory and index state WIP on master: 90127fc rename to linux-tips.md
HEAD is now at 90127fc rename to linux-tips.md

$ git log
commit 90127fc1d91c19f2f72133d330b0758ebed7491a
Author: midikang <midi13@163.com>
Date:   Mon May 30 10:45:48 2016 +0800

    rename to linux-tips.md

commit 8c432551e5ef138e8afb4fb027490858c20a5475
Author: Midi <midi13@gmail.com>
Date:   Wed May 11 09:39:06 2016 +0800

    Update useful-linux-command.md

commit d6e2b8681f9522db64cd389252c04fc7c3e4a33b
Author: midikang <midi13@163.com>
Date:   Wed May 11 09:39:35 2016 +0800

    merge from c9.io

commit eb49375b67d9c585608f11f45426d0dad5c09451
Author: midikang <midi13@163.com>
Date:   Wed May 11 09:36:38 2016 +0800

    merge to useful-linux-command
    
git fetch
git log -p HEAD..FETCH_HEAD

git pull


$ git stash pop
On branch master
Your branch is up-to-date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   mystash.txt

Dropped refs/stash@{0} (799157414ccf26fe07b2b8a47414c75a9f3548ca)
```

# grep 

```
midikang:~/workspace/rails_sample_app_03 (ch09-updating-users) $ git grep "logged_in?" -- "*.*"
app/controllers/sessions_controller.rb:    log_out if logged_in?
app/controllers/users_controller.rb:      unless logged_in?
app/helpers/sessions_helper.rb:  def logged_in?
app/views/layouts/_header.html.erb:          <% if logged_in? %>
test/integration/users_login_test.rb:    assert_not is_logged_in?
test/integration/users_signup_test.rb:    assert is_logged_in?
test/test_helper.rb:  def is_logged_in?
```

# git add -i
```
midikang:~/workspace/github/private/hello-world (master) $ git add -i
           staged     unstaged path
  1:        +3/-8        +2/-0 README.md
  2:        +2/-2        +7/-0 linux-tips.md

*** Commands ***
  1: status       2: update       3: revert       4: add untracked
  5: patch        6: diff         7: quit         8: help
What now> h
status        - show paths with changes
update        - add working tree state to the staged set of changes
revert        - revert staged set of changes back to the HEAD version
patch         - pick hunks and update selectively
diff          - view diff between HEAD and index
add untracked - add contents of untracked files to the staged set of changes
*** Commands ***
  1: status       2: update       3: revert       4: add untracked
  5: patch        6: diff         7: quit         8: help
```

# rename a branch

```
git branch -m <new_branch> [old_branch]
```

# Modify previous commit without modifying the commit message
git add --all && git commit --amend --no-edit