# How to set up db using mongodb

1. We need to create 2 VMs 
2. Open `Vagrantfile`
3. Edit the content so it looks like this: 

```bash
Vagrant.configure("2") do |config|
#
    config.vm.define "app" do |app|
        app.vm.box = "ubuntu/bionic64"
        app.vm.network "private_network", ip: "192.168.56.12"
        app.vm.synced_folder ".", "/home/vagrant/app"
        app.vm.provision "shell", path: "provision.sh", privileged: false
    end


    config.vm.define "db" do |db|
        db.vm.box = "ubuntu/bionic64"
        db.vm.network "private_network", ip: "192.168.56.13"
    end
```

4. Run `vagrant up` and `vagrant status` to make sure both machines are running
5. To make it easier have two terminals open, one with app open and one with db open
6. In db machine run 
   1. `sudo apt-get update -y`
   2. `sudo apt-get upgrade -y`
   3. `sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927`
   4. `echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list`
   5. `sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20`
7. Now we need to check the status using
   1. `sudo systemctl status mongod`
   2. `sudo systemctl restart mongod`
   3. `sudo systemctl enable mongod`
   4. `sudo systemctl status mongod`
8. Cd into etc using `cd /etc`
9. Run `sudo nano mongod.conf`
10. change the bindIp: to `0.0.0.0` so that anyone can access it.
11. run:
    1. `sudo systemctl restart mongod`
    1. `sudo systemctl enable mongod`
    2. `sudo systemctl status mongod`
12. On the app machine create a env var using bash
    1.  `nano ~/.bashrc`
    2.  Add `export DB_HOST=mongodb://192.168.56.13:27017/posts`
    3.  exit file
    4.  Run `source .bashrc`
    5.  Run `printenv DB_HOST` you should see the variable
6.  now start the app using `npm start`
7.  Go to `http://192.168.56.12/posts`
