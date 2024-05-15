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

