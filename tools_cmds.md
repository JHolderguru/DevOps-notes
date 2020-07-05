# Tools and Commands

Lists and documentation of often and useful tools and commands.


## bash commands for git
https://drive.google.com/file/d/1chCfI9dKEk5xn1EhsuBepCiudX6nKlng/view


## bash commands for vagrant
https://devopswiki.co.uk/wiki/vagrant/vagrant-commands


## Websites for installation
- Installing VirtualBox
https://www.virtualbox.org/
https://www.wikihow.com/Install-VirtualBox

- Installing Vagrant
https://www.vagrantup.com/


## nginx
1) $ sudo apt-get update -y
		- APT (package manager)
		- Gets and updates packages

2) $ sudo apt-get install nginx -y
		- Install nginx 
		- -y = "say yes"

3) $ sudo systemctl start nginx
		- starts nginx

4) Go to hosturl


## Editing file content - sed
https://www.geeksforgeeks.org/sed-command-in-linux-unix-with-examples/

### Installing Ruby
https://rubyinstaller.org/downloads/

- It's best to get the recommended version

To use Ruby, you will need to install bundler in program file.
Bundler is the package manager for ruby, which installs gems
- [] Open bash and type in
```bash
gem install bundler
```
- [] Installing gems
Find a file called Gemfile
In this case it in from starter-code
```bash
cd environment\spec-tests\Gemfile
bundle install
```


### Installing mongodb - for latest version
https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-16-04
For us:
```bash
# Getting repo and editing sources.list.d
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

# Updating Ubuntu
sudo apt-get update -y

# Installing Mongodb
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.22 mongodb-org-tools=3.2.20
sudo sed -i "s,\\(^[[:blank:]]*bindIp:\\) .*,\\1 0.0.0.0," /etc/mongod.conf

# Running db
sudo systemctl start mongod
sudo systemctl status mongod
sudo systemctl enable mongod
```