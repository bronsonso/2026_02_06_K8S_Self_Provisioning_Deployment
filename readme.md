# Kubernetes Self-Service Platform Project Plan

## 📋 General Information
- **Project Name**: K8S Self-Provisioning Platform
- **Version**: 1.0
- **Date**: 2026-01-21
- **Project Owner**: Bronson So
- **Status**: Planning Phase

---

## 1. Executive Summary ✅

<details>
<summary><strong>1.1 Project Background</strong></summary>

> This project addresses the modernization of our legacy application hosting infrastructure, which currently consists of approximately 700 systems distributed across KVM virtual machines and OpenVZ containers. The existing environment operates on disparate technologies with varying lifecycle stages, leading to operational inefficiencies, rising maintenance costs, and limited scalability. As business demands evolve, the current infrastructure cannot adequately support emerging requirements for rapid deployment, elastic scaling, and developer self-service capabilities. This initiative represents a strategic transformation to establish a unified, modern platform that aligns with industry best practices and positions the organization for future growth.

</details>

<details>
<summary><strong>1.2 Business Objectives</strong></summary>

> - **Cost Optimization**: Reduce total cost of ownership by 30% through infrastructure consolidation and improved resource utilization via Hyper-Converged Infrastructure (HCI)
> - **Operational Efficiency**: Decrease application deployment time from days to minutes through containerization and Kubernetes orchestration
> - **Scalability & Agility**: Establish a platform capable of supporting 200% growth over the next three years with automated scaling capabilities
> - **Security & Compliance**: Achieve ISO 27001 compliance for the new platform while implementing Zero Trust security principles
> - **Developer Productivity**: Enable self-service provisioning through GitOps workflows, reducing infrastructure dependencies by 70%

</details>

<details>
<summary><strong>1.3 Key Success Metrics</strong></summary>

| Metric | Baseline | Target | Measurement Method |
|--------|----------|--------|--------------------|
| **Infrastructure Cost/App** | $X/month | 30% reduction | Financial analysis |
| **Deployment Time** | 3-5 days | <2 hours | Pipeline metrics |
| **Resource Utilization** | 45% average | >70% average | Monitoring dashboards |
| **Platform Availability** | 99.5% | 99.9% uptime | SLA monitoring |
| **Migration Completion** | N/A | 100% of 700 systems | Migration tracker |
| **Security Compliance** | Partial | Full ISO 27001 | Audit reports |

</details>

---

## 2. Project Scope & Objectives

<details>
<summary><strong>2.1 In-Scope Components</strong></summary>
<blockquote>
<strong>📦 Infrastructure Foundation</strong>

- Deployment of Harvester HCI cluster on 5 Dell R610 servers (initial pilot)
- Expansion to 30+ servers for full production deployment
- Implementation of distributed storage using Longhorn
- Network segmentation and SD-WAN/SASE integration

<strong>🛠️ Platform Services</strong>

- Rancher multi-cluster management platform installation
- RKE2 Kubernetes clusters (development and production environments)
- CI/CD pipeline implementation with GitOps (Flux/ArgoCD)
- Centralized monitoring, logging, and alerting stack

<strong>🚚 Application Migration</strong>

- Assessment and migration of all 700 existing systems
- Containerization of compatible applications (target: 80% container adoption)
- Legacy VM migration to Harvester for incompatible systems (target: 20% remaining as VMs)
- Data migration strategy for persistent storage requirements

<strong>⚙️ Operational Enablement</strong>

- Infrastructure as Code (Terraform/Ansible) implementation
- Self-service developer portal and catalog
- Comprehensive documentation and runbooks
- Team training and knowledge transfer

</blockquote>
</details>

<details>
<summary><strong>2.2 Out-of-Scope Items</strong></summary>
<blockquote>

