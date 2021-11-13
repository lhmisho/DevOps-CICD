# SSH without passowrd

### We makes connections with our remote servers using ```SSH```. But we cannot login without supplying password of the user that we are trying to login.
\
![alt text](https://lh3.googleusercontent.com/-e04xK05XqlY/YY_mleSzlAI/AAAAAAAAAEE/EC_mwyLCjbwkFpgk5WcgswoJSC00vo5UgCLcBGAsYHQ/s0/Screenshot%2B2021-11-13%2Bat%2B10.22.08%2BPM.png?authuser=0)


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
![alt text](https://lh3.googleusercontent.com/-RavFBbouRsw/YY_mi1PNueI/AAAAAAAAAD4/o5i5vZG-Rm8u1G7nPHFqkUqANQePAoZ_ACLcBGAsYHQ/s0/Screenshot%2B2021-11-13%2Bat%2B10.22.33%2BPM.png?authuser=0)

Step-Three: Login into remote server and make create ```authorized_keys``` file into ```.ssh``` dir.
----------

```sh
>> mkdir .ssh
>> touch .ssh/authorized_keys
```

![alt text](https://lh3.googleusercontent.com/-jRB5Vv_59g4/YY_mo-qVNMI/AAAAAAAAAEQ/NGDvCUB9k1Ex_VdNehrCKRMDlKQCRLJYQCLcBGAsYHQ/s0/Screenshot%2B2021-11-13%2Bat%2B10.21.51%2BPM.png?authuser=0)

### Open the ```.ssh/authorized_keys``` file
```ssh
>> sudo vim .ssh/authorized_keys
```

###  AND put the copied public key into ```.ssh/authorized_keys```

![alt text](https://lh3.googleusercontent.com/-UCc3tXj6iCA/YY_qEapeTeI/AAAAAAAAAFQ/sZoxDbVwCtYzTo2a3smswm56ui1H3yjFgCLcBGAsYHQ/s0/Screenshot%2B2021-11-13%2Bat%2B10.38.12%2BPM.png?authuser=0)

```diff
- WARNING: make sure you are at the home directory
```

### Let's go back to your desktop and login agian. This time we won't need to put password for login.
