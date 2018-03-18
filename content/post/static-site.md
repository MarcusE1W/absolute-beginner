+++
title = "Create a static web site with Hugo"
date = "2017-12-07"
hide_authorbox = false
disable_comments = false
categories = ["Static site generation"]
tags = ["Hugo"]
aliases = ["/post/all-grown-up/"]
draft = true
+++

Static web sites are an excellent start to set up your blog or web site and you can be up and running in a few hours.

<!--more-->

# Beginners guide for a static web site with Hugo

A web site is called static if the content that is presented largely does not change like it is for a blog. A dynamic web site is often generated based on data base queries and other dynamic content.

If you want to create your own blog or static web site you essentially need two things.
- a static site generator tool that transforms your tests into a web site and adds a nice template
- a web hoster where you can upload your site so that everyone can acces it

## Choosing a static site generator tool

There are quite a lot good options available to create your site. Here are some alternatives that I have looked at.
- Jekyl - the apparenlty currently most used static site generator (Jan 2018) supported by GitHub.
- Pelican - preview server did not start for me
- Hexa - looks all right
- Middleman - seems to be powerful and a bit more complex
- Hugo - seems to be easy to use and only consists of one binary, so easy to install. Some good reviews as well from people who write their own blog with hugo.

After a bit of trying this and that I decided for Hugo.

# Creating a static site with Hugo

## Installing Hugo

- **Archlinux** : `sudo pacman -S hugo`
- **macOS** : follow the instructions on the [Hugo site](http://gohugo.io/getting-started/quick-start/)

to check the installation was successful type `hugo version`

## Setting up a site

### Create the draft site from a template
`hugo new site siteName`

### Add a theme

As an example the Dream template from the [Hugo template page](https://themes.gohugo.io/) will be installed in the new site (e.g quickstart)

```bash
cd quickstart
git init
git submodule add https://github.com/g1eny0ung/hugo-theme-dream themes/dream
```

**Configure the Dream theme**

Edit `config.toml`

### Add articles

<!-- TODO explain front matter -->

### Add images

_All files under the static/ directory are copied to public/ when Hugo renders a website. This directory is often used to store static web assets like images, CSS, and JavaScript files. For example, an image static/foo/bar.png can be embedded in your post using the Markdown syntax ![](/foo/bar.png)._

### Check the look of the siteName

Start a hugo preview server
`hugo server -D`
This will show your site includin all draft documents (that's what the `-D` does)

Open this page  http://localhost:1313/ to view your new site.

### Prepare to deploy

After you have created some content and are quite happy with it you can deploy it to the world wide web.

Before you publish your site you need to remove the `draft` mark from the front matter on the top of your articles. Only those articles that are **not** marked `draft` will be publisched.

To check the final result you can close the hugo preview and start a new one.
`hugo server`
This time with out `-D`. This will only show final articles.

Check your site and if all is well create the final site with
`hugo`

Now you are ready to deploy. Your static site is in folder `public`

### Deploy your static site

There are many ways to deploy your site and as is is static it is almost just like copying your site to your host.

Free and popular are:
- [Github.io](https://help.github.com/articles/what-is-github-pages/)
- [Netlify.com](https://www.netlify.com/)

Here are some texts that have help me to choose the host:

### Find open source picture

https://www.pexels.com/



### Handle submodules
- get the submodule initially
`git submodule add ssh://bla submodule_dir`
`git submodule init`

- time passes, submodule upstream is updated  and you now want to update

- change to the submodule directory
`cd submodule_dir`

- checkout desired branch
`git checkout master`

- update
`git pull`

- get back to your project root
`cd ..`

- now the submodules are in the state you want, so
`git commit -am "Pulled down update to submodule_dir"`
