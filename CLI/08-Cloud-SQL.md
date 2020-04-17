# CLI Command for Cloud SQL

## Steps in Creating a Cloud SQL instance

### Enable Google Cloud SQL Admin API

```cli
$ gcloud services enable sqladmin.googleapis.com
```

### Create the instance

<https://cloud.google.com/sdk/gcloud/reference/sql/instances/create>

``` cli
$ > gcloud sql instances create [NAME]\
    --database-version [DB_VERSION] \
    --tier [TIER] \
    --zone=[ZONE]
```

### Set password for the root user

<https://cloud.google.com/sdk/gcloud/reference/sql/users>

``` cli
$ > gcloud sql users set-password root --host=% \
    --instance mysql-instance \
    --password [PASSWORD]
```

## Creating a Database in Cloud SQL

### Connect to the Cloud SQL instance (MySQL)

``` cli
$ > gcloud sql connect [NAME] --user=root
```

will be prompted to enter password

### Creating the database (MySQL)

``` mysql
mysql > CREATE DATABASE test;

mysql > use test;

mysql > CREATE TABLE users (
        id int(11) NOT NULL auto_increment,
        name varchar(100) NOT NULL,
        age int(3) NOT NULL,
        email varchar(100) NOT NULL,
        PRIMARY KEY (id)
        );
```

ctrl+d to exit

## Connection to the SQL instance

### Cloud SQL Connection Name

``` cli
$ > gcloud sql instances describe [NAME] | grep connectionName

connectionName: [PROJECT_ID]:[REGION]:[INSTANCE_NAME]
```

