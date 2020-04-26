# Cloud Storage

- bucket names are globally unique
- bucket location is dependent on the storage class
- bucket location cannot be changed after creation
- retrieval cost can be free in Multi-Regional buckets but network transfers (leaving Google Cloud) is charged
- every object file is private by default
  - signed request URL
- public object file
  - `https://storage.googleapis.com/[BUCKET_NAME]/[FOLDER]/[OBJECT_NAME]
- updating storage class
  - affects new objects only(?)
- object versioning is only done through the console