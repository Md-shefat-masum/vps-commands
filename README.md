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

# permission to all file

```
sudo chmod -R 777 /var/DirectoryName
```

# Aftar boot / reboot, restart services

``` 
  sudo service apache2 start
  sudo systemctl start mysqld
  sudo systemctl enable mongod
  sudo systemctl restart mongod
```

