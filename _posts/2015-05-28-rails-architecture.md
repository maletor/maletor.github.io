---
layout: post
title: Rails Architecture
---

# Rails architecture

I recently came across a [great article](http://naildrivin5.com/blog/2014/05/27/rails-does-not-define-your-application-architecture.html) that emphasises an object orientated approach to view templates. 
All too often Rails projects end up with the "fat model" design pattern that spread alongside the "skinny controller" dogma and, while it was well intentioned, led to some problems.
Not everything in `app/models` must inherit from ActiveRecord::Base!
