# Create And add a user to sudo Group

### To Create & Add a user to ```sudo``` group, firstly we will create the user than we will add it to sudo group
### TO Create user type ```sudo su``` and press enter

```sh
sudo su
```
```diff
- WARNING: make sure you are at the home directory
```

### Than put the name of user and than password for the user and confirm password again. Than you will ask for some other information, put the info's or
### leave it blank. Than you will ask for confirmation press ```Y``` for confirm.

![alt text](https://lh3.googleusercontent.com/-QyvEPuDTzFE/YZpj0riNRjI/AAAAAAAAHeU/EviHLIufVQQB4gy1tD0MwbtYCbD0aMumACLcBGAsYHQ/s0/Screenshot%2B2021-11-21%2Bat%2B9.07.51%2BPM.png?authuser=0)


# Now we'll add the user to sudo group.
```sh
usermod -aG sudo deployment-user
```

![alt text](https://lh3.googleusercontent.com/-4WcOxiMTEqs/YZpj3By6D_I/AAAAAAAAHeg/B53ecBZNylgKKAOs2qpty2hA8INcXEUiACLcBGAsYHQ/s0/Screenshot%2B2021-11-21%2Bat%2B9.19.50%2BPM.png?authuser=0)

### Exit and switch to the new user.

![alt text](https://lh3.googleusercontent.com/-xcOrkxBdQck/YZpk5lnLlVI/AAAAAAAAHe8/1QS_LcXPmcwSRoCRbblIMQj1z4u-rPHEwCLcBGAsYHQ/s0/Screenshot%2B2021-11-21%2Bat%2B9.25.11%2BPM.png?authuser=0)
