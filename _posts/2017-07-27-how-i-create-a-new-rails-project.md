---
layout: single
title:  "How I Create a New Rails Project"
date:   2017-07-27
modified:   2017-08-05
description: "..."
excerpt: "I use a somewhat persnickety process for starting any given project. This is my chosen method for
starting a Rails app."
categories: article
tags:
- beginner
- ruby
- rails
---

![The Completed Project Structure](/assets/images/rails/default-rails-directory-structure.png)

I use a somewhat persnickety process for starting any given project. This is my chosen method for
starting a Rails app. I prefer to use the latest component versions for any given tech stack.
While most would just dig in with `rails new rails_app`, I prefer to be a little more precise.

## Initialize Project

### Directory

In order to lock down the versions of libraries I want and initialize things in a way I prefer, I
simply create a directory (a step that most tools would do themselves).

{% highlight bash %}
$ mkdir rails-app
$ cd rails-app
{% endhighlight %}

The above statements create and then change to a new directory named "rails-app".

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
instance we will be running the `rails` framework (based on `ruby`) to build our app.

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

Since bundler init defaults to the rails gem as a sample, it *is* commented, so it's a simple matter
to uncomment it.

{% highlight ruby %}
# frozen_string_literal: true
source "https://rubygems.org"

gem "rails"
{% endhighlight %}

At this point, a simple `bundle install` should download rails and install it into the ruby version
we selected earlier with rbenv.

{% highlight bash %}
$ bundle install
Fetching gem metadata from https://rubygems.org/.............
Fetching version metadata from https://rubygems.org/...
Fetching dependency metadata from https://rubygems.org/..
Resolving dependencies...
Using rake 12.0.0
Using concurrent-ruby 1.0.5
Fetching i18n 0.8.6
Fetching minitest 5.10.3
Installing i18n 0.8.6
Using thread_safe 0.3.6
Fetching builder 3.2.3
Installing minitest 5.10.3
Fetching erubi 1.6.1
Installing erubi 1.6.1
Using mini_portile2 2.2.0
Using rack 2.0.3
Fetching nio4r 2.1.0
Installing builder 3.2.3
Fetching websocket-extensions 0.1.2
Installing websocket-extensions 0.1.2
Fetching mime-types-data 3.2016.0521
Installing nio4r 2.1.0 with native extensions
Fetching arel 8.0.0
Installing arel 8.0.0
Using bundler 1.15.1
Fetching method_source 0.8.2
Installing mime-types-data 3.2016.0521
Using thor 0.19.4
Using tzinfo 1.2.3
Fetching nokogiri 1.8.0
Installing nokogiri 1.8.0 with native extensions
Installing method_source 0.8.2
Using rack-test 0.6.3
Fetching sprockets 3.7.1
Installing sprockets 3.7.1
Fetching websocket-driver 0.6.5
Installing websocket-driver 0.6.5 with native extensions
Fetching mime-types 3.1
Fetching activesupport 5.1.3
Installing mime-types 3.1
Installing activesupport 5.1.3
Installing nokogiri 1.8.0 with native extensions
Fetching actionpack 5.1.3
Installing actionpack 5.1.3
Fetching actioncable 5.1.3
Fetching actionmailer 5.1.3
Installing actionmailer 5.1.3
Installing actioncable 5.1.3
Fetching railties 5.1.3
Fetching sprockets-rails 3.2.0
Installing sprockets-rails 3.2.0
Installing railties 5.1.3
Fetching rails 5.1.3
Installing rails 5.1.3
Bundle complete! 1 Gemfile dependency, 38 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
{% endhighlight %}

### Rails New

Now we have rails installed, we want to force a new rails site into our current project directory.
Most command-line tools will allow you to pass `.` as the current directory, or `..` as the parent
directory. We can replace the `app-name` parameter from a typical `rails new app-name` with a `.`

{% highlight bash %}
$ rails new . --skip-bundle --skip-test-unit
      exist
      create  README.md
      create  Rakefile
      create  config.ru
      create  .gitignore
    conflict  Gemfile
Overwrite /Users/curtis/src/koc/rails-app/Gemfile? (enter "h" for help) [Ynaqdh] Y
       force  Gemfile
         run  git init from "."
