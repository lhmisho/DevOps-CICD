# Run sudo without password

### In the last article, we configured our remote server to not to require password when we SSH into remote server from our local machine.
### Similarly we can make ```sudo``` command to not to require password when we execute ```sudo``` command.
### Currently I'm logged in to remote as ```lhmisho```. If run ```sudo apt-get update``` it will required password.

![alt text](https://lh3.googleusercontent.com/-mkAmliBcqu0/YY_i5QFin_I/AAAAAAAAACM/vipe8JVQDhoMEvG3r80q26SAe6XgL6opQCLcBGAsYHQ/s0/Screenshot%2B2021-11-13%2Bat%2B8.43.05%2BPM.png?authuser=0)

### To make it execute without password we just need to edit one file.
### Let's edit the file type, sudo visudo press enter.
```sh
>> sudo visudo
```
![alt text](https://lh3.googleusercontent.com/-yQvEKKkYQTk/YY_jwwIwmNI/AAAAAAAAACg/CRm4XSiVdSwoDIf8TAoai0oo1YvQ1aK5gCLcBGAsYHQ/s0/Screenshot%2B2021-11-13%2Bat%2B8.48.31%2BPM.png?authuser=0)

### And scroll down to the line that says 
#### ```# allow member of group sudo to execute any command```
#### ```sudo ALL=(ALL:ALL) ALL```

![alt text](https://lh3.googleusercontent.com/-Rhgpxb96GXY/YY_kDAxCQwI/AAAAAAAAAC0/puCk1tum6ho0_XGPVdGPbQfDHUYhrVsfACLcBGAsYHQ/s0/Screenshot%2B2021-11-13%2Bat%2B8.52.41%2BPM.png?authuser=0)

### And edit this line to 
#### ```sudo ALL=(ALL) NOPASSWD: ALL```

![alt text](https://lh3.googleusercontent.com/-PdmcHrtjwug/YY_kGrKhcSI/AAAAAAAAADA/9BMIIkrlsCI4jhMOSQTcFrkClD6JjyHHACLcBGAsYHQ/s0/Screenshot%2B2021-11-13%2Bat%2B9.06.00%2BPM.png?authuser=0)

### And exit the terminal and reconnect. Run sudo command and you won't have type password.

![alt text](https://lh3.googleusercontent.com/-ea3I95FqZps/YY_kM2qd-3I/AAAAAAAAADM/Jcx5kxN1HrgtUMxkZkfly0M8WI8tFTRYwCLcBGAsYHQ/s0/Screenshot%2B2021-11-13%2Bat%2B9.07.32%2BPM.png?authuser=0)
