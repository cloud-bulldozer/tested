# OpenShift Tested Maximums

> **Disclaimer:** The Achieved Tested Maximum is not a guarantee or a hard limit, it is heavily dependent on many factors including infrastructure, workload type, and cluster configuration.

> **Automated Document:** This file is dynamically updated by Chaibot. It queries Prow and Performance and Scale's Orion-MCP to determine the highest scalability metrics achieved in recent successful test runs.

## Update Metadata

* **Last Updated:** `2026-10-01`
* **OpenShift Version:** `5.0.0-0.nightly-2026-08-30-014421` (k8s v1.36.3)
* **Infrastructure Platform:** `AWS` (us-west-2, OVNKubernetes SDN)
* **Prow Job Reference(s):** `[periodic-ci-openshift-eng-ocp-perfscale-main-aws-5.0-nightly-x86-control-plane-252nodes/2094357209625399296](https://prow.ci.openshift.org/view/gs/origin-ci-test/logs/periodic-ci-openshift-eng-ocp-perfscale-main-aws-5.0-nightly-x86-control-plane-252nodes/2094357209625399296)`

## Cluster-Wide Maximums

These metrics represent the highest total limits tested across the entire OpenShift cluster.

| Resource | Achieved Maximum | Notes & Observations |
| :--- | :--- | :--- |
| **Worker Nodes** | `252` | Scaled from 3 to 252 workers via workers-scale (3 MachineSets x 84 replicas across us-west-2a/c/d). Instance type: m5.xlarge. Masters: 3x m6a.4xlarge, Infra: 3x r5.8xlarge. NodeReady P99: 1026s. |
| **Pods (Cluster Total)** | `61,854` | Peak running pods observed during node-density workload (57,451 workload pods + system pods). |
| **Namespaces** | `2,343` | Peak namespace count during cluster-density-v2 (2,268 workload namespaces + 75 system namespaces). |
| **CUDNs** | `1,000` | From cudn-density-1000 job (periodic-ci-openshift-eng-ocp-perfscale-main-aws-5.0-nightly-x86-cudn-density-1000). Tested with L2 BGP CUDNs. |

## Namespace-Scoped Maximums

These metrics represent the highest density achieved within a single namespace/project.

| Resource | Achieved Maximum | Notes & Observations |
| :--- | :--- | :--- |
| **Pods per Namespace** | `1,000` | node-density workload: 57,451 pods across ~58 namespaces (iterationsPerNamespace=1000). node-density-cni also ran at 1000 pods/ns with 23,055 total pods (multus CNI). |
| **ConfigMaps per Namespace** | `10` | cluster-density-v2 workload creates 10 configmaps per namespace (34,559 total cluster-wide including system). |
| **Secrets per Namespace** | `10` | cluster-density-v2 workload creates 10 secrets per namespace (30,152 total cluster-wide including system). |
| **Services per Namespace** | `5` | cluster-density-v2 workload creates 5 services per namespace (11,437 total cluster-wide including system). |

## Networking & Routing

Tested maximums for the cluster's software-defined network and ingress controllers.

| Resource | Achieved Maximum | Notes & Observations |
| :--- | :--- | :--- |
| **Total Routes** | `4,544` | From cluster-density-v2 (2 routes per namespace x 2,268 namespaces + system routes). |
| **Total Services** | `11,437` | From cluster-density-v2 (5 services per namespace x 2,268 namespaces + system services). |
| **Endpoints per Service** | `2` | cluster-density-v2 deployments use 2 replicas per deployment, each service backs one deployment. |
| **Pods per Node** | `~228` | node-density: 57,451 pods / 252 workers. Peak cluster-wide running count: 61,854 (~245 per node including system pods). |
| **Total L2 UDNs** | `63` | udn-density-pods workload: 63 iterations (0.25 x 252 nodes), Layer 2 enabled. Job took 1m54s. |
| **Total L3 UDNs** | `N/A` | L3 UDNs were not tested in this run (--layer3=false). |
| **Total L2 BGP CUDNs** | `1,000` | From cudn-density-1000 job (periodic-ci-openshift-eng-ocp-perfscale-main-aws-5.0-nightly-x86-cudn-density-1000). |

## OpenShift Virtualization (CNV)

Tested maximums specific to virtual machine workloads running via OpenShift Virtualization.

| Resource | Achieved Maximum | Notes & Observations |
| :--- | :--- | :--- |
| **Virtual Machines (Cluster Total)** | `TBD` | From metal virt-density job (periodic-ci-openshift-eng-ocp-perfscale-main-metal-5.0-nightly-x86-virt-density). Orion reports 15 runs with vmiReadyLatency P99 avg 39s. |
| **Virtual Machines per Node** | `TBD` | Data pending from metal virt-density job on bare-metal infrastructure. |
| **Max VM Density (vCPU / Core)** | `TBD` | Data pending from metal virt-density job. |
| **Concurrent VM Migrations** | `TBD` | Not tested in current job set. |

## Additional Kubernetes Resources

| Resource | Achieved Maximum | Notes & Observations |
| :--- | :--- | :--- |
| **Deployments** | `11,411` | From cluster-density-v2 (5 deployments per namespace x 2,268 namespaces + system deployments). |
| **Custom Resource Definitions (CRDs)** | `1,024` | crd-scale workload: 1,024 CRDs created in 51s on the 252-node cluster. |
| **Persistent Volume Claims (PVCs)** | `N/A` | PVCs were not explicitly tested in this control-plane job run. |
| **RoleBindings** | `N/A` | RoleBindings were not explicitly measured in this control-plane job run. |
