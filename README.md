## This project is to build a solution for K8S Self Provisioning Deployment


## HCI Complete Pipeline Overview

| Stage | Name | Purpose | Primary Tools | Input | Output |
|-------|------|---------|---------------|-------|--------|
| **1** | HCI Platform | Resource initiation and validation | Harvester,  | Developer needs | Validated request ticket |
| **2** | **APPROVAL** | Governance and compliance check | GitHub Reviews, OPA, manual approval | Request ticket | Approved/Rejected decision |
| **3** | **PROVISION** | Infrastructure creation | Terraform, Crossplane, Pulumi | Approved request | Namespace with quotas & policies |
| **4** | **CONFIG_SYNC** | GitOps configuration deployment | Flux CD, Argo CD | Git repository | Applications deployed |
| **5** | **CI** | Build and test automation | GitHub Actions, Jenkins, GitLab CI | Source code | Container images |
| **6** | **CD** | Release and deployment | Flux CD Auto, Argo Rollouts, Spinnaker | New container images | Updated running applications |
| **7** | **OBSERVE** | Monitoring and observability | Prometheus, Grafana, ELK | Running applications | Metrics, logs, alerts |
| **8** | **MAINTAIN** | Optimization and cleanup | Custom operators, CronJobs | Time/usage data | Optimized resources |


## K8S Complete Infrastructure Decision Matrix
| Stage | Purpose | Popular Choices | Lightweight/Option | Enterprise/Option | Cloud Native/Option |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1. Host OS | Base operating system | Ubuntu LTS, RHEL, Rocky Linux | Fedora CoreOS | RHEL, SUSE Linux ES | Bottlerocket, VMware Photon |
| 2. Provisioning | Infrastructure deployment | Terraform, Ansible | Pulumi, Cluster API | Terraform Enterprise, Red Hat Ansible | Crossplane, Terraform Cloud |
| 3. Container Runtime | Run containers | containerd, CRI-O | Docker Engine (legacy) | CRI-O (OpenShift) | containerd (cloud default) |
| 4. Control Plane | Kubernetes orchestration | kubeadm, RKE2, k3s | k3s, k0s, MicroK8s | RKE2, OpenShift, Tanzu | EKS, GKE, AKS |
| 5. CNI | Pod networking | Calico, Cilium, Flannel | Flannel, Weave Net | Calico Enterprise, VMware NSX | Cilium, Amazon VPC CNI |
| 6. Storage | Persistent volumes | Longhorn, Rook/Ceph, CSI drivers | OpenEBS, NFS provisioner | Portworx, NetApp Trident | Cloud CSI (EBS, Disk, etc) |
| 7. Service Mesh | Microservices networking | Istio, Linkerd, Consul | Linkerd, Traefik Mesh | Istio Enterprise, Consul Enterprise | AWS App Mesh, GCP Anthos |
| 8. Ingress | External traffic routing | Ingress-NGINX, Traefik | Traefik, Kong | F5 NGINX Plus, HAProxy Enterprise | AWS ALB, GCP Load Balancer |
| 9. GitOps | Declarative deployment | Argo CD, Flux CD | Flux CD | Argo CD Enterprise, Weave GitOps | AWS Proton, GCP Config Sync |
| 10. Developer Portal | Internal developer platform | Backstage, Port | Gimlet, Uffizzi | Backstage (Enterprise) | AWS Service Catalog |
| 11. CI/CD | Build and deployment | Jenkins, GitLab CI, GitHub Actions | Tekton, Drone | Jenkins Enterprise, GitLab EE | GitHub Actions, CircleCI |
| 12. Monitoring | Metrics collection | Prometheus, VictoriaMetrics | Prometheus (basic) | Datadog, New Relic, Dynatrace | AWS CloudWatch, GCP Operations |
| 13. Logging | Log aggregation | Loki, EFK Stack | Grafana Cloud Logs | Splunk, Elastic Enterprise | AWS CloudWatch Logs, GCP Logging |
| 14. Tracing | Distributed tracing | Jaeger, Zipkin | Tempo (Grafana) | Lightstep, Honeycomb | AWS X-Ray, GCP Trace |
| 15. Visualization | Dashboards | Grafana, Kibana | Grafana (OSS) | Grafana Enterprise, Kibana | AWS Managed Grafana |
| 16. Security | Policy & scanning | Kyverno, OPA/Gatekeeper, Trivy | Falco, Trivy | Aqua, Prisma Cloud, Snyk | AWS Security Hub, GCP Security |
| 17. Secret Management | Secret storage | HashiCorp Vault, External Secrets | Sealed Secrets | HashiCorp Vault Enterprise | AWS Secrets Manager, GCP Secret Manager |
.\d
.\d
<br>a
<br>a
  c
  c

