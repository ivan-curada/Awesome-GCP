# Introduction to Google Cloud Platform

Instructor: Mattias Andersson

<https://learn.acloud.guru/course/gcp-101/>

**Outline**

1. Overview
    - overall context
    - operation
    - design principles
    - structure
2. Services

## GCP Context

AWS is the far-and-away market leader.

What's the right cloud for you?

### Innovation

Google is all about Big Data; huge scale.

Published many white papers

- MapReduce
- Google File System
- Colossus

Released opern source

- Kubernetes (from Borg project)

Commercialized some things in GCP

- BigTable
- Spanner
- GCS (built on Collosus)
 - BigQuery (from Dremel)

Focus on innovation.
Differentiates from AWS (focused on automating heavy lifting)

### Google Organization

Google hires Site Reliability Engineers (SREs), not Operations people

``` markdown
Site Reliability Engineering - How Google Runs Production Systems (O'Reilly Book)
```

GCP was built from dev towards ops/infra.

AWS was built from ops/infra towards dev.

``` markdown
Google is such a developer-focused cloud... Whereas AWS is a DevOps cloud.... - Lynn Langit
```

Google expects people to have a developer background.

### History of GCP

Grew some services internally

- Built by Googlers for Google
- Not originally for Enterprise

Purchased some services

- Firbase, StackDriver, Apogee
- Leaks in abstraction more evident
- logging into a different console

Catch-up to AWS

- Some functionality missing
- Avoided some mistakes in technical debt
- As an underdog, GCP is more willing to be "a cloud" that you use, not just "the cloud" that you use

## GCP Structure & Design

### Design Principle

- Global offering
- Security built on every level of the system
- Huge scale
- Designed with Developers in mind

#### Global System

GCP is intrinsically global

- services are built for world-wide customer
- good user experience, not with scalability

AWS is intrinsically region-scoped

Regional Model

- simplifies data sovereignty
- know where data is physically

Global Model

- easier to handle latency and failures in a global way
- could be more sensitive to multi-region/global failure modes
  - doesn't mean that the regional model is immune to this
  - dues to service failures, not underlyting hardware issues

#### Physical Infrastructure

- vCPU
- Physical Server
- Rack
- Data Center (building)
  - actual building
  - clear separation of duties for workers
  - Virtual tour of GCP data center
- Zone
  - on or more data centers logically grouped together
  - each zone is designed independently to other zones
- Region
  - zones are grouped into a region
  - zones within can communicate to each other quickly
- Multi-Region
  - Each region in a multi-region is at least a 100 miles away from each other
- Private Global Network
  - traffic from one server to another remains in the private network
- Points of Presence (PoP)
  - Network edges and CDN locations
  - connects to the public network
- Global System

##### Global Network

Multi-Regions

1. Europe
2. Asia
3. North America

Regions only

- numbers in push pin show number of zones in a region

1. Australia
2. South America

#### Network Ingress & Egress

Normal network

- Routes via Internet to edge location closest to destination

Google: Routes so traffic enters from Internet at edge closest to source

- Single global IP address can load balance worldwide
  - hit servers closest to them physically
  - if that server is overloaded, it will be routed to next closer region
- Sidesteps many DNS issues
- Data is as much as possible in the private network
  - can now opt for "normal" network routing to reduce price and functionality

#### Pricing

1. Provisioned
2. Usage - pay as you use
3. Network Traffic
    - Ingress - free
    - Egress by GB - paid
    - Egress to GCP services sometimes free
        - don't pay within region unless live in a particular zone
        - depends on destination service
        - depends on location of that service

#### Security

**Distrust the network**

- <https://cloud.google.com/security/security-design/>
- Separation of duties and physical security
- Absolutely everything always encrypted at rest
- Encryption at rest can be disabled, then use the strong key and identity management
- Network encryption
  - All control info within GCP services are encrypted
  - All WAN traffic within regions to be enccrypted automatically
  - Moving towards encrypting all local traffic within data centers
- BeyondCorp
  - Security Model
  - access control from network perimeter to individual devices and user
  - Best security practice: Defense in depth, layers of security

#### Scale and Automation

**Automate all the things to respond appropriately**

- Scalability must be unbounded
- Devs don't want to be answer pages
- One of the Principle of Site Reliability Engineering
  - Engineer the reliability in the system
  - Automate the things tto respond appropriately


#### Resource Quotas (Soft Limits)

- Scope
  - Regional
  - Global
- Change due to valid business reasons
  - Can be automatic
  - Can be requested
    - response in 24-48 hours
    - may be refused
- Queryable

``` cli
gcloud compute project-info describe --project myprojectid
```

#### Organization

Project
- similar to AWS accounts
- has its own resources
  - resourcecs can be shared with other projects
- can be grouped and controlled in a hierarchy