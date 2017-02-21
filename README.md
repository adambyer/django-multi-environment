# django-multi-environment

Steps for supporting multiple environments in Django:

- Create a settings folder in your project folder
- Move your settings.py file into the new settings folder and rename it base.py
- Create settings/local.py and settings/production.py
	- These should import everything from base.py
	- These should contain settings specific to your local and production environments
- Edit your manage.py file to set the DJANGO_SETTINGS_MODULE environment variable to point to your local.py module
- Edit your wsgi.py file to set the DJANGO_SETTINGS_MODULE environment variable to point to your production.py module
	- Note that the Procfile in this example allows this to work by specifying that the my_project folder should also be searched for modules (ie. my_project.settings.production). You do not need to add an __init__.py file to the top my_project folder

Notes:

- This setup assumes you are using Django's built-in web server locally (ie. python my_project/manage.py runserver)
- Another option, instead of editing manage.py and wsgi.py, would be to just set the DJANGO_SETTINGS_MODULE environment variable locally and on production as needed
