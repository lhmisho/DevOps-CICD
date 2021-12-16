# Creating a Python Virtual Environment for your Project
[Actual source](https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu-20-04)

Now that we have our [database](https://github.com/lhmisho/DevOps-CICD/blob/main/setup-postgres.md), we can begin getting the rest of our project requirements ready. We will be installing our Python requirements within a virtual environment for easier management.

To do this, we first need access to the `virtualenv` command. We can install this with `pip`.

If you are using <b>Python 3</b>, upgrade `pip` and install the package by typing:

```sh
$ sudo -H pip3 install --upgrade pip
$ sudo -H pip3 install virtualenv
```

With `virtualenv` installed, we can start forming our project. Create and move into a directory where we can keep our project files:

```sh
$ mkdir ~/myprojectdir
$ cd ~/myprojectdir
```

Within the project directory, create a Python virtual environment by typing:

```sh
$ virtualenv myprojectenv
```

This will create a directory called `myprojectenv` within your `myprojectdir` directory. Inside, it will install a local version of Python and a local version of pip. We can use this to install and configure an isolated Python environment for our project.

Before we install our project’s Python requirements, we need to activate the virtual environment. You can do that by typing:

```sh
$ source myprojectenv/bin/activate
```

Your prompt should change to indicate that you are now operating within a Python virtual environment. It will look something like this: 
`(myprojectenv)user@host:~/myprojectdir$.`

With your virtual environment active, install Django, Gunicorn, and the `psycopg2` PostgreSQL adaptor with the local instance of `pip`:

```sh
$ pip install django gunicorn psycopg2
```

You should now have all of the software needed to start a Django project.

[Next: Creating systemd Socket and Service Files for Gunicorn](systemd-socket-and-service-gunicorn.md)