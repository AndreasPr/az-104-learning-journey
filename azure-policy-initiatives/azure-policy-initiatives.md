# 1. Microsoft Cloud Adoption Framework (CAF) – Governance

## What is CAF?

* End-to-end framework for **cloud adoption strategy**
* Includes:

  * Best practices
  * Tools
  * Documentation

Helps align **business + technology goals**

---

## Cloud Governance (CAF – Govern Methodology)

* Managing **how cloud is used**
* Ensures:

  * Compliance
  * Security
  * Cost control
  * Operational efficiency

Goal: **Minimize risk + align with business objectives**

---

## Governance is Continuous

Not one-time → requires:

* Monitoring
* Adjustments
* Iteration

---

## 5 Governance Steps

1. **Build governance team**

   * Own policies + compliance

2. **Assess risks**

   * Security, cost, compliance, data, AI

3. **Document policies**

   * Define rules + boundaries

4. **Enforce policies**

   * Use automation + guardrails

5. **Monitor continuously**

   * Track compliance + improve

---

## Key Policy Considerations

* **Business risk** → risk tolerance, data sensitivity
* **Policy & compliance** → translate risk → rules
* **Process** → monitor + handle violations

---

## 5 Core Governance Disciplines

1. **Cost Management**

   * Control + optimize cloud spend

2. **Security Baseline**

   * Enforce security standards

3. **Resource Consistency**

   * Standard configs + lifecycle management

4. **Identity Baseline**

   * Enforce RBAC + identity rules

5. **Deployment Acceleration**

   * Standardize + speed deployments

---

## Azure Policy (Core Governance Tool)

### What it does:

* Enforces **rules (guardrails)** on resources
* Evaluates **compliance at scale**
* Prevents misconfigurations

---

### Key Capabilities:

* Centralized compliance dashboard
* Audit + enforce policies
* Auto-remediation (existing + new resources)
* Works across all resources

---

### Common Use Cases:

* Restrict regions (e.g., US only)
* Enforce VM sizes
* Require tags
* Enforce MFA
* Require logging
* Ensure geo-replication

---

### Behavior:

* Evaluates:

  * On resource creation
  * On updates
  * Existing resources

---

### Remediation:

* Can auto-fix (e.g., add missing tags)
* Supports **exceptions** when needed

---

## Key Design Principle

Balance:

* **Control & governance**
  vs
* **Speed & productivity**

Too many policies → slow teams
Too few policies → risk & chaos

---

# Summary

The Cloud Adoption Framework provides structured guidance for cloud adoption. Its Govern methodology focuses on continuous risk management, policy enforcement, and compliance, with Azure Policy serving as the primary tool to enforce standards and maintain control at scale while balancing governance with agility.








# 2. Azure Governance + ARM

## Core Governance Idea

* Control **access, compliance, cost, and organization**
* Implemented via:

  * Hierarchy
  * Policies
  * RBAC

---

## Governance Hierarchy

**Management Groups → Subscriptions → Resource Groups → Resources**

### Key Rules:

* Policies & access **inherit top → down**
* Each level = **scope boundary**

---

## Components

### Resources

* Basic units (VMs, DBs, VNets, etc.)

---

### Resource Groups (RGs)

* Logical grouping of resources
* Actions apply to all resources
* Delete RG → deletes everything

---

### Subscriptions

* **Billing + access boundary**
* Organize RGs
* Linked to identity in Microsoft Entra ID

---

### Management Groups (MGs)

* Above subscriptions
* Used for **enterprise governance**
* Can be nested (up to 6 levels)

---

## Inheritance Model

MG → Subscription → RG → Resource

* Policies & RBAC flow downward

---

# Azure Resource Manager (ARM)

## What is ARM?

* **Control plane** for Azure
* Manages:

  * Create / update / delete resources
  * RBAC
  * Policies
  * Templates
  * Tagging

---

## Control Plane vs Data Plane

### Control Plane (via ARM)

* Manages resources
* Examples:

  * Create VM
  * Apply policy
  * Assign roles

Includes Azure Policy enforcement

---

### Data Plane

* Interacts with actual data
* Examples:

  * Upload file to storage
  * Query database
  * Read secrets

Handled directly by service (bypasses ARM)

---

## Request Flow

