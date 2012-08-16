# CruCornell Website

Source for CruCornell.com.

A simple Jekyll-generated site to allow for ease of maintenance by busy Cornell students.

TODO: introduction and rationale

## Getting Started

### For Developers

* Bear in mind that I kindof assume you're either on a Mac or Linux. The directions may need to be adapted a bit if you're on Windows.
* [Have a GitHub account](https://github.com/signup/free)
* Be added as a member of [the crucornell organization](https://github.com/crucornell) ([email me](mailto:webmaster@crucornell.com))
* [Have Git setup on your machine](https://help.github.com/articles/set-up-git)
* [Know a bit about Git](https://github.com/blog/120-new-to-git/) so you can collaborate on the site with us stepping on one-another's toes
* [Have Ruby setup on your machine](http://www.ruby-lang.org/en/downloads/)
* [Have the Jekyll gem installed](https://github.com/mojombo/jekyll/wiki/install)
* [Know a bit about Jekyll](http://klepas.org/jekyll-a-static-site-generator/) (<-- Nice blog post about Jekyll. Note that [_our_ blog is on Tumblr](http://crucornell.tumblr.com), and we're using Jekyll's "blog-awareness" in a non-standard way: for the front-page carousel. If this doesn't make sense yet, don't worry about it.)
* Finally, clone [the main repository](https://github.com/crucornell/crucornell.github.com) on your machine with
  > git clone git@github.com:crucornell/crucornell.github.com.git

### For Designers and Content Editors

* [Have a GitHub account](https://github.com/signup/free)
* Be added as a member of [the crucornell organization](https://github.com/crucornell) ([email me](mailto:webmaster@crucornell.com))
* [Know about Prose](http://developmentseed.org/blog/2012/june/25/prose-a-content-editor-for-github/): you'll authenticate with GitHub through [Prose.io](http://prose.io]), go to the crucornell organization, go to the crucornell.github.com project, and edit files and stuff directly on the site, which then need to be uploaded to crucornell.com by the webmaster
* Notice that when you make changes, you can preview them at [crucornell.github.com](http://crucornell.github.com).
* Read **Cru Website Layout and Conventions** below so you know about how we do stuff (like change carousel images and use page "templates".)

## Normal Development Workflow

1. Pull down and merge in the latest changes by other people.
   > git pull origin master
2. Work on stuff.
3. Whenever you've done a logical unit of work (small), commit your work to your local repository so it cannot be lost.
   > git commit -am "This 'commit message' should be generally pretty short describing what you did since the last commit."
4. Repeat steps 2 and 3 until you're ready to show the world.
5. Pull down and merge in the latest changes by other people (again, in case someone's changed stuff while you're been working).
   > git pull origin master
6. Resolve any conflicts (when you and someone else have edited the same file or something) and commit the resolutions if necessary.
7. Push everything to the remote repository on GitHub!
   > git push origin master
8. Check out how things look at [crucornell.github.com](http://crucornell.github.com) (GitHub may take up to ten minutes to regenerate the site after a push) 
9. Celebrate with some nice, refreshing homework. Then start over at step 1.
10. The webmaster will upload the site to crucornell.com occasionally, whenever he or she is satisfied it's awesome.


If you're using some graphical face to Git, you're on your own. :)

# Cru Website Layout and Conventions

Coming soon. TODO