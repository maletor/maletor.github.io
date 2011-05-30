---
layout: post
title: Deployment Recipe
---

## Deployment Recipe

It is important to remember to split up the web server and the app server. We can do this by setting up [NGINX](http://nginx.org) as a front end reverse proxy and using [Unicorn](http://unicorn.bogomips.org/) for serving up the HTTP/S server.

For the stack I use [Ubuntu](http://ubuntu.com) 10.10 with 4 terabytes in a [RAID 5](http://en.wikipedia.org/wiki/RAID), making an effective 3 terabytes. NGINX, Unicorn and [Rails](http://rubyonrails.org) run on top of this. If I were getting 2 - 300 requests per minute we would probably need some kind of process monitoring framework such as [God](http://god.rubyforge.org/) or [monit](http://mmonit.com/). It is also important to host your assets, javascripts, stylesheets, images, on a server different from the one you run your application on. A good solution for this is [Amazon S3](http://s3.amazon.com) or [Slicehost](http://slicehost.com). This is per [Yahoo's list of best practices](http://developer.yahoo.com/performance/rules.html). Key issues are always going to be scalability, security and speed.

{% highlight nginx linenos %}
worker_processes 4

working_directory "/var/www/ellisberner/"

listen "/var/run/unicorn.sock", :backlog => 2048

timeout 30

pid "/var/run/unicorn.pid"

stdout_path "/var/log/unicorn.log"
{% endhighlight %}

This is the standard NGINX config that comes with the Ubuntu package. You should set the workers to the number of cores on your processor. In addition, it is important to have the master worker is running as a privilaged user and the slaves are running as www-data.

{% highlight nginx linenos %}
upstream unicorn {
    server unix:/var/run/unicorn.sock fail_timeout=0;
}

server {
	listen 80;
	server_name ellisberner.com;
	root /var/www/ellisberner/public;
	access_log /var/log/nginx/ellisberner.access.log;

	location / {
        	try_files $uri @unicorn;
	}

	location @unicorn {
		proxy_pass http://unicorn;
		proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
		proxy_set_header Host $host;
		proxy_redirect off;
	}
}
{% endhighlight %}
