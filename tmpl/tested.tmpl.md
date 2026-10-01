# OpenShift Tested Maximums

> **⚠️ Disclaimer:** The Achieved Tested Maximum is not a guarantee or a hard limit, it is heavily dependent on many factors including infrastructure, workload type, and cluster configuration.

> **Automated Document:** This file is dynamically updated by Chaibot. It queries Prow and Performance and Scale's Orion-MCP to determine the highest scalability metrics achieved in recent successful test runs.

## 🤖 Update Metadata

* **Last Updated:** `{{LAST_UPDATED_TIMESTAMP}}`
* **OpenShift Version:** `{{OCP_VERSION}}`
* **Infrastructure Platform:** `{{INFRA_PLATFORM}}` (e.g., AWS, GCP, Bare Metal)
* **Prow Job Reference(s):** `[ {{PROW_JOB_URL}} , <could be many>] `

## 🌐 Cluster-Wide Maximums

These metrics represent the highest total limits tested across the entire OpenShift cluster.

| Resource | Achieved Maximum | Notes & Observations | 
| :--- | :--- | :--- | 
| **Worker Nodes** | `{{MAX_NODES_ACHIEVED}}` | `{{NOTES_NODES}}` | 
| **Pods (Cluster Total)** | `{{MAX_PODS_CLUSTER_ACHIEVED}}` | `{{NOTES_CLUSTER_PODS}}` | 
| **Namespaces** | `{{MAX_NAMESPACES_ACHIEVED}}` | `{{NOTES_NAMESPACES}}` | 
| **CUDNs** | `{{MAX_NAMESPACES_ACHIEVED}}` | `{{CAVEATS{workaround_deployed}}}` |

## 📦 Namespace-Scoped Maximums

These metrics represent the highest density achieved within a single namespace/project.

| Resource | Achieved Maximum | Notes & Observations | 
| :--- | :--- | :--- | 
| **Pods per Namespace** | `{{MAX_PODS_PER_NS}}` | `{{NOTES_PODS_NS}}` | 
| **ConfigMaps per Namespace** | `{{MAX_CM_PER_NS}}` | `{{NOTES_CM_NS}}` | 
| **Secrets per Namespace** | `{{MAX_SECRETS_PER_NS}}` | `{{NOTES_SECRETS_NS}}` | 
| **Services per Namespace** | `{{MAX_SVC_PER_NS}}` | `{{NOTES_SVC_NS}}` | 

## 🕸️ Networking & Routing

Tested maximums for the cluster's software-defined network and ingress controllers.

| Resource | Achieved Maximum | Notes & Observations | 
| :--- | :--- | :--- | 
| **Total Routes** | `{{MAX_ROUTES}}` | `{{NOTES_ROUTES}}` | 
| **Total Services** | `{{MAX_SERVICES}}` | `{{NOTES_SERVICES}}` | 
| **Endpoints per Service** | `{{MAX_ENDPOINTS_PER_SVC}}` | `{{NOTES_ENDPOINTS}}` | 
| **Pods per Node** | `{{MAX_PODS_PER_NODE}}` | `{{NOTES_PODS_NODE}}` | 
| **Total L2 UDNs** | `{{MAX_L2_UDNS}}` | `{{NOTES_L2_UDNS}}` |
| **Total L3 UDNs** | `{{MAX_L3_UDNS}}` | `{{NOTES_L3_UDNS}}` |
| **Total L2 BGP CUDNs** | `{{MAX_L2_BGP_UDNS}}` | `{{NOTES_L2_BGP_UDNS}}` |

## 🖥️ OpenShift Virtualization (CNV)

Tested maximums specific to virtual machine workloads running via OpenShift Virtualization.

| Resource | Achieved Maximum | Notes & Observations | 
| :--- | :--- | :--- | 
| **Virtual Machines (Cluster Total)** | `{{MAX_VMS_CLUSTER_ACHIEVED}}` | `{{NOTES_VMS_CLUSTER}}` | 
| **Virtual Machines per Node** | `{{MAX_VMS_PER_NODE}}` | `{{NOTES_VMS_NODE}}` | 
| **Max VM Density (vCPU / Core)** | `{{MAX_VM_VCPU_DENSITY}}` | `{{NOTES_VM_DENSITY}}` | 
| **Concurrent VM Migrations** | `{{MAX_CONCURRENT_VM_MIGRATIONS}}` | `{{NOTES_VM_MIGRATIONS}}` | 

## ⚙️ Additional Kubernetes Resources

| Resource | Achieved Maximum | Notes & Observations | 
| :--- | :--- | :--- | 
| **Deployments** | `{{MAX_DEPLOYMENTS}}` | `{{NOTES_DEPLOYMENTS}}` | 
| **Custom Resource Definitions (CRDs)** | `{{MAX_CRDS}}` | `{{NOTES_CRDS}}` | 
| **Persistent Volume Claims (PVCs)** | `{{MAX_PVCS}}` | `{{NOTES_PVCS}}` | 
| **RoleBindings** | `{{MAX_ROLEBINDINGS}}` | `{{NOTES_ROLEBINDINGS}}` | 
