#Rails 3.1 sample app
This application has been developed, tested and deployed on Ubuntu 11.04 with Ruby 1.9.2.

    $ rails new rails31-sample-app

'rails s' after creating new Rails 3.1 app raised following error:

    $ rails s
    /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/execjs-1.2.4/lib/execjs/runtimes.rb:45:in `autodetect': Could not find a JavaScript runtime. See https://github.com/sstephenson/execjs for a list of available runtimes. (ExecJS::RuntimeUnavailable)
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/execjs-1.2.4/lib/execjs.rb:5:in `<module:ExecJS>'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31s/gems/execjs-1.2.4/lib/execjs.rb:4:in `<top (required)>'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/coffee-script-2.2.0/lib/coffee_script.rb:1:in `require'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/coffee-script-2.2.0/lib/coffee_script.rb:1:in `<top (required)>'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/coffee-script-2.2.0/lib/coffee-script.rb:1:in `require'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/coffee-script-2.2.0/lib/coffee-script.rb:1:in `<top (required)>'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/coffee-rails-3.1.0/lib/coffee-rails.rb:1:in `require'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/coffee-rails-3.1.0/lib/coffee-rails.rb:1:in `<top (required)>'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/bundler-1.0.18/lib/bundler/runtime.rb:68:in `require'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/bundler-1.0.18/lib/bundler/runtime.rb:68:in `block (2 levels) in require'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/bundler-1.0.18/lib/bundler/runtime.rb:66:in `each'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/bundler-1.0.18/lib/bundler/runtime.rb:66:in `block in require'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/bundler-1.0.18/lib/bundler/runtime.rb:55:in `each'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/bundler-1.0.18/lib/bundler/runtime.rb:55:in `require'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/bundler-1.0.18/lib/bundler.rb:120:in `require'
      from /home/my-home/techraptors/rails-31/rails31-sample-app/config/application.rb:7:in `<top (required)>'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/railties-3.1.0/lib/rails/commands.rb:52:in `require'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/railties-3.1.0/lib/rails/commands.rb:52:in `block in <top (required)>'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/railties-3.1.0/lib/rails/commands.rb:49:in `tap'
      from /home/my-home/.rvm/gems/ruby-1.9.2-p180@rails-31/gems/railties-3.1.0/lib/rails/commands.rb:49:in `<top (required)>'
      from script/rails:6:in `require'
      from script/rails:6:in `<main>'

Rails 3.1 needs a JavaScript engine for coffee-script, and Ubuntu does not have one pre-installed.

Use following instructions to install node.js: https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager

    sudo apt-get install python-software-properties
    sudo add-apt-repository ppa:chris-lea/node.js
    sudo apt-get update
    sudo apt-get install nodejs

Now run 'rails s' and WEBrick starts without any problem.

Alternative to JavaScript engines, other than node.js, were execjs and therubyracer gems.
For example adding following to Gemfile:

    gem 'execjs'
    gem 'therubyracer'

and running 'bundle install' would also solve the problem. But if you need to deploy your
application to heroku, these are not recommended as [explained on heroku doc](http://devcenter.heroku.com/articles/rails31_heroku_cedar)

"If you were previously using therubyracer or therubyracer-heroku, these gems are no longer required and strongly discouraged as these gems use a very large amount of memory."

#Git and GitHub

    $ git init
    $ git add .
    $ git commit -am "Initial commit"

Create new repository on github.com
In this case repository name is Rails-3.1-Sample-App. Now add remote origin

    $ git remote add origin git@github.com:<your-github-user-name>/Rails-3.1-Sample-App.git

#Deploy on Heroku

    $ gem install heroku
    $ heroku create rails31sampleapp

Replace rails31sampleapp with your application name.

    $ git push heroku master
    $ heroku open

'heroku open' will open your app url in your default browser.

#Troubleshoot

Clicking on "About your application's environment" link on default Rails home page shows that some error has occurred
on production server. This is because we have not created the accompanying database on heroku server.

To see the production logs:

    $ heroku logs

It shows following error in production.log file:

    ActiveRecord::ConnectionNotEstablished (ActiveRecord::ConnectionNotEstablished):

To create database on heroku:

    $ heroku rake db:migrate

raised following error:

    Please install the postgresql adapter: `gem install activerecord-postgresql-adapter` (pg is not part of the bundle. Add it to Gemfile.)
    /app/.bundle/gems/ruby/1.9.1/gems/activerecord-3.1.0/lib/active_record/connection_adapters/abstract/connection_specification.rb:71:in `rescue in establish_connection'
    /app/.bundle/gems/ruby/1.9.1/gems/activerecord-3.1.0/lib/active_record/connection_adapters/abstract/connection_specification.rb:68:in `establish_connection'
    /app/.bundle/gems/ruby/1.9.1/gems/activerecord-3.1.0/lib/active_record/railties/databases.rake:109:in `rescue in create_database'
    /app/.bundle/gems/ruby/1.9.1/gems/activerecord-3.1.0/lib/active_record/railties/databases.rake:54:in `create_database'
    /app/.bundle/gems/ruby/1.9.1/gems/activerecord-3.1.0/lib/active_record/railties/databases.rake:44:in `block (2 levels) in <top (required)>'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/task.rb:205:in `call'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/task.rb:205:in `block in execute'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/task.rb:200:in `each'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/task.rb:200:in `execute'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/task.rb:158:in `block in invoke_with_call_chain'
    /usr/ruby1.9.2/lib/ruby/1.9.1/monitor.rb:201:in `mon_synchronize'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/task.rb:151:in `invoke_with_call_chain'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/task.rb:144:in `invoke'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/application.rb:112:in `invoke_task'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/application.rb:90:in `block (2 levels) in top_level'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/application.rb:90:in `each'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/application.rb:90:in `block in top_level'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/application.rb:129:in `standard_exception_handling'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/application.rb:84:in `top_level'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/application.rb:62:in `block in run'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/application.rb:129:in `standard_exception_handling'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/lib/rake/application.rb:59:in `run'
    /app/.bundle/gems/ruby/1.9.1/gems/rake-0.9.2/bin/rake:32:in `<top (required)>'
    /app/.bundle/gems/ruby/1.9.1/bin/rake:19:in `load'
    /app/.bundle/gems/ruby/1.9.1/bin/rake:19:in `<main>'
    Couldn't create database for {"encoding"=>"unicode", "port"=>5432, "username"=>"gnfjuvhwph", "adapter"=>"postgresql", "database"=>"gnfjuvhwph", "host"=>"ec2-107-20-227-173.compute-1.amazonaws.com", "password"=>"whf_1yi9w89f6UvFjno4"}











