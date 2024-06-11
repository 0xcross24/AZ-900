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

## Describe Azure storage accounts

A storage account provides a unique namespace for your Azure Storage data that is accessible from anywhere in the world over HTP or HTTPS. Provides availability, scalability, and durability

- Locally redundant storage (LRS)
- Geo-redundant storage (GRS)
- Read-access-geo-redundant storage (RA-GRS)
- Zone-redundant storage (ZRS)
- Geo-zone-redundant storage (GZRS)
- Read-access geo-zone-redundant storage (RA-GZRS)

### Storage account endpoints

- A unite namespace in Azure for storing data

| Storage service | Endpoint |
| --------------- | -------- |
| Blog Storage | https://<storage-account-name>.blob.core.windows.net |
| Data Lake Storage Gen2 | https://<storage-account-name>.dfs.core.windows.net |
| Azure Files | https://<storage-account-name>.file.core.windows.net | 
| Queue Storage | https://<storage-account-name>.queue.core.windows.net |
| Table Storage | https://<storage-account-name>.table.core.windows.net |

## Describe Azure storage redundancy

- How your data is replicated in the primary region
- Whether your data is repliated to a second region
- Whether your application requires read access to the replicated data in the secondary region

### Redundancy in the primary region

#### Locally redundant storage

- Replicates data three times within a single data center in the primary region
- Provides at least 11 nines of durability (99.999999999%)
- Lowest-cost redundancy option
- Least durabile compared to other options

![](https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-storage-services/media/locally-redundant-storage-37247957.png)

#### Zone-redundant storage

- Replicates data synchronously across three Azure availability zones in the primary region
- Provides at least 12 nines of durability (99.9999999999%)
- Accessible for both read and write operations even if a zone is unavailable
- Recommended by Microsoft to use ZRS in the primary zone

![](https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-storage-services/media/zone-redundant-storage-6dd46d22.png)

### Redundancy in the secondary region

- Additional copy of data in your storage account
- Secondary region is automatically paired to the primary region chosen in your storage account
- By default, not available for read or write access unless there's a failover to the secondary region
- Becomes the primary region when there's a failover

#### Geo-redundant storage

- Uses locally redundant storage (LRS) locally in the primary region
- Copies the data in the primary region to the secondary region using LRS
- GRS offers 16 nines of durability (99.99999999999999%)

![](https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-storage-services/media/geo-redundant-storage-3432d558.png)

#### Geo-zone-redundant storage

- Uses zone redundant storage (ZRS) in the primary region
- Replicates the data in the primary region to the secondary region using LRS
- Provides 16 nines of durability (99.99999999999999%)

![](https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-storage-services/media/geo-zone-redundant-storage-138ab5af.png)

#### Read access to data in the secondary regiom

- By default, data is not available in the second region until failover occurs
- Can enable to read access to the secondary region
- Also called read-access geo-redundant storage (RA-GRS) or read-access geo-zone-redundant storage (RA-GZRS)

## Describe Azure storage services

- Azure Blobs
- Azure Files
- Azure Queues
- Azure Disks
- Azure Tables

### Benefits of Azure Storage

- Durable and highly available
- Secure
- Scalable
- Managed
- Accessible

### Azure Blob

- Serving images or documents to a browser
- Storing files for distributed access
- Streaming video and audio
- Storing data for backup and restore, disaster recovery and archiving
- Storing data for analysis by an on-premises or Azure-hosted service

#### Accessing blob storage

- Accessed through HTTP/HTTPS
- URLs
- Azure REST API
- Azure Powershell
- Azure CLI
- Azure Storage client library

#### Blob storage tiers

- Hot access tier - Storing frequently accessed data
     - Set at the account level
     - Set at the blob level or after upload
- Cool access tier - Storing infrequently accessed data (least 30 days)
     - Set at the account level
     - Set at the blob level or after upload
- Cold access tier - Storing infrequently  accessed data (least 90 days)
     - Set at the blob level or after upload
- Archive access tier - Storing rarely accessed data (180 days)
     - Set at the blob level or after upload
     - Stores offline data and lowest storage costs
     - Highest costs to rehydrate and access data

### Azure Files

- Accessible via NFS or SMB

#### Azure Files key benefits

- Shared access - NFS and SMB protocols
- Fully managed - Cloud provider manages updates, patches, and replaces faulty disks
- Scripting and tooling - Powershell, Azure CLI, Azure portal, Azure Storage Explorer
- Resiliency
- Familiar programmability - Azure Storage Client Libraries or Azure Storage REST API

### Azure Queues

- Stores large number of messages
- Can be used with Azure Functions to trigger an action when a message is received

### Azure Disks

- Azure Disk storage or Azure managed disks used with Azure VMs
- Virtualized physical disk

### Azure Tables

- Stores structured, non-relational data
- NoSQL datastorage

## Identify Azure data migration options

### Azure Migrate

- A unified migration platform - A portal to start, run and track your migration to Azure
- Range of tools
     - Discovery and assessment
     - Server Migration
     - Azure Migrate
- Assessment and migration - Using Azure Migrate hub, you can assess an migrate to on-premises infrastructure to Azure

#### Integrated tools

