# Deployment and APIs

## Cloud Source Repositories

- global
- AWS CodeCommit, Github
- hosted repositories with integrations to GCP and other hosted repos
- supports standard Git functionalities
- no enhanced workflow support like pull requests
- can serup automatic sync from Github or Bitbucket
- natural integration with Operations Debugger for live-debugging deployed apps
- pay project-user active each month
- pay per GB-month of data storage (prorated)
- pay per GB of data egress

## Cloud Build

- Global
- AWS CodeBuild, TravisCI
- formerly Container Builder
  - turns source code into Docker Images
- CI/CD service
  - continuously takes source code and builds, test, and deploys it
- trigger from cloud source repository by branch, tag, or commit, or zip in GCS
  - can trigger from Github and Bitbucket via Cloud Source Repositories RepoSync
- Runs many builds in parallel (currently 10 at a time)
  - no extra time
- using Dockerfiles
  - super-simple build+push - plus scans for package vulnerabilities
- describe build steps in JSON/YAML file
  - flexiblee and parallel steps
- Push to GCR and export artifacts to GCS - or anywhere your build steps write
- maintains build logs and build history
- pay per minute of build time - but free tier is 120 minutes per day

## Container Registry

- Regional and Multi-Regional
- Amazon ECR, Docker Hub
- Creates and manges a multi-regional GCS bucket, then translates GCR calls to GCS
- IAM integration simplifies buitlds and deployments within GCP
- quick deploys because of GCP networking to GCS
- Directly compatible with standard Docker CLI; native Docker Login support
- UX integrated with cloud Build and Operations Logs
- UI to manage tags and search for images
- Pay directly for storage and egress of underlying GCS (no overhead)

## Cloud Endpoints

- Global
- Amazon API Gateway, more based on NGINX
- handles authorization, monitoring, logging and API keys for APIs backed by GCP
- distributed system
  - proxy instances are distributed and hook into Cloud Load Balancer
- super fast extensible service proxy (ESP) container based oon nginx: <1ms/call>
- uses JWTs and integrates with Firebbase, Auth0, & Google Auth
- Integrates with Stackdriver Loggin and Stackdriver Trace
- Flow
  - App Request > Load Balancer > Extensible Service Proxy Container
    - gets configuration from Google Service Management
    - checks and sends logs to Google Service Control
    - ESP runs on instances
- handles gRPC and can transcode HTTP/JSON
  - can use protocol buffers for faster performance without much overhead, maintaining a RESTful intergace
    - but API needs to be resource-oriented
- Pay per call to your API
  - proxy running on instances
  - auth and logging done by GCP

## Apigee

- Global 
- AWS API Gateway + AWS Shield, CA API Gateway
- Full-featured and enterprise-scale API management platform for whole API lifecycle
- transform calls between different protocols: SOAP, REST, XML, binary, custom
- authenticate via OAuth/SAML/LDAP
  - authoize via Role-Based Access Control
- throttle traffic with quotas, manage API versions etc
- Apigee Sense identifies and alerts administrators to suspicious API behaviors
- Apigee API Monetization supprts various revenue models / rate plans
- Team and Business Tiers are flat monthly rate with API call quotas and feature sets
- Enterprose aties and special feature pricing are "Contact Sales"

## Test Lab for Android

- Global
- AWS Device Farm, Xamarin Test Cloud, Sauce Lab Mobile Testing
- Cloud Infrastructure for running test matrix across variety of real Android devices
- Production-grade devices flashed with Android version and locale you specify
- Robo test captures log giles, saves annotated screeshots and video to show steps
  - default completely automatic but still deterministic, so can show regressiosn
  - can record custom script
- Can also run Espresso and UI Automator 2.0 instrumentaion tests
- Firebase Spark and Flame plans have daily allotment of physical and virtual tests
- Blaze (PAYG) plan charges per device hour - much less for virtual devices
