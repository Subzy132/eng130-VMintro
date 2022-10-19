# Here is the cheat sheet for using the vagrant command

```bash
Usage: vagrant [options] <command> [<args>]

    -h, --help                       Print this help.

Common commands:
     autocomplete    manages autocomplete installation on host
     box             manages boxes: installation, removal, etc.
     cloud           manages everything related to Vagrant Cloud
     destroy         stops and deletes all traces of the vagrant machine
     global-status   outputs status Vagrant environments for this user
     halt            stops the vagrant machine
     help            shows the help for a subcommand
     init            initializes a new Vagrant environment by creating a 
Vagrantfile
     login           
     package         packages a running vagrant environment into a box
     plugin          manages plugins: install, uninstall, update, etc.
     port            displays information about guest port mappings
     powershell      connects to machine via powershell remoting
     provision       provisions the vagrant machine
     push            deploys code in this environment to a configured 
destination
     rdp             connects to machine via RDP
     reload          restarts vagrant machine, loads new Vagrantfile 
configuration
     resume          resume a suspended vagrant machine
     serve           start Vagrant server
     snapshot        manages snapshots: saving, restoring, etc.
     ssh             connects to machine via SSH
     ssh-config      outputs OpenSSH valid configuration to connect to the 
machine
     status          outputs status of the vagrant machine
     suspend         suspends the machine
     up              starts and provisions the vagrant environment
     upload          upload to machine via communicator
     validate        validates the Vagrantfile
     version         prints current and latest Vagrant version
     winrm           executes commands on a machine via WinRM
     winrm-config    outputs WinRM configuration to connect to the machine

For help on any individual command run `vagrant COMMAND -h`

Additional subcommands are available, but are either more advanced
or not commonly used. To see all subcommands, run the command
`vagrant list-commands`.
        --[no-]color                 Enable or disable color output
        --machine-readable           Enable machine readable output
    -v, --version                    Display Vagrant version
        --debug                      Enable debug output
        --timestamp                  Enable timestamps on log output
        --debug-timestamp            Enable debug output with timestamps
        --no-tty                     Enable non-interactive output

```
### for windows users you need hyper v and here is the documentation
https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v

### Dev Env
### Vagrant

- To access VM from directory `vagrant ssh`
- To exit vm type `exit`
- check internet connectivity `sudo apt-get update`
- check if theres any updates needed `sudo apt-get upgrade`
- Where am i? `pwd` this gives you the current location
- Who am i? `uname` or `uname -a` or `whoami` - use these to find out who is using the machine
- How to create file in linux `touch filename` and `nano filename`
- How to check file/folder available in current location `ls` or to check hidden files as well `ls -a`
- How to create a folder `mkdir folder-name`
- How to navigate to the folder `cd folder-name`
- How to navigate back/out `cd ..` or `cd` Enter
- How to delete a file/folder `rm -rf file/foldername`
- `cp [...file/directory-sources] [destination]` to copy file to a specific destination
- for Admin access `sudo` switch to admin user `sudo su`
- to check properties of files `ls -l` or `ll` which lists all hidden files 
- to change permission `chmod instruction file-name` i.e `chmod 700 test.txt`
- Currently running process `top` & `ps aux`
- To remove any process `kill PID` - Kill {processID} - `kill 7`
- How to delete folder/hidden folder `ls -a` to see all hidden folders `rm -`
- To print specific lines from a text file use `sed` for example `sed -n '1,10p' test.txt` this will print the first 10 lines
- to print from the top you would use `head -n [value] filename`
- to print from the bottom you would use `tail -n [value] filename`
- pipe | is when linux will take an output to send the output of one command/program/process to another command/program/process for further processing
- grep will search for a string within a text file.
     - for example `grep [string][filename]`
- sort will print the output of a file in given order
     - for example `sort [filename]` 
- install `nginx` in our VM
- create a `private-network` between localhost & vm
- allocate an IP address - for mac users copy and paste the one given
- `sudo apt-get install nginx -y`
- how to check a tool/software status in linux `sudo systemctl status [name]`
- how to restart a process in Linux `sudo systemctl start [name]`, `sudo systemctl stop [name]` `sudo systemctl restart [name]`
- need to put private network in vagrant file
- added `config.vm.network "private_network", ip: "192.168.56.0"` to vagrant file
- then done `vagrant reload` on local host terminal
- used `vagrant ssh` to get back in
- if `vagrant reload`doesn't work then try `vagrant destroy`  and then `vagrant up`

![alt text](https://github.com/Subzy132/eng130-VMintro/blob/main/images/Screenshot%202022-10-18%20at%2016.02.08.png)

## What is Virtualisation

virtualisation is the process of running a virtual instance of a computer system. So you are essentially running another operating system that has no interferance with your own one. 

To the applications running on top of the virtualized machine, it can appear as if they are on their own dedicated machine, where the operating system, libraries, and other programs are unique to the guest virtualized system and unconnected to the host operating system which sits below it.

## What is dev env

It stands for development environment. it is essentially a workspace which allows a developer or someone to to run process and programming tools to develop code for an application or software product. 

So it will have everything the person needs to develop an application. it will have all the tool adn services needed. Allowing them to be as efficient as possible. 

## What is Vagrant


Vagrant is a tool for building and managing virtual machine environments in a single workflow. With an easy-to-use workflow and focus on automation, Vagrant lowers development environment setup time, increases production parity, and makes the "works on my machine" excuse a relic of the past


## what is Virtual box

oracle VM VirtualBox is cross-platform virtualization software. It allows users to extend their existing computer to run multiple operating systems including Microsoft Windows, Mac OS X, Linux, and Oracle Solaris, at the same time.

## why should wwe use all of them

Building a software prototyping environment (aka lab) is far simpler than ever before. No longer do you have to wait to build a physical machine, then wait to download ISO images of the virtualization stuff, operating systems, software packages etc.

Simply use Vagrant and VirtualBox together. You'll have a highly functional lab for software development up fast with some added agility for prototyping infrastructure choices too. 

