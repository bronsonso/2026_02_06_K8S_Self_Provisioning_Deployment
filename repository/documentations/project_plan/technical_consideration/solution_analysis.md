
# Platforms for Unifying Legacy VMs and Container Orchestration

The market offers several other platforms that aim to solve the same problem: unifying legacy VM workloads with modern container orchestration, on‑premises, with manageable operational costs and developer self‑service.

Below is a structured overview of the most relevant alternatives, categorized by their architectural approach and vendor ecosystem. Each includes a brief feasibility assessment for your 700‑system environment.

---

## 1. Kubernetes‑Native Virtualization (KubeVirt Derivatives)

These solutions embed VMs into Kubernetes as custom resources. They are the closest cousins to Harvester and OpenShift Virtualization.

| Solution                           | Description                                                                                   | VM Migration Path                                 | Container Orchestration                | Cost / Licensing                        | Operational Complexity |
|------------------------------------|-----------------------------------------------------------------------------------------------|--------------------------------------------------|----------------------------------------|-----------------------------------------|------------------------|
| **OpenShift Virtualization**       | Red Hat’s enterprise Kubernetes platform with integrated KubeVirt. Full support, lifecycle management, and automation. | `virt‑v2v`, VM import UI, live migration         | OpenShift Container Platform           | Commercial (subscription per core)      | Moderate – Red Hat manages control plane |
| KubeVirt (upstream)               | Raw KubeVirt on any K8s distribution. You manage K8s yourself.                               | Manual import (`virt‑v2v`), live migration supported | Standard K8s                          | Free (open source)                     | High – you build the platform |
| KubeVirt + OKD                   | Community edition of OpenShift (OKD) with KubeVirt included. No Red Hat subscription.          | Same as OpenShift, but without paid support       | OKD K8s                               | Free                                   | High – no commercial support, community upgrades |
| Nutanix Karbon + AHV             | Nutanix hypervisor (AHV) with built‑in K8s (Karbon). VMs run natively on AHV, not inside K8s pods. | Native VM migration to AHV (Nutanix Move)         | Karbon (managed K8s on AHV)           | Commercial (per core or per TiB)        | Moderate – single vendor stack, but proprietary |
| VMware vSphere with Tanzu        | vSphere hypervisor with embedded K8s (TKG) on Supervisor Cluster. VMs run on vSphere, containers in namespaces. | Native vSphere VM migration                       | Tanzu Kubernetes Grid                 | Commercial (per core, post‑Broadcom)    | Moderate‑High – vSphere expertise needed |

**Feasibility for your case:**

- **OpenShift Virtualization** is the premium, fully supported option – but you have already evaluated it and found the licensing cost prohibitive for 700 systems.
- **KubeVirt upstream** gives you freedom but requires strong K8s operational skills and self‑built tooling.
- **OKD** is OpenShift without the price tag, but you lose enterprise support and upgrade automation – risky for 700 systems.
- **Nutanix and VMware** are mature hypervisors adding K8s capabilities. Both have significant licensing costs (Nutanix less than VMware, but still substantial). They do not unify management of VMs and containers under one scheduler – they run VMs on the hypervisor and containers on K8s, managed separately. This may perpetuate silos.

---

## 2. Hyperconverged Infrastructure (HCI) with Integrated Container Management

These platforms combine storage, compute, and virtualization with optional K8s add‑ons. They are appliance‑like and often reduce operational toil.

| Solution                         | Description                                                       | Legacy VM Support               | Container Support                  | Cost / Licensing                        | Operational Complexity |
|----------------------------------|-------------------------------------------------------------------|---------------------------------|------------------------------------|-----------------------------------------|------------------------|
| Microsoft Azure Stack HCI       | Hyper‑V based HCI with AKS hybrid (AKS on Azure Stack HCI).       | Native VM migration to Hyper‑V | AKS (managed K8s)                | Commercial (per core, Azure hybrid benefit) | Moderate – Windows Admin Center, Azure Arc integration |
| Cisco HyperFlex + Kubernetes    | HCI platform with K8s orchestration (Cisco Container Platform or Intersight K8s). | VM migration to HyperFlex       | K8s deployed on HyperFlex        | Commercial                             | Moderate – Cisco‑centric management |
| Dell VxRail + Red Hat           | VxRail HCI with integrated OpenShift (validated design).          | VMware VM migration             | OpenShift                        | Very High (VxRail + OpenShift)        | Moderate – single‑vendor stack |

**Feasibility for your case:**

