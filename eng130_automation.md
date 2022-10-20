# Learning Automation

## how to automate a script

1. Do `nano [filename].sh` - this will create a file which you can write your script in 
   
2. !/bin/bash has to be at the beginning of every .sh file

3.  Input the scripts you want run within this file andadd comments

4. need to put `-y` so you dont have to manually agree to everything

5. change the permission `chmod [instuctinon] filename`

6. run `sudo [file path][filename] `

## How to sync folders

1. Drag the unzipped folders into the same folder where the vagrant file is
   
2. Open the `Vagrantfile`

3. add `config.vm.synced_folder "[filename]", "[destination path]"`

4. run `vagrant reload` on OS

5. Go back into the VM using `vagrant ssh`

6. check if it's in the folder using `ls`

## Deployment

1. Because I use mac i had to input `export GEM_HOME="$HOME/.gem"` in order to install bundler
2. Input `gem install bundler`
3. In OS put `bundle` this will install everything needed
4. Also in OS run `rake spec` to see if test passed
5. find out what failed and install

## How to install node js

1. on VM run the following commands
   1.  `sudo apt-get install python-software-properties`
   2.  `curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -`
   3.  `sudo apt-get install -y nodejs`
2. then to check nodejs version. run `nodejs -v`

## How to install pm2 and run app

1. In the VM run `sudo npm install pm2 -g`
2. Go into the folder where you want it downloaded
3. run `npm install`
4. run `npm start`
5. You should see a prompt that it's working
6. go onto the browser and enter the IP. My one is `http://192.168.56.12:3000`

![alt text](https://github.com/Subzy132/eng130-VMintro/blob/main/images/Screenshot%202022-10-19%20at%2014.30.26.png)

## How to allow provisons to run when vagrant starts

1. create a `provison.sh`
2. add all the script into there 
```bash
    #!/bin/bash

sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
sudo apt-get install python -y
# install nodejs
sudo apt-get install python-software-properties
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install nodejs -y

# install pm2
sudo npm install pm2 -g

# go into into app folder

cd app
cd app

# run npm

npm install

```

3. add that file on the local host where the vagrantfile is saved 
4. open up `Vagrantfile`
5. And add the following command `config.vm.provision "shell", path: "provision.sh"`
6. Go back into the OS and run `vagrant destroy`
7. If that's working run `vagrant up`
8. now going into the VM using `vagrant ssh` this all should be running

