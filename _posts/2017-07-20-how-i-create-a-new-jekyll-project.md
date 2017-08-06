---
layout: single
title:  "How I Create a New Jekyll Project"
date:   2017-07-20
modified:   2017-08-05
description: "..."
excerpt: "I use a somewhat persnickety process for starting any given project. This is my chosen
method for starting a Jekyll site."
categories: article
tags:
- beginner
- jekyll
---

![The Completed Project Structure](/assets/images/jekyll/default-jekyll-directory-structure.png)

I use a somewhat persnickety process for starting any given project. This is my chosen method for
starting a Jekyll site. I prefer to use the latest component versions for any given tech stack.
While most would just dig in with `jekyll new new_site`, I prefer to be a little more precise.

## Initialize Project

### Directory

In order to lock down the versions of libraries I want and initialize things in a way I prefer, I
simply create a directory (a step that most tools would do themselves).

{% highlight bash %}
$ mkdir new-site
$ cd new-site
{% endhighlight %}

The above statements create and then change to a new directory named "new-site".

### Ruby

I *strongly* suggest the usage of a library version management tool. I use rbenv. Your tool of
choice should help you manage which version of a language VM you have installed (in this case
`ruby`).

{% highlight bash %}
$ rbenv local 2.4.1
{% endhighlight %}

