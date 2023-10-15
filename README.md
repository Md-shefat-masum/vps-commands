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

# permission to all file

```
sudo chmod -R 777 /var/DirectoryName
```

# proxy install
```
sudo a2enmod proxy
sudo /etc/init.d/apache2 restart
```

# Aftar boot / reboot, restart services

``` 
  sudo service apache2 start
  sudo systemctl start mysql.service
  sudo systemctl enable mongod
  sudo systemctl restart mongod
```

