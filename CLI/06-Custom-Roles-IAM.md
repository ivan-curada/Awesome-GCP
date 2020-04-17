# Roles

``` cli
List of permissions available for a project

$ gcloud list-testable-permissions [PROJECT_FULL_URI]

apiDisabled: true/false
name:
stage: GA/
title:


List roles that can be applied to a given resouce

$ gcloud iam list-grantable-roles [PROJECT_FULL_URI]

description:
name: roles/--
title:


Check role metadata

$ gcloud iam roles describe [ROLE_NAME]


List IAM Roles in project

$ gcloud iam roles list --project $DEVSHELL_PROJECT_ID
```

## Create Custom Role

``` cli
$ gcloud iam roles create [ROLE_NAME] \
    --project $DEVSHELL_PROJECT_ID\ 
    --title [ROLE_TITLE]\
    --description ["DESCRIPTION"]\
    --permissions [PERMISSION1,PERMISSION2,..]
    --stage [STAGE_NAME]
```

- `--project` or `--organization`
  - roles are specified per project or per organization
  - `$DEVSHELL_PROJECT_ID` - varialbe for current project ID in configuration
- `--stage`
  - stage the roles before deploying into production
  - `ALPHA`, `BETA`, `GA`, `DISABLED`, `DEPRECATED`

## Disabling and Deleting a Custom Role

```cli
$ gcloud iam roles update [ROLE_NAME]\
    --project $DEVSHELL_PROJECT_ID\
    --stage DISABLED
```

```cli
$ gcloud iam roles delete [ROLE_NAME]\
    --project $DEVSHELL_PROJECT_ID