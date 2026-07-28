---
title: Kube-VIM
linkTitle: Kube-VIM
---

{{< blocks/cover title="Kube-VIM" image_anchor="top" height="full" color="primary" >}}
<div class="mx-auto">
  <p class="lead mt-5">
    A Kubernetes-native, ETSI NFV-MANO compliant<br>
    Virtual Infrastructure Manager
  </p>
  <a class="btn btn-lg btn-primary me-3 mb-4" href="/docs/getting-started/">
    Get started <i class="fas fa-arrow-alt-circle-right ms-2"></i>
  </a>
  <a class="btn btn-lg btn-secondary me-3 mb-4" href="https://github.com/kube-nfv/kube-vim">
    View on GitHub <i class="fab fa-github ms-2"></i>
  </a>
  <p class="lead mt-4">Run VNFs on Kubernetes, alongside your CNFs on the same fabric.</p>
</div>
{{< /blocks/cover >}}

{{% blocks/lead color="dark" %}}
Kube-VIM is a **Kubernetes controller for NFV resources**. It turns ETSI MANO
requests (Or-Vi and Vi-Vnfm) into Kubernetes Custom Resources and manages their
lifecycle, statelessly. Every managed resource lives as a Kubernetes object in
etcd (KRM). Because it runs in Kubernetes and reuses standard components
(KubeVirt, CDI, Kube-OVN, Multus), your VNFs land on the same network and the
same resource pool as your CNFs, with no parallel infrastructure. It speaks the
ETSI reference points over gRPC and REST/OpenAPI, so any ETSI-compatible NFV
orchestrator can drive it.
{{% /blocks/lead %}}

{{% blocks/section color="white" type="row" %}}

{{% blocks/feature icon="fas fa-cubes" title="KRM-native" %}}
Every managed resource is a Kubernetes object in etcd. Kube-VIM reconciles NFV
resources like a native Kubernetes controller, with no external database and no
drift.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-plug" title="ETSI VIM, any NFVO" %}}
Or-Vi and Vi-Vnfm over gRPC and REST, with a generated OpenAPI client.
Standards-conformant to IFA 005/006 and SOL 013. Validated with OSM via an OSM
connector.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-bolt" title="Line-rate data plane" %}}
SR-IOV with hardware offload for near-line-rate throughput. Overlay, underlay,
and SR-IOV networks today; vDPA and vhost-user planned.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-layer-group" title="Converged NFV" %}}
Run VNFs alongside your CNFs on the same hardware and the same network fabric.
Convergence is a property of being Kubernetes-native, not a bolt-on.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-server" title="Hyperconverged and portable" %}}
Runs on any Kubernetes distribution. Proven on Talos Linux in a hyperconverged
edge topology.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-rocket" title="Easy to deploy" %}}
A single Helm bundle ships Kube-VIM together with the components it drives.
GitOps-friendly and simple to stand up.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-cube" title="Built on trusted OSS" %}}
Stands on KubeVirt, CDI, Kube-OVN, and Multus, best-in-class open source with no
vendor, NIC, or distribution lock-in.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-chart-line" title="Observable" %}}
Prometheus metrics out of the box, with `kubevim_*_info` labels that correlate
backend series to ETSI resource IDs.
{{% /blocks/feature %}}

{{% /blocks/section %}}

{{% blocks/section color="primary" %}}
### By telco, for telco, and open source
Kube-VIM is open source under Apache 2.0, backed and supported by
[Retelith](https://retelith.com), a telecom software company building
Kubernetes-native infrastructure for network operators.
{{% /blocks/section %}}
