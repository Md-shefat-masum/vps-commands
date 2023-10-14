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

# install git
```
sudo apt-get update
sudo apt-get install git-all
git version

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

