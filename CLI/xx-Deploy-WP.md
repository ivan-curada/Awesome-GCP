# Provision a Wordpress Instance

## Outline

1. Create Cloud SQL instance to host WP database
2. Create a new WP project to deploy
3. Deploy your WP project
4. Clean up

## Create Cloud SQL Instance

Create a new project

``` cli
 $ gcloud projects create [PROJECT_NAME]
``

Create a **Cloud SQL Instance**

**wordpress** : This is the Cloud SQL instance name
**--activation-policy** : This determines whether your Cloud SQL instance will be started after being provisioned.
**--tier-db** : This is the instance machine type

``` cli
$ gcloud sql instances create wordpress \
    --activation-policy=ALWAYS \
    --tier=db-n1-standard-1 \
    --region=asia-east1
```

Create a **Cloud SQL database**

``` cli
$ gcloud sql databases create wordpress --instance wordpress 
```

Update root password of the Cloud SQL instance

``` cli
$ gcloud sql users set-password root \
    --host=% \
    --instance wordpress \
    --password=[password]
```

## Create a Wordpress project

Update PHP installation in Google Cloud Shell

``` cli
$ sudo apt-get install php7.2-zip
```

Download GCP's PHP tools
**Composer** is PHP's dependency package manager. It is similar to **pip** for Python and **npm** for NodeJS.
Google provides the PHP libraries here : <https://github.com/GoogleCloudPlatform/php-tools> to make it convenient for PHP devs to use Google Cloud for their projects.

``` cli
$ composer require google/cloud-tools
```

Create a wordpress project using **wp-gae**
**wp-gae** command helps create a Wordpress project to be deployed in Google Cloud.

``` cli
$ php vendor/bin/wp-gae create
```

Select Region of Cloud SQL instance.
Enter project options.

``` cli
Please enter project_id (required): [PROJECT_ID]
Please enter db_instance (required): wordpress
Please enter db_name (required): wordpress
Please enter db_user (defaults to 'root'):     
Please enter db_password (required): [PASSWORD]
Do you want to use the same db user and password for local run? (Y/n)Y
```

## Deploy WP project using Google Cloud App Engine

``` cli
$ cd my-wordpress-project
$ gcloud app deploy app.yaml cron.yaml
```

Deployed in **http://[PROJECT_ID].appspot.com .**

## Cleaning up

``` cli
gcloud projects delete [PROJECT-ID]
```