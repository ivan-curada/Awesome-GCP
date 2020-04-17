# CLI Commands for GCP App Engine

<https://cloud.google.com/sdk/gcloud/reference/app>

## app.yaml

An App Engine configuration file taht specifies how URL paths corresponds to request handlers and static files

- runtime
- latest version identifier
  - can deploy multiple version of application service
- handlers
  - required section
  - specifies URL patterns and how it should be handled

## Deploying to App Engine

<https://cloud.google.com/sdk/gcloud/reference/app/deploy>

``` cli
$ > gcloud app deploy [DEPLOYABLES …]
[--bucket=BUCKET]
[--ignore-file=IGNORE_FILE]
[--image-url=IMAGE_URL]
[--no-promote]
[--no-stop-previous-version]
[--version=VERSION, -v VERSION]
[GCLOUD_WIDE_FLAG …]
```

will be promped for region to deploy

### Open the applicaction

``` cli
$ > gcloud app browse
```