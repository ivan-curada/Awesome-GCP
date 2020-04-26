# CLI commands for GCP Storage

## Resources

<https://cloud.google.com/storage/docs/gsutil>

<https://github.com/ACloudGuru/gcp-cloud-engineer/blob/master/storage-labs/gsutil-lab-commands.txt>

## Cloud Storage using `gsutil`

Create a new bucket
mb = make buckets

``` cli
gsutil mb gs://[BUCKET-NAME] -c [CLASS_NAME] -l [LOCATION] -p [PROJECT_ID]
```

Copy objects from Cloud Shell to bucket

- copies all to root file
  - archived files includedd
  - parent folders not included
- sharing settings not included
  - private by default

``` cli
gsutil cp [source_file] gs://[BUCKET_NAME/destination-folder]
gsutil cp gs://[BUCKET_NAME/**] gs://[BUCKET_NAME/destination-folder]
```

List buckets in project

``` cli
gsutil ls
```

List bucket's objects

``` cli
gsutil ls gs://[BUCKET_NAME]
gsutil ls gs://[BUCKET_NAME/**] # show all objects in a flat list
gsutil ls gs://[BUCKET_NAME/destination-folder]
```

List bucket's objects including versioning metadata

``` cli
gsutil ls -a gs://[BUCKET_NAME]
```

Remove object in bucket

```cli
gsutil rm gs://[BUCKET_NAME/destination-folder/object]
```

View more information about the bucket

```cli
gsutil ls -L -b gs://[BUCKET_NAME]
```

Show bucket labels (metadata)

```cli
gsutil label get gs://[BUCKET_NAME]
```

Set bucket labels (metadata)

```cli
gsutil label set [FILENAME].json gs://[BUCKET_NAME]

gsutil label ch -l "key:value" gs://[BUCKET_NAME]
```

Change Sharing Settings (Access Control List)

``` cli
gsutil acl ch -u AllUsers:R gs://[BUCKET_NAME/destination-folder/object]

# user -u member:permission

```

### CLI only features

Object Versioning Control

Check if versioning is available

```cli
gsutil versioning get gs://[BUCKET_NAME]
```

Enable versioning

```cli
gsutil versioning set on gs://[BUCKET_NAME]
```