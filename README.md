## General Information
Project Name: K8S Self Provisioning Deployment<br>
Version: 1.0<br>
Date: 2026-01-21<br>
Project Owner: Bronson So<br>

<br>

## Table of Content
### Background and Objectives
### Considerations    
### Scope
1. Included
2. Excluded
### Stakeholder Management
### Current Environment Analysis
1. Applications on Openvz and KVM
2. Resources acquired
3. New project growth rate
4. Special policies / rules
### Implementation Plan
1. Overview
2. Phases
### Appendix
1. Suggested github directory structure 
2. K8S Pipeline Decision Matrix
3. Workflow Overview
4. Network Diagram

<br><br>

## Background and Objectives
### 1. Overview
Modernizing IT Infrastructure with Self-Service Kubernetes & HCI

**Goal**: Replace ~700 legacy VM and container workloads with a modern, on-premises Kubernetes platform that enables self-provisioning for development teams while lowering operational costs.

**Approach**:
- Build a scalable Kubernetes foundation on cost-efficient Hyper-Converged Infrastructure (HCI).
- Validate the solution using 5 existing Dell servers, then scale to full production.

**Key Outcomes**:
- Lower Costs via infrastructure consolidation and higher resource efficiency.
- Faster Delivery through self-service provisioning and automated resource management.
- Reduced Risk with a phased, pilot-tested migration strategy.

### 2. Summary
```
✅ CURRENT:
- 700 VMs on KVM/OpenVZ
- Mix of containerizable and legacy VMs
- Moving toward HCI
- Need developer self-service

✅ GOALS:
- Modernize infrastructure
- Kubernetes for new apps
- VM support for legacy
- Self-service platform
- HCI integration
```

<br>

## Considerations
   1. Technology Stack<br>
      Key architectural and platform decisions that will shape the solution’s design, scalability, and lifecycle management.
      - **Bare metal vs Virtualized Infrastructure**<br>
        Evaluate performance, manageability, and isolation trade-offs for hosting Kubernetes nodes.<br>
        [References](./Repository/Documentations/k8s_bare_metal_vm_decision_matrix.md)
      - **HCI integration Strategy**<br>
        Compare the performance of K8S on HCI and selection of Hyper-Converged Infrastructure platform (e.g., Harvester) for integrated compute, storage, and networking.<br>
        [References](./Repository/Documentations/hci_infrastructure_framework_decision_matrix.md)
      - **Cluster Topology**<br>
        Single vs. multi-cluster design based on isolation, security, and operational requirements.<br>
        [References](./Repository/Documentations/k8s_single_multi_cluster_decision_matrix.md)
      - **Kubernetes Infrastructure Framework**<br>
        Choice of Kubernetes distribution, networking (CNI), storage (CSI), and ingress, etc...<br>
        [References](./Repository/Documentations/k8s_infrastructure_framework_decision_matrix.md)
      - **Component End-of-Life/Support (EOSL)**<br>
        Ensure all selected software and hardware components are within supported lifecycles.<br>
        [References](./Repository/Documentations/eosl.md)

   2. Resources estimation
      Detailed analysis of current usage and projected requirements to ensure adequate capacity and cost-effective scaling.
      - **Baseline Metrics from Legacy Environment**<br>
        Aggregate RAM, CPU, storage, and network bandwidth usage from existing KVM VMs and OpenVZ containers.
      - **Existing Server Utilization for HCI Pilot**<br>
        Assessment of available capacity on 10 Dell R610/R650 servers for Phase 1 testing.
      - **New Server Procurement Forecast**<br>
        Projected hardware requirements for scaling to 30+ servers in production.
      - **Kubernetes Overhead Calculation**<br>
        Justification for additional resources needed for K8s control plane, worker nodes, and system overhead.

   2. Business (Cost)
      Financial modeling to justify investment and forecast long-term operational impact.

Total Cost of Ownership (TCO)

Setup Costs: Hardware, software licenses, professional services, training.

