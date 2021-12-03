# Configure Nginx to Proxy Pass to Gunicorn

+ main source link: https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu-20-04

Now that Gunicorn is set up, we need to configure Nginx to pass traffic to the process.

Start by creating and opening a new server block in Nginx’s sites-available directory:

```sh
$ sudo vim /etc/nginx/sites-available/myproject
```

Inside, open up a new server block. We will start by specifying that this block should listen on the normal port `80` and that it should respond to our server’s domain name or IP address:

```sh
server {
    listen 80;
    server_name 'server_domain_or_IP';
}
```

Next, we will tell Nginx to ignore any problems with finding a favicon. We will also tell it where to find the static assets that we collected in our `~/myprojectdir/static` directory. All of these files have a standard URI prefix of `“/static”`, so we can create a location block to match those requests:

```sh
server {
    listen 80;
    server_name 'server_domain_or_IP';

    location = /favicon.ico { access_log off; log_not_found off; }
    location /static/ {
        root /home/'project-user'/'myprojectdir';
    }
}
```

Finally, we’ll create a `location / {}` block to match all other requests. Inside of this location, we’ll include the standard `proxy_params` file included with the Nginx installation and then we will pass the traffic directly to the Gunicorn socket:

```sh
server {
    listen 80;
    server_name 'server_domain_or_IP';

    location = /favicon.ico { access_log off; log_not_found off; }
    location /static/ {
        root /home/'project-user'/'myprojectdir';
    }

    location / {
        include proxy_params;
        proxy_pass http://unix:/run/gunicorn.sock;
    }
}
```

Save and close the file when you are finished. Now, we can enable the file by linking it to the `sites-enabled` directory:

```sh
$ sudo ln -s /etc/nginx/sites-available/myproject /etc/nginx/sites-enabled
```

Test your Nginx configuration for syntax errors by typing:

```sh
$ sudo nginx -t
```

If no errors are reported, go ahead and restart Nginx by typing:

```sh
$ sudo systemctl restart nginx
```

Finally, we need to open up our firewall to normal traffic on port 80. Since we no longer need access to the development server, we can remove the rule to open port 8000 as well:

```sh
$ sudo ufw delete allow 8000
$ sudo ufw allow 'Nginx Full'
```

You should now be able to go to your server’s domain or IP address to view your application.