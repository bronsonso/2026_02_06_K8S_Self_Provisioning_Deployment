## File Structure
Convention: snake_case
Use for: Files, directories, configuration files, data files, scripts

Examples:
```
text
config/
├── database_config.yaml
├── network_settings.conf
└── backup_schedule.json

scripts/
├── migrate_legacy_vms.py
├── validate_cluster_health.sh
└── generate_reports.sql
```

Why snake_case :
- ✅ Clear word separation without ambiguity
- ✅ Common convention in Python, Ruby, configuration files
- ✅ Easy to type (underscore vs. hyphen depends on keyboard layout preference)


## Github Structure

```
github-self-service-platform/
├── 📁 .github/
│   ├── 📁 workflows/                    # GitHub Actions workflows
│   │   ├── 📁 k8s-cluster-ops/
│   │   │   ├── provision-cluster.yaml   # Request new RKE2 cluster
│   │   │   ├── scale-cluster.yaml       # Scale existing cluster
│   │   │   ├── upgrade-cluster.yaml     # Upgrade cluster version
│   │   │   └── delete-cluster.yaml      # Decommission cluster
│   │   ├── 📁 namespace-ops/
│   │   │   ├── create-namespace.yaml    # Create namespace via PR
│   │   │   ├── update-quotas.yaml       # Update resource quotas
│   │   │   └── delete-namespace.yaml    # Delete namespace
│   │   ├── 📁 app-deployment/
│   │   │   ├── deploy-app.yaml          # Deploy app via PR
│   │   │   ├── update-app.yaml          # Update app via PR
│   │   │   ├── rollback-app.yaml        # Rollback deployment
│   │   │   └── delete-app.yaml          # Delete app
│   │   ├── 📁 vm-ops/                   # VM operations (Harvester)
│   │   │   ├── create-vm.yaml           # Create VM via PR
│   │   │   ├── snapshot-vm.yaml         # Create VM snapshot
│   │   │   └── delete-vm.yaml           # Delete VM
│   │   ├── 📁 security/
│   │   │   ├── scan-images.yaml         # Trivy image scanning
│   │   │   ├── audit-compliance.yaml    # CIS compliance check
│   │   │   └── secret-rotation.yaml     # Automatic secret rotation
│   │   └── 📁 platform-ops/
│   │       ├── backup-trigger.yaml      # Trigger backups
│   │       ├── monitor-alerts.yaml      # Alert response
│   │       └── disaster-recovery.yaml   # DR procedures
│   ├── 📁 ISSUE_TEMPLATE/              # GitHub Issue templates
│   │   ├── cluster-request.md           # Request new cluster
│   │   ├── namespace-request.md         # Request namespace
│   │   ├── app-deployment-request.md    # Deploy application
│   │   ├── vm-request.md               # Request VM
│   │   └── bug-report.md               # Bug reports
│   ├── 📁 PULL_REQUEST_TEMPLATE/
│   │   ├── cluster-pr.md               # Cluster provisioning PR
│   │   ├── namespace-pr.md             # Namespace PR template
│   │   ├── app-deployment-pr.md        # App deployment PR
│   │   └── vm-provisioning-pr.md       # VM provisioning PR
│   └── 📁 environments/                # GitHub Environments
│       ├── dev/
│       ├── staging/
│       ├── uat/
│       └── prod/
├── 📁 fluxcd/                          # FluxCD GitOps configuration
│   ├── 📁 clusters/                    # RKE2 cluster configurations
│   │   ├── 📁 rke2-prod/
│   │   │   ├── flux-system/            # Flux bootstrap
│   │   │   │   ├── gotk-components.yaml
│   │   │   │   ├── gotk-sync.yaml
│   │   │   │   └── kustomization.yaml
│   │   │   ├── 📁 infrastructure/      # Platform infra
│   │   │   │   ├── monitoring/
│   │   │   │   ├── logging/
│   │   │   │   ├── networking/
│   │   │   │   └── security/
│   │   │   ├── 📁 teams/              # Team namespaces
│   │   │   │   ├── team-a/
│   │   │   │   │   ├── namespace.yaml
│   │   │   │   │   ├── rbac.yaml
│   │   │   │   │   ├── quotas.yaml
│   │   │   │   │   └── kustomization.yaml
│   │   │   │   ├── team-b/
│   │   │   │   └── team-c/
│   │   │   └── 📁 applications/       # Team applications
│   │   │       ├── team-a/
│   │   │       │   ├── app-1/
│   │   │       │   └── app-2/
│   │   │       └── team-b/
│   │   ├── 📁 rke2-staging/
│   │   ├── 📁 rke2-uat/
│   │   └── 📁 rke2-dev/
│   ├── 📁 policies/                    # OPA/Gatekeeper policies
│   │   ├── namespace-policies.yaml
│   │   ├── pod-security-policies.yaml
│   │   ├── network-policies.yaml
│   │   └── resource-quotas.yaml
│   └── 📁 notifications/              # Flux notifications
│       ├── alert-provider.yaml
│       └── notification-rules.yaml
├── 📁 backstage/                      # Backstage developer portal
│   ├── 📁 catalog/                    # Service catalog
│   │   ├── 📁 components/            # Software components
│   │   │   ├── vm-component.yaml    # VM component template
│   │   │   ├── k8s-namespace.yaml   # K8s namespace template
│   │   │   ├── microservice.yaml    # Microservice template
│   │   │   └── database.yaml        # Database template
│   │   ├── 📁 systems/              # System definitions
│   │   ├── 📁 domains/              # Domain definitions
│   │   └── 📁 locations/            # Location definitions
│   ├── 📁 scaffolder/               # Templates for new resources
│   │   ├── 📁 templates/
│   │   │   ├── new-vm/              # Create new VM
│   │   │   │   ├── template.yaml
│   │   │   │   ├── skeleton/
│   │   │   │   └── actions/
│   │   │   ├── new-namespace/       # Create namespace
│   │   │   ├── new-microservice/    # Create microservice
│   │   │   └── new-database/        # Create database
│   │   └── 📁 actions/              # Custom scaffolder actions
│   │       ├── create-github-pr.js
│   │       ├── trigger-flux-sync.js
│   │       └── validate-resources.js
│   ├── app-config.yaml              # Backstage configuration
│   └── 📁 plugins/                  # Custom Backstage plugins
│       ├── k8s-self-service/
│       ├── vm-provisioning/
│       └── github-actions/
├── 📁 terraform/                     # Infrastructure as Code
│   ├── 📁 modules/
│   │   ├── harvester-cluster/       # Harvester module
│   │   ├── rke2-cluster/           # RKE2 cluster module
│   │   ├── networking/             # Network module
│   │   └── storage/               # Storage module
│   ├── 📁 environments/
│   │   ├── dev/
│   │   │   ├── main.tf
│   │   │   ├── variables.tf
│   │   │   └── terraform.tfvars
│   │   ├── staging/
│   │   ├── prod/
│   │   └── global/
│   └── 📁 state/                   # Remote state config
├── 📁 helm-charts/                  # Custom Helm charts
│   ├── 📁 platform-charts/
│   │   ├── team-namespace/         # Namespace with quotas
│   │   ├── basic-microservice/     # Basic app template
│   │   ├── stateful-microservice/  # Stateful app template
│   │   └── cron-job/              # Cron job template
│   └── 📁 dependency-charts/       # External dependencies
│       ├── redis/
│       ├── postgresql/
│       └── elasticsearch/
├── 📁 kubernetes-manifests/         # K8s manifests (GitOps source)
│   ├── 📁 platform/
│   │   ├── monitoring/
│   │   ├── logging/
│   │   ├── ingress/
│   │   └── security/
│   ├── 📁 teams/
│   │   ├── team-a/
│   │   │   ├── namespace.yaml
│   │   │   ├── 📁 apps/
│   │   │   │   ├── app-1/
│   │   │   │   └── app-2/
│   │   │   └── 📁 infrastructure/
│   │   └── team-b/
│   └── 📁 policies/
│       ├── network-policies/
│       └── pod-security/
├── 📁 scripts/                      # Helper scripts
│   ├── bootstrap/
│   │   ├── bootstrap-flux.sh       # Bootstrap FluxCD
│   │   ├── bootstrap-backstage.sh  # Deploy Backstage
│   │   └── bootstrap-github.sh     # Setup GitHub repos
│   ├── validation/
│   │   ├── validate-pr.sh          # PR validation
│   │   ├── validate-manifests.sh   # K8s manifest validation
│   │   └── security-scan.sh        # Security scanning
│   └── utilities/
│       ├── kubeconfig-generator.sh
│       ├── secret-manager.sh
│       └── backup-manager.sh
├── 📁 docs/
│   ├── 📁 developer-guides/
│   │   ├── self-service-workflow.md
│   │   ├── creating-namespace.md
│   │   ├── deploying-application.md
│   │   └── vm-provisioning.md
│   ├── 📁 administrator-guides/
│   │   ├── onboarding-teams.md
│   │   ├── managing-quotas.md
│   │   └── troubleshooting.md
│   ├── 📁 api/
│   │   ├── github-actions-api.md
│   │   ├── fluxcd-api.md
│   │   └── backstage-api.md
│   └── 📁 policies/
│       ├── naming-conventions.md
│       ├── resource-limits.md
│       └── security-policies.md
├── 📁 tests/
│   ├── 📁 e2e/
│   │   ├── self-service-workflow/
│   │   ├── gitops-sync/
│   │   └── security-compliance/
│   ├── 📁 integration/
│   │   ├── github-flux-integration/
│   │   ├── flux-backstage-integration/
│   │   └── harvester-integration/
│   └── 📁 performance/
│       ├── flux-sync-performance/
│       └── github-actions-performance/
├── 📁 config/
│   ├── github-actions/
│   │   ├── secrets.example.yaml
│   │   ├── environments.yaml
│   │   └── permissions.yaml
│   ├── fluxcd/
│   │   ├── sync-config.yaml
│   │   ├── notification-config.yaml
│   │   └── kustomization-config.yaml
│   └── backstage/
│       ├── catalog-config.yaml
│       ├── scaffolder-config.yaml
│       └── techdocs-config.yaml
├── Makefile                         # Make commands for common tasks
├── docker-compose.yml              # Local development
├── README.md
├── CONTRIBUTING.md
├── SECURITY.md
├── .gitignore
├── .pre-commit-config.yaml         # Pre-commit hooks
├── renovate.json                   # Dependency updates
└── LICENSE

```