Mental Health Prototype 

Prototype goal => Help to overcome the stigma of mental health. Stigma can lead to discrimination. Discrimination may be obvious and direct, such as someone making a negative remark about your mental illness or your treatment. We will provide a list of therapist to our community in order that the people who need help could find some resources. We will help to address this systemic issue as a society.



We will assume that everyone is running either mac or linux ubuntu. Windows users will run linux ubuntu under vagrant as for the class.
We will use Rails 6.x. For this version of Rails, you must install a current version of node.js, and you must also install yarn. We will also have to install the database sqlite3, which will be our production database. Ubuntu setup (including for Ubuntu under vagrant)
sudo apt-get update
sudo apt-get install npm
sudo npm install npm@latest -g
sudo npm cache-clean -f
sudo npm install -g n
sudo n stable

At this point, you will have installed the latest stable version of node.js. You should exit your command window and start a new one to get the right path statement. Then, to install yarn, you do the following:

curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt install yarn

Note for vagrant users: In the slack channel, some additional instructions were provided so that yarn would work correctly in vagrant environments. First, edit your Vagrantfile in rails-ctd. Add the following lines just before the final end statement:
config.vm.provider "virtualbox" do |v| v.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"] end
Once you have done so, you must exit your vagrant ssh and do vagrant halt. Then you must start a new git bash window running as administrator, and do vagrant up and vagrant ssh as before. You will have to do this each time you start vagrant, so that vagrant up is run as windows administrator, for yarn to work correctly because of yarn use of symlinks.


This project was developed with

Rails 6.1.7
Ruby 2.6.5
Gems:
- gem 'sqlite3'
- gem 'sass-rails', '>= 6'
- gem 'webpacker', '~> 5.0'
- gem 'turbolinks', '~> 5'
- gem 'jbuilder', '~> 2.7'
- gem 'devise'
- gem "font-awesome-rails"
- gem 'bootstrap', '~>5.0'
- gem 'letter-opener'
- gem 'rspec-rails'
- gem 'factory_bot_rails'
- gem 'faker'
- gem 'rails-controller-testing'



Installing and setting up the app
Clone this repository.
Back to the comand line:
cd mhproject
SQL must be installed
rake db:create:all
rails db:migrate
rails db:migrate RAILS_ENV=test

Go to the browser and type http://localhost:3000/. Make a new account (sign up) and a confirmation message will be sent to your email. Click the confirmation link and login.



This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
