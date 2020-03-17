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
`Site Reliability Engineering - How Google Runs Production Systems (O'Reilly Book)`

GCP was built from dev towards ops/infra
AWS was built from ops/infra towards dev

Lynn Langit
`Google is such a developer-focused cloud... Whereas AWS is a DevOps cloud....`

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
    - servicese are built for world-wide customer
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

#### Physical Infrasture

vCPU
Physical Server
Rack
Data Center (building)
    - actual building
    - clear separation of duties for workers
    - Virtual tour of GCP data center
Zone
    - on or more data centers logically grouped together
    - each zone is designed independently to other zones
Region
    - zones are grouped into a region
    - zones within can communicate to each other quickly
Mu
