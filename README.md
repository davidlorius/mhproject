Mental Health Prototype 

Prototype goal => Help to overcome the stigma of mental health. Stigma can lead to discrimination. Discrimination may be obvious and direct, such as someone making a negative remark about your mental illness or your treatment. We will provide a list of therapist to our community in order that the people who need help could find some resources. We will help to address this systemic issue as a society.


Getting Started with Mental Health Prototype Project

This README describes the steps needed to get up and running as a developer of the project. This project uses Rails 6, SQL, Bootstrap and to send emails we use the gem letter_opener. The instructions below describe how you set up an ubuntu linux environment, including linux running under vagrant on Windows. The steps for Mac are similar except that you do brew install.

Configuring Vagrant if you are using it
Rails 6 uses Webpacker and Yarn. As a result, it requires support in the environment for symbolic links. To enable this, add the following to your Vagrantfile:

config.vm.provider "virtualbox" do |v|
      v.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]
  end

You may already have the config.vm.provider block, in which case you add the line described. Then, bring down your vagrant environment with "vagrant halt" if it is running, and close the Git Bash session. Then, start a new Git Bash session running it as the windows administrator. Then do a "vagrant up". From now on, whenever you do "vagrant up", you will need to do it from a Git Bash session that was run as the windows administrator.

Installing Prerequisites on Linux (and Vagrant)
Do:

sudo apt-get update
sudo apt-get install postgresql
sudo apt-get install postgresql-contrib
sudo apt-get install libpq-dev
sudo apt-get install yarn
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
nvm install --lts
sudo apt remove nodejs
which node

The which command will return a filename like

/home/vagrant/.nvm/versions/node/v14.15.1/bin/node

You create a symbolic link to it via

ln -s /usr/bin/nodejs /home/vagrant/.nvm/versions/node/v14.15.1/bin/node

Be sure that the ln command is passed the actual location returned by which. The node/nodejs stuff is not needed on mac.

Installing Prerequisites on Mac OS

Check if you are running Mac OS Catalina. That is done by clicking on the apple icon in the upper left corner of your screen, and then clicking on About This Mac. If you are running Catalina, which is the most current release, you will have to do the following steps:

curl -sL https://github.com/nodejs/node-gyp/raw/master/macOS_Catalina_acid_test.sh | bash

The above command may return an error. If so, do the following:

sudo rm -rf /Library/Developer/CommandLineTools (You will have to enter your admin password)
sudo xcode-select --reset
xcode-select --install

Then repeat the curl command above. The error should go away. If it does not, you can contact me.

Now we can actually install the prerequisites. You should have installed brew when you originally set up your Mac to run rails. Check that it is there with this command:

brew -v

If you do not have brew, instructions for installing it are here: https://brew.sh/ . Now, do the following commands:

brew update
brew doctor
brew services start postgresql
brew install yarn

Each of these commands should complete without error. If not, you can contact me adi_111@icloud.com.

Getting started with the git repository
In your browser, go to https://github.com/adrianagithub/mhproject Then fork that repository into your own github workspace. Then clone your mhproject  workspace to your laptop, in an appropriate directory. 

git remote add upstream https://github.com/adrianagithub/mhproject

Setting up the Mental Health Prototype


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
- Clone this repository.
- Back to the comand line and run => cd mhproject
- SQL must be installed
- rake db:create:all
- rails db:migrate
- rails db:migrate RAILS_ENV=test
- Install the gems. Run this command in the terminal => bundle install
- Install font-aswesome https://blog.corsego.com/rails-6-install-fontawesome-with-webpacker

<img width="681" alt="Screen Shot 2022-10-23 at 10 10 45 PM" src="https://user-images.githubusercontent.com/56941883/197452631-332ff09c-2829-40bc-ac8a-ceef74a14105.png">

- Install bootstraps 5 => https://www.bootrails.com/blog/rails-bootstrap-tutorial/
- Setup letter opener https://github.com/ryanb/letter_opener You need to add the settings in this path to config letter opener.    config/environments/development.rb

<img width="994" alt="Screen Shot 2022-10-23 at 9 53 52 PM" src="https://user-images.githubusercontent.com/56941883/197451044-bc04fcc9-d9c5-4d87-87ad-8eaf165d31a9.png">

Here you are some commands to be able to install bootstraps. 

<img width="344" alt="Screen Shot 2022-10-23 at 9 55 54 PM" src="https://user-images.githubusercontent.com/56941883/197451264-2195c771-6963-465f-91ff-b983d37b7c30.png">

And these are the prerequisites to install bootstraps

<img width="190" alt="Screen Shot 2022-10-23 at 9 56 58 PM" src="https://user-images.githubusercontent.com/56941883/197451361-3bd9fb45-cbd8-4e20-a469-2d75113499e3.png">


Each of these commands should complete without failures, including Rspec. You will see tests passing when you run the rspec command.

<img width="1235" alt="Screen Shot 2022-10-23 at 10 03 45 PM" src="https://user-images.githubusercontent.com/56941883/197451991-4c9494b9-7672-4a6c-a739-41bc621d3c10.png">


Then run bin/rails s

adding -b 0.0.0.0 if you are running in vagrant. Then see if you can get to the server at localhost:3000.

If any of this fails, post the problem adi_111@icloud.com

Go to the browser and type http://localhost:3000/. Make a new account (sign up) and a confirmation message will be sent to your email. Click the confirmation link and login.

