# gcloud Overview

<https://cloud.google.com/sdk/docs/properties>

- command line tool to interact with GCP
- `gsutil` = gcloud storage
- `bq` = gcloud bigquery
- REST API > CLI > Console
- `gcloud alpha` and `gcloud beta`

## Syntax

<https://cloud.google.com/sdk/gcloud/reference/>

```cli
gcloud [global_flags] [service] [group] [command] [flags] [parameter]
``` 

### Global Flags

```cli
--help / -h
--project [PROJECT_ID]
--account [ACCOUNT]
--filter
--format [JSON/YAML/CSV..]
--quiet/-q
```

## Config Properties

<https://cloud.google.com/sdk/docs/properties>

- values entered once and used  by any command that needs them
- can be overriden on a specific command with corresponding flag
- used very often for account, project, region, and zone

```cli
gcloud config set [PROPERTY] [VALUE]
gcloud config get-value [PROPERTY]
gcloud config unset [PROPERTY]
```

## Configurations

<https://cloud.google.com/sdk/docs/configurations>

- can maintain groups of settings and switch between them
- most useful when using multiple projects
- interactive workflow to set uncommon properties in a config with `gcloud init`
- list all properties in a configuration with `gcloud config list`
- list all configurations with `gcloud config configurations list`
  - `IS_ACTIVE` - current
- make a new config `gcloud config configurations create [NAME]`
- use a config `gcloud config configurations activate [NAME]`
  - `--configuration [NAME]`
- list properties of inactive configuration
  - `gcloud config configuration describe [NAME]`
  - `gcloud --configuration [NAME] config list`