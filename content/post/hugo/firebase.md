+++
tags = [
	"firebase",
	"hosting",
	"hugo"
]
categories = ["howto"]
date = "2017-03-05T00:09:41+01:00"
description = "Howto host you Hugo site on firebase using gitlab for source and CI"
title = "Hosting a Hugo site with firebase"
draft = false
thumbnail = "/img/logo/firebase.png"

+++
This are all the steps needed to deploy your static [Hugo](/tags/hugo) page on [Firebase](/tags/firebase) for free (until you exceed the traffic of the free tier a.k.a Spark plan).
<!--more-->

# Firebase

## Create a Firebase project
1. Go to https://console.firebase.google.com and create a new project (unless you already have a project and this is just an additional component to it). 
2. Install `firebase-tools` (node.js) using: `npm install -g firebase-tools`
3. Login to firebase (setup on your local machine) using `firebase login` which opens a browser and you can select your account. Use `firebase logout` in case you are already logged in but to the wrong account.
3. In the root of your hugo site initialize the Firebase project with `firebase init`
4. Choose Hosting in the feature question
5. Choose the project you did just setup
6. Accept the default for database rules file
7. Accept the default for the publish directory which is `public`
8. Choose No in the question if it is a single-page app
10. Create a `deploy.sh` file with the following content and make it executable `chmod +x deploy.sh`:

{{< highlight bash "style=emacs" >}}
#!/bin/sh
rm -rf public
hugo
firebase deploy
{{< /highlight >}}

9. Commit those files into your repository
10. Deploy your page using `./deploy.sh`


## Map a custom domain to a Firebase project
//TODO

# Gitlab.com

## Configure CI runner
1. Get a deploy token for your Firebase project executing ```firebase login:ci```which will bring up a browser with the authentication dialog and afterwards gives you a token to be used in CI
2. In your GitLab project, go to Pipelines > Environments and then add a new environment called Production

//TODO