Initialized empty Git repository in /Users/curtis/src/koc/rails-app/.git/
      create  app
      create  app/assets/config/manifest.js
      create  app/assets/javascripts/application.js
      create  app/assets/javascripts/cable.js
      create  app/assets/stylesheets/application.css
      create  app/channels/application_cable/channel.rb
      create  app/channels/application_cable/connection.rb
      create  app/controllers/application_controller.rb
      create  app/helpers/application_helper.rb
      create  app/jobs/application_job.rb
      create  app/mailers/application_mailer.rb
      create  app/models/application_record.rb
      create  app/views/layouts/application.html.erb
      create  app/views/layouts/mailer.html.erb
      create  app/views/layouts/mailer.text.erb
      create  app/assets/images/.keep
      create  app/assets/javascripts/channels
      create  app/assets/javascripts/channels/.keep
      create  app/controllers/concerns/.keep
      create  app/models/concerns/.keep
      create  bin
      create  bin/bundle
      create  bin/rails
      create  bin/rake
      create  bin/setup
      create  bin/update
      create  bin/yarn
      create  config
      create  config/routes.rb
      create  config/application.rb
      create  config/environment.rb
      create  config/secrets.yml
      create  config/cable.yml
      create  config/puma.rb
      create  config/spring.rb
      create  config/environments
      create  config/environments/development.rb
      create  config/environments/production.rb
      create  config/environments/test.rb
      create  config/initializers
      create  config/initializers/application_controller_renderer.rb
      create  config/initializers/assets.rb
      create  config/initializers/backtrace_silencers.rb
      create  config/initializers/cookies_serializer.rb
      create  config/initializers/cors.rb
      create  config/initializers/filter_parameter_logging.rb
      create  config/initializers/inflections.rb
      create  config/initializers/mime_types.rb
      create  config/initializers/new_framework_defaults_5_1.rb
      create  config/initializers/wrap_parameters.rb
      create  config/locales
      create  config/locales/en.yml
      create  config/boot.rb
      create  config/database.yml
      create  db
      create  db/seeds.rb
      create  lib
      create  lib/tasks
      create  lib/tasks/.keep
      create  lib/assets
      create  lib/assets/.keep
      create  log
      create  log/.keep
      create  public
      create  public/404.html
      create  public/422.html
      create  public/500.html
      create  public/apple-touch-icon-precomposed.png
      create  public/apple-touch-icon.png
      create  public/favicon.ico
      create  public/robots.txt
      create  test/fixtures
      create  test/fixtures/.keep
      create  test/fixtures/files
      create  test/fixtures/files/.keep
      create  test/controllers
      create  test/controllers/.keep
      create  test/mailers
      create  test/mailers/.keep
      create  test/models
      create  test/models/.keep
      create  test/helpers
      create  test/helpers/.keep
      create  test/integration
      create  test/integration/.keep
      create  test/test_helper.rb
      create  test/system
      create  test/system/.keep
      create  test/application_system_test_case.rb
      create  tmp
      create  tmp/.keep
      create  tmp/cache
      create  tmp/cache/assets
      create  vendor
      create  vendor/.keep
      create  package.json
      remove  config/initializers/cors.rb
      remove  config/initializers/new_framework_defaults_5_1.rb
{% endhighlight %}

During the `rails new` command, you'll likely get a prompt ("Overwrite ... Gemfile? above)
informing you that one or more files currently exist (we created `.ruby-version` and `Gemfile`
earlier). It requires you to choose what to do with the existing file. In this case we pick 'Y'
which represents "Yes". This will overwrite our Gemfile with a more comprehensive Gemfile from the
rails new project generator.
{: .notice--warning}

