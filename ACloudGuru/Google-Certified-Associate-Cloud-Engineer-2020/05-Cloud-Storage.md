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


## Bucket Locations

Specify location for sotring object data

- **region**
  - specific geographic place
- **dual-region**
  - specific pair of regions
  - geo-redundant
- **multi-region**
  - large geographic area that contains two or more geographic places
  - geo-redundant

### Considetiaons

- Good Location balances latency, availability, and bandwidth costs for data consumers
- store data in a location that is convenient or contains the majority of the users of teh data
- region
  - optimize latency and network bandwidth (analytics pieplines) that are grouped in same region
- dual-region
  - similar performance advantages as rgions
  - higher availability
- multi-region
  - serve content ot data consumers outside of Google Netwo and distributed across large geographic areas
  - higher availabiltiy

### Compute Engine VM notes

- storing in the same region as VM isntances can provide better performance
  - applies to both regions and dual-regions

### Available Locations

- Multi-Regions
  - ASIA
  - EU
  - US
- Dual-Regions
  - EUR4
    - EUROPE-NORTH1 and EUROPE-WEST4
  - NAM4
    - US-CENTRAL1 and US-EAST1

### Alpha Locations

- exist for `Durable Reduced Availability Storage`
  - not recommended for production use
- US-CENTRAL2