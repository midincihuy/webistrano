Webistrano - Capistrano deployment the easy way



About:
  Webistrano is a Web UI for managing Capistrano deployments.
  It lets you manage projects and their stages like test, production, 
  and staging with different settings. Those stages can then
  be deployed with Capistrano through Webistrano.


Installation:

  1. Configuration
  
    Copy config/webistrano_config.rb.sample to config/webistrano_config.rb
    and edit appropriatly. In this configuration file you can set the mail
    settings of Webistrano.
  
  2. Database
  
    Copy config/database.yml.sample to config/database.yml and edit to
    resemble your setting. You need at least the production database.
    The others are optional entries for development and testing.
  
    Then create the database structure with Rake:
  
    > cd webistrano
    > RAILS_ENV=production rake db:migrate
  
  3. Start Webistrano  
  
    > cd webistrano
    > ruby script/server -d -p 3000 -e production
  
    Webistrano is then available at http://host:3000/
  
    The default user is `admin`, the password is `admin`. Please change the password
    after the first login.
  
Author:
  Jonathan Weiss <jw@innerewut.de>
  
License: 
  Code: BSD, see LICENSE.txt
  Images: Right to use in their provided form in Webistrano installations. No other right granted.



=========================

install script :

sudo apt-get install git mysql-server ruby -y
# check ruby version
ruby -v
# create database
mysql -uXXX -pXXX -e "CREATE DATABASE webistrano_production;"
# retrive repository
git clone https://github.com/midincihuy/webistrano.git && cd webistrano
# install bundler
sudo gem install bundler -v 1.0.10
bundle install
# migrate db
bundle exec rake:db migrate RAILS_ENV=production
ruby script/server -p 3000 -e production