1. Request sent (CLI / API / Portal)
2. ARM receives it
3. **RBAC check (permissions)**
4. **Azure Policy evaluation**
5. Resource provider executes

Important:

* If RBAC fails → policy not evaluated

---

# Policy Evaluation Scenarios

## Greenfield (Policy-first)

* Policy exists before resource creation
* Evaluated during:

  * Create
  * Update

Can **block non-compliant resources**

---

## Brownfield (Resource-first)

* Resources exist before policy
* Policy applied later

Behavior:

* Existing resources → **flagged non-compliant**
* Not deleted automatically
* Future changes → enforced

---

## Compliance Scan

* Runs every ~24h (or manual)
* Updates compliance status

---

# Azure Policy + Data Plane

* Limited support via specific providers:

  * Kubernetes
  * Key Vault
  * Networking
  * ML, etc.

---

# Key Insight

Governance =

* **Structure (hierarchy)**
* * **Control (RBAC + Policy)**
* * **Enforcement (ARM)**

---

# Summary

Azure governance is implemented through a hierarchical model (management groups, subscriptions, resource groups, resources) with policies and RBAC inherited downward. Azure Resource Manager acts as the control plane, enforcing access and policy checks before resources are created or modified, while data plane operations interact directly with the resource data.





# 3. Azure Policy (Core Concepts)

## What is Azure Policy?

* Enforces **rules (governance)** across resources
* Evaluates **compliance at scale**
* Provides **centralized visibility + control**

---

# 6 Core Policy Components

## 1. Definitions

* Define:

  * **Condition** (what to check)
  * **Effect** (what happens)

Examples of effects:

* Deny
* Audit
* Modify
* deployIfNotExists

---

## Scope

* Where policy applies:

  * Management Group
  * Subscription
  * Resource Group
  * Resource

Inheritance:

* Higher scope → applies to all lower levels

---

## 2. Initiatives (Policy Sets)

* Group multiple policies into **one unit**

Use for:

* Compliance frameworks
* Organizational standards

### Types:

* **Built-in** → provided by Azure
* **Custom** → created by you

---

## 3. Assignments

* Apply policy/initiative to a **scope**

### Key Features:

* Inclusion / Exclusion scopes

* Parameters

* Enforcement mode:

  * Enabled → enforce
  * Disabled → “what-if” (audit only)

* Overrides → change effect at assignment level

* Managed identity → for remediation

---

## 4. Exemptions

* Exclude specific resources **after assignment**

### Types:

* **Mitigated** → compliant via another method
* **Waiver** → temporary exception

---

## 5. Attestations

* Manual compliance marking
* Used when:

  * Policy cannot be auto-evaluated

---

## 6. Remediation

* Fix noncompliant resources

### Works with:

* `modify`
* `deployIfNotExists`

Can:

* Auto-fix new resources
* Fix existing resources via task

---

# Policy Lifecycle

1. Define policy
2. Group into initiative (optional)
3. Assign to scope
4. Evaluate compliance
5. Remediate / Exempt / Attest

---

# Key Insights

* Policies are **inherited top-down**
* Assignment = where enforcement happens
* Exemptions ≠ exclusions (applied after assignment)
* Remediation enables **auto-correction**

---

# Summary

Azure Policy enforces governance by defining rules and applying them at different scopes. Policies can be grouped into initiatives, assigned to resources, and enforced with options like remediation, exemptions, and compliance tracking to manage cloud environments at scale.





# 4. Azure Policy Definition 

## Core Idea

A policy = **Condition (if)** + **Effect (then)**

---

## Structure (JSON Anatomy)

* **displayName / description** → human-readable

* **policyType** → Built-in | Custom | Static

* **mode** → what is evaluated

  * `All` / `Indexed` (ARM resources)
  * Resource Provider modes (e.g., Kubernetes, Key Vault)

* **metadata** → version, category, etc.

* **parameters** → reusable inputs

* **policyRule** → logic (if + then)

---

# Policy Rule

## 1. IF (Condition)

Defines **when policy applies**

### Logical Operators:

* `allOf` → AND
* `anyOf` → OR
* `not` → NOT

Can be **nested**

---

## Condition Types

* **Field** → resource property (e.g., location, tags)
* **Value** → static/dynamic values
* **Count** → evaluate arrays

