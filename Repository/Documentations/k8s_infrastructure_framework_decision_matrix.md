## K8S Infrastructure Decision Matrix

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
