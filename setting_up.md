Add an ssh key for the computer to Droplet
ssh into it
useradd -s /bin/bash -G sudo -m jeff
passwd jeff
Login to user
ssh jeff@host
Change root login: sudo nano /etc/ssh/sshd_config
sudo restart ssh
sudo apt-get upgrade
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install ruby1.9.3 sqlite3 libsqlite3-ruby1.9.1 libsqlite3-dev postgresql postgresql-client libpq-dev libcurl4-openssl-dev
sudo apt-get install git
sudo apt-get install libxml2-dev libxslt1-dev
sudo gem install bundler
sudo gem install pg sinatra
sudo gem install passenger

local - gem install capistrano -v '2.15.5'
capify app
edit deploy.rb
add deploy key
deploy

sudo passenger-install-nginx-module

user www-data;

To configure nginx to serve your app, ocate the `location` block in the config file,
which looks like:

    location / {
      root   html;
      index  index.html index.htm;
    }

Delete the whole block and replace it with the following 2 lines:

    root /home/USERNAME/APPNAME/current/public;
    passenger_enabled on;

    sudo ln -s /opt/nginx/sbin/nginx /usr/local/sbin/
    sudo nginx


sudo su - postgres
createuser jeff
su - jeff
createdb jeff
psql
ALTER USER jeff WITH PASSWORD '#{password}';


sudo nano ~/.profile
add export DATABASE_URL='postgres://jeff:#{password}@localhost/cjournal_production'
Add deploy key to git hub
cd cjournal/current
bundle exec rake db:migrate



