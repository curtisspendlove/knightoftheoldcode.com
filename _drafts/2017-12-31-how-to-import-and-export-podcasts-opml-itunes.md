---
layout: single
title:  "How to Import and Export Podcasts (OPML) with iTunes"
date:   2017-12-31
description: "..."
excerpt: "I always forget where the Podcasts import/export feature resides in iTunes. This post is for
'future me'."
categories: article
tags:
- itunes
- podcast
- opml
- import
- export
---

![The Completed Project Structure](/assets/images/angular/default-angular-directory-structure.png)

I use a somewhat persnickety process for starting any given project. This is my chosen method for
starting an Angular app. I prefer to use the latest component versions for any given tech stack.

## Initialize Project

AngularCLI prefers a workflow of simply creating a project with the project's generators. In order
to run AngularCLI, you need the following prerequisites installed on your computer:

- [Node.js](https://nodejs.org/en/download/)
- [TypeScript](http://www.typescriptlang.org/#download-links)
- [Angular CLI](https://cli.angular.io)

### Angular-CLI

I *strongly* suggest the usage of a library version management tool. However, the node.js
environment is a little less mature for binary version managers at the moment.
[nvm](https://github.com/creationix/nvm) is a good one (and is available via homebrew). I have my
eye on [asdf](https://github.com/asdf-vm/asdf) as well.

Once you have the above prerequisites installed (node.js, typescript, and angular-cli), you're ready
to generate your angular app.

### Ng New

{% highlight bash %}
$ ng new angular-app
installing ng
  create .editorconfig
  create README.md
  create src/app/app.component.css
  create src/app/app.component.html
  create src/app/app.component.spec.ts
  create src/app/app.component.ts
  create src/app/app.module.ts
  create src/assets/.gitkeep
  create src/environments/environment.prod.ts
  create src/environments/environment.ts
  create src/favicon.ico
  create src/index.html
  create src/main.ts
  create src/polyfills.ts
  create src/styles.css
  create src/test.ts
  create src/tsconfig.app.json
  create src/tsconfig.spec.json
  create src/typings.d.ts
  create .angular-cli.json
  create e2e/app.e2e-spec.ts
  create e2e/app.po.ts
  create e2e/tsconfig.e2e.json
  create .gitignore
  create karma.conf.js
  create package.json
  create protractor.conf.js
  create tsconfig.json
  create tslint.json
Installing packages for tooling via npm.
Installed packages for tooling via npm.
Successfully initialized git.
Project 'angular-app' successfully created.
{% endhighlight %}

AngularCLI will create the needed resources and download and install required components via `npm`.

You'll need to change over to the newly created directory:

{% highlight bash %}
$ cd angular-app
{% endhighlight %}

### Git

If you're unfamiliar with the `git` version control system, you *can* skip this part, but it's
worthwhile to perform these steps. If you're entirely unfamiliar with git, it's wise to
[Learn Enough Git to Be Dangerous][learn-enough-git].
{: .notice--info}

By default AngularCLI initializes a git repository and creates an initial commit on your behalf.

### Git Status

{% highlight bash %}
$ git status
On branch master
nothing to commit, working tree clean
{% endhighlight %}

The above command shows the current status of the git repository. As it stands, it shows no
untracked files, which is a little strange. We just created a project. It seems we'd have a *lot*
of new files.

It turns out, AngularCLI is quite helpful and tries to provide best-practices as defaults. It
expects that you want to place your project under source control, and it assumes you'll use `git`.

Incidentally, if you don't like its defaults, you can run `ng new --help` for a listing of
possible parameters. Among other options, you'll find `--skip-git` and `--skip-commit` to help
customize the behavior of `ng new`.
{: .notice--info}

### Git Log

{% highlight bash %}
$ git log
commit f2f96d26ce62f716e6cd0c43dfebf0008335e991 (HEAD -> master)
Author: Angular CLI <angular-cli@angular.io>
Date:   Sun Aug 6 15:54:13 2017 -0600

    chore: initial commit from @angular/cli

        _                      _                 ____ _     ___
       / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
      / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
     / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
    /_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
                   |___/
{% endhighlight %}

The above command shows the git log. This lists a summarized history of all commits in the
repository.

### Git Push

A wise programmer pushes code to a remote server early and often. I use Github. Many developers
and engineering departments use it too. There are others which are also used. It doesn't really
matter which one you use, once you've learned one, you've learned enough to use them all.

Once you've created a repository on a remote site, you can add that repository URI as a remote
destination to your code repository and push your code.

{% highlight bash %}
$ git remote add origin git@github.com:knightoftheoldcode/angular-app.git
$ git push -u origin master
Counting objects: 35, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (33/33), done.
Writing objects: 100% (35/35), 11.48 KiB | 0 bytes/s, done.
Total 35 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), done.
To github.com:knightoftheoldcode/angular-app.git
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

### Angular Serve

AngularCLI contains many available commands to help you build a webapp. One of those features is an
integrated web server.

{% highlight bash %}
$ ng serve
** NG Live Development Server is listening on localhost:4200, open your browser on http://localhost:4200 **
Hash: 48d32fe426e04c8a5370
Time: 7546ms
chunk    {0} polyfills.bundle.js, polyfills.bundle.js.map (polyfills) 178 kB {4} [initial] [rendered]
chunk    {1} main.bundle.js, main.bundle.js.map (main) 5.28 kB {3} [initial] [rendered]
chunk    {2} styles.bundle.js, styles.bundle.js.map (styles) 10.5 kB {4} [initial] [rendered]
chunk    {3} vendor.bundle.js, vendor.bundle.js.map (vendor) 2.19 MB [initial] [rendered]
chunk    {4} inline.bundle.js, inline.bundle.js.map (inline) 0 bytes [entry] [rendered]
webpack: Compiled successfully.
{% endhighlight %}

The above tells us our base installation of angular is good. You can verify this by hitting
http://localhost:4200 in your browser.

![Default Angular App](/assets/images/angular/default-angular-app.png)

## What We've Done

At this point, we're left with a fairly clean project.

- a new default angular app (with all the fixins')
- a clean git repository
- a [remote repository][github-knightoftheoldcode-angular-app]

[learn-enough-git]: http://amzn.to/2fhJqx2
[thoughtbot-git-commit-tips]: https://robots.thoughtbot.com/5-useful-tips-for-a-better-commit-message
[github-knightoftheoldcode-angular-app]: https://github.com/knightoftheoldcode/angular-app