#Github Training Notes

####Background:
On March 27th, 2014, I attended a free day-long training held by Git trainer [@PeterBell](https://twitter.com/PeterBell) and TA'ed by Github's [@aidenfeldman](https://twitter.com/aidanfeldman). These are my edited notes from the day, organized in Question/Answer format. 

IMO, the training is really useful for the intermediate git user. One of the first things we did was to configure git to be more user-friendly, creating aliases such as `git lg` and `git s`. We also delved into more advanced topics such as when to branch, what to do with branches, how to merge branches without any fast forward `--no-ff`, the steps for resolving merge conflicts and rebase conflicts, why `rebase` should be used when working in teams, and how to undo almost any commit. 

We ran out of time a little at the end rushing through cherrypicking and git stashing, but overall it was a wonderful training that broke down concepts into simple examples. Peter Bell delivered the presentation and answered questions with alacrity. 

####Table of Contents:
#####[I. General Commands to Remember](https://github.com/lpatmo/git-training-notes#i-general-commands-to-remember-1)
* [How do I check or configure a username?](https://github.com/lpatmo/git-training-notes#how-do-i-check-or-configure-a-username)
* [How do I check or change my e-mail address?](https://github.com/lpatmo/git-training-notes#how-do-i-check-or-change-my-e-mail-address)
* [What's the most simple workflow for creating and pushing up to a repository?](https://github.com/lpatmo/git-training-notes#whats-the-most-simple-workflow-for-creating-and-pushing-up-to-a-repository)
* [How do I rename or delete a file?](https://github.com/lpatmo/git-training-notes#how-do-i-rename-or-delete-a-file)
* [How do I create a new branch?](https://github.com/lpatmo/git-training-notes#how-do-i-create-a-new-branch)
* [How do I switch to a branch?](https://github.com/lpatmo/git-training-notes#how-do-i-switch-to-a-branch)
* [How do I see all the branches?](https://github.com/lpatmo/git-training-notes#how-do-i-see-all-the-branches)
* [What does it mean when your terminal tells you "your branch is ahead of 'origin/master' by 3 commits"?](https://github.com/lpatmo/git-training-notes#what-does-it-mean-when-your-terminal-tells-you-your-branch-is-ahead-of-originmaster-by-3-commits)
* [.gitignore?](https://github.com/lpatmo/git-training-notes#gitignore)
* [How do I create and then merge a branch?](https://github.com/lpatmo/git-training-notes#how-do-i-create-and-then-merge-a-branch)
* [How do I do a recursive merge, and why is a recursive merge preferable to a fast-forward merge?](https://github.com/lpatmo/git-training-notes#how-do-i-do-a-recursive-merge-and-why-is-a-recursive-merge-preferable-to-a-fast-forward-merge)
* [How do I resolve a merge conflict?](https://github.com/lpatmo/git-training-notes#how-do-i-resolve-a-merge-conflict)
* [What is git rebase, and why do I need to do it?](https://github.com/lpatmo/git-training-notes#what-is-git-rebase-and-why-do-i-need-to-do-it)
* [Can you give me an example of when I would use git rebase?](https://github.com/lpatmo/git-training-notes#can-you-give-me-an-example-of-when-i-would-use-git-rebase)
* [What happens if there is a rebase conflict?](https://github.com/lpatmo/git-training-notes#what-happens-if-there-is-a-rebase-conflict)
* [What do I do if I forget the --no-ff when I merge?](https://github.com/lpatmo/git-training-notes#what-do-i-do-if-i-forget-the---no-ff-when-i-merge)
* [What is the difference between a git fetch and a git pull?](https://github.com/lpatmo/git-training-notes#what-is-the-difference-between-a-git-fetch-and-a-git-pull)
* [Why should I do a git fetch but not a git pull?](https://github.com/lpatmo/git-training-notes#why-should-i-do-a-git-fetch-but-not-a-git-pull)
* [What is the difference between git pull --rebase' andgit fetch+git rebase origin master`?](https://github.com/lpatmo/git-training-notes#what-is-the-difference-between-git-pull---rebase-andgit-fetchgit-rebase-origin-master)
* [When would I clone a repository from the shared repository and when should I fork a repository?](https://github.com/lpatmo/git-training-notes#what-is-the-difference-between-git-pull---rebase-andgit-fetchgit-rebase-origin-master)

#####[II. Useful Tips](https://github.com/lpatmo/git-training-notes#ii-useful-tips-1)
* [How do I see a history of commands I typed into the terminal?](https://github.com/lpatmo/git-training-notes#how-do-i-see-a-history-of-commands-i-typed-into-the-terminal)
* [What git configuration settings should I take advantage of?](https://github.com/lpatmo/git-training-notes#what-configuration-settings-can-i-take-advantage-of)
* [https://github.com/lpatmo/git-training-notes#how-do-i-see-whats-under-the-hood-in-git](How do I see what's under the hood in git?)
* [What are some shortcuts for adding or staging files?](https://github.com/lpatmo/git-training-notes#what-are-some-shortcuts-for-adding-or-staging-files)
* [How do I see all the changes going into the next commit?](https://github.com/lpatmo/git-training-notes#how-do-i-see-all-the-changes-going-into-the-next-commit)
* [What if I want to uncommit something from the staging area?](https://github.com/lpatmo/git-training-notes#what-if-i-want-to-uncommit-something-from-the-staging-area)

#####[III. Releasing to Production, Stashing, and How to Undo](https://github.com/lpatmo/git-training-notes#iii-releasing-to-production-stashing-and-how-to-undo-1)
* [What are tags?](https://github.com/lpatmo/git-training-notes#what-are-tags)
* [What if we need to add a hotfix?](https://github.com/lpatmo/git-training-notes#what-if-we-need-to-add-a-hotfix)
* [What is cherrypicking?](https://github.com/lpatmo/git-training-notes#what-is-cherrypicking)
* [What is stashing?](https://github.com/lpatmo/git-training-notes#what-is-stashing)
* [How do I undo a commit message message that the cat walked over?](https://github.com/lpatmo/git-training-notes#how-do-i-undo-a-commit-message-message-that-the-cat-walked-over)
* [How do I undo any commit?](https://github.com/lpatmo/git-training-notes#how-do-i-undo-any-commit)
* [Let's play with git reset! (a.k.a. 'What is git reset?')](https://github.com/lpatmo/git-training-notes#lets-play-with-git-reset-aka-what-is-git-reset)
* [How do I take the last two commits and squash them into one?](https://github.com/lpatmo/git-training-notes#how-do-i-take-the-last-two-commits-and-squash-them-into-one)
* [What if I want a file that I excised via git reset --hard back within the next 30 days?](https://github.com/lpatmo/git-training-notes#what-if-i-want-a-file-that-i-excised-via-git-reset---hard-back-within-the-next-30-days)

#####[IV. Some External Resources](https://github.com/lpatmo/git-training-notes#iv-some-external-resources-1)

###I. General Commands To Remember
####How do I check or configure a username?
```
git config --global user.name
```
returns your user name.

```
git config --global user.name "Daffy Duck"
```
changes your user name to Daffy Duck.

####How do I check or change my e-mail address?
```
git config --global user.email
```

Returns your e-mail address.

```
git config --global user.email daffy@disney.com
```

This changes your e-mail addresses.

####What's the most simple workflow for creating and pushing up to a repository?
1. `git init new_website`
2. `cd new_website`
3. `touch index.html about.html about.css contact.html` creates a couple of files that are both unstaged and untracked.
4. Edit index.html.
5. `git add .` adds all the untracked files for staging.
6. `git commit . -m "first commit!"` First commit of all the files!
7. Go to github.com, log in, and manually create a new repository by clicking on a button.
8. DO NOT hit the checkbox to initiate a README. Do pay attention to the last two lines on the page, though. 
9. Copy/paste the last two lines into your terminal. For example:
```
git remote add origin https://github.com/USERNAME/new_website.git
git push -u origin master
``` 
Note that `git push -u origin master` does two things: 1) it pushes up; 2) `-u` sets the default to be upstream. If you don't have `-u`, the next time you push, you'd have to type `git push -u origin master` again instead of just `git push`.
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

####How do I rename or delete a file?
```
git mv index.html home.htm
```
This renames index.html to home.htm. Then you'll have to commit home.htm. 

Note that if you only do:
```
mv index.html home.htm
```
...git will think that home.htm is untracked and index.html was deleted, when it was really a rename. In this case, you'd have to do `git add -A` (note the capital A!) instead of a normal `git add .` which will only add untracked files or modified files, but not ALL files.

####How do I create a new branch?
```
git branch name_of_branch
```
or
```
git checkout -b name_of_branch
```

####How do I switch to a branch?
```
git checkout name_of_branch
```

####How do I see all the branches?
```
git branch
```


####What does it mean when your terminal tells you "your branch is ahead of 'origin/master' by 3 commits"?
It just means that if you lose your laptop right now, you'll lose three commits. So you may want to commit. Typing `git status -s` (or `git s`, if you gave "status -s" an alias -- see below in the Useful Tips section) will not give you this extraneous descriptor.

####.gitignore?
Example: put * .log into your .gitignore file in order to git ignore every file that ends with a .log

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

####How do I create and then merge a branch?
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

####How do I do a recursive merge, and why is a recursive merge preferable to a fast-forward merge?
```
git merge --no-ff BRANCH
```
If you do a branch merge when nothing has happened with the master branch, git will "fast forward" -- or pretend that you had committed some changes to the master branch. This is bad because you lose the ability to see all of the individual commits when you do a fast foward. For example, if we git merge a branch when no change to the master has bee made, and if we do `git lg`, it'll look like we created the branch changes directly on the master branch when we didn't really. So it's best forwrd to do a recursive, or "no fast forward" `--no-ff` merge.

####How do I resolve a merge conflict?
```
git status
```

Next, go into the file where the conflict exists and delete the lines git added. Edit as appropriate. Since the commit message will be called "merge conflict resolved," don't try to add in new features; just resolve the conflict. 

A VIM trick: hit 'dd' before hitting 'I' to delete a entire line before going into INSERT mode.

After you've saved your changes, type:
```
git add <FILENAME>
```
... and then:

```
git commit
```
Note that this is a straight-up "git commit" without a message. This resolves the merge, and you'll be transferred to VIM to write your merge resolve message.

####What is `git rebase`, and why do I need to do it?
Rebasing is the process of moving a branch to a new base commit. The primary reason for rebasing is to maintain a linear project history, making it look like the developers on your team only ever worked on one feature at a time. 

####Can you give me an example of when I would use `git rebase`?
Let's say you created a branch named `first_branch` and a branch named `second_account`. Then you created some files i each and added/committed the files. Next you'd do:
```
git checkout master
git merge --no-ff first_branch
git branch -d first_branch
```
In other words, you'd run a non-fast-forward merge of one of the branches with master (make sure you're in the master branch when you run the merge), and delete the branch right after you merge. Then:
```
git checkout second_branch
git rebase master
git lg
``` 

####Why is "Should I do git rebase or git merge?" not a useful question?
This is not a useful question because a merge will always happen. You don't * have*  to do rebase, but rebasing will help you when you look back through the history of commits and make progress tracking look more readable, since it'll look like you only worked on one feature at a time. The more people on the team who rebase, the cleaner the final history will appear.  

####What happens if there is a rebase conflict?
You'd resolve the conflict the same way you'd resolve a merge conflict -- by going into the file and editing/deleting lines as appropriate. The difference is that after you `git add .` and `git lg` and `git status`, you'd type `git rebase --continue` instead of `git commit`. Then you'd checkout the master branch again and merge the branch in question. Summary of steps below:
```
git merge --no-ff first_branch
git branch -d first_branch
git lg
git checkout second_branch
git rebase master
vi fix-conflicts-in-this-file.html
git add .
git lg
git status
git rebase --continue
git lg
git checkout master
git merge --no-ff second_branch -m "merged second branch"
git lg
git branch -d second_branch
```

Note that `git status` will tell you what need to do, in most cases. For exmple, right after I fixed my rebase conflict by going into the conflicted file, this is what `git status` told me:
```
$ git status
# Not currently on any branch.
# You are currently rebasing.
#   (all conflicts fixed: run "git rebase --continue")
#
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#     modified:   index.html
#
```

####What do I do if I forget the `--no-ff` when I merge?
You can go one step back in history on the master branch by typing:
```
git reset --keep master@{1}
```

####What is the difference between a `git fetch` and a `git pull`?

`git pull` == `git fetch` + `git merge`. 

In other words, `git fetch` fetches changes from github, but does not merge the changes. So after you fetch, you'd have to run `git merge origin/master` to merge the changes. 

####Why should I do a `git fetch` but not a `git pull`?
You should do a `git fetch` if you know you might get back a bunch of conflicts, and you know it's going to take a while to resolve the conflicts.

####What is the difference between `git pull --rebase' and `git fetch` + `git rebase origin master`?
No difference! They're the same. `git pull --rebase` is the shortcut version of saying `git fetch` and `git rebase origin master`. 

####When would I clone a repository from the shared repository versus fork a repository?
If you want to make a pull request, you'd need to FORK it, then git clone your own copy of the repository. Remember to git clone your own copy of the repo, not the original repo; otherwise, you won't be able to push up to it. 

Pull requests are intended for development environments where the trust between the collaborators is low. That is, you'd submit pull requests if you were just starting out on a project, or contributing to a stranger's open source project.

Close working teammates should be added as COLLABORATORS on a repo so that everyone has master pushing permissions.



###II. Useful Tips
####How do I see a history of commands I typed into the terminal?
```
history
```

####What configuration settings should I take advantage of?
#####1. Colors:
```
git config --global color.ui true 
```
This turns on default terminal coloring. 

#####2. Start typing `git lg` instead of `git log` to seeing a cleaner log by configuring an alias:
```
git log --online --decorate --all --graph
```
This makes `git log` output a much cleaner history! So let's make an alias for it:

```
git config --global alias.lg "log --oneline --decorate --all --graph
```
W00t, now I can type `git lg` instead of `git log`!


#####3. Take out extraneous descriptions when typing `git status`:
```
git status -s
```
#####4. Use aliases to get back a cleaner version of `git status` too!
```
git config --global alias.s "status -s"
```
This allows you to type `git s` to get the equivalent of `git status -s`. 

Note that all the repositories you create will be configured at --global. If you must write `git config`, it silently implies `--local`.

#####5. Configure git so that when do a `git push` without specifying a branch, you push just to your branch, not to all matching branches. 
```
git config --global push.default simple
```
More information: http://blog.nicoschuele.com/posts/git-2-0-changes-push-default-to-simple

Note that `git pull` is not branch-specific. 

####How do I see what's under the hood in git?
```
open .git
```
This opens up all the .git files in your mac finder!

```
vi ~/.gitconfig
```
This lets you see everything in your hidden .gitconfig file, and you can edit the settings in vim too. 

If I create a new file called index.css, there will be three objects added in .git. 

####What are some shortcuts for adding or staging files?
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
This adds * and*  commits the file(s). This won't work with untracked files, however. 

```
git branch -a
```
This shows all hidden branches. 

####How do I see all the changes going into the next commit?
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

####What if I want to uncommit something from the staging area?
For example, after I `git add .`, how do I unstage it? The answer is to use 
```
git reset HEAD <file>
```
Note that there is a difference between un-staged and un-tracked files. Un-tracked files have never been added. Un-staged files are just not in the queue for being committed. 


###III. Releasing to Production, Stashing, and How to Undo
####What are tags?
Whenever you release to production, you should add a tag. There are three types of tags, but the one recommended by Peter (the trainer) is the annotated tag. Example:
```
git tag -a r0.1 -m "initial home page release"
```

Then if you run `git show r0.1` you'll be able to see the tag message.

####What if we need to add a hotfix?
```
$ git checkout -b rb0.1
//create a new branch
//make the fixes
//add and commit the fixes
//push to production
//then tag it as seen below
$ git tag -a r0.1.1 -m "hot fix for home page error"
```

####What is cherrypicking?
Not sure yet. Ran over this too quickly. To Be Updated.

####What is stashing?
Git stashing allows you to 'save' a piece of your work and move it to the side until you need it again. For example:

```
touch half_finished.html
git stash
```
You created a half-finished file and stashed it.

```
git stash apply
```
This will get your stashed file back.

You can switch to another branch and type `git stash apply` to get that file back too.

You want to run `git stash pop` as the last place you want the stashed file to work.

Another useful command:
```
git stash list
```
... allows you to see a lsit of what's happening.

####How do I undo a commit message message that the cat walked over?
Example problem:
```
git commit -m "added about us pagesldfjsdlfjsldfkjsdf"
```
Solution:
```
git commit --amend
```
Note that this only works on the * last*  commit.


####How do I undo any commit?
Run `git lg` so you can see the hash of the commit. For example:
```
*  83f6a24 (HEAD, master) a bad idea
*  baa9473 added about us pages
```
In this case, you want to revert the "bad idea" commit message corresponding to 83f6a24. So you'd do:

```
git revert 83f6a24
```

Git will then create a new commit message stating that you reverted the mistake:

```
*  c91ffbb (HEAD, master) Revert "a bad idea"
*  83f6a24 a bad idea
*  baa9473 added about us pages
```

Yay! But what if you wanted to * revert*  your revert?

It's easy, now; just find the hash for the revert:

```
git revert c91ffbb
```

So now you'll have something like:
```
$ git lg
*  80135c7 (HEAD, master) Revert "Revert "a bad idea""
*  c91ffbb Revert "a bad idea"
*  83f6a24 a bad idea
*  baa9473 added about us pages
```
Basically, reverting doesn't change history; it just adds new history.

####Let's play with git reset! (a.k.a. 'What is git reset?')

Example:
```
git reset HEAD~2
```
...resets the last two commits from history.

There are three types of `git reset`:

```
git reset --soft 
```
A soft reset will leave the files in the staging area.

```
git reset --mixed 
```
The files will be gone, but will still be left in the staging area.

```
git reset --hard 
```
Goodbye, files! They will be completley excised. 

####How do I take the last two commits and squash them into one?
```
git reset --soft HEAD~2
git commit -m "took the last two commits and squashed them into one"
```

####What if I want a file that I excised via `git reset --hard` back within the next 30 days?
You can only do this if you're on * the same computer* , and it's not been more than 30 days:
```
git reflog
```
... to see a list of commit hashes.
```
git reset --hard 0e529c0
```
... assuming 0e529c0 is the hash you want. 

This will undo your `git reset --hard`.


###IV. Some External Resources
*  http://training.github.com/kit/
*  http://training.github.com/kit/downloads/github-git-cheat-sheet.pdf
*  https://www.atlassian.com/git/tutorial/rewriting-git-history#!rebase
