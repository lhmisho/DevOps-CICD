# Creating systemd Socket and Service Files for Gunicorn

To run Django project by systemd socket and service gunicorn, We need to install ```gunicorn```. Assuming that our system already has other dependency installed like virtualenv,django,db dependencies etc.

```sh
$ pip install gunicorn
```

## Testing Gunicorn’s Ability to Serve the Project
We can test ```gunicorn``` entering our project directory and using gunicorn to load the project’s WSGI module:

```sh
(myprojectenv) $ cd ~/myprojectdir
(myprojectenv) $ gunicorn --bind 0.0.0.0:8000 myproject.wsgi
```

This will start Gunicorn on the same interface that the Django development server was running on.
We have tested that Gunicorn can interact with our Django application, but we should implement a more robust way of starting and stopping the application server. To accomplish this, we’ll make systemd service and socket files.

The Gunicorn socket will be created at boot and will listen for connections. When a connection occurs, systemd will automatically start the Gunicorn process to handle the connection.

Start by creating and opening a systemd socket file for Gunicorn with `sudo` privileges:

```sh
$ sudo vim /etc/systemd/system/gunicorn.socket
```

Inside, we will create a [Unit] section to describe the socket, a [Socket] section to define the socket location, and an [Install] section to make sure the socket is created at the right time:

```sh
[Unit]
Description=gunicorn socket

[Socket]
ListenStream=/run/gunicorn.sock

[Install]
WantedBy=sockets.target
```


Save and close the file when you are finished.

Next, create and open a systemd service file for Gunicorn with sudo privileges in your text editor. The service filename should match the socket filename with the exception of the extension:

```sh
$ sudo vim /etc/systemd/system/gunicorn.service
```

This will tell systemd what to link this service to if we enable it to start at boot. We want this service to start when the regular multi-user system is up and running:

```diff
[Unit]
Description=gunicorn daemon
Requires=gunicorn.socket
After=network.target

[Service]
User=PROJECT-USER
Group=www-data
WorkingDirectory=/home/PROJECT-USER/MYPROJECTDIR
ExecStart=/home/PROJECT-USER/MYPROJECTDIR/MYPROJECTENV/bin/gunicorn \
          --access-logfile - \
          --workers 3 \
          --bind unix:/run/gunicorn.sock \
          MYPROJECT.wsgi:application

[Install]
WantedBy=multi-user.target
```

+ change `PROJECT-USER,PROJECT-USER,MYPROJECTDIR,MYPROJECT` as your own project credentials.

With that, our systemd service file is complete. Save and close it now.

We can now start and enable the Gunicorn socket. This will create the socket file at /run/gunicorn.sock now and at boot. When a connection is made to that socket, systemd will automatically start the gunicorn.service to handle it:

```sh
$ sudo systemctl start gunicorn.socket
$ sudo systemctl enable gunicorn.socket
```

Reload the daemon to reread the service definition and restart the Gunicorn process by typing:

```sh
$ sudo systemctl daemon-reload
$ sudo systemctl restart gunicorn
```

## Checking for the Gunicorn Socket File

Check the status of the process to find out whether it was able to start:

```sh
sudo systemctl status gunicorn.socket
```

You should receive an output like this:

```diff
Output
● gunicorn.socket - gunicorn socket
     Loaded: loaded (/etc/systemd/system/gunicorn.socket; enabled; vendor prese>
     Active: active (listening) since Fri 2020-06-26 17:53:10 UTC; 14s ago
   Triggers: ● gunicorn.service
     Listen: /run/gunicorn.sock (Stream)
      Tasks: 0 (limit: 1137)
     Memory: 0B
     CGroup: /system.slice/gunicorn.socket
```