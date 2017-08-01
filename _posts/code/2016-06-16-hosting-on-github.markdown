---
layout: post
title:  "Hosting one or more websites on github.io"
permalink: /code/hosting-one-or-more-websites-on-github.io/
date:   2016-06-16
tags:   code jekyll
categories: code
---

Github allows you to host a static website on its servers. The benefit is that because it is a static site it can take advantage of their CDN and it is fast.
The downside (if you choose to see it as one) is that it is a static site - no database, no server side interaction. Basically read only.
Personally I love it and it becomes very useful when using Jekyll to generate the site for you.

Below I'll go through the very basic steps of setting up a site on github.io and pointing your domain to it

&nbsp;

##### 1. Setting up your site on github.io
To create your first site you'll need to create a new repo on Github called `username.github.io` (where username is your Github username). In the `master` branch
add and commit an `index.html` file. Add a line of text in there so you'll know it is working: `<h1>Hello Github</h1>`

Once you pushed these changes point your browser to `http://<username>.github.io` and you should see the index file displayed.

&nbsp;

##### 2. Point your domain to your hosted site
Add and commit a new file called `CNAME` to your repo with a single line of text that points to your site:
```
www.yoursite.com
```

The following will differ depending on your hosting provider where the domain is parked but the gist of it is the same in that you need to update your A or C record to point
to github. At the time of writing the IP was 192.30.252.153.

* Login to your cPanel
* Navigate to Advanced Zone Editor
* Update the A record of yoursite.com to point to 192.30.252.153

&nbsp;

```
Name          | Type | Record  
--------------|------|---------------
yoursite.com. | A    | 192.30.252.153

```
&nbsp;

That should be all. If you point your browser to `http://www.yoursite.com` you'll see your site displayed. Free hosting!

&nbsp;

##### 3. Sub project sites
Any other repo (let's call it `popcorn`) you may have can be used to host a website. What you'll need to do is create a `gh-pages` branch and commit your site to it.
It will then be accessible through `http://www.yoursite.com/popcorn`

However, what if you want to host multiple sites on one github account? In your `popcorn` repo's `gh-pages` branch, add another CNAME file and repeat step 2 above but using your `popcorn.com` domain.

&nbsp;

##### 4. Done!
Once done you should have two repos each with its own domain:

`http://www.yoursite.com` in the `master` branch of `username.github.io`\\
`http://www.popcorn.com` in the `gh-pages` branch of `popcorn`