- ❌ Application code refactoring or redevelopment
- ❌ Major network infrastructure upgrades beyond SD-WAN integration
- ❌ Legacy hardware refresh beyond the identified servers
- ❌ Third-party application licensing negotiations
- ❌ Business process re-engineering unrelated to infrastructure
- ❌ End-user device upgrades or changes

</blockquote>
</details>

<details>
<summary><strong>2.3 Success Criteria</strong></summary>
<blockquote>

<strong>Technical Success Criteria</strong>
- ✅ All 700 systems successfully migrated to new platform
- ✅ Zero data loss during migration process
- ✅ Platform availability of 99.9% post-migration
- ✅ Automated scaling operational for both VMs and containers
- ✅ Full backup and disaster recovery capabilities implemented

<strong>Business Success Criteria</strong>
- ✅ 30% reduction in infrastructure operational costs within 12 months
- ✅ 80% reduction in application deployment time
- ✅ Positive feedback from development teams on platform usability
- ✅ Successful audit for ISO 27001 compliance
- ✅ All critical business applications operating on new platform

</blockquote>
</details>

<details>
<summary><strong>2.4 Deliverables Matrix</strong></summary>


| Deliverable | Description | Owner | Due Date | Status | Dependencies |
|-------------|-------------|-------|----------|--------|--------------|
| **HCI Cluster Deployment** | Production-ready Harvester HCI cluster on 5 Dell R610 servers with HA configuration | Infrastructure Team | Phase 1 (Week 4) | Not Started | Hardware delivery, Network configuration |
| **Kubernetes Platform** | RKE2 clusters (dev/prod) with Rancher management plane | Platform Team | Phase 2 (Week 8) | Not Started | HCI Cluster operational |
| **Migration Assessment Report** | Detailed analysis of all 700 systems with migration categorization | Migration Team | Phase 3 (Week 6) | Not Started | Resource utilization data |
| **CI/CD Pipeline** | GitOps implementation with Flux/ArgoCD and self-service capabilities | DevOps Team | Phase 4 (Week 12) | Not Started | K8s Platform operational |
| **Monitoring Stack** | Prometheus/Grafana/Loki stack with custom dashboards and alerting | Operations Team | Phase 5 (Week 10) | Not Started | Platform deployment complete |
| **Security Framework** | ISO 27001 controls implementation with audit documentation | Security Team | Phase 6 (Week 16) | Not Started | Platform baseline established |
| **Backup/DR Solution** | Velero + Longhorn backup strategy with DR runbooks | Operations Team | Phase 7 (Week 14) | Not Started | Storage configuration complete |
| **Automation Framework** | Infrastructure as Code (Terraform/Ansible) for all components | DevOps Team | Phase 8 (Week 18) | Not Started | Platform standardized |
| **Documentation Portal** | Complete operational runbooks, procedures, and knowledge base | Technical Writer | Phase 9 (Week 20) | Not Started | All systems migrated |
| **Training Program** | Team enablement materials and hands-on workshops | Training Lead | Phase 10 (Week 22) | Not Started | Documentation complete |

</details>

---

## 3. Current Environment Analysis
*To be completed*

---

## 4. Considerations

### Technology Stack

<details>
<summary><strong>4.1 Technology Stack ✅</strong></summary>

Key architectural and platform decisions that will shape the solution's design, scalability, and lifecycle management.

