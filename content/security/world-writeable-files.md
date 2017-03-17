+++
description = "Howto find world writable files that could be attacked on your server?"
title = "Scanning a Filesystem for files with weak restrictions"
draft = false
thumbnail = ""
tags = [
	"shell",
	"security",
	"linux",
	"hacking"
	]
categories = []
date = "2008-06-05T14:45:52+01:00"
aliases = ["/security/scanning-filesystem-files-with-weak-retriktions"]
project2030 = "migrated"
+++

Howto find world writable files that could be attacked on your server?

<!--more-->

{{< highlight bash "style=emacs" >}}
find / -perm -2 ! -type l -ls
{{< /highlight >}}
