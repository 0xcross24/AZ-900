# Module 2

## Describe core Azure services (30-35%)

### Data Center
- A physical facility
- Has it's own power, cooling, and networking infrastructure

### Region
- A general area or a location on the planet
- One or more datacenters connected with low-latency network (<2 milliseconds)
- Some services are only available in certain regions
- Some services are global services and not assigned to a specific region
- 50+ globally available regions
- Special government regions (US DoD Central, US Gov Virginia, etc.)
- Special partnered regions (China East, China North)

### Availability Zone
- A group of physically separated facilities
- Designed to protect from data center failures
- If a zone goes down, it ensures that service is still available
- Two service categories
     - Zonal services (Virtual Machines, Disks, etc.)
     - Zone-redundant services (SQL, Storage, etc.)
- Not all regions are supported
- Supports region that has three or more zones
- A zone has one or more data centers

### Region Pair
- Each region is paired with a second specific region
- Region pairs can not be selected
- At least 300 miles distance of physical isolation
- Provides durability for data against natural disaster

| Region Pair A | Region Pair B |
| ------------- | ------------- |
| East US | West US |
| UK West | UK South |
| North Europe (Ireland) | West Europe (Netherlands) |
| East Asia (Hong Kong) | Southeast Asia (Singapore) |

### Geographies
- Contains two or more regions
- Ensures data residency, sovereignty, resiliency, and compliance requirements are met
- Fault tolerant to avoid single point of failure
- Broken up in to areas ("Continents")
     - America
     - Europe
     - Asia Pacific
     - Middle East and Africa
- Each region belongs to only one Geography

### Azure Resource
- Used to manage services in azure
- Represents service lifecycle
- Uses JSON format

### Resources Groups
- Grouping of resources
- Organized by:
     - Type
     - Lifecycle (app, environment)
     - Department
     - Location
     - Combination of above

### Resource Manager
- Each resource must be in one and only one resource group
- Resource groups have their own location assigned
- Resources can reside in different locations
- Resources can be moved between resource groups
- Resource groups can not be nested
- Organized based on organization
     - Billing
     - Security and access management
     - Application Lifecycle

### Virtualization
- Emulation of physical machines
- Different virtual hardware configuration per machine/app
- Different operating systems per machine/app
- Total separation of environments
     - file systems
     - services
     - ports
     - middleware
     - configuration

### Virtual Machines
- Infrastructure as a Service (IaaS)
- A virtualized computer that is allocated on top of a primary host using Hypervisor
- Can run any applications or services

### Virtual Machine Scale Sets
- Infrastructure as a Service (IaaS)
- An identical virtual machine
- Built-in auto scaling features
- Designed for manual and auto-scaled workloads

### Containers
- Uses host's operating system
- Emulates it's own operating system
- Dependencies are independent from the host's operating system
     - If a host is on a Ubuntu 16.04, the container can run other versions dependencies such as other distro on the host server.

### Azure Container Instances
- Simplest and fastest way to run a container in Azure
- Platform as a Service (PaaS)
- Serverless Containers
- Designed for
     - small and simple web applications / services
     - Background jobs
     - Scheduled scripts

### Azure Kubernetes Service (AKS)
- Open-source container orechestration platform
- Platform as a Service (PaaS)
- Highly scalable and customizable
- Designed for high scale container deployments

### App Service
- Platform as a Service (PaaS)
- Designed as an enterprise grade web application services
- Supports different kinds of programming languages and containers

### Azure Functions (Function Apps)
- Platform as a Service (PaaS)
- Serverless
- Two hosting/pricing models
     - Consumption-based plan
     - Dedicated plan
- Designed for micro/nano-services

### Summary
- Virtual Machines (IaaS) - Custom software, custom requirements, very specialized, high degree of control
- VM Scale Sets (IaaS) - Auto-scaled workloads for VMs
- Container Instances (PaaS) - Simple container hosting, easy to start
- Kubernetes Service (PaaS) - Highly scalable and customizable container hosting platform
- App Services (PaaS) - Web applications, mainly for enterprise web app
- Functions (PaaS) - Serverless, consumption based pricing

### Azure Virtual Network
- Logically isolated networking components
- Segmented into one or more subnets
- Subnets are disxrete sections
- Enables communication of resources with each other, internet and on-premises
- Scoped to a single region
- Virtual Network peering allows cross region communication
- Isolation, Segmentation, Communication, Filtering, Routing

### Azure Load Balancer
- Evenly distributes traffic
- Supports inbound and outbound traffic
- High availability
- Uses both TCP and UDP

### VPN Gateway
- A specific type of virtual network gateway for on-premises to azure traffic over the internet

### Application Gateway
- Web traffic load balancer
- Web application firewall
- URL Routing
- SSL Termination
- Redirection

### Content Delivery Network
- Minimizes latency
- Has a copy of content from the main server for faster delivery