These are costly, enterprise‑grade stacks suitable for organisations that prefer appliance‑like operations and can afford vendor lock‑in.

They do not unify VM and container scheduling under one control plane; VMs stay on the hypervisor layer, containers run on top. Your team still manages two distinct platforms, even if they share hardware.

---

## 3. Lightweight Schedulers & Container Orchestration Alternatives

Beyond Nomad, there are other schedulers that can handle mixed workloads. **Nomad itself** is included here as a direct alternative.

| Solution                       | Description                                                                  | VM Handling                                      | Container Orchestration       | Cost          | Operational Complexity |
|--------------------------------|------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------|---------------|------------------------|
| **HashiCorp Nomad**           | Simple, flexible scheduler. Supports containers, VMs, and more via task drivers. | QEMU driver, can run VMs as tasks; `nomad-driver-podman` for containers | Native, no separate platform needed | Free (open source), Enterprise paid | Low‑Moderate – single binary, integrates with Consul/Vault |
| Docker Swarm                  | Built into Docker Engine. Simple clustering.                                 | No native VM support; run VMs in containers (Docker‑in‑Docker, KVM‑in‑container) | Docker Swarm                  | Free          | Very Low              |
| Apache Mesos + Marathon       | Mature cluster manager, can run VMs via tasks.                               | Can launch QEMU processes as Mesos tasks         | Marathon                      | Free          | High (Mesos is complex, declining community) |
| Slurm + Enroot/Pyxis          | HPC workload manager, sometimes used for containerized services.             | Not designed for VMs                             | Container runtime (Enroot)     | Free          | High (not intended for general IT) |
| K3s                           | Lightweight K8s distribution, no VM capabilities alone.                      | Add KubeVirt on top                              | K3s (standard K8s)            | Free          | Moderate (small control plane) |

**Feasibility for your case:**

- **Nomad** is already on your evaluation list. It excels at simplicity and mixed workloads, but **does not provide a unified VM/container management UI**, lacks built‑in storage orchestration for VMs, and would require significant custom scripting to match the developer self‑service of a Kubernetes‑based platform. For 700 systems, it could become an integration burden.
- **Docker Swarm** is too limited for 700 mixed workloads; no native VM support and limited ecosystem.
- **Mesos** is largely obsolete in the cloud‑native era.
- **Slurm** is not suitable for enterprise application hosting.
- **K3s + KubeVirt** is technically possible, but you would be assembling the platform yourself – similar to upstream KubeVirt but with a smaller control plane footprint.

---

## 4. PaaS on Kubernetes (Developer‑Focused Abstraction)

These solutions do not handle VMs, but they can be layered on top of any K8s distribution to deliver the self‑service experience you want for new applications. They are complementary, not primary platforms.

| Solution              | Description                                                | VM Support | Self‑Service Capabilities                 | Cost            |
|-----------------------|------------------------------------------------------------|------------|-------------------------------------------|-----------------|
| Cloud Foundry (Korifi)| Cloud Foundry running on Kubernetes (Korifi).              | None – apps must be containerized | Push‑to‑deploy, services marketplace      | Free (open source) |
| Knative               | Serverless platform on K8s.                                | None       | Build, serving, eventing                 | Free            |
| Waypoint              | HashiCorp’s application delivery abstraction.              | Can run Nomad jobs, K8s, Docker | Single workflow to deploy, manage        | Free            |
| Acorn                 | Simpler application packaging and deployment on K8s.       | None       | `acorn run` – lightweight PaaS           | Free            |
| Kubevela              | Modern application platform with OAM.                      | None       | Declarative app deployment               | Free            |
| Rainbond              | Open‑source PaaS for K8s (Chinese origin, but mature).     | None       | DevOps, service mesh, plug‑and‑play      | Free            |

**Feasibility for your case:**

These are not replacements for your VM hosting. They are valuable add‑ons after you have a K8s foundation.

For your immediate goal of unifying VMs and containers, they are not sufficient alone.

---

## 5. Public‑Cloud‑On‑Premises Solutions

If your hesitation about OpenShift was cost, these are even more expensive but offer a pure “as‑a‑service” experience inside your datacenter.

| Solution                              | Description                                          | VM Support        | Container Support | Operational Model                 |
|---------------------------------------|------------------------------------------------------|-------------------|-------------------|-----------------------------------|
| Google Distributed Cloud Virtual (formerly GDC) | Google’s on‑prem solution for VMs, air‑gapped.      | Full VM lifecycle | GKE on‑prem       | Fully managed by Google (very high cost) |
| AWS Outposts                         | AWS hardware in your DC, runs EC2 and EKS locally.   | EC2 VMs           | EKS               | Fully managed by AWS             |
| Azure Stack Edge / Hub               | Smaller footprint, but can run AKS and VMs.          | Hyper‑V VMs       | AKS               | Managed by Microsoft             |

