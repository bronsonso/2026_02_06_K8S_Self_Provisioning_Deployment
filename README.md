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
- K8S infrastructure framework decision [Link](./Repository/Documentations/k8s_infrastructure_framework_decision_matrix.md)
### HCI integration
- [Link](./Repository/Documentations/hci_infrastructure_framework_decision_matrix.md)
### Single vs multi cluster implementation
- [Link](./Repository/Documentations/k8s_single_multi_cluster_decision_matrix.md)

<br><br>

<details>
<summary><b>📋 K8S Infrastructure Decision Matrix</b></summary>
<table>
<tr>
<th>Stage</th>
<th>Purpose</th>
<th>Popular Choices</th>
<th>Lightweight Option</th>
<th>Enterprise Option</th>
<th>Cloud Native Option</th>
</tr>
<tr>
<td><strong>1. Host OS</strong></td>
<td>Base operating system for nodes</td>
<td>Ubuntu LTS, RHEL, Rocky Linux</td>
<td>Fedora CoreOS, Alpine</td>
<td>RHEL, SUSE Linux Enterprise Server</td>
<td>Bottlerocket, VMware Photon OS</td>
</tr>
<tr>
<td><strong>2. Provisioning</strong></td>
<td>Infrastructure deployment automation</td>
<td>Terraform, Ansible</td>
<td>Pulumi, Cluster API</td>
<td>Terraform Enterprise, Red Hat Ansible Automation Platform</td>
<td>Crossplane, Terraform Cloud</td>
</tr>
<tr>
<td><strong>3. Container Runtime</strong></td>
<td>Runs containers at lower level</td>
<td>containerd, CRI-O</td>
<td>Docker Engine (legacy)</td>
<td>CRI-O (OpenShift default)</td>
<td>containerd (cloud default)</td>
</tr>
<tr>
<td><strong>4. Control Plane</strong></td>
<td>Kubernetes orchestration engine</td>
<td>kubeadm, RKE2, k3s</td>
<td>k3s, k0s, MicroK8s</td>
<td>RKE2, OpenShift, Tanzu Kubernetes Grid</td>
<td>EKS, GKE, AKS, DigitalOcean Kubernetes</td>
</tr>
<tr>
<td><strong>5. CNI (Networking)</strong></td>
<td>Pod networking and policies</td>
<td>Calico, Cilium, Flannel</td>
<td>Flannel, Weave Net</td>
<td>Calico Enterprise, VMware NSX</td>
<td>Cilium, Amazon VPC CNI, Azure CNI</td>
</tr>
<tr>
<td><strong>6. Storage</strong></td>
<td>Persistent storage for stateful applications</td>
<td>Longhorn, Rook/Ceph, CSI drivers</td>
<td>OpenEBS, NFS provisioner</td>
<td>Portworx, NetApp Trident, Red Hat OpenShift Data Foundation</td>
<td>Cloud CSI (EBS, Azure Disk, Persistent Disk)</td>
</tr>
<tr>
<td><strong>7. Service Mesh</strong></td>
<td>Microservices networking, security, observability</td>
<td>Istio, Linkerd, Consul Connect</td>
<td>Linkerd, Traefik Mesh</td>
<td>Istio Enterprise, Consul Enterprise</td>
<td>AWS App Mesh, Google Anthos Service Mesh, Azure Service Fabric Mesh</td>
</tr>
<tr>
<td><strong>8. Ingress Controller</strong></td>
<td>External HTTP/S traffic routing</td>
<td>Ingress-NGINX, Traefik</td>
<td>Traefik, Kong</td>
<td>F5 NGINX Plus, HAProxy Enterprise</td>
<td>AWS ALB Ingress Controller, Google Cloud Load Balancer</td>
</tr>
<tr>
<td><strong>9. GitOps</strong></td>
<td>Declarative deployment and synchronization</td>
<td>Argo CD, Flux CD</td>
<td>Flux CD</td>
<td>Argo CD Enterprise, Weave GitOps Enterprise</td>
<td>AWS Proton, Google Cloud Config Sync, Azure Arc GitOps</td>
</tr>
<tr>
<td><strong>10. Developer Portal</strong></td>
<td>Internal developer platform</td>
<td>Backstage, Port</td>
<td>Gimlet, Uffizzi</td>
<td>Backstage (Enterprise), Port (Enterprise)</td>
<td>AWS Service Catalog, Google Cloud Developer Portal</td>
</tr>
<tr>
<td><strong>11. CI/CD</strong></td>
<td>Build and deployment automation</td>
<td>GitHub Actions, GitLab CI, Jenkins</td>
<td>Tekton, Drone</td>
<td>Jenkins Enterprise, GitLab EE</td>
<td>GitHub Actions, CircleCI, Google Cloud Build</td>
</tr>
<tr>
<td><strong>12. Monitoring</strong></td>
<td>Metrics collection and alerting</td>
<td>Prometheus, VictoriaMetrics</td>
<td>Prometheus (basic)</td>
<td>Datadog, New Relic, Dynatrace</td>
<td>AWS CloudWatch, Google Cloud Operations, Azure Monitor</td>
</tr>
<tr>
<td><strong>13. Logging</strong></td>
<td>Log aggregation and analysis</td>
<td>Loki, ELK Stack</td>
<td>Grafana Cloud Logs</td>
<td>Splunk, Elastic Enterprise</td>
<td>AWS CloudWatch Logs, Google Cloud Logging, Azure Monitor Logs</td>
</tr>
<tr>
<td><strong>14. Tracing</strong></td>
<td>Distributed request tracing</td>
<td>Jaeger, Zipkin</td>
<td>Tempo (Grafana)</td>
<td>Lightstep, Honeycomb</td>
<td>AWS X-Ray, Google Cloud Trace, Azure Application Insights</td>
</tr>
<tr>
<td><strong>15. Visualization</strong></td>
<td>Visualization and dashboards</td>
<td>Grafana, Kibana</td>
<td>Grafana (OSS)</td>
<td>Grafana Enterprise, Kibana</td>
<td>AWS Managed Grafana, Google Cloud Monitoring Dashboards</td>
</tr>
<tr>
<td><strong>16. Security</strong></td>
<td>Policy enforcement and security scanning</td>
<td>Kyverno, OPA/Gatekeeper, Trivy</td>
<td>Falco, Trivy</td>
<td>Aqua, Prisma Cloud, Snyk</td>
<td>AWS Security Hub, Google Cloud Security Command Center</td>
</tr>
<tr>
<td><strong>17. Secret Management</strong></td>
<td>Secret storage and management</td>
<td>HashiCorp Vault, External Secrets</td>
<td>Sealed Secrets</td>
<td>HashiCorp Vault Enterprise</td>
<td>AWS Secrets Manager, Google Secret Manager, Azure Key Vault</td>
</tr>
</table>
</details>


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