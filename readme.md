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
        [References](./repository/documentations/k8s_bare_metal_vm_decision_matrix.md)
      - **HCI integration Strategy**<br>
        Compare the performance of K8S on HCI and selection of Hyper-Converged Infrastructure platform (e.g., Harvester) for integrated compute, storage, and networking.<br>
        [References](./Repository/documentations/hci_infrastructure_framework_decision_matrix.md)
      - **CI/CD Pipeline Architecture**<br>
        Selection of pipeline tools (Jenkins, GitLab CI, GitHub Actions, Argo CD) and strategy (GitOps vs traditional CI/CD)<br>
        [References](./repository/documentations/k8s_pipeline_decision_matrix.md)
      - **Cluster Topology**<br>
        Single vs. multi-cluster design based on isolation, security, and operational requirements.<br>
        [References](./repository/documentations/k8s_single_multi_cluster_decision_matrix.md)
      - **Kubernetes Infrastructure Framework**<br>
        Choice of Kubernetes distribution, networking (CNI), storage (CSI), and ingress, etc...<br>
        [References](./repository/documentations/k8s_infrastructure_framework_decision_matrix.md)
      - **Component End-of-Life/Support (EOSL)**<br>
        Ensure all selected software and hardware components are within supported lifecycles.<br>
        [References](./repository/documentations/eosl.md)

   2. Resources estimation<br>
      Detailed analysis of current usage and projected requirements to ensure adequate capacity and cost-effective scaling.
      - **Baseline Metrics from Legacy Environment**<br>
        Aggregate RAM, CPU, storage, and network bandwidth usage from existing KVM VMs and OpenVZ containers.
      - **Existing Server Utilization for HCI Pilot**<br>
        Assessment of available capacity on 10 Dell R610/R650 servers for Phase 1 testing.
      - **New Server Procurement Forecast**<br>
        Projected hardware requirements for scaling to 30+ servers in production.
      - **Kubernetes Overhead Calculation**<br>
        Justification for additional resources needed for K8s control plane, worker nodes, and system overhead.

   3. Business (Cost)<br>
      Financial modeling to justify investment and forecast long-term operational impact.
      - **Total Cost of Ownership (TCO)**<br>
        - Setup Costs: Hardware, software licenses, professional services, training.
        - Running Costs: Power, cooling, maintenance, support subscriptions.
      - **Return on Investment (ROI)**
        Quantify savings from infrastructure consolidation, improved efficiency, and reduced operational overhead.
   4. Security & Compliance<br>
      Ensuring the platform meets organizational and regulatory security standards.
      - **Compliance Frameworks**
        Align with ISO 27001, CISA guidelines, and NIST cybersecurity framework.
      - **Component Hardening**
        Apply security baselines to Kubernetes nodes, container images, and orchestration tools.
      - **Network Segmentation & Access Controls**
        Define vLAN schemas, firewall rules, and zero-trust network policies.
   5. Schedule & Phasing<br>
      Time-bound roadmap with clear milestones, deliverables, and risk-mitigation checkpoints.
      - **Phase 1: Proof of Concept & Testing**<br>
        - Deploy Harvester HCI on 2 hosts.<br>
        - Install Rancher for cluster management.<br>
        - Provision RKE2 clusters (dev, prod).<br>
        - Migrate 10% of representative workloads (high/low usage, VM/container, legacy/modern, web/database/CMS).<br>
      - **Phase 2: Fine-Tuning & Validation**<br>
        - Optimize Kubernetes configurations based on PoC results.
        - Validate performance, resilience, and operational procedures.
      - **Phase 3: Production Migration**<br>
        - Scale platform to full capacity (30+ servers).<br>
        - Execute phased migration of remaining ~700 systems.<br>
      - **Phase 4: Advanced Capabilities & SASE Integration**<br>
        - Implement Secure Access Service Edge (SASE) for secure multi-site connectivity.
        - Deploy developer portal (Backstage) for self-service provisioning.   
   6. Operations & Management<br>
      Processes and tooling to ensure sustainable, agile platform operations.
      - **Agile Infrastructure Practices**<br>
        Infrastructure-as-Code (IaC), GitOps workflows, and CI/CD for platform management.
      - **Self-Service Developer Enablement**<br>
        Provide RBAC-governed, API-driven provisioning for application teams.
      - **Workflow and Processes**<br>
        Describe workflow and processes
      - **Resource Projection & Capacity Planning**<br>
        Ongoing monitoring, forecasting, and scaling of resources based on usage trends.
   7. Documentation & Governance<br>
      Structured knowledge management and version control for long-term maintainability.
      - **Implementation Procedures**<br>
        Detailed runbooks for deployment, upgrades, and disaster recovery.
      - **Credentials & Secrets Management**<br>
        Secure storage and rotation of access keys, certificates, and passwords.
      - **Repository Structure (GitHub/GitLab)**<br>
        Organized version control for IaC, manifests, documentation, and policies.
      - **Namespace Design & Governance**<br>
        Logical grouping strategy for tenants, applications, and environments within Kubernetes.

<br>


<br>


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