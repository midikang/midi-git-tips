# Clone a repository

	git clone https://github.com/midikang/Spoon-Knife.git


# You'll see the current configured remote repository for your fork.
	$ git remote -v
  
    origin  https://github.com/midikang/Spoon-Knife.git (fetch)
    origin  https://github.com/midikang/Spoon-Knife.git (push)


$ git remote add upstream https://github.com/octocat/Spoon-Knife
  
$ git remote -v
  
    origin  https://github.com/midikang/Spoon-Knife.git (fetch)
    origin  https://github.com/midikang/Spoon-Knife.git (push)
    upstream        https://github.com/octocat/Spoon-Knife (fetch)
    upstream        https://github.com/octocat/Spoon-Knife (push)
    
    
$git fetch upstream

  From https://github.com/octocat/Spoon-Knife
   * [new branch]      change-the-title -> upstream/change-the-title
   * [new branch]      master     -> upstream/master
   * [new branch]      test-branch -> upstream/test-branch

$git merge upstream/master

https://help.github.com/articles/syncing-a-fork/
