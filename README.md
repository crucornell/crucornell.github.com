# CruCornell Website

Source for CruCornell.com.

A simple Jekyll-generated site to allow for ease of maintenance by busy Cornell students.

## Introduction

The Cru website was originally developed as a WordPress theme, but it quickly became clear that the learning curve for new web-team members was too high, and that development on the site had stalled. In an effort to simplify things, the design was rebuilt as a Jekyll-generated static site and two Tumblr blogs (for the dynamic content that should be editable by non-technical people: News and Events and the Cru Blog).

## Getting Started

### For Developers

* Bear in mind that I kindof assume you're either on a Mac or Linux. The directions may need to be adapted a bit if you're on Windows. [This blog post](http://blog.ntotten.com/2012/03/02/github-pages-with-jekyll-local-development-on-windows/) will get you through the Jekyll install on Windows.
* [Have a GitHub account](https://github.com/signup/free)
* Be added as a member of [the crucornell organization](https://github.com/crucornell) ([email me](mailto:webmaster@crucornell.com))
* [Have Git setup on your machine](https://help.github.com/articles/set-up-git)
* [Know a bit about Git](https://github.com/blog/120-new-to-git/) so you can collaborate on the site without us stepping on one-another's toes
* [Have Ruby setup on your machine](http://www.ruby-lang.org/en/downloads/)
* [Have the Jekyll gem installed](https://github.com/mojombo/jekyll/wiki/install)
* [Understand Jekyll well](http://klepas.org/jekyll-a-static-site-generator/) (<-- Nice blog post about Jekyll. Note that [_our_ blog is on Tumblr](http://crucornell.tumblr.com), and we're using Jekyll's "blog-awareness" in a non-standard way: for the front-page carousel. If this doesn't make sense yet, don't worry about it.)
* It would probably help to [know a little bit about Markdown](http://daringfireball.net/projects/markdown/basics/), 'cause it's cool and Jekyll and GitHub have native support for it. This README.md was written with Markdown, which GitHub automatically displays as HTML.
* Finally, clone [the main repository](https://github.com/crucornell/crucornell.github.com) on your machine with

  > git clone git@github.com:crucornell/crucornell.github.com.git

### For Designers and Content Editors

* [Have a GitHub account](https://github.com/signup/free)
* Be added as a member of [the crucornell organization](https://github.com/crucornell) ([email me](mailto:webmaster@crucornell.com))
* [Know about Prose](http://developmentseed.org/blog/2012/june/25/prose-a-content-editor-for-github/): you'll authenticate with GitHub through [Prose.io](http://prose.io]), go to the crucornell organization, go to the crucornell.github.com project, and edit files and stuff directly on the site, which then need to be uploaded to crucornell.com by the webmaster
* Notice that when you make changes, you can preview them at [crucornell.github.com](http://crucornell.github.com).
* Read **Cru Website Layout and Conventions** below so you know about how we do stuff (like change carousel images and use page "templates".)

## Normal Development Workflow

1. Run to start a server that automatically rebuilds the site when you change files, and serves the site from [http://localhost:4000/](http://localhost:4000/) for your convenience:
   
   > jekyll --server --auto
   
2. Pull down and merge in the latest changes by other people.
   
   > git pull origin master
   
3. Work on stuff.
4. Whenever you've done a logical unit of work (small), commit your work to your local repository so it cannot be lost.
   
   > git commit -am "This 'commit message' should be generally pretty short describing what you did since the last commit."
   
5. Repeat steps 2 and 3 until you're ready to show the world.
6. Pull down and merge in the latest changes by other people (again, in case someone's changed stuff while you're been working).
   
   > git pull origin master
   
7. Resolve any conflicts (when you and someone else have edited the same file or something) and commit the resolutions if necessary.
8. Push everything to the remote repository on GitHub!
   
   > git push origin master
   
9. Check out how things look at [crucornell.github.com](http://crucornell.github.com) (GitHub may take up to ten minutes to regenerate the site after a push) 
10. Celebrate with some nice, refreshing homework. Then start over at step 1.
11. The webmaster will upload the site to crucornell.com occasionally, whenever he or she is satisfied it's awesome.


If you're using some graphical face to Git, you're on your own. :)

# Cru Website Layout and Conventions

The Cru website makes use of Jekyll in some interesting ways, which are probably best understood by cloning the repository and poking around. Some of the more important wizardry is explained below.

## Normal Layout

With a few exceptions, the Cru website uses the normal Jekyll layout, which is:

* _includes/ - contans reusable small pieces of the layout like the navigation bar, header and footer, used in templates and pages
* _layouts/ - contains the main page templates used by individual pages
* _posts/ - *unlike* normal Jekyll usage, doesn't contain blog posts, so to speak, but rather contains metadata necessary to display the hero images in the front-page carousel - see below
* _config.yml - site-wide configuration file
* _site/ - when you run jekyll command, the generated site goes in this directory

All other folders and files (except those ignored by _config.yml) are transformed by Jekyll (templates applied and Markdown converted to HTML, etc.) and copied into "_site/", the contents of which is what gets uploaded to the main web server periodically (the "generated" site).

## Cru Special Cases

* The file "tumblr_theme.html" is a back-up of the tumblr theme that looks like the blog, and is ignored in _config.yml.
* The file "deploy" is the deployment script for regenerating the site and uploading it to the main website with rsync. Only the webmaster knows the username and password, so only the webmaster can change the live site with:
  > ./deploy USERNAME
* "Static" assets are in the "assets/" directory, which contains three sub-directories: "stylesheets/", "javascripts/" and "images". Even these will get processed by Jekyll if they contain YAML front-matter.

## Cru Conventions

### Front-Page Carousel

The front-lage carousel is populated dynamically from the contents of "_posts/". Each file in there has special YAML front-matter (metadata) which specifies a hero image to be displayed.

*They are ordered in reverse-order by date*, which is determined by the filename by default, but may be overridden inside the metadata. The following information must be provided in the metadata for an image to be displayed correctly in the front-page carousel:

* src: assets/images/heroes/blogmoved.jpg - relative path to hero image, which  *must* be 880x350
* href: blog - relative link to internal page a user will be taken to when they click the hero image
* title: New Blog - text to be displayed when a user hovers the mouse over the hero image
* published: true - whether or not to display the image at all
* date: 2012-06-01 - optional. the date you would like the system to *think* the image was created, if different from the one in the filename

A file in posts must have this format:

> YYYY-MM-DD-some-name-for-your-own-memory-aid.md

### Common Page Layouts

All pages (with the exception of index.html) must specify a layout (from "_layouts", and add one if necessary) and a title in the YAML front-matter. The following layouts are available to you already, and of course you may make your own.

* Pages with a sidebar (like "about-us") should use the convention in existing sidebar pages. For instance, "about-us" and sub-pages all use the "about-us" layout because that layout knows what pages are in the sidebar, contains their text and links, and renders the sidebar accurately based on the user's current location in the sub-pages.
* Pages without a sidebar may use the "without-sidebar" layout.
* Pages that should appear under a strikingly beautiful hero image should use the "under-image" layout, and specify a "link" (where you want to go if you click the hero image) and "src" (where the hero image should come from, which *must* be 880x350) in addition to the "layout" and "title". Check out "the-mott-house.md" for an example.
* Pages that should appear under a Vimeo video iframe should use the "under-video" layout, and specify a "src" for the iframe in addition to the usual "layout" and "title". Note that this layout could be used to display *anything* you specify as the "src" that fits into the 880x350 hero box. Check out "upstate-fall-retreat.html" as an example.

### Miscellaneous Important

* *ANY* page in the site may be either HTML or Markdown (or any of the other templating languages Jekyll supports). A case in point would be the-mott-house.md, which was converted to Markdown just to make an example. When you generate the site, this gets converted to the-mott-house.html with appropriate formatting.
* There's actually a misc/ directory in which you could put some random pages that don't seem to fit anywhere else in the hierarchy, FYI.

