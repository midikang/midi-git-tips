# git tips

# Everyday Git in twenty commands or so
```
git help everyday
```
# git tutorial
```
git help toturial
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