| Consideration | Description | Reference |
|---------------|-------------|-----------|
| **VM K8S Migration Stack Analysis** | Modernization approach to transition legacy VMs and containers into HCI, traditional VM environments, and Kubernetes, with self-service provisioning for developers | [Doc](./repository/documentations/project_plan/technical_consideration/vm_k8s_stack_analysis.md) |
| **K8S Stack Analysis** | Modernization approach to transition legacy VMs and containers into HCI, traditional VM environments, and Kubernetes, with self-service provisioning for developers | [Doc](./repository/documentations/project_plan/technical_consideration/k8s_stack_analysis.md) |
| **K8S Distributions** | Choice of K8s distributions: k3s, kubeadm, rke2, kind, etc... | [Doc](./repository/documentations/project_plan/technical_consideration/k8s_distribution_analysis.md) |
| **K8S Infrastructure Components** | Choice of K8s components: control plane, networking (CNI), storage (CSI), and ingress | [Doc](./repository/documentations/project_plan/technical_consideration/k8s_infrastructure_component_analysis.md) |
| **Rancher & RKE2 Components Coverage** | Rancher and RKE2 components coverage in k8s framework | [Doc](./repository/documentations/project_plan/technical_consideration/rancher_rke2_stack_coverage_matrix.md) |
| **Component End-of-Life/Support (EOSL)** | Ensure all selected components are within supported lifecycles | [Doc](./repository/documentations/project_plan/technical_consideration/eosl.md) |
| **K8S Pipeline Components** | Choice of K8s pipeline components: CI, CD | [Doc](./repository/documentations/project_plan/technical_consideration/k8s_pipeline_decision_matrix.md) |
| **Bare metal vs Virtualized Infrastructure** | Evaluate performance, manageability, and isolation trade-offs for hosting Kubernetes nodes | [Doc](./repository/documentations/project_plan/technical_consideration/k8s_bare_metal_vm_decision_matrix.md) |
| **HCI Integration Strategy** | Compare performance of K8S on HCI and selection of Hyper-Converged Infrastructure platform (e.g., Harvester) | [Doc](./repository/documentations/project_plan/technical_consideration/hci_infrastructure_framework_decision_matrix.md) |
| **K8S Cluster Topology Analysis** | Single vs. multi-cluster design based on isolation, security, and operational requirements | [Doc](./repository/documentations/project_plan/technical_consideration/k8s_single_multi_cluster_decision_matrix.md) |
      
</details>

<details>
<summary><strong>4.2 Resource Estimation</strong></summary>

Detailed analysis of current usage and projected requirements to ensure adequate capacity and cost-effective scaling.

### 📊 Baseline Metrics from Legacy Environment
Aggregate RAM, CPU, storage, and network bandwidth usage from existing KVM VMs and OpenVZ containers.

- **Report generated**: 11 Feb 2026
- **Utility**: Cacti (Data center)
- **Data capture time range**: From 2025-02-12 to 2026-02-11

| Category | Server | CPU (avg/max) | RAM (avg/max) | Storage (avg/max) | Traffic Inbound (avg/max) | Traffic Outbound (avg/max) |
|----------|--------|---------------|---------------|-------------------|-----------------|------------------|
| KVM (Prod) | Dell42 (R440) | 42.59% / 82.1% | 92.19GB / 114.5GB | 3.38TB / 3.78TB | 2.38M / 225.34M | 2.48M / 209.04M |
| KVM (Prod) | Dell43 | *Data pending* | *Data pending* | *Data pending* | *Data pending* | *Data pending* |
| KVM (Prod) | Dell47 | *Data pending* | *Data pending* | *Data pending* | *Data pending* | *Data pending* |
| KVM (Prod) | Dell50 | *Data pending* | *Data pending* | *Data pending* | *Data pending* | *Data pending* |
| KVM (Prod) | Dell51 | *Data pending* | *Data pending* | *Data pending* | *Data pending* | *Data pending* |
| KVM (UAT) | Dell40 | *Data pending* | *Data pending* | *Data pending* | *Data pending* | *Data pending* |
| KVM (UAT) | Dell41 | *Data pending* | *Data pending* | *Data pending* | *Data pending* | *Data pending* |
| KVM (UAT) | Dell46 | *Data pending* | *Data pending* | *Data pending* | *Data pending* | *Data pending* |

### 🔧 Additional Considerations
- **Existing Server Utilization for HCI Pilot**: Assessment of available capacity on 10 Dell R610/R650 servers for Phase 1 testing
- **New Server Procurement Forecast**: Projected hardware requirements for scaling to 30+ servers in production
- **Kubernetes Overhead Calculation**: Justification for additional resources needed for K8s control plane, worker nodes, and system overhead

