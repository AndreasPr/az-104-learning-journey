# Core Architectural Components of Azure 

* Describe Azure regions, region pairs, and sovereign regions.
* Describe Availability Zones.
* Describe Azure datacenters.
* Describe Azure resources and Resource Groups.
* Describe subscriptions.
* Describe management groups.
* Describe the hierarchy of resource groups, subscriptions, and management groups.



# 1. Azure Physical Infrastructure

## Core Idea

Azure infrastructure = **Datacenters → Regions → Availability Zones → Region Pairs**

---

## Datacenters

* Physical facilities (servers, power, cooling, networking)
* You **don’t interact directly** with them

---

## Regions

* Geographic area with **1+ datacenters (low latency)**
* You **deploy resources to a region**
* Some services are:

  * **Region-specific** (VM sizes, storage)
  * **Global** (e.g., Microsoft Entra ID, DNS)

Purpose: **Latency + resource organization**


## Availability Zones (AZs)

* **Physically separate datacenters within a region**
* Independent:

  * Power
  * Cooling
  * Networking
* Connected via **high-speed fiber**

Purpose: **High availability within a region**

### Key facts:

* Minimum **3 AZs** (in supported regions)
* Not all regions support AZs


## AZ Service Types

* **Zonal** → tied to a specific AZ (VMs, disks)
* **Zone-redundant** → auto-replicated across AZs
* **Non-regional** → globally resilient


## Region Pairs

* Two regions in same geography (~300+ miles apart)
* Example: East US ↔ West US

Purpose: **Disaster recovery (region-level failures)**

### Benefits:

* Cross-region replication
* One region prioritized during outages
* Updates rolled out **one region at a time**
* Meets **data residency requirements**

Important:

* Failover/replication is **NOT always automatic** → must configure


## Resiliency Strategy (Layered)

* AZs → protect from **datacenter failure**
* Region pairs → protect from **regional disasters**


## Sovereign Regions

* Isolated Azure environments for **compliance/legal needs**

### Examples:

* US Gov regions → for government agencies
* China regions → operated with local partner

Purpose: **Regulatory isolation + compliance**

---

# Summary

Azure infrastructure is organized into regions and availability zones. Regions provide geographic deployment boundaries, availability zones ensure high availability within a region, and region pairs enable disaster recovery across regions.













# 2. Azure Management Infrastructure 

## Core Hierarchy

**Management Groups → Subscriptions → Resource Groups → Resources**

---

## Resources

* Basic building blocks (VMs, DBs, VNets, AI services)
* Everything in Azure = **resource**

---

## Resource Groups (RGs)

* Logical grouping of resources

### Rules:

* Each resource → **1 RG only**
* No nesting of RGs
* Cannot rename
* Can move some resources between RGs

### Behavior:

* Delete RG → deletes all resources inside
* Access control → applies to all resources

Use for:

* Project grouping
* Environment isolation (dev/test/prod)
* Easy cleanup (e.g., delete dev environment)

---

## Subscriptions

* **Billing + access control boundary**

### Key points:

* Required to use Azure
* Linked to an identity in Microsoft Entra ID
* One account → multiple subscriptions

### Two main roles:

* **Billing boundary** → separate invoices
* **Access boundary** → RBAC + policies

Use multiple subscriptions for:

* Environments (dev/test/prod)
* Teams/projects
* Cost tracking

---

## Management Groups (MGs)

* Sit **above subscriptions**
* Used for **governance at scale**

### Features:

* Apply policies across multiple subscriptions
* RBAC inheritance (set once, applies everywhere)
* Can be nested (**up to 6 levels**)

### Structure:

* Top level = **Tenant Root Group**
* All subscriptions roll up to it

---

## Inheritance Model

* Policies & access flow **top → down**

MG → Subscription → RG → Resource

---

## Real Use Cases

### Governance

* Restrict regions (e.g., only US)
* Enforce compliance policies

### Access Control

* Assign roles at MG level → applies everywhere

### Cost Organization

* Separate subscriptions per team/project

---

## Key Constraints

* Max **10,000 management groups per directory**
* Each subscription/MG → **only one parent**

---

# Summary

Azure uses a hierarchy of management groups, subscriptions, resource groups, and resources. Subscriptions define billing and access boundaries, resource groups organize resources, and management groups enable governance and policy enforcement across multiple subscriptions.
