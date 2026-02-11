## General Information
Project Name: K8S Self Provisioning Deployment<br>
Version: 1.0<br>
Date: 2026-01-21<br>
Project Owner: Bronson So<br>

<br>

## 1. Executive Summary
  <details>
    <Summary><strong>1.1 Project Background</strong></Summary>
     <blockquote>This project addresses the modernization of our legacy application hosting infrastructure, which currently consists of approximately 700 systems distributed across KVM virtual machines and OpenVZ containers. The existing environment operates on disparate technologies with varying lifecycle stages, leading to operational inefficiencies, rising maintenance costs, and limited scalability. As business demands evolve, the current infrastructure cannot adequately support emerging requirements for rapid deployment, elastic scaling, and developer self-service capabilities. This initiative represents a strategic transformation to establish a unified, modern platform that aligns with industry best practices and positions the organization for future growth.</blockquote>
  </details>
  <details>
    <Summary><strong>1.2 Business Objectives ✅</strong></Summary>
    <blockquote>
      - Cost Optimization: Reduce total cost of ownership by 30% through infrastructure consolidation and improved resource utilization via Hyper-Converged Infrastructure (HCI)
      - Operational Efficiency: Decrease application deployment time from days to minutes through containerization and Kubernetes orchestration
      - Scalability & Agility: Establish a platform capable of supporting 200% growth over the next three years with automated scaling capabilities
      - Security & Compliance: Achieve ISO 27001 compliance for the new platform while implementing Zero Trust security principles
      - Developer Productivity: Enable self-service provisioning through GitOps workflows, reducing infrastructure dependencies by 70%
    </blockquote>
  </details>
  <details>
    <Summary><strong>1.3 Key Success Metrics</strong></Summary>
    <blockquote>
| Metric | Baseline | Target | Measurement Method |
|--------|----------|--------|--------------------|
| Infrastructure Cost/App | $X/month | 30% reduction | Financial analysis |
| Deployment Time | 3-5 days | <2 hours | Pipeline metrics |
| Resource Utilization | 45% average | >70% average | Monitoring dashboards |
| Platform Availability | 99.5% | 99.9% uptime | SLA monitoring |
| Migration Completion | N/A | 100% of 700 systems | Migration tracker |
| Security Compliance | Partial | Full ISO 27001 | Audit reports |
    </blockquote>
  </details>

### 2. Project Scope & Objectives
TBC

### 3. Current Environment Analysis
TBC

### 4. Technical Considerations    

### 5. Implementation Plan ✅
1. Overview ✅
2. Phases ✅

### 6. Stakeholder Management
TBC

### 7. Governance & Operations
7.1 Security & Compliance Framework
7.2 Backup & Disaster Recovery
7.3 Monitoring & Alerting Strategy
7.4 Cost Management & Optimization
7.5 Support & Maintenance Model

### 8. Risk Management
8.1 Risk Identification Register
8.2 Mitigation Strategies
8.3 Contingency Plans
8.4 Issue Escalation Procedures

### 9. Resource Management
9.1 Resource Allocation Plan
9.2 Budget and Cost Analysis

### Appendices
<ol type="A">
  <li><strong>Technical Documentation</strong>
    <ol type="i">
      <li>GitHub Repository Structure</li>
      <li>Kubernetes Pipeline Decision Matrix</li>
      <li>Workflow & Process Diagrams</li>
      <li>Network Topology Diagrams</li>
      <li>Hardware Specifications</li>
    </ol>
  </li>
  
  <li><strong>Operational Documentation</strong>
    <ol>
      <li>Deployment Procedures</li>
      <li>Troubleshooting Guides</li>
      <li>Performance Tuning Guidelines</li>
      <li>Security Hardening Checklists</li>
    </ol>
  </li>
  
  <li><strong>Reference Materials</strong>
    <ol>
      <li>Glossary of Terms</li>
      <li>Acronym List</li>
      <li>Related Documentation Links</li>
      <li>Regulatory Compliance References</li>
    </ol>
  </li>
  
  <li><strong>Supporting Analysis</strong>
    <ol>
      <li>Resource Utilization Reports</li>
      <li>Cost-Benefit Analysis</li>
      <li>Vendor Comparison Matrix</li>
      <li>Technology Evaluation Criteria</li>
    </ol>
  </li>
</ol>
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