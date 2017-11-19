---
title: "Create Your Own Blog With Hugo Static Website Generator"
author: "Peter Puglisi"
cover: "/img/cover.jpg"
tags: ["Hugo", "JAMStack"]
date: 2017-11-04T13:08:29+10:00
---

## How To Create Your own Blog With Hugo Website Generator

For a long time now I've put creating my own blog, mainly because of a lack of motivation and thinking i just don't have the time.  After spending some time reading posts and watching videos from John Sonmez at simpleprogrammer.com, I decided it was finally time to take the plunge as I understood the benefits of having your own blog greatly outweighed not starting one.

John Sonmez recommends just using Wordpress but after reading up about the benefits of  static websites and the power of the ["Jam Stack"](https://jamstack.org/), I decided to build my blog using a JAM stack approach using Hugo static website generator.

There are a number of cool static website to chose from but after some online research I decided on Hugo because of it's simplicity and speed.  If you're going through the motions of choosing your own static website generator I highly recommend [Hugo](http://hugo.io/)  It's speed, simplicity and rising popularity were compelling reasons for me.

In this blog post I'm going to save you some time and give you an overview on how I built my site. I won't go into the nitty gritty details as I'm going to assume those reading this have a development background or website design experience.

Here are the tools and APIs I've used to build and maintain this blog in a Windows development environment: 

* [Visual Studio Code](https://code.visualstudio.com/) - There are a number of popular text editors out there for developers like Sublime and Atom but I'm sold on Visual Studio Code because it's fast, free, growing in popularity and offers a smooth integration with Git.

* [Git](https://git-scm.com/) - Simple UI and console tools for interfacing with Git.

* [Netlify](https://www.netlify.com) - Simplifies hosting and deployment of your static website using the Netlify CDN. They have a free subscription option that is perfect for anyone starting their own blog using a static website generator. I'm currently using their personal plan for this blog and setup my custom domain to point to their DNS servers. Everdything has gone smootly since I launched the blog and I haven't needed to use their email or chat support which only comes with their paid plans.

* [Hugo](https://gohugo.io) - A fast, flexible and popular static website generator.

* [Disqus](https://disqus.com/) - Comments and engagment plugin.


### Step 1 - Install Hugo and add the Hugo binary path to your user environment path

* Firstly I downloaded the latest binary release from [here](https://github.com/gohugoio/hugo/releases). One thing I love about Hugo is the simple installation process, you just need to get the latest .exe file for the version you want to use.
* Add a user environment variable to the path of the Hugo binary you've downloaded.

![Hugo Path Variable](/media/posts/create-your-own-blog-with-hugo-static-website-generator/hugo-path-variable.png)


### Step 2 - Create the new blog and select your theme

```
hugo new site adaptiveprogrammer.com
cd adaptiveprogrammer.com
git init
```

I then selected a theme I liked from [Huho Themes](https://themes.gohugo.io). I chose the [Hugo Nuo](https://themes.gohugo.io/hugo-nuo/) theme.

To install the theme, I ran this:

```
cd themes
git clone https://github.com/laozhu/hugo-nuo 
```

Next I ran hugo once to build your initial site:

```
hugo
```

This creates an extra `public` folder containing the built html files to be deployed.

{{<highlight dos "hl_lines=6,linenostart=1">}}
archetypes
config.toml
content
data
layouts
public
static
themes
{{</highlight>}}


### Step 3 - Set up live reload for visual feedback while working on markdown context

One of the things I love about Hugo is the fast live reload feature which is built right into Hugo.  

To kick it off, I just run the following from a command line window:

```
hugo server -w
```

Where -w is short for -watch.

```
Started building sites ...

Built site for language en:
0 draft content
0 future content
0 expired content
4 regular pages created
16 other pages created
8 non-page files copied
6 paginator pages created
4 tags created
0 categories created
total in 17 ms
Watching for changes in C:\SITES\adaptiveprogrammer.com\{data,content,layouts,static,themes}
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

If I navigate to `http://localhost:1313/`, I can see site up and running on my machine. Now I can make changes to my site's content and see the rendered changes to my website virtually instantaneously. 


### Step 4 - Setup the site's main configuratiion file `config.toml`

* Here I just copied over the sample config file from `.\themes\hugo-nuo\exampleSite\config.toml` as a first step. The theme's github page at `https://github.com/laozhu/hugo-nuo` had some good documentation on how to get started with the theme.  If you choose a different theme, I suggest checking the theme's github page first for any instructions relevant to setting up that theme.

* For the `hugo-nuo` theme, I setup the main configuration variables as below.

``` yaml
baseURL = "http://adaptiveprogrammer.com"
languageCode = "en"
title = "Adaptive Programmer"
theme = "hugo-nuo"
enableRobotsTXT = true
pygmentsUseClasses = false
pygmentsCodeFences = true
pygmentsCodefencesGuessSyntax = true
canonifyurls = true

# Disqus Username
disqusShortname = "adaptive-programmer"

# Google Analytics UA number
googleAnalytics = "UA-XXXXXXXX-X"

# Copyright of your post
copyright = "© Copyright 2017 - AdaptiveProgrammer.com - Learn. Adapt. Build. Thrive."

# Add your own params here
[params]
  author = "Peter Puglisi"
  avatar = "/img/logo.png"
  seotitle = "Adaptive Programmer - Modern Agile Transformation and Adaptive Software Engineering"
  subtitle = "Learn. Adapt. Build. Thrive."
  description = "A veteran software developer's blog about riding the wave of modern agile transformation. Bloggers mindset: Be happy and satisfied today and always be eager for more."
  paginate = 10

  # Choose your social networks
  email = "peter@peterpuglisi.com"
  github = "peterpuglisi"
  twitter = "puglisi_peter"
  linkedin = "peterpuglisi"
```

### Step 5 - Setup a Disqus Account and update the site configuration with the site's disqus name

For this I just setup an account at [disqus.com](http://www.disqus.com).

And then setup the details for the website I want to add the comments plugin into.

![Disqus settings](/media/posts/create-your-own-blog-with-hugo-static-website-generator/hugo-disqus-settings.png)

Finally all I had to do was configure the disqus name highlighted above in the `config.toml' file.

``` yaml
# Disqus Username
disqusShortname = "adaptive-programmer"
```

### Step 6 - Sign up to Netlify and setup the site configuration

It didn't take long to understand why so many developers love Netlify. Basically Netlify just needs a link to your git repository along with some build commands and it will handle the rest.

Here's my setup for this blog which is pointing to the public Git repository for my website:

![Netlify Setup](/media/posts/create-your-own-blog-with-hugo-static-website-generator/hugo-netlify-setup.png)

* Repository - The Git repository for the AdaptiveProgrammer.com website.

* Build command - For the Hugo Static Website Generatorm this is just `hugo`.

* Public directory - Hugo builds static pages under the public directory and these are the files that are deployed to Netlify's CDN.

All other settings I left as default.


### Step 7 - Setup build environment variables in Netlify

This is where you can override any build environment variables in Netlify for controlling the build process. Here I just set `HUGO_VERSION` to `0.30` to ensure my website is built using the same version of Hugo as my local website.

![Netlify Build Variables](/media/posts/create-your-own-blog-with-hugo-static-website-generator/netlify-build-variables.png)

In my case this is all I needed to do to get the site up and running but Netlify allows more advanced control using a `netlify.toml` file added to the base of your Git repository. In the Netlify configuration file, you can specify build environment variables for different deploy contexts.  For more information about continuous deployment using Netlify, go [here](https://www.netlify.com/docs/continuous-deployment/). 
 

