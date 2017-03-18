---
categories:
- howto
tags:
- security
- apache
- administration
- ssl
created: 1199097851
date: 2007-12-31T11:44:11Z
title: Apache Force SSL on vhost
aliases: /wiki/Apache_Force_SSL_on_vhost
project2030: migrated
---
Howto configure Apache to redirect all http requests to the SSL version of the site.

<!--more-->

Edit your htaccess (or server conf file) to look like this one :
{{< highlight xml "style=emacs" >}}
<Files *.ini>
Order Allow,Deny
Deny from all
</Files>

RewriteEngine on
RewriteBase /

RewriteCond %{SERVER_PORT} !443
RewriteRule ^(.*)?$ https://%{SERVER_NAME}$1 [L,R]
{{< /highlight >}}
For thoses of you who don't know about RewriteCond, the first one checks the server port used to connect. If it's not 443 (default HTTPS port), it redirects all request to the same https vhost and URI.


<strong>Reference</strong>
<li> https://trac.usvn.info/wiki/Documentation/HTTPSAccess</li>
