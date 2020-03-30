# Create a Project using the gcloud CLI

## List and Create

### List all projects associated with your account

``` cli
gcloud projects list
```

### Create a new project

Google Cloud Project IDs need to be unique accross ALL projects by ALL users

``` cli
gcloud projects create [unique-project-name] --folder [organization-folder]
```

## Change Projects and Configuration

### Check current project

``` cli
gcloud config get-value project
```

### Change project

``` cli
gcloud config set project [project-id]
```

### Show current configuration

``` cli
gcloud config configurations list
```

### Show current configuration properties

``` cli
gcloud config list
```

### Create a new configuration

``` cli
gcloud config configuratiosn create [configuration_name]
```