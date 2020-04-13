# CLI commands for GCP Storage

## Cloud Storage using `gsutil`

Create a new bucket
mb =

``` cli
gsutil mb gs://[BUCKET-NAME]
```


Copy objects from Cloud Shell to bucket

``` cli
gsutil cp [source_file] gs://[BUCKET_NAME/destination-folder]
```


List bucket contents

``` cli
gsutil ls gs://[BUCKET_NAME/destination-folder]
```


View more information about the bucket

```cli
gsutil ls -L -b gs://[BUCKET_NAME]
```