Above, we chose to `--skip-test-unit`. This will skip the default minitest testing framework. This
is simply due to preference of RSpec (which we'll install below). There is nothing wrong with
omitting this skip parameter and therefore using minitest. This is a user preference.

Above, we chose to `--skip-bundle`. This is because I like to run bundle myself (especially when
creating a rails project in a current directory, like we are doing, instead of letting rails create
the directory itself).

{% highlight bash %}
$ bundle install
  ...
{% endhighlight %}

### Git

If you're unfamiliar with the `git` version control system, you *can* skip this part, but it's
worthwhile to perform these steps. If you're entirely unfamiliar with git, it's wise to
[Learn Enough Git to Be Dangerous][learn-enough-git].
{: .notice--info}

By default (one can use the `--skip-git` parameter to skip) rails' new project generator initializes
a git repository and adds a `.gitignore` file, pre-populated with good defaults for a rails project.

### Git Status

{% highlight bash %}
$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.gitignore
	.ruby-version
	Gemfile
	Gemfile.lock
	README.md
	Rakefile
	app/
	bin/
	config.ru
	config/
	db/
	lib/
	log/
	package.json
	public/
	test/
	tmp/
	vendor/

nothing added to commit but untracked files present (use "git add" to track)
{% endhighlight %}

The above command shows the current status of the git repository. As it stands, rails just Initialized
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
	new file:   Gemfile
	new file:   Gemfile.lock
	new file:   README.md
	new file:   Rakefile
	new file:   app/assets/config/manifest.js
	new file:   app/assets/images/.keep
	new file:   app/assets/javascripts/application.js
	new file:   app/assets/javascripts/cable.js
	new file:   app/assets/javascripts/channels/.keep
	new file:   app/assets/stylesheets/application.css
	new file:   app/channels/application_cable/channel.rb
	new file:   app/channels/application_cable/connection.rb
	new file:   app/controllers/application_controller.rb
	new file:   app/controllers/concerns/.keep
	new file:   app/helpers/application_helper.rb
	new file:   app/jobs/application_job.rb
	new file:   app/mailers/application_mailer.rb
	new file:   app/models/application_record.rb
	new file:   app/models/concerns/.keep
	new file:   app/views/layouts/application.html.erb
	new file:   app/views/layouts/mailer.html.erb
	new file:   app/views/layouts/mailer.text.erb
	new file:   bin/bundle
	new file:   bin/rails
	new file:   bin/rake
	new file:   bin/setup
	new file:   bin/update
	new file:   bin/yarn
	new file:   config.ru
	new file:   config/application.rb
	new file:   config/boot.rb
	new file:   config/cable.yml
	new file:   config/database.yml
	new file:   config/environment.rb
	new file:   config/environments/development.rb
	new file:   config/environments/production.rb
	new file:   config/environments/test.rb
	new file:   config/initializers/application_controller_renderer.rb
	new file:   config/initializers/assets.rb
	new file:   config/initializers/backtrace_silencers.rb
	new file:   config/initializers/cookies_serializer.rb
	new file:   config/initializers/filter_parameter_logging.rb
	new file:   config/initializers/inflections.rb
	new file:   config/initializers/mime_types.rb
	new file:   config/initializers/wrap_parameters.rb
	new file:   config/locales/en.yml
	new file:   config/puma.rb
	new file:   config/routes.rb
	new file:   config/secrets.yml
	new file:   config/spring.rb
	new file:   db/seeds.rb
	new file:   lib/assets/.keep
	new file:   lib/tasks/.keep
	new file:   log/.keep
	new file:   package.json
	new file:   public/404.html
	new file:   public/422.html
	new file:   public/500.html
	new file:   public/apple-touch-icon-precomposed.png
	new file:   public/apple-touch-icon.png
	new file:   public/favicon.ico
	new file:   public/robots.txt
	new file:   test/application_system_test_case.rb
	new file:   test/controllers/.keep
	new file:   test/fixtures/.keep
	new file:   test/fixtures/files/.keep
	new file:   test/helpers/.keep
	new file:   test/integration/.keep
	new file:   test/mailers/.keep
	new file:   test/models/.keep
	new file:   test/system/.keep
	new file:   test/test_helper.rb
	new file:   tmp/.keep
	new file:   vendor/.keep

{% endhighlight %}

`git status` now shows files are tracked and ready to be committed. It also shows the per-file
status ("new file:"). In this case all files are the same, but would differ over time as you make
modifications and commits.

### Git Commit

{% highlight bash %}
$ git commit -m "Initial commit."
master (root-commit) 75218b7] Initial commit.
 76 files changed, 1169 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 .ruby-version
 create mode 100644 Gemfile
 create mode 100644 Gemfile.lock
 create mode 100644 README.md
 create mode 100644 Rakefile
 create mode 100644 app/assets/config/manifest.js
 create mode 100644 app/assets/images/.keep
 create mode 100644 app/assets/javascripts/application.js
 create mode 100644 app/assets/javascripts/cable.js
 create mode 100644 app/assets/javascripts/channels/.keep
 create mode 100644 app/assets/stylesheets/application.css
 create mode 100644 app/channels/application_cable/channel.rb
 create mode 100644 app/channels/application_cable/connection.rb
 create mode 100644 app/controllers/application_controller.rb
 create mode 100644 app/controllers/concerns/.keep
 create mode 100644 app/helpers/application_helper.rb
 create mode 100644 app/jobs/application_job.rb
 create mode 100644 app/mailers/application_mailer.rb
 create mode 100644 app/models/application_record.rb
 create mode 100644 app/models/concerns/.keep
 create mode 100644 app/views/layouts/application.html.erb
 create mode 100644 app/views/layouts/mailer.html.erb
 create mode 100644 app/views/layouts/mailer.text.erb
 create mode 100755 bin/bundle
 create mode 100755 bin/rails
 create mode 100755 bin/rake
 create mode 100755 bin/setup
 create mode 100755 bin/update
 create mode 100755 bin/yarn
 create mode 100644 config.ru
 create mode 100644 config/application.rb
 create mode 100644 config/boot.rb
 create mode 100644 config/cable.yml
 create mode 100644 config/database.yml
 create mode 100644 config/environment.rb
 create mode 100644 config/environments/development.rb
 create mode 100644 config/environments/production.rb
 create mode 100644 config/environments/test.rb
 create mode 100644 config/initializers/application_controller_renderer.rb
 create mode 100644 config/initializers/assets.rb
 create mode 100644 config/initializers/backtrace_silencers.rb
 create mode 100644 config/initializers/cookies_serializer.rb
 create mode 100644 config/initializers/filter_parameter_logging.rb
 create mode 100644 config/initializers/inflections.rb
 create mode 100644 config/initializers/mime_types.rb
 create mode 100644 config/initializers/wrap_parameters.rb
 create mode 100644 config/locales/en.yml
 create mode 100644 config/puma.rb
 create mode 100644 config/routes.rb
 create mode 100644 config/secrets.yml
 create mode 100644 config/spring.rb
 create mode 100644 db/seeds.rb
 create mode 100644 lib/assets/.keep
 create mode 100644 lib/tasks/.keep
 create mode 100644 log/.keep
 create mode 100644 package.json
 create mode 100644 public/404.html
 create mode 100644 public/422.html
 create mode 100644 public/500.html
 create mode 100644 public/apple-touch-icon-precomposed.png
 create mode 100644 public/apple-touch-icon.png
 create mode 100644 public/favicon.ico
 create mode 100644 public/robots.txt
 create mode 100644 test/application_system_test_case.rb
 create mode 100644 test/controllers/.keep
 create mode 100644 test/fixtures/.keep
 create mode 100644 test/fixtures/files/.keep
 create mode 100644 test/helpers/.keep
 create mode 100644 test/integration/.keep
 create mode 100644 test/mailers/.keep
 create mode 100644 test/models/.keep
 create mode 100644 test/system/.keep
 create mode 100644 test/test_helper.rb
 create mode 100644 tmp/.keep
 create mode 100644 vendor/.keep
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
$ git remote add origin git@github.com:knightoftheoldcode/rails-app.git
$ git push -u origin master
Counting objects: 84, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (69/69), done.
Writing objects: 100% (84/84), 20.20 KiB | 0 bytes/s, done.
Total 84 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), done.
To github.com:knightoftheoldcode/rails-app.git
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

