# Quick Start

Make sure you've read [What is Pinax?](what_is_pinax.md) to get a conceptual overview of Pinax.

We strongly recommend running Pinax (or indeed, any Django) projects in a virtual environment:

```
pip install virtualenv
virtualenv mysiteenv
source mysiteenv/bin/activate
```

Once your virtual environment has been activated, install Django and use `django-admin` to create a new project based on the Account Pinax starter project:

```
pip install pinax-cli
pinax start account mysite
```

**NOTE**: _The CLI method for starting a Pinax project has been added for convenience.
The more manual method, using Django’s command-line utility, is also still supported.
Please refer to the [Quick Start Manual](quick_start_manual.md) page for details._

Now install the requirements, initialize your database, load the default sites fixtures, and run the dev server:

```
cd mysite
pip install -r requirements.txt
chmod +x manage.py
./manage.py migrate
./manage.py loaddata sites
./manage.py runserver
```

You now have a running Django site complete with account management and bootstrap-based templates.


To add one more app you will first have to modify the `requirements.txt` file by adding the new app:

    myapp

Make sure to install the requirements once again.
```
pip install -r requirements.txt
```

Next, you will modify the `settings.py`, by adding your app to the `INSTALLED_APPS`:
```
INSTALLED_APPS = [
    ...
    "myapp"
]
```

This will also be a good time to make any additional changes to `settings.py` if needed for the new app.

Be sure to migrate the new app:
```
./manage.py migrate
```

Next, you will modify the `urls.py` to contain a new url for the new app:
```
url(r"^myapp/", include("myapp.url")),
```

This will be a good time to make any adjustments to any templates if needed for the new app.
