# vps-commands

# ui install
```
sudo apt update && sudo apt upgrade
sudo apt install kde-plasma-desktop
sudo apt install xrdp
sudo adduser xrdp ssl-cert

```

# apache install

```
sudo apt-get update
sudo apt install apache2
```

# php install 
```
sudo apt update
sudo apt install -y lsb-release gnupg2 ca-certificates apt-transport-https software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt update

sudo apt install php8.2
sudo apt install php8.2-fpm
sudo apt install php8.2-{bcmath,fpm,xml,mysql,zip,intl,ldap,gd,cli,bz2,curl,mbstring,pgsql,opcache,soap,cgi}

sudo apt install apache2 libapache2-mod-php8.2
sudo a2enmod php8.2
sudo systemctl restart apache2
```

# composer
```
sudo apt-get update
sudo apt install php-cli unzip
cd ~
curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
HASH=`curl -sS https://composer.github.io/installer.sig`
php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
composer
```

# node js install with nvm
```
sudo apt-get update
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
source ~/.bashrc
nvm list-remote
nvm install v20.8.1

```

# git install
```
sudo apt-get update
sudo apt-get install git-all
git version

```

# mySQL install
```
sudo apt update
sudo apt install mysql-server
sudo systemctl start mysql.service
```

# mySQL setup
```
sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'dbMa$%!@#*@95ext965874-+/';
exit
```

# remote connection
```
SELECT host, user FROM mysql.user;
CREATE USER 'username'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'username'@'%' WITH GRANT OPTION;
```
```
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```
```
bind-address            = 0.0.0.0
```
```
sudo systemctl restart mysql
```
```
CREATE USER 'sammy'@'remote_server_ip' IDENTIFIED BY 'password';
```


# mongo DB install
```
sudo apt install software-properties-common gnupg apt-transport-https ca-certificates -y
curl -fsSL https://pgp.mongodb.com/server-7.0.asc |  sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg --dearmor
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse
sudo apt update
sudo apt install mongodb-org -y
mongod --version
sudo systemctl start mongod
sudo systemctl enable mongod

```

# mongo status 
```
sudo systemctl status mongod
```

#run mongo and secure 
```
mongosh
use admin
db.createUser(
  {
    user: "root",
    pwd: "m2451238228",
    roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
 }
)
exit
```
```
sudo nano /etc/mongod.conf
```
```
security:
    authorization: enabled
```
```
sudo systemctl restart mongod
sudo systemctl status mongod
mongosh
```
## log as auth user
```
mongosh -u root -p --authenticationDatabase admin
m2451238228
```
```
show dbs
```
## mongo remote connect
```
bindIp: 127.0.0.1, vps-mongo-server-ip
sudo systemctl restart mongod
sudo ufw allow from remote_machine_ip to any port 27017
sudo ufw reload
```
## mongo remote shell
```
sudo apt install netcat
nc -zv mongodb_server_ip 27017
mongosh "mongodb://username@mongo_server_ip:27017"
```
## mongo error 14
```
sudo chown -R mongodb:mongodb /var/lib/mongodb
sudo chown mongodb:mongodb /tmp/mongodb-27017.sock
sudo service mongod restart
sudo systemctl status mongod
```
## mongodb shell
```
sudo apt update
wget https://downloads.mongodb.com/compass/mongodb-compass_1.39.0_amd64.deb
sudo apt install ./mongodb-compass_1.39.0_amd64.deb
mongodg-compass --no-sandbox
```

## mongo backup and restore
install https://www.mongodb.com/try/download/database-tools
```
mongodump --uri="uri_link?authSource=admin" --db=blogDB --out=d:/folder_name
mongorestore -d meal-management-system D:\db.json\blogDB

mongorestore --db it_database --verbose G:/it_database_18_oct_23_12_8p/it_database
mongodump --uri="mongodb+srv://user:pass@cluster0.0fsdqn6.mongodb.net/?authSource=admin" --db=it_database --out=G:/it_databse
```
restore local to atla
```
mongorestore --uri mongodb+srv://username:pass@noortahervpstpit.pfgs6qb.mongodb.net -d DBname --verbose ./backup_dir
```

# permission to laravel project diretories

```
sudo chmod -R 777 /var/DirectoryName
```
```
sudo chown -R www-data:www-data
```
```
sudo chown -R www-data:www-data /var/www/html/laravel/storage
sudo chown -R www-data:www-data /var/www/html/laravel/bootstrap/cache
```

# proxy install
```
sudo a2enmod proxy
sudo a2enmod proxy_http
sudo /etc/init.d/apache2 restart
```

# Aftar boot / reboot, restart services

```
  sudo a2enmod rewrite
  sudo service apache2 start
  sudo systemctl restart apache2
  sudo systemctl start mysql.service
  sudo systemctl enable mongod
  sudo systemctl restart mongod
