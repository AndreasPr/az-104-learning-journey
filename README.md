<div align="center">
  
# ☁️ AZ-104 Learning Journey
 
**Microsoft Certified: Azure Administrator Associate — Exam Preparation Repository**
 
*Topic-by-topic notes, hands-on labs, ARM templates, and scripts built while studying for the AZ-104 certification*
 
[![Microsoft Azure](https://img.shields.io/badge/Microsoft_Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)](https://azure.microsoft.com/)
[![AZ-104](https://img.shields.io/badge/Exam-AZ--104-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)](https://learn.microsoft.com/en-us/credentials/certifications/azure-administrator/)
[![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white)](https://learn.microsoft.com/en-us/powershell/)
[![Azure CLI](https://img.shields.io/badge/Azure_CLI-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)](https://learn.microsoft.com/en-us/cli/azure/)
[![ARM Templates](https://img.shields.io/badge/ARM_Templates-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/)
 
</div>

---
 
## 📌 Overview
 
This repository documents a **structured, topic-by-topic learning journey toward the AZ-104 Microsoft Azure Administrator Associate certification**, issued by Microsoft. Each folder maps directly to a domain or learning path from the official [Microsoft Learn AZ-104 curriculum](https://learn.microsoft.com/en-us/credentials/certifications/azure-administrator/) and contains hands-on notes, scripts, ARM templates, and lab exercises built while working through each topic from the ground up.
 
The repository is **actively growing** as the study journey progresses through the full AZ-104 exam scope.
 
> This repository demonstrates practical, hands-on knowledge of Microsoft Azure administration — covering core infrastructure, governance, identity, policy enforcement, and Infrastructure as Code — built through deliberate exam-driven study across Microsoft's official certification curriculum.
 
---
 
## 🏅 AZ-104 Exam — What It Tests
 
The [AZ-104: Microsoft Azure Administrator](https://learn.microsoft.com/en-us/credentials/certifications/azure-administrator/) is a role-based certification issued by Microsoft that validates expertise in managing an organisation's Azure environment. Candidates must demonstrate the ability to:
 
- Manage **Azure identities and governance** (RBAC, Azure AD, policies, subscriptions)
- Implement and manage **storage** (accounts, redundancy, lifecycle management)
- Deploy and manage **Azure compute resources** (VMs, containers, App Service)
- Implement and manage **virtual networking** (VNets, peering, DNS, load balancing)
- **Monitor and maintain** Azure resources (Azure Monitor, Log Analytics, backups)
---
 
## 🛠️ Skills & Technologies Demonstrated
 
| Category | Topics Covered |
|---|---|
| **Azure Fundamentals** | Regions, availability zones, resource groups, subscriptions, management groups |
| **Azure Resource Manager** | ARM template authoring, resource hierarchy, deployment scopes |
| **Governance & Compliance** | Azure Policy definitions, initiative groupings, compliance assessment, resource tagging |
| **Identity & Access** | Role-based access control (RBAC), Azure Active Directory fundamentals |
| **Tooling** | Azure Cloud Shell, PowerShell, Azure CLI, VS Code with ARM extension |
| **Infrastructure as Code** | JSON ARM templates, declarative resource definitions, parameterised deployments |
 
---
 
## 📂 Repository Structure
 
```
az-104-learning-journey/
│
├── 📁 prerequisites-azure-admins/       # Azure Cloud Shell · PowerShell · Azure CLI · ARM templates
├── 📁 core-architectural-components/    # Regions · Availability Zones · Resource Groups · Subscriptions · Management Groups
└── 📁 azure-policy-initiatives/         # Azure Policy definitions · Initiatives · Compliance assessment · Resource tagging
```
 
---
 
## 📓 Folder Map — Aligned to the AZ-104 Curriculum
 
The three folders currently in this repository correspond to the following Microsoft Learn learning paths and AZ-104 exam domains:
 
### 📁 `prerequisites-azure-admins`
**Aligned to:** [AZ-104: Prerequisites for Azure administrators](https://learn.microsoft.com/en-us/training/paths/az-104-administrator-prerequisites/)
 
Covers the foundational tooling every Azure administrator must be fluent with before managing Azure at scale:
 
- **Azure Cloud Shell** — browser-based shell environment (Bash and PowerShell), how it works, and how to use it for administration tasks without local tooling
- **PowerShell for Azure** — cross-platform scripting and task automation with Azure PowerShell modules; the cmdlet model, piping, and scripting patterns used in day-to-day Azure administration
- **Azure CLI** — command-line interface for managing Azure resources; imperative commands, output formatting, and scripting for automation
- **ARM Templates** — authoring JSON Azure Resource Manager templates in VS Code for declarative, repeatable infrastructure deployments; template structure, parameters, variables, and outputs
---
 
### 📁 `core-architectural-components`
**Aligned to:** [Azure core architectural components](https://learn.microsoft.com/en-us/training/modules/azure-architecture-fundamentals/) — foundational domain of the AZ-104
 
Covers the structural building blocks of the Azure platform that all administration work is built upon:
 
- **Regions and Region Pairs** — physical datacenter groupings, paired regions for disaster recovery, and sovereign cloud regions
- **Availability Zones** — physically separate datacentres within a region, used to protect against datacenter-level failures; zone-redundant services vs. zonal pinning
- **Azure Resource Manager (ARM)** — the unified management layer behind all Azure operations (Portal, CLI, PowerShell, REST API); declarative vs. imperative management
- **Resource Groups** — logical containers for Azure resources; grouping strategies, lifecycle management, and access control scoping
- **Subscriptions** — billing and access boundary within Azure; subscription types, limits, and when to use multiple subscriptions
- **Management Groups** — hierarchical containers above subscriptions for organising governance at enterprise scale; policy and RBAC inheritance through the hierarchy
---
 
### 📁 `azure-policy-initiatives`
**Aligned to:** [Azure Policy initiatives](https://learn.microsoft.com/en-us/training/modules/sovereignty-policy-initiatives/) — part of the **Manage Identities and Governance** domain (20–25% of the AZ-104 exam)
 
Covers Azure's governance and compliance enforcement system — one of the highest-weighted domains in the exam:
 
- **Azure Policy** — defining rules that enforce organisational standards and assess resource compliance at scale; built-in vs. custom policy definitions; effects (Deny, Audit, Append, Modify, DeployIfNotExists)
- **Policy Initiatives (Policy Sets)** — grouping multiple policy definitions into a single assignable initiative to pursue a specific compliance goal (e.g. enabling Azure Security Center recommendations, enforcing tagging standards)
- **Policy Assignment** — scoping policies to management groups, subscriptions, or resource groups; exclusions and exemptions
- **Compliance Assessment** — understanding compliance state, remediating non-compliant resources, and using compliance reports
- **Resource Tagging via Policy** — enforcing metadata tagging strategies across resources for cost management, ownership tracking, and operational reporting
---
 
## 🗺️ Full AZ-104 Exam Domains — Coverage Tracker
 
The table below shows the complete AZ-104 exam curriculum and maps the current state of this repository against it.
 
| Domain | Exam Weight | Status |
|---|---|---|
| Prerequisites (Cloud Shell, PowerShell, CLI, ARM) | Foundation | ✅ In Progress |
| Core Architectural Components | Foundation | ✅ In Progress |
| Manage Identities & Governance (RBAC, Policy, AD) | ~20–25% | ✅ In Progress (Policy/Initiatives) |
| Implement & Manage Storage | ~15–20% | 🔜 Coming |
| Deploy & Manage Compute Resources (VMs, Containers) | ~20–25% | 🔜 Coming |
| Implement & Manage Virtual Networking | ~15–20% | 🔜 Coming |
| Monitor & Maintain Azure Resources | ~10–15% | 🔜 Coming |
 
---
 
## 🚀 Getting Started
 
This repository is primarily a **learning and reference artefact**. To explore any topic, navigate to the relevant folder and review the notes, scripts, or templates inside.
 
### Prerequisites
 
- An [Azure free account](https://azure.microsoft.com/en-us/free/) or active Azure subscription
- [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli) installed locally (or use Azure Cloud Shell)
- [PowerShell 7+](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell) with the `Az` module installed
- [VS Code](https://code.visualstudio.com/) with the [Azure Resource Manager Tools](https://marketplace.visualstudio.com/items?itemName=msazurermtools.azurerm-vscode-tools) extension (for ARM template work)
### Cloning the Repository
 
```bash
git clone https://github.com/AndreasPr/az-104-learning-journey.git
cd az-104-learning-journey
```
 
### Connecting to Azure (CLI)
 
```bash
# Log in to Azure
az login
 
# Set your active subscription
az account set --subscription "<your-subscription-id>"
 
# Verify the connection
az account show
```
 
### Connecting to Azure (PowerShell)
 
```powershell
# Install the Az module (if not already installed)
Install-Module -Name Az -Scope CurrentUser -Repository PSGallery
 
# Connect to Azure
Connect-AzAccount
 
# Verify the connection
Get-AzContext
```
 
---
 
