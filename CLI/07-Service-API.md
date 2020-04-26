# Enable/Disable Google APIs and Services

<https://cloud.google.com/sdk/gcloud/reference/services>

## Generic Command

``` cli
    gcloud services GROUP | COMMAND [GCLOUD_WIDE_FLAG …]
```

### GROUPS

- operations
  - Manage Operation for various services.
- vpc-peerings
  - VPC Peerings to various services.

### COMMANDS

- disable
  - Disable a service for consumption for a project.
- enable
  - Enables a service for consumption for a project.
- list
  - List services for a project.

## CLI

List enabled services

```cli
gcloud services list
```

- --enabled 
  - default
- --available | grep [keyword]
  - not enabled

```cli
gcloud services enable [SERVICE]
```