This creates a `.ruby-version` file, indicating to many developer tools which version of `ruby` the
project expects to run upon. (In this case, I'm locking down to ruby `2.4.1`.)

### Bundler

With `ruby` locked down, we have a fairly isolate environment to run our application in. In this
instance we will be running the `jekyll` static site generator (based on `ruby`) to build our
site.

It's best to manage a `ruby` based project via `bundler`.

{% highlight bash %}
$ bundle init
{% endhighlight %}

`bundle init` is the easiest way to get a cleanly installed, basic `Gemfile`.

The default Gemfile will look something like the following:

{% highlight ruby %}
# frozen_string_literal: true
source "https://rubygems.org"

# gem "rails"
{% endhighlight %}

Although bundler init defaults to the rails gem as a sample, it *is* commented, and you certainly
can use any set of valid gems. As we want to install jekyll, we'll uncomment the gem lline and load
jekyll instead.

{% highlight ruby %}
# frozen_string_literal: true
source "https://rubygems.org"

gem "jekyll"
{% endhighlight %}

At this point, a simple `bundle install` should download jekyll and install it into the ruby version
we selected earlier with rbenv.

{% highlight bash %}
$ bundle install
Fetching gem metadata from https://rubygems.org/..............
Fetching version metadata from https://rubygems.org/...
Fetching dependency metadata from https://rubygems.org/..
Resolving dependencies...
Fetching public_suffix 2.0.5
Fetching colorator 1.1.0
Installing colorator 1.1.0
Fetching rb-fsevent 0.10.2
Installing public_suffix 2.0.5
Fetching ffi 1.9.18
Installing rb-fsevent 0.10.2
Fetching kramdown 1.14.0
Installing kramdown 1.14.0
Fetching liquid 4.0.0
Installing liquid 4.0.0
Fetching mercenary 0.3.6
Installing mercenary 0.3.6
Fetching forwardable-extended 2.6.0
Installing forwardable-extended 2.6.0
Fetching rouge 1.11.1
Installing rouge 1.11.1
Fetching safe_yaml 1.0.4
Installing safe_yaml 1.0.4
Using bundler 1.15.1
Fetching addressable 2.5.1
Installing addressable 2.5.1
Fetching pathutil 0.14.0
Installing pathutil 0.14.0
Installing ffi 1.9.18 with native extensions
Fetching rb-inotify 0.9.10
Installing rb-inotify 0.9.10
Fetching sass-listen 4.0.0
Fetching listen 3.0.8
Installing listen 3.0.8
Fetching jekyll-watch 1.5.0
Installing sass-listen 4.0.0
Fetching sass 3.5.1
Installing jekyll-watch 1.5.0
Installing sass 3.5.1
Fetching jekyll-sass-converter 1.5.0
Installing jekyll-sass-converter 1.5.0
Fetching jekyll 3.5.1
Installing jekyll 3.5.1
Bundle complete! 1 Gemfile dependency, 20 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
{% endhighlight %}

### Jekyll New

Now we have jekyll installed, we want to force a new jekyll site into our current project directory.
Most command-line tools will allow you to pass `.` as the current directory, or `..` as the parent
directory. We can replace the `site-name` parameter from a typical `jekyll new site-name` with a `.`

{% highlight bash %}
$ jekyll new .
         Conflict: /Users/curtis/src/koc/new-site exists and is not empty.
{% endhighlight %}

When we try, however, we'll notice the error message above. This is a safety guard in the jekyll
project to prevent you from dropping a site skeleton into any random folder on your hard drive.
We know what we are doing, though. So let's override this behavior with the `--force` flag.

{% highlight bash %}
$ jekyll new . --force
Running bundle install in /Users/curtis/src/koc/new-site...
  Bundler: The dependency tzinfo-data (>= 0) will be unused by any of the platforms Bundler is
    installing for. Bundler is installing for ruby but the dependency is only for
    x86-mingw32, x86-mswin32, x64-mingw32, java. To add those platforms to the bundle,
    run `bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java`.
  Bundler: Fetching gem metadata from https://rubygems.org/............
  Bundler: Fetching version metadata from https://rubygems.org/...
  Bundler: Fetching dependency metadata from https://rubygems.org/..
  Bundler: Resolving dependencies...
  Bundler: Using public_suffix 2.0.5
  Bundler: Using colorator 1.1.0
  Bundler: Using rb-fsevent 0.10.2
  Bundler: Using ffi 1.9.18
  Bundler: Using kramdown 1.14.0
  Bundler: Using liquid 4.0.0
  Bundler: Using mercenary 0.3.6
  Bundler: Using forwardable-extended 2.6.0
  Bundler: Using rouge 1.11.1
  Bundler: Using safe_yaml 1.0.4
  Bundler: Using bundler 1.15.1
  Bundler: Using addressable 2.5.1
  Bundler: Using rb-inotify 0.9.10
  Bundler: Using pathutil 0.14.0
  Bundler: Using sass-listen 4.0.0
  Bundler: Using listen 3.0.8
  Bundler: Using sass 3.5.1
  Bundler: Using jekyll-watch 1.5.0
  Bundler: Using jekyll-sass-converter 1.5.0
  Bundler: Using jekyll 3.5.1
  Bundler: Fetching minima 2.1.1
  Bundler: Fetching jekyll-feed 0.9.2
  Bundler: Installing minima 2.1.1
  Bundler: Installing jekyll-feed 0.9.2
  Bundler: Bundle complete! 4 Gemfile dependencies, 22 gems now installed.
  Bundler: Use `bundle info [gemname]` to see where a bundled gem is installed.
  Bundler: The latest bundler is 1.15.3, but you are currently running 1.15.1.
  Bundler: To update, run `gem install bundler`
New jekyll site installed in /Users/curtis/src/koc/new-site.{% endhighlight %}

If you get error messages when you try to create the site, it's probably unhappy about the
existing `Gemfile`, you *may* need to delete the Gemfile from the directory (`rm -rf Gemfile`) and
rerun the `jekyll new . --force` command. (Even if you do get an error, it's likely that the site
has been created regardless, and a simple `bundle install` will complete successfully.)
{: .notice--warning}

### Git

If you're unfamliar with the `git` version control system, you *can* skip this part, but it's
worthwhile to perform these steps. If you're entirely unfamliar with git, it's wise to
[Learn Enough Git to Be Dangerous][learn-enough-git].
{: .notice--info}

If you look in your jekyll directory, you'll find a `.gitignore` file. This file ensures certain,
unwanted files won't be stored in our git repository. (I generally prefer to wait until this file
is created before creating the git repository, but it's not neccessary. It *is*, however, why I've
waited until this point to initialize git.)

### Git Init

