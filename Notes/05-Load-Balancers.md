# Load Balancers

## HTTP Internal Load Balancer

- regional load balancer

Requirements:

- subnets must be in the same region
  - subnet of backend managed instance group must be in the same region as the load balancer
- subnet for the backend where managed instance groups are created
- reserved subnet for proxy
  - managed by Google
  - contains the source IPs of the HTTP load balancers in that region

### Steps

1. Create a VPC, subnets and firewall rules
2. Create an instance template
3. Create a managed instance group
4. Create an internal load balancer
5. Test traffic to internal load balancer

### Firewall rule

- allow traffic from reserved subnet (load balancer subnet) to instance subnet
  - tcp: 80
- allow GCP health checks to check if managed instance group backend can be reachable
  - source IP: 130.211.0.0/22, 35.191.0.0/16
    - probe IP addresses for Internal HTTP Load Balancer
  - tcp
- allow SSH to main instance subnet
  - source IP: 0.0.0.0/0
  - tcp: 
  
### Creating Internal Load Balancer

GCP Navigation Menu > Networking Section > Network Services > Load balancing > Create Load Balancer

- Select **HTTP(S) Load Balancing**
- Internal, choose **Only between my VMs**
- Details for Name, Region, Network
- Create Reserved Subnet
- Click Create
- Backend Configuration - Create Backend Service
  - Backend type: Instance Groups
  - Create Health Check (use default)
- Routing Rules
  - Select Backend Service
  - Mode: Simple host and path rule
- Frontend Configuration
  - Protocol: HTTP
  - Choose instance subnet
  - Internal IP: Static or Ephemera
  - Port: 80