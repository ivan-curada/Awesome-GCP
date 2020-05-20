# Networking Services

## Virtual Private Cloud

- Collection of Subnets, Instances, Resources
  - default subnets
  - external IP
  - firewall rules
  - routes
- Private cloud
- Global resource
- VPC network
- Subnets in regions
- resources can communicate using private IP addressing

### default VPC

- when a VPC is created, subnets can be automatically created
  - distinct ip addresses that don't overlap

### Routes

- define paths that the network traffic takes form one resource to another
- each route has a destination subnet or internet

### Creating a VPC and custom subnets

- VPC name and description
- Custom Subnet
  - name
  - region
  - IP address range (private address space)
  - Private Google Access
    - default: off
    - allows subnets to access Google services without assigning external IP address
  - Flow logs
    - generates large data
    - costly for operations monitoring
  - dynamic routing mode
    - Regional
      - learn routes in the region it is created
    - Global
      - learn routes in all the region, or interconnect

## Cloud Router

- Dynamic Routing - Border Gateway Protocol (BGP)
  - allow GCP connect to non-Google networks
  - routes can be learned

## Shared VPC

- share VPC resources across projects in same organization
- centrally managed

## VPC Peering

- share VPC resources across projects in different organizations

## Hybrid Connectivity

- Hybrid Cloud Computing
- VPN service to connect on-prem to GCP
- types
  - VPN
  - Cloud Interconnect
  - Peering

## Virtual Private Network

- Securely connecct networks
- Implemented using IPSec
  - secure IP protocol
- link on-premise networks to GCP
- Traffic routed over public internet
- Up to 3 Gbps
- Types
  - High Availability VPN
    - beta
  - Classic VPN
    - create VPN gateway
      - virtual gateway
      - regional resource
      - uses 1 or more external IP address
      - connects to a peer VPN gateway
        - GCP, other cloud, on premise
    - define Tunnels
      - share traffic between networks
      - secure and encrypted mechanism
      - uses IPsec
      - used between 2 VPN gateways

### Creating VPN Connection

- Create VPN gateway
  - name
  - choose VPC network
  - choose subnet
  - choose/create IP address for VPN gatewway
- Create Tunnel
  - name
  - description
  - remote peer IP address
    - destination VPN gateway endpoint
  - Internet Key Exchange protocol version (IKE)
    - default: v2
    - specify shared key
      - can be generated
  - Specify routes
    - Dynamic Routing (BGP)
      - recommended, best-practice
    - Route-based
    - Policy-based
  - Select/Create Router
    - name
    - description
    - VPC network
    - specify ASN (Autonomous System Number)
      - choose a private ASN
        - "65413"
  - Create BGP Session
    - name
    - Peer ASN
      - ASN at the peer VPC gateway
    - BGP Cloud Router IP Address
    - BGP peer IP

## Interconnect

- Google Networking service
- links GCP VPC to your data center
- High-bandwidth dedicated connectivity if VPN can't provide the bandwidth
- Dedicated
  - direct connection to Google network
  - minimum of 10Gbps - 100Gbps
- Partner
  - connect through 3rd party carrier
  - minimum of 50Mbps - 10Gbps

## VPC Network Peering

- low level network connecction
- uses private communication links between VPCs
- traffic routed using BGP
- does not use GCP objects
  - no access to GCP objects
- Dedicated
  - direct connection to Google network
- Partner
  - connect through 3rd party carrier

## Firewalls

- Control flow of traffic

### default firewall rules

- can be deleted
- default-allow-icmp
  - internal control manangement protocol traffic
- default-allow-internal
  - tcp, up. icmp accross subnets
- default-allow-rdp
  - microsoft remote desktop protocol
- default-allow-ssh
  - ssh connection to linux server

### implied firewall rules

- not listed
- cannot be deleted

### Creating Firewall Rules

- name
- description
- log events to operations logging
- VPC network
- priority
  - default: 1000
  - the higher the number, the lower the priority (65534)
  - highest priority = 0
- Traffic Direction
  - Ingress or Egress
- Action on match
  - Allow or Deny
- Targets
  - all instances
  - specified target tags
  - specified service account
- Source filter
  - IP Address
  - service tags
  - service account
- Ports and Protocols
  - tcp
  - udp
  - other protocols
  - all

## Load Balancing

- Global vs Regional
- Internal vs External
- traffic type

### Global Load Balancers

- workload distributed globally or across multiple regions
- all global load balancers are externa;
- requires Premium Tier Networking
- types
  - HTTP(S) for HTTP and HTTPS traffic
  - TCP Proxy for other TCP traffic
  - SSL Proxy for non-HTTPS SSL/TLS Traffic

### Regional Load Balancers

- used when workload distributed within a region
- types
  - Internal TCP/UDP
    - balances TCP and UDP traffic on private GCP networks
    - only internal load balancer
  - Network TCP/UDP
    - balances SSL and TCP traffic not supported by SSL or TCP proxy

### Implementing load balancing

- create a managed instance group to load balance
- network services > load balancing
  - HTTP(S) load balancing between th VMs
    - name
    - region
    - VPC network
    - Backend Service Configuration
      - consumes the workload/traffic
      - type
        - instance group
        - network endpoint groups
      - choose instnace group
      - port number: 80
      - health check
        = make sure if VM is healthy, otherwise it will be restarted
    - Frontend Service Cofiguration
      - name
      - protocol
      - subnet

## Cloud DNS

- domain name service
- DNS Zone
  - containers for DNS records
  - same DNS name suffix
  - zone type
    - public/private
  - Zone name
  - DNS name (domain)
- SOA record
  - default created
  - start of authority record
  - domain is delegated from parent
- NS record
  - default created
  - stores info about name servers
- A record
  - associate name with IP address
- Adding a record type
  - DNS Name
    - subdomain.domain.ext
  - Resource Record Type
  - TTL
    - amount of time the record to be cached before looking up the value again from the datastore
  - IPv4 Address