### Rails Server

Rails contains many available commands to help you build a webapp. One of those features is an
integrated web server.

{% highlight bash %}
$ rails server
=> Booting Puma
=> Rails 5.1.3 application starting in development on http://localhost:3000
=> Run `rails server -h` for more startup options
Puma starting in single mode...
* Version 3.9.1 (ruby 2.4.1-p111), codename: Private Caller
* Min threads: 5, max threads: 5
* Environment: development
* Listening on tcp://0.0.0.0:3000
Use Ctrl-C to stop
{% endhighlight %}

The above tells us our base installation of rails is good. You can verify this by hitting
http://localhost:3000 in your browser.

![Default Rails App](/assets/images/rails/default-rails-app.png)

## Testing

The Ruby and Rails communities practically ooze a "test driven" mentality. It's an excellent
software practice. And unless I'm working on spikes (even sometimes then) I generally code
test-first.

In order to do this, you need a good test suite. I prefer RSpec (for most tasks). We'll install and
configure RSpec and a few supporting libraries.

### RSpec

In the default rails `Gemfile` you should find a section for `:development, :test`. We want to add
the `rspec-rails` gem to this section.

{% highlight ruby %}
group :development, :test do
  # Call 'byebug' anywhere in the code to stop execution and get a debugger console
  gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]
  # Adds support for Capybara system testing and selenium driver
  gem 'capybara', '~> 2.13'
  gem 'selenium-webdriver'
  gem 'rspec-rails'
end
{% endhighlight %}

We will then need to `bundle install` again (you need to do this whenever you add to the `Gemfile`).