---

## Common Operators

* equals / notEquals
* in / notIn
* like / match
* greater / less
* contains / exists

---

## Important

* Errors in evaluation → **deny by default**
* Use `enforcementMode = disabled` for testing

---

## Functions (Advanced Logic)

* `field()` → get property
* `current()` → iterate arrays
* `ipRangeContains()` → network checks
* `utcNow()` → current time

---

## 2. THEN (Effect)

Defines **what happens if condition = TRUE**

---

# Effect Types (MOST IMPORTANT)

## Enforcing

* **deny** → block request
* **denyAction** → block specific action (e.g., delete)

---

## Modifying

* **modify** → change resource (tags, properties)
* **append** → add fields (legacy)

---

## Monitoring

* **audit** → log only
* **auditIfNotExists** → check related resources

---

## Automation

* **deployIfNotExists** → auto-deploy missing resources

---

## Special

* **manual** → requires attestation
* **disabled** → turns off policy

---

# Evaluation Behavior

* Runs on:

  * Create
  * Update
  * Existing resources

* Multiple policies:
  - Evaluated independently
  - Final result = **most restrictive wins**

---

# Key Insights

* `deny` = strongest enforcement
* `audit` = safe for testing
* `modify` / `deployIfNotExists` = auto-remediation
* Policies are **composable + cumulative**

---

# Example (Concept)

Restrict regions:

* IF: location NOT IN allowed list
* THEN: deny

---

# Summary

An Azure Policy definition consists of an if condition and a then effect. The condition evaluates resource properties using logical operators and functions, and the effect determines whether to deny, audit, modify, or remediate the resource, with policies evaluated cumulatively and the most restrictive result applied.




# 5. Azure Policy – Evaluation & Compliance

## Evaluation Triggers

Policy evaluation happens when:

* Policy/initiative **assigned or updated**
* Resource **created or updated**
* Subscription **created/moved**
* **Exemptions** change
* **Manual/on-demand scan**
* **Periodic scan (~24h)**

---

## Evaluation Timing

### Automatic:

* Full scan every **~24 hours**

### Manual (Brownfield):

* Trigger via CLI: `az policy state trigger-scan`

---

## Delays to Know

* Policy assignment → up to **~30 min delay**
* Caused by **ARM cache**
  - Fix: sign out/in

---

## Scan Duration Depends On:

* Number of policies
* Policy complexity
* Scope size
* System load (low priority)

---

# Compliance States (IMPORTANT)

### Possible States:

1. **Non-compliant**
2. **Compliant**
3. **Error**
4. **Conflicting**
5. **Protected** (denyAction)
6. **Exempt**
7. **Unknown** (manual)

---

## Priority Order

Most restrictive wins (top = highest priority):

* Non-compliant > Compliant > others

---

## Compliance % Calculation

Includes:

* Compliant
* Exempt
* Unknown

Divided by:

* Total resources (all states)

---

# Enforcement Mode

## Modes:

* **Enabled** (default) → enforce policy
* **Disabled (DoNotEnforce)** → evaluate only (What-If)

---

## Key Difference:

* `disabled effect` → no evaluation
* `enforcementMode disabled` → evaluate but don’t enforce

---

# Safe Deployment (CRITICAL)

## Step 1: What-If Mode

* Assign policy with **enforcementMode = Disabled**
* Check compliance without impact

---

## Step 2: Deployment Rings

* Roll out gradually:

  * Dev → Test → Prod (small → large)

---

## Step 3: Validate

* Compliance check
* App health check

---

## Step 4: Enable Enforcement

* Switch to **Enabled** after validation

---

# Best Practice

Treat policy as code:

* Version control
* Test before deploy
* Avoid breaking production

---

# Reacting to Policy Changes

## Event-Driven Architecture:

* Azure Policy → Event Grid → Handlers

### Event Handlers:

* Azure Functions
* Logic Apps
* Webhooks

Enables:

* Automation
* Real-time reactions

---

# Summary

Azure Policy evaluates resources based on triggers like deployments, assignments, and periodic scans, assigning compliance states such as compliant or non-compliant. Policies can be tested using enforcement mode before being enforced, and best practices include gradual rollout using deployment rings and event-driven automation via Event Grid.
