# SSH without passowrd

Step One: Generate ssh key for desktop at my desktop
---------

```sh
ssh-keygen
```
pres enter until process is finish.
WARNING: make sure you are at the home directory

Step Two: Copy the public from .ssh folder
--------
```sh
cat .ssh/id_rsa.pub
```
![alt text](https://bit.ly/3HmkoVR)

Step-Three: Login into remote server and put the copied public key into .ssh/authorized_keys
----------
```sh
mkdir .ssh
touch .ssh/authorized_keys
```
![alt text](https://bit.ly/3Fe11N2)
![alt text](https://bit.ly/3HmkoVR)

WARNING: make sure you are at the home directory
-------

Let's go back to your desktop and login agian. This time we won't need to put password for login.