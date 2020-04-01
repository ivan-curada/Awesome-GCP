# Account Setup

## Free Tier GCP Accounts

Billing account that does not get charged

- $300 credit that can last 12 months
- requires credit card for verification
- "When your trial ends, your account will be paused and you'll have the option to upgrade to a paid account"
- Business accounts are not eligible

### Free trial Restrictions

- No more than 8 vCPUs simultatneously
- No GPUS
- Np TPUs
- No Quota increases
- No crypto-mining
- No SLA
- No premium OS licenses
- No Cloud Launcher products with extra usage fee

### Always Free

<https://cloud.google.com/free/docs/gcp-free-tier>

- no count againt free trial credits
- lasts beyond end of free trial

### Principle of Least Privilege

``` markdown
Every program and every privileged user of the system should operate using the least amount of privilege necessary to complete the job.
- Jerome Saltzer, Communications of the ACM
```

- bad habit to run with admin for normal activites
- admin account with billing access very rarely needed

Create a separate GMail account for billing
<https://console.cloud.google.com/freetrial>

- secure with 2FA (two-factor authentication)
- can forward to main account
  - This is a potential attack vector to consider

## GCP Console

<https://console.cloud.google.com/>

## Billing Export

<https://cloud.google.com/billing/docs/how-to/export-data-bigquery>

``` markdown
Billing export to BigQuery enable you to export you daily usage and cost estimates automatically thoughout the day to a BigQuery dataset you specify. 
You can then access your billing data from BigQuery.
```

Billing >> Billing Export >> Edit Settings

- data is stored in a context of a project and inside in a BigQuery dataset

BigQuery >> Create Dataset

- Dataset ID = `billing_export`
- Data location = region
- Default table expiration = Never
  - keep historical data
- Description
- Label 
  - resource label/tag for tracking
  - key value pairs
    - `key: value`

Billing >> Billing Export >> Edit Settings

- choose project
- choose `billing_export` BigQuery dataset
- click `save`

Use **Projects** to manage groups of resources

- `Project Names` do not need to be globally unique
- `Project IDs` should be unique

- export must be set up billing account
- resources should be placed in appropriate projects
- resources should be tagged with labels
- billing export is not real-time
  - delay is in hours
- previous charges before the Billing Export are not exported

## Billing Alerts

<https://cloud.google.com/billing/docs/how-to/budgets>

``` markdown
You can apply a budget to either a billing account or a project, and you can set the budget at a specifi amount ir atch it to the previous month's spend.
You can also create alerts to notify billing administrators when spending exceeds a percentage of your budget.
```

Billing > Billing & Alerts >> Create a Budget

- Budget Name
- Project or Billing Account
- Budget amount
  - may include credit
- Alert based on percentage of budget
- Manage notification using Pub/Sub is possible

## Set up Non-Admin User Access

**Roles** are collections of permissions to use or manage resources

### Role: Billing Account User

**Purpose:** Link projects to billing accounts
**Level:** Organization or biling account
**Use Case:**

- very restricted permissions
- typically in combination with ``Project Creator``
  - These two roles allow a user to create new projects linked to the billing account on which the role is granted
- unable to upgrade free trial billing
- able to view users and admin
    - cannot add new users or admin
- can disable or change billing account

Log In as Admin account

Billing >> Select Billing Account >> Shwow Info Panel

- Add email address to Member
- Select Role `Billing Account User`

## Cloud Shell and Editor

<https://cloud.google.com/shell/>

Command Line access to cloud resources directly from browser

- Web browser access
  - no need for local terminal
  - Automatic SSH key management
- 5GB of persistent storage in home directory
- Easy-access to pre-installed tools
  - Docker
  - Git
  - Python, Java, Go, Node.js
- Pre-authorized and always up-to date
- Web preview of web app running on local port
- Linux Debian-based OS
- Boost Mode
  - temporarily increases power of Cloud Shell VM for 24 hours
  - subject to regular usage limits
  - experimental
  - data in home directory will persist but all running processes will be lost
- VM is ephemeral and will be reset approximately 20 minutes after session ends
- no system-wide change will persist beyond that
- Web preview
- Cloud Shell Editor 