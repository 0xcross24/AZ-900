# Describe the core architectural components of Azure

- Physical Infrastructure
- Management Infrastructure

## Describe Azure physical infrastructure

### Regions

- A geographical area on the planet that contains at least one datacenter
- Networked together with low-latency network

### Availability Zones

- A physically separated datacenters within an Azure Region
- One or more datacenters
- Primarily for VMs, managed disks, load balancers, SQL databses
     - Zonal services: pin a resource to a specific zone
     - Zone-redundant services: replicates automatically across zones (zone-redundant storage, SQL Database)
     - Non-regional services: always available from Azure geographies and are resilient to zone/region-wide outages

### Region Pairs

- Paired with another region within the same geography at least 300 miles away
- Static pairing so they can't be chosen
- Example: West US and East US
- Provides backup to each other incase of an outage

#### Sovereign Regions

- Regions that are isolated from the main instances of Azure
- US DoD Central, US Gov Virginia, US Gov Iowa
     - These regions are physical and logical network-isolated
- China East, China North

## Describe Azure Management infrastructure 

- Azure resources and resource groups
- Subscriptions and accounts

### Azure resources and resource groups

#### Resource

- Can be created, provision, and deployed
     - Virtual Machines (VMs)
     - Virtual Networks
     - Databases
     - Cognitive services
- Can only be in one resource group at a time
- Can move between resource groups


#### Resource group

- A group of resources
- Can't be nested

### Azure subscription

![](https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/subscriptions-d415577b.png)

- Provides authentication and authorization to access products and services
- Linked to an account which is an identity in Microsoft Entra ID
- Used to configure billing models and access-management policies
- Defines boundaries around Azure products, services, and resources

#### Billing boundary

- Determines how an Azure account is billed
- Azure generates separate billing reports and invoices for each subscription

#### Access control boundary

- Applies access-management policies at the subscription level
- Apply different subscriptions per different departments
- Resource access control occurs at the subscription level

#### Additional Azure subscriptions

- Environments for development, testing, security, isolation, production
- Organizational structure to manage and control access to the resources that users provision within each subscription
- Billing to manage and track cost based on each subscriptions. Dev and testing billing may be different from production billing

### Azure account

- Can have multiple subscriptions
- Required to have at least one

### Azure management groups

- Resources > Resource groups > Subscriptions > Azure management groups
- All subscriptions within a management group inherit the conditions applied to the management group
- Management groups can be nested

### Management group, subscription, and resource group hierarchy

![](https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/management-groups-subscriptions-dfd5a108.png)

- Create a hierarchy that applies a policy
     - Limiting VM locations to a region in a group called production
     - Security policy can't be altered by the resource or subscription owner
- Provide user access to multiple subscriptions
     - Create one Azure role-based access control by moving multiple subscription under a management group

--------------------------------------------------------------------------------------------------------------------

# Describe Azure compute and networking services

## Describe Azure virtual machines

- VMs are Infrastructure as a service (IaaS)
- Total control over the operating system
- Ability to run custom software
- Custom hosting configurations
- Need to configure, maintain and update software on the VMs

### Scale VMs in Azure

- Group of VMs to provide high availability, scalability, and redundancy

#### Virtual machine scale sets 

- Create and manage a group of identical, load-balanced VMs
- Automatically creates the same configured virtual machines
- Automatically decrease and increase based on demand of load of the resource

#### Virtual machine availability sets

- Ensure VMs stagger updates and have varied power and network connectivity
- Update domain
     - Groups VMs to be rebooted at the same time to apply updates while keeping availability
- Fault domain
     - Groups VMs by common power source and network switch
     - Splits VMs across up to three fault domains
     - Protects against physical and network failure
- No additional cost for configuring an availabilty set

### When to use VMs

- Testing and development
- Running applications in the cloud
- Extending datacenter to the cloud
- During disaster recovery

### Move to the cloud with VMs

- Lift and shift - when you move from a physical server to the cloud
- Responsible for maintaining and installing OS and software

### VM Resources
- Size (CPU, RAM)
- Storage disks (HDD, SSD)
- Networking (virtual network, IP address, and ACL rules)

## Describe Azure virtual desktop

- A desktop and virtualization service that runs on the cloud
- Enables cloud-hosted version of Windows
- Can access remotely through web browsers

### Enhance security

- Centralized security management with Microsoft Entra ID
- MFA (multifactor authentication)
- Role-based access control

## Describe Azure containers

- To run multiple instances of an application on a single host machine

### What are containers?

- A virtualization environment
- Run multiple containers on a single physical or virtual host
- No managing the OS for a container
- Allow you to respond to changes on demand

### Different Azure containers

#### Azure Container Instances

- Fastest and simplest way to run a container in Azure
- Platform as a Service (PaaS)
- Upload your containers and then the services will run the containers

