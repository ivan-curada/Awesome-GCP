# GCP Cloud Storage

## Cloud Storage Bucket Public Access

By default, **Not Public** access

2 main ways to control access

- Uniform Bucket Level Access
  - uses **Cloud IAM permissions** 
  - whole bucket and all of its objects
  - **GCP recommended practice** - < https://cloud.google.com/storage/docs/access-control#recommended_bucket_architecture>
- Fine Grained Access
  - uses **Access Control Lists**
    - legacy acces control system to set permissions at object level
  - created to have interoperability with AWS S3

## Bucket 

Bucket names are **globally unique.**