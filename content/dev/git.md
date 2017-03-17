+++
categories = ["developement"]
date = "2011-02-16T12:10:57+01:00"
description = "Some useful notes on GIT usage"
title = "GIT"
draft = false
thumbnail = "/img/logo/git.png"
tags = [
	"SCM",
	"GIT"
]
aliases = [
	"/post/dev/git",
	"wiki/Git"
	]
project2030 = "migrated"
+++
Some GIT commands I use and wanted to note for my own reference in case I don't use it anymore for some time and can't remember ;-)

<!--more-->

# Submodules
## Adding a submodule to a project
{{< highlight bash "style=emacs" >}}$ git submodule add <insert.repo.uri> destination/path{{< /highlight >}}

## Initialize submodules in a fresh checkout
{{< highlight bash "style=emacs" >}}
$ git submodule init
$ git submodule update
{{< /highlight >}}

## Fetch changes from submodule
Doing it for all existing submodules
{{< highlight bash "style=emacs" >}}$ git submodule foreach git pull{{< /highlight >}}
Doing it for only a specific submodule is standard git usage, you have to go to the root directory of the submodule and execute git pull or any other operation (including committing and pushing).

# Forking
## Adding upstream to your fork
{{< highlight bash "style=emacs" >}}
$ git checkout master
$ git remote add upstream <insert.repo.uri>
$ git fetch upstream
$ git rebase upstream/master
{{< /highlight >}}

# Hosting git repositories
Here are some projects which help you to self host your environment

* https://try.gitea.io/

# Initialize local git repository and create origin master
Go to the root directory you want for this repo and execute following commands
{{< highlight bash "style=emacs" >}}
local$ git init
{{< /highlight >}}
Create the repo on your server
{{< highlight bash "style=emacs" >}}
local$ ssh server
server$ cd /path/to/git/root
server$ mkdir newrepo.git && cd newrepo.git
server$ git --bare init
server$ exit
{{< /highlight >}}
Add the origin master to your local git
{{< highlight bash "style=emacs" >}}
local$ git remote add origin ssh://server/path/to/repo.git
local$ git push origin master
{{< /highlight >}}

# clone a git for local changes that can be pushed again to origin master
{{< highlight bash "style=emacs" >}}
local$ git clone ssh://server/path/to/repo.git
{{< /highlight >}}

# Remove files from git
In this example it's the .DS_Store file created automatically on a mac

{{< highlight bash "style=emacs" >}}
local$ find . -depth -name '.DS_Store' -exec git rm --cached '{}' \; -print
{{< /highlight >}}

## Add them to the ignore list
Execute this command in the root of the git directory
{{< highlight bash "style=emacs" >}}
local$ echo ".DS_Store" >> .gitignore
local$ git add .gitignore
local$ git commit -m ".DS_Store removed and ignored"
{{< /highlight >}}

### Ignores for mac client
{{< highlight bash "style=emacs" >}}
.DS_Store
._*
{{< /highlight >}}

### Ignores for working with latex
{{< highlight bash "style=emacs" >}}
*.aux
*.dvi
*.ilg
*.ind
*.log
*.lol
*.out
*.toc
*.ps
*.glo
*.nlo
*.ilg
*.nls
*.bbl
*.blg
{{< /highlight >}}

# Upload to remote master
If you have not added the origin yet, do this first
{{< highlight bash "style=emacs" >}}
local$ git remote add origin ssh://server/path/to/repo.git
{{< /highlight >}}

To push the files
{{< highlight bash "style=emacs" >}}
local$ git push origin master
{{< /highlight >}}
# Stay in sync with remote repository
{{< highlight bash "style=emacs" >}}
local$ git pull origin master
{{< /highlight >}}

# add changes
Add all changed / new files to the next commit
{{< highlight bash "style=emacs" >}}
local$ git add .
{{< /highlight >}}
or as a synonym you can use
{{< highlight bash "style=emacs" >}}
local$ git stage .
{{< /highlight >}}
Interactive session to choose which files to be added
{{< highlight bash "style=emacs" >}}
local$ git add -i
{{< /highlight >}}

# create local branch, do your work and merge it back to local master
New Branch from whatever branch you are in
{{< highlight bash "style=emacs" >}}
local$ git branch task1
{{< /highlight >}}

Do your changes and commit as usual.
You can even switch branches in between.

Switch to the master (or whatever branch you branched from)
{{< highlight bash "style=emacs" >}}
local$ git checkout master
{{< /highlight >}}

Merge your temporary branch into master
{{< highlight bash "style=emacs" >}}
local$ git merge task1
{{< /highlight >}}

Delete your temporary branch
{{< highlight bash "style=emacs" >}}
local$ git branch -D task1
{{< /highlight >}}

# Show me all branches
{{< highlight bash "style=emacs" >}}
local$ git branch -a
{{< /highlight >}}

# Switch branch
{{< highlight bash "style=emacs" >}}
local$ git checkout master
{{< /highlight >}}

# Show me changes since last commit
To see the actual code / cleartext:
{{< highlight bash "style=emacs" >}}
local$ git diff --cached
{{< /highlight >}}
or
{{< highlight bash "style=emacs" >}}
local$ git diff --staged
{{< /highlight >}}

More details and a nice graphic can be seen at http://365git.tumblr.com/post/474079664/whats-the-difference-part-1

# Save dirty code and revert back to HEAD
{{< highlight bash "style=emacs" >}}
local$ git stash --keep-index
{{< /highlight >}}

To restore into the dirty code (merging it into your current state)
{{< highlight bash "style=emacs" >}}
local$ git stash apply
{{< /highlight >}}

Detailed description of the stash command can be found at http://www.kernel.org/pub/software/scm/git/docs/git-stash.html

# Links
* http://help.github.com/removing-sensitive-data/
* http://www.uhlme.ch/artikel.php?artikel=git
* http://www.kernel.org/pub/software/scm/git/docs/gittutorial.html
* https://gist.github.com/569530
* http://www.kernel.org/pub/software/scm/git/docs/everyday.html
* http://365git.tumblr.com/post/474079664/whats-the-difference-part-1
* http://linux.yyz.us/git-howto.html
* http://cheat.errtheblog.com/s/git
* http://progit.org/book/

