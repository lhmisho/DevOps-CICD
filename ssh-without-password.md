# SSH without passowrd

### We makes connections with our remote servers using ```SSH```. But we cannot login without supplying password of the user that we are trying to login.
\
![alt text](https://raw.githubusercontent.com/lhmisho/DevOps-CICD/main/images/ssh-with-pass.png)


### In this article I've tried to describe how we can login to remote server without supplying password.

Step One: Generate ```SSH``` key for desktop from where we will try to login to remote server.
---------

```sh
>> ssh-keygen
```

### ```Press enter until process is finish.```


```diff
- WARNING: make sure you are at the home directory
```

Step Two: Copy the public key from .ssh folder
--------
```sh
>> cat .ssh/id_rsa.pub
```
![alt text](https://raw.githubusercontent.com/lhmisho/DevOps-CICD/main/images/rsa-pub.png)

Step-Three: Login into remote server and make create ```authorized_keys``` file into ```.ssh``` dir.
----------

```sh
>> mkdir .ssh && touch .ssh/authorized_keys
```

![alt text](https://raw.githubusercontent.com/lhmisho/DevOps-CICD/main/images/authorized-key-folder-create.png)

### Open the ```.ssh/authorized_keys``` file
```ssh
>> sudo vim .ssh/authorized_keys
```

###  AND put the copied public key into ```.ssh/authorized_keys```

![alt text](https://raw.githubusercontent.com/lhmisho/DevOps-CICD/main/images/rsa-pub-3.png)

```diff
- WARNING: make sure you are at the home directory
```

### Let's go back to your desktop and login agian. This time we won't need to put password for login.
