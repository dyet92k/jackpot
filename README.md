Jackpot
==========

# WORK IN PROGRESS

[![Build Status](https://secure.travis-ci.org/pellegrino/jackpot.png)](http://travis-ci.org/pellegrino/jackpot)

_WORK IN PROGRESS_

 Jackpot is the easiest way to get paid using ruby. It abstracts all the nasty details about billing that every Saas app have to deal with.

It started out as my may 2011 session @ [Mendicant University](http://mendicantuniversity.org) project and now its finally taking shape.

## Recurring Payments  

Even though some gateways will provide you a recurring payment option, normally it isn't a fire and forget process as you'ld normally imagine. Also, its needed to have information about when this payments actually did happen so you can send invoices accordingly. That being said, in Jackpot we opt to use Gateways that support credit card storage, instead of relying on Gateway Recurring payments. 




The main goal of this project is to provide billing to rails apps via a rails-engine. 

### List of supported gateways

_TODO_ 

* Braintree

## Contributing to jackpot  ## 

### How to run jackpot locally 
This application uses bundler and rvm for dependencies management, so its
recommended to create a gemset to test it.

Run the following commands at the directory where you've checked out
jackpot.

    rvm use 1.9.3@jackpot --create
    gem install bundler
    bundle install

### Migrations and RSpec 

Since this project is basically a Rails Engine, some additional steps are required to run the spec suite locally. Its a pretty straightfoward process, don't worry much about it. 

Before running the specs for the first time, or after adding a new migration, make sure to run the following command 

    bundle exec rake -f spec/dummy/Rakefile db:drop db:create db:migrate db:test:prepare

That will create and initialize the database for you. The dataase.yml file used is the one located at spec/dummy/config/database.yml. If changed something that did require a migration to be created, make sure you've copied that one to spec/dummy/db/migrate folder.
   
    bundle exec rake -f spec/dummy/Rakefile jackpot:install:migrations 

The command above will copy every migration you created at Jackpot to the dummy app folder. Also, make sure to run the database initializer command above or your changes won't be reflected. 


### Rails development Server 

If you ran the migrations correctly, you can start the dummy app as you normally would start a regular Rails 3.x app.

    bundle exec rails server 

### Migrations 

If the work you want to do has something to do with creating a new migration, you will probably want to copy migrations from jackpot's db/ folder to the dummy app. To achieve this, use the following command from inside your local copy of jackpot source code.

    cd spec/dummy
    bundle exec rake app:jackpot:install:migrations 

Your newly added migration will be copied to dummy app. After this, you'll be able to run `bundle exec rake db:migrate` as usual.
    
    

### General advice   

* Check out the latest master to make sure the feature hasn't been implemented or the bug hasn't been fixed yet
* Check out the issue tracker to make sure someone already hasn't requested it and/or contributed it
* Fork the project
* Start a feature/bugfix branch
* Commit and push until you are happy with your contribution
* Make sure to add tests for it. This is important so I don't break it in a future version unintentionally.
* Please try not to mess with the Rakefile, version, or history. If
* you want to have your own version, or is otherwise necessary, that
* is fine, but please isolate to its own commit so I can cherry-pick
* around it.

### Get in contact! 

There is a #jackpot channel @ freenode for this project. Feel free to stop by to ask questions and interact with other users. 

## Copyright ##

Copyright (c) 2011-2012 Vitor Pellegrino. See LICENSE.txt for
further details.

