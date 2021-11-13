# SSH without passowrd

We makes connections with our remote servers using SSH. But we cannot login without supplying password of the user that we are trying
to login.
In this article I've tried to describe how we can login to remote server without supplying password.

Step One: Generate ssh key for desktop from where we will try to login to remote server.
---------

```sh
ssh-keygen
```
Pres enter until process is finish.

```diff
- WARNING: make sure you are at the home directory
```

Step Two: Copy the public from .ssh folder
--------
```sh
cat .ssh/id_rsa.pub
```
![alt text](https://bit.ly/3FbgP2R)

Step-Three: Login into remote server and put the copied public key into .ssh/authorized_keys
----------
```sh
mkdir .ssh
touch .ssh/authorized_keys
```
![alt text](https://bit.ly/3kxMrIh)
![alt text](https://bit.ly/3FbgP2R)

```diff
- WARNING: make sure you are at the home directory
```

Let's go back to your desktop and login agian. This time we won't need to put password for login.
