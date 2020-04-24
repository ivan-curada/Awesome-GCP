# Virtual Private Cloud 

<https://cloud.google.com/vpc/docs/overview>

- provices networking functionality for cloud-based resources that is global, scalable, and flexible.
- **`global` resource**
  - consists of a list of regional virtual subnetworks (subnets) in data centers connected by a global wide area network
- VPC networks are **logically isolated** from each other
- **a subnet can be in multi-zones**
- all Compute Engine VM instances, GKE Clusters, and App Engine flexible environment instances rely on a VPC network for commuication 
  - the network connects the resources to each other and to the internet

## Firewall Rules

- Each VPC network inplements a distributed virtual firewall you can configure
- Firewall rules allow to control which packets are allowed to travel to which destinations

### Implied Firewall Rules

- block all incoming connections
- block all outgoing connections

### Default Network

<https://cloud.google.com/vpc/docs/firewalls#more_rules_default_vpc>

- pre-populated firewall rules that allow traffic to instances. can be deleted or modified as necessary
  - `default-allow-internal`
    - allow ingress connections
    - all protocols and ports 
    - among instances in the network
    - priority: 65534 (2nd to lowest)
    - permits incoming connections to VM instances from others in the same network
  - `default-allow-ssh`
    - allow ingress
    - TCP port 22
    - from any source to any instance in the network
    - priority: 65534
  - `default-allow-rdp`
    - allow ingress
    - TCP port 3380 
    - from any source to any instance in the network
    - priority: 65534
    - enables connections to instances running Microsoft Remote Desktop Protocol
  - `default-allow-icmp`
    - allow ingress
    - from any source to any instance in the network
    - priority: 65534
    - enables tools such as ping

## Routes

- govern traffic leaving an isntance
- tell VM instances and VPC network how to send traffic from an instance to a destination, either inside the network or outside of Google cloud
- Each VPC network comes with some system generated routes to route traffic among its subnets and send traffic from eligible instance to the internet
- can create custom static routes to direct some packets to specific destinations
  - create a route that sends all outbound traffic to an instance configures as a NAT gateway

## Forwarding Rules

- forwarding rules direct traffic to a Google Cloud resource in a VPC network on IP address, protocol, and port
- direct traffic from outside of Google Cloud to a destination in the network 
- direct traffic from inside the network
- destinations for forwarding rules are `target instances`, `load balancer targets` (target proxies, target pools, and backend services), and Cloud VPN gateways

## Interfaces and IP addresses

### IP addresses

- Google cloud resources (Compute Engine VM instances, forwarding rules, GKE containers, and App Engine) rely on IP address to communicate

### Aliad IP ranges

- if multiple services are running on a single VM instance
  - each service can be gicen a different internal IP address by using alias IP ranges

### Multiple Network Interfaces

- multiple network interfaces can be given to a VM instances
  - each interface resides a unique VPC network
- enable network appliance VM to act as a gateway for securing traffic among different VPC networks or to and from the internet

## VPC Sharing and Peering

### Shared VPC

- A VPC network from one project (`host project`) can be share to other projects in the Google Cloud organization
- access can be granted to the entire Shared VPC networks or select subnets therein using specific IAM permissions
  - allow to provide centralized control over a common network while maintaining organizational flexibility

### VPC Network Peering

- allows you to build (SaaS) ecosystems in Google Cloud
  - making services available privately acreoss different VPC networks
  - regardless if network are in the same project, different projects, or projects in different organizations
- all communication happen by using private `RFC 1918` IP address
- VM instaces in each peered network can communicate with one another without using external IP addresses
- Peered networks share subnet routes
  - Optionally, both networks can be configures to share custom static and dynamic routes
- Network and Security Administration, Project Owners, Editors, Compute Instance Admins from one network do not automatically get roles for the other network

## Hybrid Cloud

### Cloud VPN

- allows to connect a VPC network to physical, on-premise network or another cloud provider using a secure virtual private network.

### Cloud Interconnect

- allows to connect a VPC network to on-premises network by using a high speed physical connection

## Cloud Load Balancing