#### Azure Container Apps

- Platform as a Service (PaaS)
- Ability to load balance and scale

#### Azure Kubernetes Service (AKS)

- Container orchestration service
- Manages the lifecycle of containers

## Describe Azure functions

- Event-driven
- Serverless computing
- No maintenance of virtual machines or containers
- Concerned only about the code running
- Scales automatically based on demand
- Runs when triggered by an event and automatically deallocated when the code is finished
- Stateless (restarts every time they respond to an event)
- Stateful (a Durable Function where a context is passed through the function)

## Describe application hosting options

- VMs give you maximum control of the hosting environment
- Containers have the ability to isolate and manage different hosting solution

### Azure App Service

- Build and host web apps, background jobs, mobile back-ends and RESTFUL APIs
- No need to manage the infrastructure
- Automatic scaling and high availabilty
- Supports Windows and Linux

#### Types of app serices

- Web apps
- API apps
- WebJobs
- Mobile apps

##### Responsibilities handled by App Service

- Deployment and management
- Endpoint security
- Scaling and Load balancing

## Describe Azure virtual networking

- Isolation and segmentation
- Internet communications
- Communicate between Azure resources
- Communicate with on-premises resources
- Route network traffic
- Filter network traffic

### Isolation and Segmentation

- A Private or public IP space
- Uses subnets to segment and isolate network blocks

### Communicate between Azure resources

- Virtual networks can connect to other Azure resources
     - Power Apps
     - Azure Kubernetes Service
     - Azure virtual machine scale sets
- Service endpoints connects to other Azure resource types
     - Azure SQL databases
     - Storage accounts

### Communicate with on-premises resources 

- Point to site - a virtual private network connections from outside to corporate network
- Site to Site - a virtual private network that links your on-premise VPN device or gateway to Azure VPN gateway
- Azure ExpressRoute - a dedicated private connectivity to Azure that doesn't travel over the internet. Good for greater bandwidth and higher level of security

### Route network traffic

- Route tables - defined rules about how traffic should be directed
- Border Gateway Protocol (BGP) - works with Azure VPN gateways, Azure Route Server, or Azure ExpressRoute to propagate on-premises BGP routes to Azure virtual networks

### Filter network traffic

- A network security group that contain multiple inbound and outbound security rules. Used to block traffic, based on source and destination IP address, port and protocol
- A network virtual appliance that carries out particular network function such as running a firewall or performing wide area network (WAN) optimization

### Connect virtual networks

- Virtual network peering - Allows two virtual networks to connect directly to each other and never through the public internet
- User defined routes (UDR) - Allows you to control the routing tables between subnet within virtual network or between virtual networks

## Describe Azure virtual private networks

- An encrypted tunnel to connect two or more trusted private network over the internet
- Allows sharing of data securely and safely

### VPN gateways

- Connect on-premises datacenters to virtual networks (Site to Site)
- Connect individual device to virtual networks (Point to Site)
- Connect virtual networks to other virtual networks (Network to Network)

#### Policy-based VPN gateway

- Statically assigns IP address that should be encrypted through each tunnel
- If the IP address matches, it is then traversed through a specifically assigned tunnel

#### Route-based gateway

- IP routing decides which tunnel interfaces to use when sending each packet
- On-premises devices preferred connection
- Connections between virtual networks
- Point to site
- Multisite connections
- Coexistence with an Azure ExpressRoute gateway

### High-availability scenarios

#### Active/standby

- Two instances here one is active and the other is on standby
- If active instance is disrupted, the standby takes over and becomes active

#### Active/active

- Assigns a unique public IP address to each instance
- Create separate tunnels from the on-premises device to each IP address
- Traffic will be routed to multiple tunnels

#### ExpressRoute failover

- Built-in resiliency
- Ensures there's always a connection to the virtual network

#### Zone-redundant gateways

- In regions that support availability zones
- Provides resiliency, scalability, and higher availability to virtual network gateways
- Uses standard public IP addresses instead of basic public IP addresses

## Describe Azure ExpressRoute

- Extends your on-premises network into Microsoft cloud over a private connection
- Connection is called ExpressRoute Circuit
- Any to Any (IP VPN) network, Point to Point (Ethernet network), or a virtual cross-connection
- Connections don't go over the public internet

### Features and benefits of ExpressRoute

- Connects to Microsoft cloud services across all regions
- Global connectivity with ExpressRoute Global Reach
- Dynamic routing using BGP
- Built-in redundancy

### ExpressRoute connectivity models

- CloudExchnage colocation - physically co-located at a cloud datacenter
- Point to Point Ethernet connection
- Any to any connection
- Directly from ExpressRoute sites

## Describe Azure DNS

- Reliability and performance
- Security
- Ease of Use
- Customizable virtual networks
- Alias records

-------------------------------------------------------------------

# Describe Azure storage services


