#Github Training Notes

####Background:
These are my edited notes from a day-long training held at Gilt by Github trainer https://twitter.com/PeterBell, organized in Q/A format. The training assumed that attendees were already familiar with using version control. 

####Table of Contents:
I. General Commands to Remember
II. Useful Tips
III. How to Undo
V. External Resources

###I. General Commands To Remember
#####How do I check or configure a user name?
```
git config --global user.name
```
returns your user name.

```
git config --global user.name "Daffy Duck"
```
changes your user name to Daffy Duck.

#####How do I check or change my e-mail address?
```
git config --global user.email
```

Returns your e-mail address.

```
git config --global user.email daffy@disney.com
```

This changes your e-mail addresses.

#####What's the most simple workflow for creating and pushing up to a repository?
1. `git init new_website`
2. `cd new_website`
3. `touch index.html about.html about.css contact.html` creates a couple of files that are both unstaged and untracked.
4. Edit index.html.
5. `git add .` adds all the untracked files for staging.
6. `git commit . -m "first commit!"` First commit of all the files!
7. Go to github.com, log in, and manually create a new repository by clicking on a button.
8. DO NOT hit the checkbox to initiate a README. Do pay attention to the last two lines on the page, though. 
9. Copy/paste the last two lines in to your terminal. For example:
```
git remote add origin https://github.com/USERNAME/new_website.git

git push -u origin master
``` 
10. `git status`
11. `git push` 
12. If you refresh the page you created on github.com, you should see it change to reflect the file(s) you just pushed up.
13. In general, make good use of `git status`. Helpful for telling you what to do when there's a merge conflict, too.
14. Note: Always try to use HTTP, not SSH. SSH takes longer to send over the server. 
15. When you do `git push -u origin master`, and if you get an error that says the remote origin already exists (which may happen on a Windows machine), do:
```
git remote set-url origin https://github.com/USERNAME/new_website.git
```
16. Another Windows note: if you're using HTTPS on windows, and you get an error that says "file doesn't exist for username," the person should just use SSH instead. This is a known bug. 
17. Note for first-time git users: the first time you push to git, you'll have to input your username/password. You can set up github to bypass this step, though. Go to (https://help.github.com/articles/set-up-git and search for "password caching" to find out the steps how. 

#####How do I rename or delete a file?
```
git mv index.html home.htm
```
This renames index.html to home.htm. Then you'll have to commit home.htm. 

Note that if you only do:
```
mv index.html home.htm
```
...git will think that home.htm is untracked and index.html was deleted, when it was really a rename. In this case, you'd have to do `git add -A` (note the capital A!) instead of a normal `git add .` which will only add untracked files or modified files, but not ALL files.


#####What does it mean when your terminal tells you "your branch is ahead of 'origin/master' by 3 commits"?
It just means that if you lose your laptop right now, you'll lose three commits. So you may want to commit. Typing `git status -s` (or `git s`, if you gave "status -s" an alias -- see below in the Useful Tips section) will not give you this extraneous descriptor.

#####.gitignore?
Example: put *.log into your .gitignore file in order to git ignore every file that ends with a .log

Try typing `git status` after creating a test file called test.log. Notice that test.log did not show up as something to stage. 

Note: If a person isn't seeing a file after cloning a repo, here are some useful places to check:
```
~/.gitignore
```
```
open .git
```
```
cat .git/info/exclude
```

#####How do I create and then merge a branch?
```
git checkout -b new_branch
```
creates a branch called new_branch.

In practice, the only time you'd want to create a new branch is when you're ready to check out a branch; no one sits around at the start of a project and decides to create 50 branches from the start. 

Also, a good practice is to delete a branch as soon as you've merged it in with master. You don't want to end up with too many branches that aren't being worked on anymore.

```
git checkout master
git merge new_branch
```
merges the branch. Make sure you're in the `master` branch when you merge the side branch. 

#####How do I do a recursive merge, and why is a recursive merge preferable to a fast-forward merge?
```
git merge --no-ff BRANCH
```
If you do a branch merge when nothing has happened with the master branch, git will "fast forward" -- or pretend that you had committed some changes to the master branch. This is bad because you lose the ability to see all of the individual commits when you do a fast foward. For example, if we git merge a branch when no change to the master has bee made, and if we do `git lg`, it'll look like we created the branch changes directly on the master branch when we didn't really. So it's best forwrd to do a recursive, or "no fast forward" `--no-ff` merge.

#####How do I resolve a merge conflict?
Step One:
```
git status
```

Step Two:
Go into the file where the conflict exists and delete the lines git added. Edit as appropriate. Since the commit message will be called "merge conflict resolved," don't try to add in new features; just resolve the conflict. 

A VIM trick: hit 'dd' before hitting 'I' to delete a entire line before going into INSERT mode.

Step Three:
After you've saved your changes, type:
```
git add <FILENAME>
```

Step Four:
```
git commit
```
Note that this is a straight-up "git commit" without a message. This resolves the merge, and you'll be transferred to VIM to write your merge resolve message.

###II. Useful Tips
#####How do I see my history of what I typed into the terminal?
```
history
```

#####What configuration settings can I take advantage of?
1. Colors:
```
git config --global color.ui true 
```
This turns on default terminal coloring. 

2. Clean up `git log` output using `git lg` alias
```
git log --online --decorate --all --graph
```
This makes `git log` output a much cleaner history! So let's make an alias for it:

```git config --global alias.lg "log --oneline --decorate --all --graph
```
W00t, now I can type `git lg` instead of `git log`!



3. Take out extraneous descriptions when typing `git status`:
```
git status -s
```
4. USE ALIASES! For example:
```
git config --global alias.s "status -s"
```
This allows you to type `git s` to get the equivalent of `git status -s`. 

Note that all the repositories you create will be configured at --global. If you must write `git config`, it silently implies `--local`.

#####How do I see what's under the hood in git?
```
open .git
```
This opens up all the .git files in your mac finder!

```
vi ~/.gitconfig
```
This lets you see everything in your hidden .gitconfig file, and you can edit the settings in vim too. 

If I create a new file called index.css, there will be three objects added in .git. 

#####What are some shortcuts for adding or staging files?
```
git add ab*
```
This adds the first two files for staging. 

```
git add co*
```
This adds all untracked files.

```
ls -a
```
This lists all hidden files.

```
git commit -am "commit messages"
```
This adds *and* commits the file(s). This won't work with untracked files, however. 

#####How do I see all the changes going into the next commit?
```
git diff
```
Note that this does not work with untracked files, so it's a little anoying. You ahve to add the untracked file. 

```
git diff --staged
```
This will show us everything going into the next commit. 

```
git diff HEAD
```
This will show you what's been modified by unstaged files AND staged changes. 

#####What if I want to uncommit something from the staging area?
For example, after I `git add .`, how do I unstage it? The answer is to use 
```
git reset HEAD <file>
```
Note that there is a difference between un-staged and un-tracked files. Un-tracked files have never been added. Un-staged files are just not in the queue for being committed. 






###III. How to Undo


###IV. Working in Branches


###V. External Resources
1. http://training.github.com/kit/
2. http://training.github.com/kit/downloads/github-git-cheat-sheet.pdf