Running Costs: Power, cooling, maintenance, support subscriptions.

Return on Investment (ROI)
Quantify savings from infrastructure consolidation, improved efficiency, and reduced operational overhead.
   3. Security
      - Compliances 27001, CISA, NIST
      - Hardening on components
      - vLAN & Firewall configurations     
   3. Schedule
        - Phase 1: Testing - K8S, HCI
                 - Testing of HCI
                   - Setup Harvester on 2 hosts
                 - Test K8S cluster management
                   - Setup Rancher on Harvester
                 - Setup RKE2 2 clusters (dev, prod)
                 - test with 10% systems (one from each type: heavy usage, low usage, one from vm, one from container, one legacy system, one modern system, one web site, one database, one cms)
        - Phase 2: Fine Tuning - K8S
        
        - Phase 2: Production -

        - Phase 3: SASE 

        - Phase 4: Addition Features
                 - Backstage User GUI
   4. Operations
      - agile infrastructure
      - application developer self provisioning
      - RBAC
   5. Management
      - resoureces projection
   6. Documentations and Versioning
      - Implementation procedures
      - Credentials
      - File Structure (github, )
      - Namespace ()

<br>

## K8S Pipeline Decision Matrix

| Stage | Name | Purpose | Primary Tools | Input | Output |
|-------|------|---------|---------------|-------|--------|
| **1** | **REQUEST** | Resource initiation and validation | GitHub Issues/PRs, Backstage, Jira | Developer needs | Validated request ticket |
| **2** | **APPROVAL** | Governance and compliance check | GitHub Reviews, OPA, manual approval | Request ticket | Approved/Rejected decision |
| **3** | **PROVISION** | Infrastructure creation | Terraform, Crossplane, Pulumi | Approved request | Namespace with quotas & policies |
| **4** | **CONFIG_SYNC** | GitOps configuration deployment | Flux CD, Argo CD | Git repository | Applications deployed |
| **5** | **CI** | Build and test automation | GitHub Actions, Jenkins, GitLab CI | Source code | Container images |
| **6** | **CD** | Release and deployment | Flux CD Auto, Argo Rollouts, Spinnaker | New container images | Updated running applications |
| **7** | **OBSERVE** | Monitoring and observability | Prometheus, Grafana, ELK | Running applications | Metrics, logs, alerts |
| **8** | **MAINTAIN** | Optimization and cleanup | Custom operators, CronJobs | Time/usage data | Optimized resources |

<br>

## Workflow Overview

| Step | Stage Name | Description | Tools/Systems | Owner |
|------|------------|-------------|---------------|-------|
| **1** | **REQUEST_INITIATION** | User submits project request via email | Email, Request Form | User |
| **2** | **ACCOUNT_PROVISIONING** | Support creates project account and base access | Active Directory, IAM | Support Team |
| **3** | **RESOURCE_SELECTION** | User selects resources via self-service portal | Backstage Portal | User |
| **4** | **GIT_PR_CREATION** | Portal generates Pull Request with resource specs | GitHub, Backstage | System |
| **5** | **APPROVAL_WORKFLOW** | Team/project leader reviews and approves | GitHub Reviews, Slack | Project Lead |
| **6** | **INFRA_AUTOMATION** | Automated provisioning pipeline executes | GitHub Actions, Terraform, Ansible | CI/CD System |
| **7** | **RESOURCE_DEPLOYMENT** | GitOps syncs configuration to Kubernetes | FluxCD, Kubernetes | GitOps System |
| **8** | **NOTIFICATION** | User notified of resource availability | Email, Slack | Notification System |

<br>


<br>

## Suggested github directory structure 
 - Github Structure [Link](./Repository/Documentations/github_structure.md)
<br>

## Suggested namespace


## Network Diagram

![Github Logo](./Network/k8s_infra_v2.svg)


## Cluster Map
# Architecture:


' why 3 database for k8s
' can namespace has inheritance