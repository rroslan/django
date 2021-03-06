# Getting started with Django on Google Cloud Platform on App Engine Standard

[![Open in Cloud Shell][shell_img]][shell_link]

[shell_img]: http://gstatic.com/cloudssh/images/open-btn.png
[shell_link]: https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/GoogleCloudPlatform/python-docs-samples&page=editor&open_in_editor=appengine/standard_python38/django/README.md

This repository is an example of how to run a [Django](https://www.djangoproject.com/) 
app on Google App Engine Standard Environment. It uses the 
[Writing your first Django app](https://docs.djangoproject.com/en/2.1/intro/tutorial01/) as the 
example app to deploy.


# Tutorial
See our [Running Django in the App Engine Standard Environment](https://cloud.google.com/python/django/appengine) tutorial for instructions for setting up and deploying this sample application.

# Custom Setup
I am using postgresql instead of mysql

Create postgresql instance on google sql

Create a database on postgresql

Edit settings.py to your setup

gsutil defacl set public-read gs://<your-gcs-bucket> for public access

python manage.py collectstatic

gsutil rsync -R static/ gs://your-gcs-bucket/static

STATIC_URL = 
https://storage.googleapis.com/your-gcs-bucket/static/

gsutil defacl set public-read gs://your-gcs-bucket

gsutil cors set cors.config.json gs://your-gcs-bucket

gsutil acl ch -u AllUsers:R gs://your-gcs-bucket

gsutil iam ch allUsers:objectViewer gs://your-gcs-bucket

gcloud app deploy