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

## Describe Azure Storage Accounts

When you create a storage account, you pick your own storage account type.

- Locally redundant storage (LRS)
- Geo-redundant storage (GRS)
- Read-access geo-redundant storage (RA-GRS)
- Zone-redundant storage (ZRS)
- Geo-zone-redundant storage (GZRS)
- Read-access geo-zone-redundant storage (RA-GZRS)

### Redundancy in the primary region
Data is always replicated three times in the primary region

#### Locally Redundant Storage
- Replicates data three times within a SINGLE DATA CENTER
- Provides 11 NINES of durability 99.999999999%
- Lowest cost redundancy option
- Least durability compared to other options
- Only protects from disk failures but NOT against natural disasters such as fire or a flood

#### Zone-Redundant Storage
- Replicates data synchronously across three other Azure availability zones in the primary zone.
- Provides 12 NINES of durability 99.9999999999%
- Data is accessible for RW even if a zone becomes unavailable
- Microsoft recommends ZRS in the primary region for applications that require high availability
- Recommended to restrict data replication within a country or region to meet data governance requirements

### Redundancy in a secondary region
- Provides high durability
- Copies data to a secondary region
- Secondary region is paired based on Azure Region Pairs and cannot be changed

#### Geo-Redundant Storage
- Copies data synchronously three times within a single location in a primary region using LRS
- Copies data asynchronously to a single location in a secondary region using LRS
- Provides 16 NINES of durability 99.99999999999999%

#### Geo-Zone-Redundant Storage
- Replicates data synchronously across three other Azure availability zones in the primary region
- Replicates data to a secondary region using LRS
- Recommended for requiring maximum consistency, durability, availability, excellent performance, and resilience for disaster recovery
- Provides 16 NINES of durability 99.99999999999999

### Data Types
- Structured - Data that are represented using strict table schema. Each row must follow the defined schema. Some tables may have defined relationships between them and are sed in relational databases
- Semi-structured - Data that can be represented using tables but without a strict defined schema. Rows must have a unique key identifier
- Unstructured - Any files in any format. Examples: binary files, application files, images, movies, etc.

### Storage Account
- Group of services used to store files, messages, and semi-structured data 
     - Blob Storage
     - Queue Storage
     - Table Storage
     - File Storage
- Highly Scalable (Up to Petabytes of data)
- Highly durable (99.999999999%, up to 16 nines)
- Cheapest per GB storage

#### Blob Storage
- BLOB - Binary Large Object File
- Designed to store any types of files
     - Streaming video and audio
     - Serving images or documents
     - Storing data for backup and restore, disaster recovery and archiving
     - Storing data by an on-premises or Azure-hosted service
- Three storage tiers
     - Hot - Frequently accessed data
     - Cool - Infrequently acessed data (lower availability, high durability) and stored for at least 30 days
     - Cold - Infrequently accessed data and stored for at least 90 days
     - Archive - Rarely accessed data and stored for at least 180 days

#### Queue Storage
- Storage for small pieces of data (messages)
- Designed for scalable asynchronous processing

#### Table Storage
- Storage for semi-structured data (NoSQL)
     - Doesn't require foreign keys, relationships, or strict schema
     - Designed for quick access
- Used by many programming interfaces and SDKs

#### File Storage
- Storage for files through shared drive protocols such as NFS
- Designed to extend on-premise file shares or implement lift-and-shift-scenarios

#### Disk Storage
- Disk emulated in the cloud
- Persistent storage for Virtual Machines
- Contains different sizes, types (SSD, HDD), and performance tiers
- Disk can be unmanaged or managed

#### Benefits of Azure Storage
- Durable and highly available
- Secure
- Scalable
- Managed
- Accessible

### Azure Migrate

A service used to help you migrate from on-premises to the cloud

- Unified migration platform - A single portal to start, run, and track your migration to Azure
- Range of tools
     - Discovery and Assessment
     - Server Migration
     - Independent software vendor (ISV) offerings
- Assessment and migration - Assess and migrate on-premises infrastructure from the Azure Migrate Hub

#### Integrated Tools
- Discovery and assessment - Discover and assess on-premises servers running on VMware, Hyper-V, and physical servers in preparation for migration to Azure
- Server Migration - Migrate VMware VMs, Hyper-V VMs, physical servers, other virtualizes servers, and public cloud VMs to Azure
- Data Migration Assistant - A Stand-alone tool to assess SQL Servers. Helps pinpoint potential problems blocking migration
- Database Migration Service - Migrates on-premises databases to Azure VMs running SQL server, Azure SQL Database, or SQL Manages Instances
- Service migration assistant - A standalone tool to assess on-premises websites for migration to Azure App Service. Helps migrate .NET and PHP web apps to Azure
- Data Box - Helps move large amounts of offline data to Azure

#### AzCopy
- A Command-line utility to copy blobs or files from or to your storage account.
- Upload, download, copy and sync files between storage account
- Can be configured to work with other cloud providers to help move files back and forth between clouds

#### Azure Storage Explorer
- A GUI to manage files and blobs in your Azure Storage Accounts
- Works on Windows, MacOS, and Linux
- Uses AzCopy on the backend to perform all of the file and blob management tasks
- Upload, Download, or move between storage accounts in Azure

#### Azure File Sync
- A tool that centralizes your file shares in Azure Files
- Automatically configures a bi-directional sync with your files in Azure
- Miniture version of CDN of your Windows Server

### Database Services
- Different types of databases in Azure

#### Cosmos DB
- Globally distributed NoSQL Database services
- Schema-less
- Semi-structured (NoSQL)
- Multiple APIs (SQL, MongoDB, Cassandra, Gremlin, Table Storage)
- Used for highly responsive applications with super low latency responses and multi-regional applications

#### SQL Database
- Relational database service in the cloud (PaaS) (DBaaS - Database as a Service)
- Structured data service (Uses schema and relationships)
- High performance, reliable, fully managed and secure database for building applications

#### Azure SQL Database
- Azure SQL Database - A Relational database based on SQL server
- Azure Database for MySQL - Azure SQL version of MySQL engine
- Azure Database for PostgreSQL - Azure SQL version for PostgreSQL engine
- Azure SQL Managed Instance - Fully fledged SQL server managed by cloud provider
- Azure SQL on VM - Fully fledged SQL Server on IaaS
- Azure SQL DW (Synapse) - Massively Parallel Processing (MPP) version of SQL server
