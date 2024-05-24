# Module 1
## Describe cloud concepts (15-20%)

### Cloud Computing

1. Compute Power - Servers such as windows, linux, hosting environmens, etc.
2. Storage - files, databases
3. Networking - Network in Azure, or connecting to Azure or your company's network
4. Analytics - Services for visualization and other data

### Cloud Concept

- Scalability - the ability to scale, can ALLOCATE and DEALLOCATE resources at any time
- Elasticity - the ability to DYNAMICALLY scale
- Agility - the ability to scale QUICKLY based on demand
- Fault tolerance - the ability to maintain the UPTIME while physical and service component failures happen
- Disaster recovery - the process and design principle which allows a system to RECOVER from nautral or human induced disasters
- High availability - the agreed level of operational uptime for the system. A calculation of system uptime versus whole lifetime of the system.
* availability = uptime/(uptime + downtime)

### Economies of Scale

The principle of economies of scale states that as the companies grow they become more effective at managing shared operations.
* As company becomes bigger, they save/earn more reduced cost of their services: discounts, bundle, partnership. This is called PRICE PER UNIT

### CapEx vs OpEx

Capital Expenditure
* Initial up front cost
* Pay taxes over time
* Low ongoing cost
* No early termination
* Heavy maintenance
* Loses value over time

Operational Expenditure
* No up front cost
* Pay based on usage of resource
* Pay taxes in the same year
* Can terminate service at any time
* Low maintenance
* No change in value over time

### Consumption-based model

A pricing model that is used in cloud so that customers are only charged based on their resource usage
* No associated upfront cost
* No wasted resources. Resources are spun up based on need and can be terminated if not used

Consumption - a virtual metric used to calculate how much each resource in Azure was used. 

### Service Models responsibilities

1. Software as a Service (SaaS)
2. Platform as a Service (PaaS)
3. Infrastructure as a Service (IaaS)
4. On-prem

#### Responsibility always retained by the customer

* Information and data
* Devices (Mobile and PCs)
* Accounts and Identities

#### Responsibility varies by type

* Identity and directory infrastructure
     - IaaS and On-prem - Customer's responsbilities
     - SaaS and PaaS - Responsibility is shared between cloud and customer

* Applications
     - SaaS - Cloud provider's responsibility
     - PaaS - Responsibility is shared between cloud and customer
     - IaaS and On-prem - Customer's responsibility

* Network controls
     - SaaS - Cloud provider's responsibility
     - PaaS - Responsibility is shared between cloud and customer
     - IaaS and On-prem - Customer's responsibility

* Operating System
     - SaaS and PaaS - Cloud provider's responsibility
     - IaaS and On-Prem - Customer's responsibility

#### Responsibility transfers to cloud provider

* Physical Hosts, Network, Datacenter
     - SaaS, PaaS, IaaS - Cloud provider's responsibility
     - On-Prem - Customer's responsibility

#### Summary

When using cloud provider, you'll always be responsible for:
* The information and data stored in the cloud
* Devices that are allowed to connect to your cloud (cell phones. computers, and so on)
* The accounts and identities of the people, services, and devices within your organization

The cloud provider is always responsible for:
* The physical datacenter
* The physical network
* The physical hosts

Your service model will determine responsibility for things like:
* Operating systems
* Network controls
* Applications
* Identity and infrastructure

### Define Cloud Models

#### Private Cloud

Private cloud provides much greater control for the company and its IT department. Private cloud is the most similar to conventional corporate datacenter. This cloud comes with a greater cost and fewer benefits of a public department but gives full control the the customerl

#### Public Cloud

A public cloud is built, controlled, and maintained by a third-party cloud provider. Anyone can purchase these cloud services to use the resources.

#### Hybrid Cloud

A hybrid cloud is a combination of both public and private clouds in an intern-connected environment. A company can still have the control of the cloud it needs equivalent to a private cloud and deploy public cloud resources based on the need of the company.


| Public cloud | Private cloud | Hybrid cloud |
| ------------ | ------------- | ------------ |
| No capital expenditures to scale up | Organizations have complete control over resources and security | Provides the most flexibility |
| Applications can be quickly provisioned and deprovisioned | Data is not collocated with other organizations data | Organizations determine where to run their applications |
| Organizations pay only for what they use | Hardware must be purchased for startup and maintenance | Organizations control security, compliance, or legal requirements |
| Organizations don't have complete control over resources and security | Organizations are responsible for hardware maintenance and updates | |

#### Multi-cloud

Dealing with two or more public cloud providers and manage resources and security in both environments

#### Azure Arc

Set of technollogies that helps manage your cloud environment. Provides management in public cloud, a private cloud in datacenter, or a hybrid cloud.

#### Azure VMware Solution

Allows you to run your VMware workloads in Azure with seamless integration and scalability
