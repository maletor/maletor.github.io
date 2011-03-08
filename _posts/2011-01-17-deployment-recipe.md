---
layout: post
title: Deployment Recipe
---

It is important to remember to split up the web server and the app server. We can do this by setting up NGINX as a front end reverse proxy and using Unicorn, the new kid on the block, for serving up HTTP.

For the stack I use Ubuntu 9.10 with 4 terabytes in a RAID 5, making an effective 3 terabytes. NGINX, Unicorn and Rails run on top of this. If I were getting 2 - 300 requests per minute I would probably need some kind of process monitoring framework such as God. It is also important to host your assets, javascripts, stylesheets, images, on a server different from the one you run your application on. A good solution for this is Amazon S3 or Slicehost. This is per Yahoo's exhaustive list of best practices. With this in place we should be scalable, speedy, and secure.

{% highlight nginx linenos %}
worker_processes 4

working_directory "/var/www/ellisberner/"

listen "/var/run/unicorn.sock", :backlog => 2048

timeout 30

pid "/var/run/unicorn.pid"

stdout_path "/var/log/unicorn.log"
{% endhighlight %}

This is the standard NGINX config that comes with the Ubuntu package. You should set the workers to the number of cores on your processor. In addition, it is important to have the master worker running as root and the slaves running with www-data.

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
