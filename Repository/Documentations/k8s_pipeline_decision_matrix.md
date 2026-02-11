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
