#Github Training Notes

####Background:
These are my edited notes from a day-long training held at Gilt by Github trainer https://twitter.com/PeterBell, organized in Q/A format. The training assumed that attendees were already familiar with using version control. 

####Table of Contents:
I. General Notes to Remember
II. Useful Tips
III. How to Undo
IV. External Resources

###I. General Notes To Remember
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
9. Copy/paste the last two lines in to your terminal. 
10. `git status`
11. `git push` 
12. If you refresh the page you created on github.com, you should see it change to reflect the file(s) you just pushed up.
13. In general, make good use of `git status`. Helpful for telling you what to do when there's a merge conflict, too.



###II. Useful Tips
#####What configuration settings can I take advantage of?
1. Colors:
```
git config --global color.ui true 
```
2. Take out extraneous descriptions:
```
git status -s
```
3. USE ALIASES! For example:
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


###III. How to Undo


###IV. External Resources
1. http://training.github.com/kit/
2. http://training.github.com/kit/downloads/github-git-cheat-sheet.pdf
