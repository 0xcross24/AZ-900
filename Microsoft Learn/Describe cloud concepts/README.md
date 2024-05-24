# Describe cloud computing

## What is cloud computing

A delivery of computing services over the internet.
- Virtual Machines
- Storage
- Databases
- Networking
- Also expands to IoT, machine learning, and artificial intelligence

## Describe the shared responsibility model

Shared responsibility model is to inform who is responsible for what

![Shared Responsibility](https://learn.microsoft.com/en-us/training/wwl-azure/describe-cloud-compute/media/shared-responsibility-b3829bfe.svg)

Customers are always responsible for:
- The information and data
- Devices that are allowed to connect to your cloud
- The accounts and identities of the people, services, and devices within your organization

Cloud providers are always responsible for:
- The physical datacenter
- The physical network
- The physical hosts

Service model determines responsbilities:
- Operating systems
- Network controls
- Applications
- Identity and infrastructure

## Define cloud models

### Private cloud

- Most equivalent to on-premise datacenter of a company
- Has the most control for the company
- Comes with greater cost and fewer benefits

### Public cloud

- Built, controlled, and maintained by a third-party cloud provider
- Anyone can purchase cloud services can access and use resources

### Hybrid cloud

- Uses both public and private clouds
- Provides the most flexibility
- Provides extra layer of security
- Organization has control to where to run their applications

| Public cloud | Private cloud | Hybrid cloud |
| ------------ | ------------- | ------------ |
| No CapEX to scale up | Has the most control for companies | Has the most flexibility |
| Applications can be provisioned and deprovisioned | Data is not grouped with other organizations' data | Organizations determine where the run their applications |
| Pay only for what they use | Hardware must be purchased for startup and maintenance | Companies control security, compliance, or legal requirements |
| No complete control over resources and security | Responsible for hardware maintenance and updates | |

### Multi-cloud

- Use multiple public cloud providers
- Deal with two or more public cloud providers

### Azure Arc

- Helps manage your cloud environment

### Azure VMware Solution

- Allows you to run your VMware workloads in Azure with seamless integration and scalability

## Describe the consumption-based model

### Capital Expenditure (CapEx)

- One-time, up-front expenditure
- Examples: A new building, building a datacenter, hardware

### Operational Expenditure (OpEx)

- No upfront costs
- Only pay for used resources
- Stop paying for resources that are no longer needed
- Pay for more resources when they are needed
- AKA: Pay As You Go (PAYG)

# Describe the benefits of using cloud services

## Describe the benefits of high availabilty and scalability in the cloud

### High availability

- Resources are available when needed, regardless of disruptions or events that occur

### Scalability

- The ability to adjust resources to meet demand
- Add more resources to handle the increased demand

#### Vertical scaling

- Adding or removing CPUs or RAM to a virtual machine

#### Horizontal scaling

- Adding additional virtual machines or containers

## Describe the benefits of reliability and predictability in the cloud

### Reliability

- The ability to recover from failures and continue to function
- One of Microsoft Azure Well-Architected Framework
- Resources can be deployed in other regions

### Predictability

- Predicting the resources needed to deliver

#### Performance

- Autoscaling is deploying additional resources to meet demand
- Load balancing is redirecting traffic evenly to lessen overloaded servers

#### Cost

- Predicting or forecasting the cost of the cloud spend
- Total Cost of Ownership (TCO) or Pricing Calculator to get an estimate of potential cloud spending

## Describe the benefits of security and governance in the cloud

- Set templates help ensure that all deployed resources meet corporate standards and government regulatory requirements
- Cloud-based auditing helps flag and resources out of compliance
- Operating systems and software patches can be automatically updated
- Infrastructure as a Service (IaaS) provides the maximum control of security
- Platform as a Service (PaaS) and Software as a Service (SaaS) automatically take care of patching and maintenance

## Describe the benefits of manageability in the cloud

### Management of the cloud

Managing your cloud resources. In the cloud you can:

- Automatically scale resource deployment
- Deploy resources based on preconfigured template
- Monitor the health of resources and automatically replace failing resources
- Receive automatic alerts based on configured metrics

### Management in the cloud

Manage your cloud environment and resources. Manage these through:

- Web portal
- Command line interface
- Using APIs
- Powershell

