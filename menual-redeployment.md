# Menual Redeployment of a Django project

Firstly take from the git server

```dif
$ git pull
```

After taking pull activate your project environment and reinstall all the packages

```diff
$(myprojectdir): source venv/bin/activate
$(myprojectenv): pip install -r requirements.txt
```

After re-installing packages now run migrations if there are any migrations on the project.

```diff
$(myprojectenv): python manage.py migrate
```

Now Restart the nginx server and gunicorn.

```dif 
$ sudo systemctl restart nginx
$ sudo systemctl restart gunicorn
```