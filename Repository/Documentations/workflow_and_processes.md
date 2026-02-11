

## Developer Self Provisioning Workflow

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