{% highlight bash %}
$ bundle install
Fetching gem metadata from https://rubygems.org/............
Fetching version metadata from https://rubygems.org/...
Fetching dependency metadata from https://rubygems.org/..
Resolving dependencies...
...
Fetching rspec-support 3.6.0
Fetching diff-lcs 1.3
Installing diff-lcs 1.3
...
Installing rspec-support 3.6.0
Fetching rspec-core 3.6.0
Fetching rspec-expectations 3.6.0
Installing rspec-core 3.6.0
Fetching rspec-mocks 3.6.0
Installing rspec-expectations 3.6.0
Installing rspec-mocks 3.6.0
Fetching rspec-rails 3.6.0
Installing rspec-rails 3.6.0
Bundle complete! 17 Gemfile dependencies, 77 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
{% endhighlight %}

We then need to run the RSpec installation generator.

{% highlight bash %}
$ rails generate rspec:install
     create  .rspec
      create  spec
      create  spec/spec_helper.rb
      create  spec/rails_helper.rb
{% endhighlight %}

### Factory Girl

FactoryGirl is a gem that helps setup our environment for specific tests. It's best to have
`factory_girl` in a specific `:test` group in the `Gemfile`. (This prevents ruby from loading
unneccessary code in other environments, such as development, where that code isn't useful.)

{% highlight ruby %}
group :test do
  gem 'factory_girl_rails', "~> 4.0"
end
{% endhighlight %}

Remember to `bundle install` again.

{% highlight bash %}
$ bundle install
Fetching gem metadata from https://rubygems.org/.............
Fetching version metadata from https://rubygems.org/...
Fetching dependency metadata from https://rubygems.org/..
Resolving dependencies...
...
Fetching factory_girl 4.8.0
...
Installing factory_girl 4.8.0
Fetching factory_girl_rails 4.8.0
Installing factory_girl_rails 4.8.0
Bundle complete! 18 Gemfile dependencies, 79 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
{% endhighlight %}

## Check Testing

RSpec installs itself in a way to allow testing via a simple `rake` command. Running `rake` with no
parameters should execute the test suite (if all is installed correctly).

{% highlight bash %}
$ rake
No examples found.


Finished in 0.0004 seconds (files took 0.08979 seconds to load)
0 examples, 0 failures
{% endhighlight %}

The above result makes sense, as we haven't yet added any tests.

## Commit and Push

We have made changes to the code since we last committed and pushed. We'll correct that. I like
checking the status before I stage and commit files (I also generally like to `git diff` my changes
but that's a subject for another article).

{% highlight bash %}
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   Gemfile
	modified:   Gemfile.lock

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.rspec
	spec/

no changes added to commit (use "git add" and/or "git commit -a")
{% endhighlight %}

{% highlight bash %}
$ git add --all
{% endhighlight %}

{% highlight bash %}
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   .rspec
	modified:   Gemfile
	modified:   Gemfile.lock
	new file:   spec/rails_helper.rb
	new file:   spec/spec_helper.rb

{% endhighlight %}

{% highlight bash %}
$ git commit -m "Add RSpec and FactoryGirl"
master e41c580] Add RSpec and FactoryGirl
 5 files changed, 184 insertions(+)
 create mode 100644 .rspec
 create mode 100644 spec/rails_helper.rb
 create mode 100644 spec/spec_helper.rb
{% endhighlight %}

{% highlight bash %}
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
nothing to commit, working tree clean
{% endhighlight %}

`git status` tells us that we are ahead of 'origin/master' by 1 commit. This means that we have
one unpushed change. As above, we can `git push` to push the changes to `origin` (commonly the
identifier for your remote repository, in this case Github).

{% highlight bash %}
$ git push
Counting objects: 8, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (7/7), done.
Writing objects: 100% (8/8), 4.23 KiB | 0 bytes/s, done.
Total 8 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
To github.com:knightoftheoldcode/rails-app.git
   75218b7..e41c580  master -> master
{% endhighlight %}

The above flow isn't the best usage of `git`. It is better to use a branching flow to isolate code
off of your `master` branch, which you can then merge (or better, rebase) into `master` when it's
complete. I continue to recommend the "Learn Enough..." series to anyone who wants to learn more:
[Learn Enough Git to Be Dangerous][learn-enough-git].
{: .notice--info}

## What We've Done

At this point, we're left with a fairly clean project.

- a new default rails app (with all the fixins')
- a ruby lock-down
- a clean git repository
- a [remote repository][github-knightoftheoldcode-rails-app]

[learn-enough-git]: http://amzn.to/2fhJqx2
[thoughtbot-git-commit-tips]: https://robots.thoughtbot.com/5-useful-tips-for-a-better-commit-message
[github-knightoftheoldcode-rails-app]: https://github.com/knightoftheoldcode/rails-app