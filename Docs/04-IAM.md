# Cloud Identity and Access Management

<https://cloud.google.com/iam/docs/overview>

- grant granular access to specific Google Cloud resources and helps prevent access to other resources
- security principle of least privilege
  - grant only necessary permissions to access specific resources
- manage access control by defining `who` (identity) has `what access` (role) for `which resource`
  - Google Cloud resources
    - Compute Engine virtual machine instances
    - Google Kubernetes Engine clusters
    - Cloud Storage buckets
    - organizations, folders, projects
- permission to access a resource isn't granted directly to the end user
- permission are grouped into `roles`
- roles are granted to `authenticated members`
- `Cloud IAM Policy`
  - defines and enforces what roles are granted to which memvers
  - attached to a resource

## Access Management Model

### Member

- The identity of a member is an email address associated with:
  - Google Account (end users)
    - represents a developer, an administrator, or any other person who interacts with Google Cloud
    - can be associated with other domains
  - Service Account (apps and virtual machines)
    - account for an application instead of an individual end user
      - the code runs hosted on Google Cloud as the specified account
    - can represent different logical components of an application
  - Google Group
    - named collection of Google Accounts and Service Accounts
    - every Google Group has a unique email address that's associated 
    - convenient way to apply access policy to a collection of users
    - don't have login credentials and cannot use to establish identity to make a request to access a resource
- The identity of a member is a domain name associated with:
  - G Suite
    - represets a virtual group of all the Google Accounts created in an organization's GSuite account
    - cannot be used to establish identity, but enable convenient permission management
  - Cloud Identity
    - represets a virtual group of all the Google Accounts created in an organization
    - don't have access to G Suite applications and features
- `userid@gmail.com`

### allAuthenticatedUSers

- a special identifier that represents all service accounts and all users in the internet who have authenticated with a Google Account
  - includes personal Gmail accounts not connected to GSuite or Cloud Identity domain
- anonymous visitors aren't included

### allUsers

- special identifier that represents anyone who is on the internet, including authenticated and unauthenticated users

### Role

- collection of permissions
- permissions determie what operations are allowed on a resource
- when a role is granted to a member, all permissions that role contains will be granted.
- `roles/appengine.appAdmin`
- 3 kinds of roles
  - **Primitive Roles**

### Policy

- `Cloud IAM Policy` binds one or more members to a role
- defines who (`member`) has what type of access (`role`) on a resource and attach to the resource

## Concepts

### Resources

- grant Cloud IAM permissions at a granular finer than the project level
- grant Cloud IAM permissions at project level
  - permissions are inherited by all resources within the project

### Permissions

- determines what operations are allowed on a resource
- `service.resource.verb`
- often correspond one-to-one with REST API methods