</details>

<details>
<summary><strong>4.3 Business (Cost) Analysis</strong></summary>

Financial modeling to justify investment and forecast long-term operational impact.

### 💰 Total Cost of Ownership (TCO)
| Category | Components |
|----------|------------|
| **Setup Costs** | Hardware, software licenses, professional services, training |
| **Running Costs** | Power, cooling, maintenance, support subscriptions |

### 📈 Return on Investment (ROI)
Quantify savings from:
- Infrastructure consolidation
- Improved operational efficiency
- Reduced operational overhead
- Increased developer productivity

</details>

<details>
<summary><strong>4.4 Security & Compliance</strong></summary>

Ensuring the platform meets organizational and regulatory security standards.

| Area | Considerations |
|------|----------------|
| **Compliance Frameworks** | ISO 27001, CISA guidelines, NIST cybersecurity framework |
| **Component Hardening** | Security baselines for K8s nodes, container images, orchestration tools |
| **Network Segmentation & Access Controls** | vLAN schemas, firewall rules, zero-trust network policies |

</details>

<details>
<summary><strong>4.5 Operations & Management</strong></summary>

Processes and tooling to ensure sustainable, agile platform operations.

| Practice | Description |
|----------|-------------|
| **Agile Infrastructure Practices** | Infrastructure-as-Code (IaC), GitOps workflows, CI/CD for platform management |
| **Self-Service Developer Enablement** | RBAC-governed, API-driven provisioning for application teams |
| **Workflow and Processes** | Automated deployment, scaling, and management workflows |
| **Resource Projection & Capacity Planning** | Ongoing monitoring, forecasting, and scaling based on usage trends |

</details>

<details>
<summary><strong>4.6 Documentation & Governance</strong></summary>

Structured knowledge management and version control for long-term maintainability.

| Component | Purpose |
|-----------|---------|
| **Implementation Procedures** | Runbooks for deployment, upgrades, and disaster recovery |
| **Credentials & Secrets Management** | Secure storage and rotation of access keys, certificates, passwords |
| [**Repository Structure**](./repository/documentations/project_plan/appendix/github_structure.md) | Organized version control for IaC, manifests, documentation, policies |
| **Namespace Design & Governance** | Logical grouping for tenants, applications, and environments within K8s |

</details>

<details>
<summary><strong>4.6 Miscellaneous</strong></summary>

### 1. Contextual Integration & Existing Systems

- **Identity Management Integration**
  - Integration with HKEdCity's existing identity management (AD/LDAP, potentially HKEdCity SSO for schools)
  
- **Compliance Requirements**
  - Alignment with Hong Kong data residency requirements
  - Compliance with Education Bureau guidelines
   
- **Infrastructure Adaptation**
  - Customisation to fit network topology (on-premises, cloud hybrid, or HKEdCity-specific constraints)

---

### 2. Operational Readiness, Not Just Functionality

- **High Availability**
  - Design for education services that cannot tolerate downtime during examination periods
  
- **Disaster Recovery**
  - Fully validated recovery procedures, not merely documented plans
  
- **Data Protection**
  - Backup strategies for etcd and persistent volumes in line with retention policies
  
- **Observability**
  - Integration with existing monitoring stack (Nagios / Prometheus / Datadog)
  - Audit-ready log aggregation for security and compliance teams

---

### 3. Governance & Guardrails

- **Resource Management**
  - Quotas to prevent resource starvation across teams
  
- **Security Controls**
  - Network policies isolating sensitive education data
  - Pod security standards aligned with HKEdCity's security posture
  
- **Cost Governance**
  - Transparent cost visibility to avoid billing surprises in self-service models
  
- **Access Control**
  - RBAC modelled on actual organisational structure, not generic placeholders

---

### 4. The "Last Mile" Work

- **Storage Configuration**
  - StorageClass tuning for education workload performance characteristics
  
