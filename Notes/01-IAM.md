# GCP Identity and Access Maangement

<https://cloud.google.com/iam/docs/overview#how_cloud_iam_works >

## Main parts

### Member

Identity of a user is an email address associated with:

- a Google Account (for end users)
- a service account (for apps and virtual machines)
- a Google Group
- or a domain name associated with a GSuite or Cloud Identity Domain

### allUsers

<https://cloud.google.com/iam/docs/overview#allusers>

- represents anyone on the internet
    - authenticated users and unauthenticated users

### Role

- A **collection of permissions**.
- **Permissions** determine what operations are allowed on a resource.
    - cannot be granted directly to an end user
- When you grant a role to a member, you grant all the permissions that the role contains.
- not an identity (AWS)

### Cloud IAM Policy

- binds one or more members to a role
- we give access to users by attaching a policy to a resource giving permission to a user
- defines *who* (**member**) has what type of access (**role**) on a resource
    - grants **roles** to an authenticaed user
- attached only to a resource not a user (**except service accounts with are both identities and resources**)

## Primitive Roles

<https://cloud.google.com/iam/docs/understanding-roles#primitive_roles>

A Project creator is automatically given a primitive role **Owner.**
    - read/write permissions for the whole project and it's resources
    - can change permissions for resources/services
    - a pre-defined role

## Roles

### Storage Object Viewer

Read only permissions on the bucket
