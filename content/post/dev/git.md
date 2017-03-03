+++
categories = ["developement"]
date = "2017-03-02T16:24:32+01:00"
description = "Some useful notes on GIT usage"
title = "GIT"
draft = false
thumbnail = "/img/logo/git.png"
tags = [
	"SCM",
	"GIT"
]
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
