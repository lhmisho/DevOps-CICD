# Create And add a user to sudo Group

### To create & add a user to ```sudo``` group, firstly we will create the user than add into to sudo group. To Create user type ```sudo su``` and press enter

```sh
>> sudo su
```
```diff
- WARNING: make sure you are at the home directory
```

### Than put the name of user and than password for the user and confirm password again. Than you will ask for some other information, put the info's or
### leave it blank. Than you will ask for confirmation press ```Y``` for confirm.

![alt text](https://raw.githubusercontent.com/lhmisho/DevOps-CICD/main/images/add-user.png)


### Now add the user to sudo group.
```sh
>> usermod -aG sudo deployment-user
```

![alt text](https://raw.githubusercontent.com/lhmisho/DevOps-CICD/main/images/add-sudo-user-group.png)

### Exit and switch to the new user.

![alt text](https://raw.githubusercontent.com/lhmisho/DevOps-CICD/main/images/switch-to-new-sudo-user.png)