- **Networking**
  - Ingress controller configuration with proper SSL termination
  - Support for custom school domains
  
- **Service Mesh**
  - Deliberate service mesh decisions (Istio required, or overkill?)
  
- **CI/CD Integration**
  - Plug into existing HKEdCity pipelines (Jenkins / GitLab / Azure DevOps)
  
- **Developer Experience**
  - Polish the inner loop—making adoption genuinely easy, not just theoretically possible

---

### 5. Risk Management

- **Failure Analysis**
  - Systematic failure mode identification, detection, and recovery protocols
  
- **Platform Stability**
  - Upgrade strategies that prioritise stability in a fast-moving ecosystem
  
- **Technical Debt**
  - Proactive prevention of unmaintainable patterns introduced by development teams
  
- **Security Response**
  - Predefined response plan for CVEs and emerging vulnerabilities

---

### 6. Organisational Translation

Bridging perspectives across stakeholders:

- **Developers** – desire for autonomy and access to latest capabilities  
- **Security** – requirement for controls and compliance adherence  
- **Finance** – need for predictability and cost efficiency  
- **Management** – expectation of reliability and service level commitments

</details>


---

## 5. Implementation Plan ✅

<details>
<summary><strong>5.1 Overview</strong></summary>

We're implementing a production-ready infrastructure platform that leverages Harvester HCI to create a unified virtualization and container environment on 5 Dell R610 servers. The solution provides both VM and Kubernetes capabilities through a single management interface, with Rancher for multi-cluster orchestration and RKE2 for enterprise-grade Kubernetes.

**Adoption Strategy**: 80% container, 20% VM
- Legacy systems → Harvester VMs
- Modern applications → RKE2 clusters

**Key Features**:
- Built-in security compliance
- VM and container scaling
- Infrastructure-as-Code support
- GitOps pipelines
- Developer self-service capabilities

</details>

<details>
<summary><strong>5.2 Phases</strong></summary>

[View detailed schedule and phasing](./repository/documentations/project_plan/implementation_plan/schedule_and_phasing.md)

</details>

---

## 6. Stakeholder Management
*To be completed*

---

## 7. Governance & Operations
- **7.1 Security & Compliance Framework**
- **7.2 Backup & Disaster Recovery**
- **7.3 Monitoring & Alerting Strategy**
- **7.4 Cost Management & Optimization**
- **7.5 Support & Maintenance Model**

---

## 8. Risk Management
- **8.1 Risk Identification Register**
- **8.2 Mitigation Strategies**
- **8.3 Contingency Plans**
- **8.4 Issue Escalation Procedures**

---

## 9. Resource Management
- **9.1 Resource Allocation Plan**
- **9.2 Budget and Cost Analysis**

---

## 📚 Appendices

<ol type="A">
  <li><strong>Technical Documentation</strong>
    <ol type="i">
      <li>Workflow & Process Diagrams</li>
      <li><a href="./network/k8s_infra_v2.svg" target="_blank">Network Topology Diagrams</a></li>
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
      <li>Related Documentation Links</li>
      <li>Regulatory Compliance References</li>
    </ol>
  </li>
  
  <li><strong>Supporting Analysis</strong>
    <ol>
      <li>Resource Utilization Reports</li>
      <li>Cost-Benefit Analysis</li>
      <li>Technology Evaluation Criteria</li>
    </ol>
  </li>
</ol>

---

## 📊 Progress Tracking

| Section | Status | Last Updated | Owner |
|---------|--------|--------------|-------|
| Executive Summary | ✅ Complete | 2026-02-11 | Bronson So |
| Technical Considerations | 🔄 In Progress | 2026-02-11 | Bronson So |
| Implementation Plan | ✅ Complete | 2026-02-11 | Bronson So |
| Appendices | 🔄 In Progress | 2026-02-11 | Bronson So |
| All Other Sections | ⏳ Pending | - | - |

