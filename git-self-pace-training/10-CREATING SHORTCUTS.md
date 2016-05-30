Creating Command Shortcuts: Recap
========
You can create aliases in git that let you call on the short alias instead of writing out a full long command.
You do this by setting a global alias using git config.
git config --global alias.lol "log --oneline --graph --decorate --all" would let you type git lol instead of the entire log command with all its options.
git config --global alias.co "commit -m" would let you write git co "Commit Message" to quickly commit with a message attached.

Creating Aliases
========
1
Create an alias for pushing a new branch upstream.
2
Create an alias for the status command
