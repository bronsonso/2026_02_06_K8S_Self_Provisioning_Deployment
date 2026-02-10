## General Information
Project Name: K8S Self Provisioning Deployment<br>
Version: 1.0<br>
Date: 2026-01-21<br>
Project Owner: Bronson So<br>

<br><br>

## Background and Objectives
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
<br><br>

## Considerations
### Bare metal vs VM
- K8S infrastructure framework decision [Link](./Repository/Documentations/k8s_bare_metal_vm_decision_matrix.md)
### HCI integration
- [Link](./Repository/Documentations/hci_infrastructure_framework_decision_matrix.md)
### Single vs multi cluster implementation
- [Link](./Repository/Documentations/k8s_single_multi_cluster_decision_matrix.md)
## K8S Infrastructure Decision Matrix
- [Link](./Repository/Documentations/k8s_single_multi_cluster_dk8s_infrastructure_framework_decision_matrixecision_matrix.md)


<br><br><br>

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

<br><br><br>

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

<br><br><br>

## Considerations
1. maintenance cost
2. cost management
3. utilization
4. agile infrastructure
5. self provisioning
3. future resoureces provisioning
4. RBAC



## Suggested github directory structure for multi cluster implementation
### Your Git repo becomes:

```
clusters/
├── cluster-us-east-1-dev/
│   ├── kustomization.yaml
│   ├── config/
│   └── apps/
├── cluster-us-east-1-staging/
├── cluster-us-east-1-prod/
├── cluster-eu-west-1-dev/
├── cluster-eu-west-1-staging/
├── cluster-eu-west-1-prod/
└── ... 50 more directories
```

## Suggested namespace




## Cluster Map
# Architecture:
```
┌─────────────────────┐     ┌─────────────────────┐
│   Cluster-East      │     │   Cluster-West      │
│  (Rack A - 25 nodes)│     │  (Rack B - 25 nodes)│
│                     │     │                     │
│  • Full app stack   │     │  • Full app stack   │
│  • K8s control plane│     │  • K8s control plane│
│  • Local storage    │     │  • Local storage    │
└──────────┬──────────┘     └──────────┬──────────┘
           │                            │
           └─────────────┬──────────────┘
                         │
           ┌─────────────▼─────────────┐
           │    Shared Storage (SAN)   │
           │  • NFS/SMB for failover   │
           │  • iSCSI for block storage│
           │  • Min 2 storage heads    │
           └───────────────────────────┘
```

' why 3 database for k8s
' can namespace has inheritance