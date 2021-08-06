# django-allauth

## To add allauth to django project

`pip install django-allauth==0.44.0`

## Settings.py > Installed Apps
```
#ADD TO INSTALLED APPS

# 3rd party
"allauth", # new
"allauth.account", # new
"allauth.socialaccount", # new
# social providers
"allauth.socialaccount.providers.google", # For Google Authentication
"allauth.socialaccount.providers.twitter", # For Twitter Authentication

'django.contrib.sites', # NEW
```

## Settings.py > Add the following code
```
# ADD AT THE BOTTOM
# ALLAUTH
AUTHENTICATION_BACKENDS = (
    "allauth.account.auth_backends.AuthenticationBackend",
)

SITE_ID = 1
ACCOUNT_EMAIL_VERIFICATION = "none"
LOGIN_REDIRECT_URL = "/"
ACCOUNT_LOGOUT_ON_GET = True

ACCOUNT_USER_MODEL_USERNAME_FIELD = None
ACCOUNT_EMAIL_REQUIRED = True
ACCOUNT_USERNAME_REQUIRED = False
ACCOUNT_AUTHENTICATION_METHOD = 'email'
```

## Run Migration
`python manage.py migrate`


## Admin
`Add your site to Sites`

## Create Social Application
1. Select Provider
2. Enter Name
3. Client ID = API Key
4. Secret Key = API Secret Key
5. Select Site(s)

## On Login Template
Add the following at the top of the template:
`{% load socialaccount %}`

Login button - The following is an example:
```
<a href="{% provider_login_url 'google' %}" class="btn btn-sm btn-google">
    <i class="fab fa-google"></i>
    <span>Login with Google</span>
</a>
```