{% highlight bash %}
$ git init
Initialized empty Git repository in /Users/curtis/src/koc/new-site/.git/
{% endhighlight %}

The above command initializes a new git repository on our local development environment.

### Git Status

{% highlight bash %}
$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.gitignore
	.ruby-version
	404.html
	Gemfile
	Gemfile.lock
	_config.yml
	_posts/
	about.md
	index.md

nothing added to commit but untracked files present (use "git add" to track)
{% endhighlight %}

The above command shows the current status of the git repository. As it stands, we just Initialized
the repository, so all files are currently untracked. We'll need to track them before we can commit
them.

### Git Add

{% highlight bash %}
$ git add --all
{% endhighlight %}

The above command adds all untracked files to the repository for future tracking.

{% highlight bash %}
$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   .gitignore
	new file:   .ruby-version
	new file:   404.html
	new file:   Gemfile
	new file:   Gemfile.lock
	new file:   _config.yml
	new file:   _posts/2017-07-20-welcome-to-jekyll.markdown
	new file:   about.md
	new file:   index.md
{% endhighlight %}

`git status` now shows files are tracked and ready to be committed. It also shows the per-file
status ("new file:"). In this case all files are the same, but would differ over time as you make
modifications and commits.

### Git Commit

{% highlight bash %}
$ git commit -m "Initial commit."
[master (root-commit) 9e91c6d] Initial commit.
 9 files changed, 205 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 .ruby-version
 create mode 100644 404.html
 create mode 100644 Gemfile
 create mode 100644 Gemfile.lock
 create mode 100644 _config.yml
 create mode 100644 _posts/2017-07-20-welcome-to-jekyll.markdown
 create mode 100644 about.md
 create mode 100644 index.md
{% endhighlight %}

The above command commits the changes, using a shortcut parameter (`-m`) to specify a brief
commit message via the command. In general, you'll want to
[provide good commit messages][thoughtbot-git-commit-tips].

### Git Push

A wise programmer pushes code to a remote server early and often. I use Github. Many developers
and engineering departments use it too. There are others which are also used. It doesn't really
matter which one you use, once you've learned one, you've learned enough to use them all.

Once you've created a repository on a remote site, you can add that repository URI as a remote
destination to your code repository and push your code.

{% highlight bash %}
$ git remote add origin git@github.com:knightoftheoldcode/new-site.git
$ git push -u origin master
Counting objects: 12, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (10/10), done.
Writing objects: 100% (12/12), 3.79 KiB | 0 bytes/s, done.
Total 12 (delta 0), reused 0 (delta 0)
To github.com:knightoftheoldcode/new-site.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
{% endhighlight %}

The above commands (usually noted on the results page after creating a remote repository) tie your
local repository to to the remote repository using the tag "origin".

Don't worry if this "push" section is a challenge, using remote repositories is certainly more
complex than using git locally. Again, this functionality is well covered in
[Learn Enough Git to Be Dangerous][learn-enough-git].
{: .notice--info}

## Check Project

### Jekyll Server

Jekyll contains many available commands to help you build a website. One of those features is an
integrated web server.

{% highlight bash %}
$ jekyll server
Configuration file: none
            Source: /Users/curtis/src/koc/new-site
       Destination: /Users/curtis/src/koc/new-site/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 0.007 seconds.
 Auto-regeneration: enabled for '/Users/curtis/src/koc/new-site'
    Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
{% endhighlight %}

The above tells us our base installation of jekyll is good. You can verify this by hitting
http://localhost:4000 in your browser.

![Default Jekyll Site](/assets/images/jekyll/default-jekyll-site.png)

## What We've Done

At this point, we're left with a fairly clean project.

- a new default jekyll site (with all the fixins')
- a ruby lock-down
- a clean git repository
- a [remote repository][github-knightoftheoldcode-new-site]

[learn-enough-git]: http://amzn.to/2fhJqx2
[thoughtbot-git-commit-tips]: https://robots.thoughtbot.com/5-useful-tips-for-a-better-commit-message
[github-knightoftheoldcode-new-site]: https://github.com/knightoftheoldcode/new-site