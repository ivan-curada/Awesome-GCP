# Identity and Access Management

## Concepts

- use predefined role
  - exception: use primitive roles in small dev env where small number of users have broad access
- define resource hierarchy
  - specify organization and structure
  - attach pilicies at appropriate level to take advantage of inheritance
- use groups and service accounts 
  - create collection of users
    - assign roles to groups
    - add/remvoe users to/from groups
  - use separate service accoutns for separrate functions
- use custom roles sparingly
  - only when predefined roles does not meet your needs
- cant assign permissions to identities directly
  - permissions > roles > identity