**Feasibility:**

These are turnkey, vendor‑operated solutions. They eliminate your operational burden but at a very high subscription cost.

They also lock you into a specific public cloud provider’s APIs, which may conflict with your desire for industry‑best practices (though GKE/GDC does use standard Kubernetes).

For 700 systems, this could be prohibitively expensive compared to self‑managed open‑source stacks.

---

## 6. Emerging / Niche Solutions

| Solution                  | Description                                                                   | Relevance                                                                     |
|---------------------------|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| KubeSphere                | Open‑source multi‑tenant K8s platform with VM support via KubeVirt.           | Similar to Rancher + Harvester, but less mature.                             |
| Zadara                    | Edge and on‑prem as‑a‑service, storage and compute with K8s.                  | Niche, may be costly.                                                         |
| Platform9                 | Managed K8s on‑prem, also offers VM management via KubeVirt (SaaS control plane). | Reduces ops, but SaaS control plane may raise security concerns.            |
| Spectro Cloud Palette     | Managed K8s with edge and on‑prem support, supports KubeVirt.                 | Similar to Platform9.                                                         |
| Canonical MicroCloud      | Low‑touch small‑scale K8s + Ceph + LXD.                                      | LXD is system containers, not full VMs; limited scale.                       |

---

## Summary: Which Other Solutions Are Truly Relevant?

After evaluating the market, the platforms you already considered (**OpenShift Virtualization**, **Harvester**, **Nomad**) remain the frontrunners. Among the additional alternatives, three stand out as genuinely competitive for your 700‑system modernization, each with distinct trade‑offs:

| Solution                                  | Best For                                                                  | Critical Weakness                                               | Verdict                                                                 |
|-------------------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------------|-------------------------------------------------------------------------|
| Nutanix AHV + Karbon                     | Organisations already on Nutanix, wanting HCI + K8s.                     | Separate VM and container management; licensing cost.           | Maybe – if you have existing Nutanix.                                  |
| VMware vSphere with Tanzu               | Organisations deeply invested in VMware, seeking incremental K8s adoption. | VMware licensing now very expensive (Broadcom).                 | Maybe – only if you are already on VMware.                             |
| Platform9 / Spectro Cloud (Managed K8s + KubeVirt) | Teams that want open‑source technology but no in‑house control plane management. | SaaS control plane; you still manage VMs.                      | Possible – reduces ops, but adds SaaS dependency and cost.             |

**OpenShift Virtualization** – your previously evaluated enterprise option – offers the most polished experience but at a cost you deemed too high for 700 systems without a clear ROI.

**Nomad** is lightweight and flexible but would require extensive customisation to match the VM lifecycle management and developer self‑service that Kubernetes‑native platforms provide out of the box. It also lacks a unified management UI for both VMs and containers.

**Harvester + Rancher + RKE2** remains the only solution that delivers:

- **Zero licensing cost** – no per‑core or per‑socket fees.
- **Unified VM+container management** under a single UI and API – VMs are first‑class citizens in Kubernetes, not a separate silo.
- **No vendor lock‑in** – upstream Kubernetes, standard KubeVirt, open APIs.
- **On‑prem control plane** – no mandatory SaaS dependency.
- **Enterprise‑ready** – CNCF‑accepted, backed by a large community and SUSE’s commercial support option if needed.

---

## Final Recommendation

**Stick with your earlier conclusion:** Harvester + Rancher + RKE2 is the most feasible and suitable solution on the market today. The alternatives either:

- **Cost significantly more** (OpenShift, Nutanix, VMware, Azure Stack HCI, public‑cloud‑on‑prem),
- **Do not truly unify VM and container management** (all HCI + separate K8s, Nomad without extensive customisation),
- **Require you to build everything yourself** (raw KubeVirt, OKD, K3s + KubeVirt), or
- **Add unnecessary complexity for marginal benefit** (Docker Swarm, Mesos, Slurm).

Your chosen stack is not only viable – it is the industry‑leading approach for organisations modernising from legacy hypervisors to cloud‑native, as evidenced by the CNCF’s acceptance of Harvester and the widespread adoption of Rancher. Invest your budget in training your team on Kubernetes and Rancher, not in expensive proprietary licenses.