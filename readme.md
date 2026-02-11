## General Information
Project Name: K8S Self Provisioning Deployment<br>
Version: 1.0<br>
Date: 2026-01-21<br>
Project Owner: Bronson So<br>

<br>

## Table of Content
### Executive Summary

    <details>
    <summary> 1. Project Background </summary>
    This project addresses the modernization of our legacy application hosting infrastructure, which currently consists of approximately 700 systems distributed across KVM virtual machines and OpenVZ containers. The existing environment operates on disparate technologies with varying lifecycle stages, leading to operational inefficiencies, rising maintenance costs, and limited scalability. As business demands evolve, the current infrastructure cannot adequately support emerging requirements for rapid deployment, elastic scaling, and developer self-service capabilities. This initiative represents a strategic transformation to establish a unified, modern platform that aligns with industry best practices and positions the organization for future growth.
    </details>
    
    2. Business Objectives ✅
    3. Key Success Metrics
### Technical Considerations    
### Scope
    TBC
### Implementation Plan ✅
1. Overview ✅
2. Phases ✅
### Stakeholder Management
    TBC
### Current Environment Analysis
1. Applications on Openvz and KVM
2. Resources acquired
3. New project growth rate
4. Special policies / rules
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
   1. Technology Stack ✅<br> 
      Key architectural and platform decisions that will shape the solution’s design, scalability, and lifecycle management.
      - **Bare metal vs Virtualized Infrastructure**<br>
        Evaluate performance, manageability, and isolation trade-offs for hosting Kubernetes nodes.<br>
        [References](./repository/documentations/k8s_bare_metal_vm_decision_matrix.md)
      - **HCI integration Strategy**<br>
        Compare the performance of K8S on HCI and selection of Hyper-Converged Infrastructure platform (e.g., Harvester) for integrated compute, storage, and networking.<br>
        [References](./repository/documentations/hci_infrastructure_framework_decision_matrix.md)
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

        Report generated: 11 Feb 2026 
        Utility: Cacti (data center)
        Data capture time range: 2025-02-12 - 2026-02-11

        | Category | Server   | CPU | RAM | Storage | Traffic (inbound) | Traffic (outbound) |
        | -------- | -------- | --- | --- | ------- | ----------------- | ------------------ |
        | KVM (Prod)     | Dell42   | 42.59 (avg) / 82.1 (max) | 92.19 (avg) / 114.5 (max) | 3.38 (avg) \ 3.78 (max) | 2.38M / 225.34M | 2.48M / 209.04M
        | KVM (Prod)       | Dell43   | 
        | KVM (Prod)       | Dell47   |
        | KVM (Prod)       | Dell50   |
        | KVM (Prod)       | Dell51   |
        | KVM (UAT)       | Dell40   |
        | KVM (UAT)       | Dell41   |
        | KVM (UAT)       | Dell46   |




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
   5. Operations & Management<br>
      Processes and tooling to ensure sustainable, agile platform operations.
      - **Agile Infrastructure Practices**<br>
        Infrastructure-as-Code (IaC), GitOps workflows, and CI/CD for platform management.
      - **Self-Service Developer Enablement**<br>
        Provide RBAC-governed, API-driven provisioning for application teams.
      - **Workflow and Processes**<br>
        Describe workflow and processes
      - **Resource Projection & Capacity Planning**<br>
        Ongoing monitoring, forecasting, and scaling of resources based on usage trends.
   6. Documentation & Governance<br>
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

## Scope

<br>

## Stakeholder Management

<br>

## Current Environment Analysis

<br>

## Implmentation Plan

   1. We're implementing a production-ready infrastructure platform that leverages Harvester HCI to create a unified virtualization and container environment on 5 Dell R610 servers. The solution provides both VM and Kubernetes capabilities through a single management interface, with Rancher for multi-cluster orchestration and RKE2 for enterprise-grade Kubernetes. Legacy systems will migrate to Harvester VMs, while modern applications will deploy to RKE2 clusters, following an 80% container, 20% VM adoption strategy. The platform includes built-in security compliance, vm scaling, Infrastructure-as-Code support, and GitOps pipelines to enable developer self-service while maintaining operational control.
   
   2. Schedule & Phasing<br>
      [References](./repository/documentations/implementation_plan/schedule_and_phasing.md)
      





## Suggested github directory structure 
 - Github Structure [Link](./repository/documentations/github_structure.md)
<br>

## Suggested namespace


## Network Diagram

![Github Logo](./network/k8s_infra_v2.svg)


## Cluster Map
# Architecture:


' why 3 database for k8s
' can namespace has inheritance