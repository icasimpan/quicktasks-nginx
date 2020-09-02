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

Use below if need to redirect non-www to www
```
...
  RewriteCond %{HTTP_HOST} !foo\.example\.com [NC]  # exclude foo.example.com domain
  RewriteCond %{HTTP_HOST} !bar\.example\.net [NC]  # exclude foo.example.net domain
  RewriteCond %{HTTP_HOST} .
  RewriteCond %{HTTP_HOST} !^www\. [NC]
  RewriteRule ^ http%{ENV:protossl}://www.%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
...
```
