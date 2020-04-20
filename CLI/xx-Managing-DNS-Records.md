# Managing DNS Records with Cloud DNS

Managed Zones == Supported Domains

DNSSEC

- authenticates responses to domain name lookups
- does not provide privacy protections 
- but prevents attackers from manipulating or poisoning the responses to DNS requests
- <https://cloud.google.com/dns/docs/dnssec?hl=en_US&_ga=2.254679816.-129804501.1586835056>

## Using the Console

Networking > Network services > Cloud DNS > Create Zone

- Enter the details
  - Zone type: Public
  - Zone name: [domain]-[suffix]
  - DNS name: [domain].[suffix]
  - DNSSEC: Disabled
  - Description
- Click Create
- Add Record set
- Enter the Record set details
  - DNS Name: [subdomain].[domain].[suffix]
  - Resource Record Type
  - TTL
  - TXT data
- Click Create

## Using CLI

### Creating DNS Zones

<https://cloud.google.com/sdk/gcloud/reference/dns/managed-zones/create>

```cli
gcloud dns managed-zones create [ZONE_NAME ]--description=[DESCRIPTION] --dns-name=[DNS_NAME]
```

### Creating DNS Records

``` cli
$ gcloud dns record-sets transaction start --zone=[ZONE_NAME]

$ gcloud dns record-sets transaction add ["TEXT_DATA
] --name=[subdomain].[domain].[suffix] --ttl=60 --type=[RESOURCE_RECORD_TYPE]--zone=[ZONE_NAME]

$ gcloud dns record-sets transaction execute --zone=[ZONE_NAME]
```

### List DNS Records

``` cli
$ gcloud dns record-sets list --zone=[ZONE_NAME]
```