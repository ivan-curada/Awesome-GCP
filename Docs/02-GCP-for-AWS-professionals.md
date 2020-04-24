# Google Cloud for AWS Professionals

<https://cloud.google.com/docs/compare/aws>

## Regions and Zones

### AWS

- products are deploreyed within `Regions`
  - devides regions into `Availabiltiy Zones`
- By design, each AWS Region is isolated and independent from other AWS Regions
  - ensures availability of one region doesn't affect the availability of other regions
- AWS POP provides Content Delivery Network, `AWS CloudFront`

### GCP

- service availability is divided into `Regions` and `Zones`
- also located at `Multi-Regional` level rather than more granular `Regional` or `Zonal` level
  - includes `Google App Engine` and `Google Cloud Storage`
  - locations: United States, Europe, and Asia
- Google Cloud Regions are isolated from each other bbut has built-in functionality that enables Regions to synchronize data across Regions according to the needs of a given Google Cloud Service
- GCP POP provides `Google Cloud CDN` and built-in caching for `Google App Engine`, `Google Cloud Storage` and others.

| Concept | AWS | GCP |
| --| -- | -- |
| Cluster of data centeres and services | Region | Region |
| Absracted data center | Availability Zone | Zone |
| Edge caching | POP (CloudFront) | POP (multiple services) |

## Accounts, Limits, Pricing

## AWS

- sign up for an AWS Account
- can emualte a standard organizational billing structure
  - billed to a specific account
  - billing accounts can be created than create sub-accounts that roll up to them
- has soft limits for new accounts
- Amazon Pricing Calculator

## GCP
- requires a Google account
- service usage is grouped by `Project` rather by account
  - can create muliple, wholly separaate projects under the same account
  - allows to create project spaces for separate divisions or groups within the company
- has soft limits for new accounts
- Google Cloud Calculator

## Web Consoles and Command-Line Interfaces

- both provide web-based consoles
  - allows users to create, manage, and monitor their resources
- both provide command-line interafaces for interacting with the services and resources
  - Amazon CLI
  - Cloud SDK

## Service Types

- Baseline Services
  - Compute
  - Storage
  - Networking
  - Databases
- Higher-level Services
  - Application
    - designed to optimize applications in cloud
  - Big Data and Analytics
    - designed to help process large amounts of data
  - Machine Learning
    - designed to help incorporate perceptual AI, or to train and deploy own machine learning models
  - Operations
    - designed to help track the performance of an application
  - Security
    - designed to keep applications secure

## Service Comparisons

<https://cloud.google.com/docs/compare/aws#service_comparisons>