- Discovery and assessment - Assess on-premises servers running on VMware, Hyper-V and physical servers in preparation for migration to Azure
- Server Migration - Migrates VMware VMs, Hyper-V VMs, physical servers and public VMs to Azure
- Data Migration Assistant - A stand-alone tool to assess SQL Servers that provides potential problems for migration
- Database Migration Service - Migrate on-premises databases to Azure VMs running SQL Server, Azure SQL Database, or SQL Managed Instances
- App Service migration assistant - A standalone tool to assess on-premises websites for migration to Azure App Service
- Azure Data Box - To move large amounts of offline data to Azure

### Azure Data Box

- A physical migration service that helps transfer large amounts of data quickly
- Ideally suited for transferring 40TBs of data

## Identify Azure file movement options

### AzCopy

- A command-line utility to copy blobs or files
- Upload, download, copy files between storage accounts

### Azure Storage Explorer

- A GUI that manages files and blobs in your Storage account

### Azure File Sync

- Centralize file share
- Azure File Sync will stay bi-directionally synced with your files in Azure
- Syncs your Windows file server to Azure
- Act as a CDN from your windows file server to Azure

# Describe Azure identity, access, and security

## Describe Azure directory services

Microsoft Entra ID is a directory that helps you maintain your on-premises Active Directory deployment
Microsoft cloud-based Active Directory

### Microsoft Entra ID

- Authentication
- Single sign on
- Application management
- Device management

### Connecting On-premise AD with Microsoft Entra ID

- Uses Microsoft Entra Connect
     - Synchronizes user identities between Active Directory and Microsoft Entra ID

### Microsoft Entra Domain Services

- Manages domain services such as domain join, group policy, LDAP and Kerberos/NTLM authentication
- Microsoft cloud-based domain controller
- Performs a one-way synchronization from Microsoft Entra ID to Microsoft Entra Domain Services

![](https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-identity-access-security/media/azure-active-directory-sync-topology-7359f2b8.png)

## Describe Azure authentication methods

![](https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-identity-access-security/media/passwordless-convenience-security-30321b4d.png)

### Single Sign On

- User can sign in one time and access multiple resources and applications
- Users only memorize one password

### Multifactor Authentication

- Uses multiple authentication to access
- Something the user knows
- Something the user has
- Something the user is

#### Microsoft Entra multifactor authentication

- Microsoft allows user to choose an additional form of authentication
     - Phone call
     - App notification

### Passwordless authentication

- More convenient
- Requires setting up on a device
- Uses a fingerprint or a pin to authenticate

### Microsoft Authenticator App

- A convenient multifactor authentication
- Uses a phone app to confirm by using a PIN or biometric

### FIDO2 security keys

- Fast IDentity Online
- Unphishable standards-based passwordless authentication method
- Doesn't require a username or a password

## Describe Azure external identities

- A person, device, service, etc. that is outside your org
- External users can bring their own "identities"
     - Google or Facebook sign on
- Business to business (B2B) collaboration - External users are allowed to use their preferred identity to sign-in to your Microsoft applications
- B2B direct connect - A mutual, two-way trust with another Microsoft Entra org
- Microsoft Azure Active Directory business to customer (B2C) - Publish modern SaaS apps or custom-developed apps to consumers and customers while using Azure AD B2C for IAM

## Describe Azure conditional access

- A tool that Microsoft Entra ID uses to allow or deny access to resources. Also known as identity signals
     - Who the user is
     - Where the user is
     - What device the user is requesting access from
- MFA is used if a user logs in from an unknown location and not used if a user logs in from a known location
![](https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-identity-access-security/media/conditional-access-9bd268b8.png)

### When can I use Conditional Access

- Require MFA based on role, location or network
- Require access to services only through approved client applications
- Require users to access only from managed devices that meets your standards for security and compliance
- Block access from untrusted sources, unkown or unexpected locations

## Describe Azure role-based access control

- Least privilege - only grant access up to the level needed to complete a task
- Azure role-based access control (Azure RBAC) - A defined roles where you assign individuals or groups to one or more roles, they all receive the associated access permissions

### How is role-based access control applied to resources

![](https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-identity-access-security/media/role-based-access-scope-4b12a8f3.png)

- A Scope includes
     - A management group
     - A single subscription
     - A resource group
     - A single resource
- Azure RBAC is hierarchical, when you grant access at a parent scope, child scopes get inherited

### How is Azure RBAC enforced?

- Any action that's initiated against an Azure resource that passes through Azure Resource Manager
- Azure Resource Manager is accessed through Azure portal, Cloud Shell, Powershell, and Cli
- Doesn't enforce access permissions at the application or data level
- Application security must be handled by your application

## Describe zero trust model

- A security model that assumes the worsat case scenario
     - Verify explicitly - Always authenticate and authorize based on all available data points
     - Use least privilege access - Limit user access with Just-In-Time and Just-Enough-Access
     - Assume breach - Minimize blast radius and segment access. Verify end-to-end encryption.

### Adjusting to Zero Trust

- Doesn't assume that a device is safe within corporate network
- Requires everyone to authenticate
- Grants access based on authentication rather than location

![](https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-identity-access-security/media/zero-trust-cf9202be.png)
