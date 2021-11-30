# Run sudo without password

### In the last article, we configured our remote server to not to require password when SSH into remote server from our local machine.
### Similarly we can make ```sudo``` command to not to require password when we execute any ```sudo``` command.
### Currently I'm logged in to remote as ```lhmisho```. If run ```sudo apt-get update``` it will required password.

![alt text](https://raw.githubusercontent.com/lhmisho/DevOps-CICD/main/images/apt-update.png)

### To make it execute without password we just need to edit one file.
### Let's edit the file type, ```sudo visudo``` press enter.
```sh
>> sudo visudo
```
![alt text](https://raw.githubusercontent.com/lhmisho/DevOps-CICD/main/images/visudo.png)

### And scroll down to the line that says 
#### allow member of group sudo to execute any command
#### ```sudo ALL=(ALL:ALL) ALL```

![alt text](https://raw.githubusercontent.com/lhmisho/DevOps-CICD/main/images/visudo1.png)

### And edit this line to 
#### ```sudo ALL=(ALL) NOPASSWD: ALL```

![alt text](https://raw.githubusercontent.com/lhmisho/DevOps-CICD/main/images/visudo-nopass.png)

### And exit the terminal and reconnect. Run sudo command and you won't have type password.

![alt text](https://raw.githubusercontent.com/lhmisho/DevOps-CICD/main/images/apt-update-nopass.png)