```
#open servers
```
cd /var/www/deepseahost.com
pm2 start 5001_deep_sea_host.js --watch
```
```
pm2 start npm --name next.techparkit.org -- run start -- -p 3001
```

# apache server setup
php
```
<VirtualHost *:80>
     ServerName domain
     DocumentRoot /var/www/domain/public
  
     <Directory /var/www/domain/public>
    		Options Indexes FollowSymLinks
    		AllowOverride All
    		Require all granted
     </Directory>
     ErrorLog ${APACHE_LOG_DIR}/error.log
     CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
proxy
```
 <VirtualHost *:80>
  	ServerName domain
  	ProxyPreserveHost on
  	ProxyPass / http://localhost:5001/
  	ProxyPassReverse / http://localhost:5001/
</VirtualHost>
```

# check opened ports
```
netstat --listen --tcp -n
```

# continious deployment

# How to Automate Deployment using Github Action
On Your Local Machine, Open Your Project using VS Code or any Editor
Create A Folder named .scripts inside your root project folder e.g. miniblog/.scripts
Inside .scripts folder Create A file with .sh extension e.g. miniblog/.scripts/deploy.sh
Write below script inside the created .sh file
```
#!/bin/bash
set -e

echo "Deployment started ..."

# Pull the latest version of the app
git pull origin master
echo "New changes copied to server !"

echo "Installing Dependencies..."
npm install --yes

echo "Deployment Finished!"

```
Go inside .scripts Folder then Set File Permission for .sh File
```
git update-index --add --chmod=+x deploy.sh

```

Create Directory Path named .github/workflows inside your root project folder e.g. miniblog/.github/workflows
Inside workflows folder Create A file with .yml extension e.g. miniblog/.github/workflows/deploy.yml
Write below script inside the created .yml file

```
name: Deploy

# Trigger the workflow on push and
# pull request events on the master branch
on:
  push:
    branches: ["master"]
  pull_request:
    branches: ["master"]

# Authenticate to the the server via ssh
# and run our deployment script
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Deploy to Server
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.HOST }}
          username: ${{ secrets.USERNAME }}
          port: ${{ secrets.PORT }}
          key: ${{ secrets.SSHKEY }}
          script: "cd /var/www/miniblog && ./.scripts/deploy.sh"

```
Go to Your Github Repo Click on Settings
Click on Secrets and Variables from the Sidebar then choose Actions
On Secret Tab, Click on New Repository Secret
Add Four Secrets HOST, PORT, USERNAME and SSHKEY as below
```
host: ${{ secrets.HOST }}
username: ${{ secrets.USERNAME }}
port: ${{ secrets.PORT }}
key: ${{ secrets.PRIVATE_KEY }}
script: "cd /var/www/myreportbd && ./.scripts/deploy.sh"
```
You can get Server User Name by loging into your server via ssh then run below command
```
whoami
```
Generate SSH Key for Github Action by Login into Remote Server then run below Command OR You can use old SSH Key But I am creating New one for Github Action

Syntax:- 
```
ssh-keygen -f key_path -t ed25519 -C "your_email@example.com"
```
Example:- 
```
ssh-keygen -f /home/root/.ssh/gitaction_ed25519 -t ed25519 -C "gitactionautodep"
```
Open Newly Created Public SSH Keys then copy the key
```
cat ~/.ssh/gitaction_ed25519.pub
```
Open authorized_keys File which is inside .ssh/authroized_keys then paste the copied key in a new line
```
cd .ssh
```
nano authorized_keys
Open Newly Created Private SSH Keys then copy the key, we will use this key to add New Repository Secret On Github Repo
```
cat ~/.ssh/gitaction_ed25519
```
Name: SSHKEY
Secret: Private_SSH_KEY_Generated_On_Server
Commit and Push the change to Your Github Repo
Get Access to Remote Server via SSH
Syntax:- 
```
ssh -p PORT USERNAME@HOSTIP
```
Example:- 
```
ssh -p 22 root@216.32.44.12
```
Go to Your Project Directory
Syntax:- 
```
cd /var/www/project_folder_name
```
Example:- 
```
cd /var/www/miniblog
```
Pull the changes from github just once this time.
```
git pull
```
Your Deployment should become automate.

On Local Machine make some changes in Your Project then Commit and Push to Github Repo It will automatically deployed on Live Server
You can track your action from Github Actions Tab
If you get any File Permission error in the action then you have to change file permission accordingly.
All Done

