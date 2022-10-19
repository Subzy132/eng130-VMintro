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
7. 