## K8S Complete Pipeline Overview

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

## Considerations
1. maintenance cost
2. cost management
3. future resoureces provisioning
4. RBAC

5. Seperate Cluster Based On the following considerations

   **1. Regulatory/Compliance Requirements**
  regulatory_separation:
    - student_personal_data: "GDPR/HK Privacy Ordinance"
    - examination_data: "Exam authority requirements"
    - financial_data: "Audit and compliance"
    
  **2. Security Boundaries**
  security_domains:
    - internet_facing: "High risk, exposed apps"
    - internal_only: "School network only"
    - vpn_required: "Sensitive admin systems"
    
  **3. Business Criticality**
  sla_differences:
    - tier_1_critical: "99.99% uptime, exam systems"
    - tier_2_important: "99.9% uptime, learning platforms"
    - tier_3_standard: "99.5% uptime, admin tools"
    
  **4. Team/Organizational Structure**
  team_autonomy:
    - different_teams: "Each team owns their cluster"
    - different_budgets: "Separate cost centers"
    - different_deployment_schedules: "Independent upgrade cycles"
    
  **5. Technical Requirements**
  technical_divergence:
    - windows_vs_linux: "Different node OS requirements"
    - gpu_nodes: "AI/ML workloads"
    - special_hardware: "High-performance storage"
    
  **6. Risk Management**
  blast_radius_control:
    - critical_exam_periods: "Isolate exam systems"
    - geographic_separation: "Different data centers"
    - upgrade_safety: "Gradual K8s version upgrades"

  **1. Regulatory/Compliance Requirements**
  regulatory_separation:
    - student_personal_data: "GDPR/HK Privacy Ordinance"
    - examination_data: "Exam authority requirements"
    - financial_data: "Audit and compliance"
    
  **2. Security Boundaries**
  security_domains:
    - internet_facing: "High risk, exposed apps"
    - internal_only: "School network only"
    - vpn_required: "Sensitive admin systems"
    
  **3. Business Criticality**
  sla_differences:
    - tier_1_critical: "99.99% uptime, exam systems"
    - tier_2_important: "99.9% uptime, learning platforms"
    - tier_3_standard: "99.5% uptime, admin tools"
    
  **4. Team/Organizational Structure**
  team_autonomy:
    - different_teams: "Each team owns their cluster"
    - different_budgets: "Separate cost centers"
    - different_deployment_schedules: "Independent upgrade cycles"
    
  **5. Technical Requirements**
  technical_divergence:
    - windows_vs_linux: "Different node OS requirements"
    - gpu_nodes: "AI/ML workloads"
    - special_hardware: "High-performance storage"
    
  **6. Risk Management**
  blast_radius_control:
    - critical_exam_periods: "Isolate exam systems"
    - geographic_separation: "Different data centers"
    - upgrade_safety: "Gradual K8s version upgrades"

  **Benefits Multi-Cluster**
  benefits:
    risk_reduction: "No single point of failure"
    team_autonomy: "Faster feature development"
    compliance: "Easier audit and certification"
    upgrade_safety: "Gradual upgrades, less risk"


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