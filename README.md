# wagtail_streamforms

[![CircleCI](https://circleci.com/gh/AccentDesign/wagtail_streamforms/tree/master.svg?style=svg)](https://circleci.com/gh/AccentDesign/wagtail_streamforms/tree/master)
[![Coverage Status](https://coveralls.io/repos/github/AccentDesign/wagtail_streamforms/badge.svg?branch=master)](https://coveralls.io/github/AccentDesign/wagtail_streamforms?branch=master)

## General Setup

1. Add wagtail_streamforms to your INSTALLED_APPS:

```
INSTALLED_APPS = [
    ...
    'wagtail_streamforms'
    ...
]
```

2. Define the form templates in your settings.py:

```python
# defaults 
WAGTAIL_STREAMFORMS_FORM_TEMPLATES = (
    ('streamforms/form_block.html', 'Default Form Template'),
)
```

## Enable Recaptcha

Has been enabled via the [django-recaptcha](https://github.com/praekelt/django-recaptcha) package. Please note that only one recapcha should be used per page.

Just add captcha to your INSTALLED_APPS:

```
INSTALLED_APPS = [
    ...
    'captcha'
    ...
]
```

and add the required keys in your settings.py which you can get from google's recapcha service:

```
RECAPTCHA_PUBLIC_KEY = 'xxx'
RECAPTCHA_PRIVATE_KEY = 'xxx'
 
# To use the new No Captcha reCaptcha
NOCAPTCHA = True
```

## Styling Form Errors

Below is an example of the css you will need to highlight the form errors:

```scss
// errors
.has-error input,
.has-error select,
.has-error textarea { border-color: red; }
 
.has-error label,
.has-error .error-msg { color: red; }
 
// recaptcha
.g-recaptcha { margin-bottom: 20px; }
```

## Example Site

1. Run the docker container

```bash
$ docker-compose up
```

2. Create yourself a superuser
```bash
$ docker exec -it <container_name> bash
$ python manage.py createsuperuser
```

3. Go to [http://127.0.0.1:8000](http://127.0.0.1:8000)

## Tests

1, Install dependencies

You will need pyenv installed see [http://snippets.accentdesign.co.uk/snippets/pyenv-osx/](http://snippets.accentdesign.co.uk/snippets/pyenv-osx/)

Also tox
```bash
$ pip install tox
```

2, Install python versions in pyenv

```bash
$ pyenv install 3.4.4
$ pyenv install 3.5.3
$ pyenv install 3.6.2
```

3, Set local project versions

```bash
$ pyenv local 3.4.4 3.5.3 3.6.2
```

4, Run the tests

```bash
$ tox
```

or run for a single environment

```bash
$ tox -e py36-dj111-wt112
```
