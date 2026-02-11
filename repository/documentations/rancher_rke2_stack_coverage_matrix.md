
## Complete RKE2 + Rancher Stack Coverage Table

| Component | Included in RKE2 | Included in Rancher | Need to Add | Notes |
|-----------|-----------------|-------------------|-------------|--------|
| **Host OS** | ❌ Not included | ❌ Not included | ✅ **YOU PROVIDE** | Ubuntu/RHEL/Rocky Linux on your servers |
| **Provisioning** | ❌ Not included | ✅ **Node Drivers** | ⚠️ Basic only | Rancher can provision VMs/nodes via drivers |
| **Control Plane** | ✅ **Full K8s** | ✅ Multi-cluster mgmt | ❌ Nothing | Production-grade control plane |
| **Container Runtime** | ✅ **containerd** | - | ❌ Nothing | Default, no Docker needed |
| **CNI (Networking)** | ✅ **Calico/Cilium/Canal** | - | ❌ Nothing | Choose during installation |
| **Storage (CSI)** | ✅ Local Path | ✅ Longhorn (catalog) | ⚠️ Basic included | Add advanced storage if needed |
| **Ingress** | ✅ **Traefik** | ✅ NGINX Ingress | ❌ Nothing | Both available out of the box |
| **Service Mesh** | - | ✅ **Istio (catalog)** | ⚠️ One-click install | Available in Rancher marketplace |
| **GitOps** | - | ✅ **Fleet** | ❌ Nothing | Rancher's built-in GitOps engine |
| **CI/CD** | - | - | ✅ **Add separately** | Jenkins/GitHub Actions/GitLab CI |
| **Monitoring** | - | ✅ **Prometheus + Grafana** | ❌ Nothing | Full monitoring stack |
| **Logging** | - | ✅ **EFK/OpenSearch** | ❌ Nothing | Full logging stack |
| **Tracing** | - | - | ✅ **Add separately** | Jaeger, Tempo, etc. |
| **Visualization** | - | ✅ **Grafana** | ⚠️ Basic included | Advanced dashboards via Grafana |
| **Secret Management** | - | ✅ **Secrets encryption** | ⚠️ Basic included | Add Vault for advanced features |
| **Developer Portal** | - | - | ✅ **Add separately** | Backstage, Port, etc. |
| **Backup** | - | ✅ **Backup Operator** | ❌ Nothing | Built-in backup/restore |
| **Security** | ✅ **CIS-hardened** | ✅ Scanner + OPA | ❌ Nothing | Security policies included |
