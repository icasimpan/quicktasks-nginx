---
title: "Apache Redirect for http to https via .htaccess"
date: 2020-07-10T00:20:25+08:00
tags: [apache, webserver, .htaccess, redirect]
draft: false
---

```
...
RewriteCond %{HTTPS} off
RewriteCond %{HTTP:X-Forwarded-Proto} !https
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
...
```
