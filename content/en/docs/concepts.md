---
title: Concepts
weight: 4
description: The ETSI reference points Kube-VIM serves and the resources it manages.
---

Kube-VIM speaks two languages. Towards orchestrators it is an ETSI VIM: it manages virtual
infrastructure through the Or-Vi and Vi-Vnfm reference points. Towards the cluster it is a
Kubernetes application: every resource it manages ends up as ordinary Kubernetes objects. This
page introduces the terms from both sides.

## Reference points

An ETSI orchestration stack has three management roles. The **NFVO** (orchestrator) runs
network services, the **VNFM** (VNF manager) runs the lifecycle of each virtual network
function (VNF), and the **VIM** manages the infrastructure under them. Kube-VIM is the VIM.

- **Or-Vi** connects the NFVO to the VIM.
- **Vi-Vnfm** connects the VNFM to the VIM.

Both use the same Kube-VIM APIs. The difference is permission: the orchestrator usually gets
every scope, while a VNF manager can query images but not add or delete them.

## Resources

| Resource | ETSI name | In Kubernetes |
| --- | --- | --- |
| **Image** | Software image | A disk image imported by CDI into a volume that VMs clone |
| **Flavour** | Virtualised compute flavour | A KubeVirt instance type and preference |
| **Network** | Virtualised network | A Kube-OVN subnet, or an SR-IOV network |
| **Subnet** | Network subnet | The IPv4 or IPv6 address range of a network |
| **Compute** | Virtualised compute resource | A KubeVirt virtual machine |
| **Volume** | Virtualised storage resource | A persistent volume claim |
| **Snapshot** | (an operation in ETSI) | A KubeVirt VM snapshot or a volume snapshot |
| **Placement group** | Affinity or anti-affinity group | Pod affinity rules on the group's VMs |

### Images

An image is the disk a VM boots from. You create it from a source, such as an HTTP URL, an S3
object, a container registry or an upload, and Kube-VIM imports it into the cluster. Images in
a Glance or local catalog configured in Kube-VIM show up without a create call. An image is
imported either when you create it or when the first VM uses it.

### Flavours

A flavour sizes a VM: virtual CPUs, memory, optional hugepages and CPU pinning, and its disks.
One disk is the boot disk, which receives the image; the others are created empty with each
VM. Disks name a Kubernetes storage class, or use the default one.

### Networks and subnets

A network is one layer 2 segment. Its subnets are its address families, at most one IPv4 and
one IPv6, so a dual-stack network has two. A network is either an overlay (`GENEVE`) or sits
on a provider network that the operator has prepared (`VLAN` or `FLAT`). The provider network's
name tells Kube-VIM which backend to use: Kube-OVN for ordinary NICs, or SR-IOV for direct
access to the NIC's virtual functions.

### Compute

A compute resource is a VM built from a flavour and an image. Its network interfaces attach to
networks and get one address per subnet, assigned automatically or given statically. Every VM
also gets a management interface on the cluster's pod network. Each interface reports its MAC
address, its PCI address and name inside the guest, and, for SR-IOV, the host PCI address of
its virtual function.

VMs are started, stopped, paused, resumed and rebooted with the operate action, moved to a
bigger flavour with scale, and moved to another node with live migration.

### Volumes

A volume is a persistent disk that you create on its own and attach to a VM. Volumes can grow,
move to another storage class, and be snapshotted. A VM's own disks, from its flavour, are part
of the VM and go away with it; attached volumes stay unless you ask for them to be deleted too.

### Snapshots

VMs and volumes can be snapshotted and reverted to a snapshot. Snapshots are listed under
their VM or volume, and they stay readable after the VM or volume is deleted.

### Placement groups

A placement group keeps its VMs together or apart, per node or per zone, as a hard rule or as
a preference. A VM joins groups when it is created. Use anti-affinity to spread the instances
of a VNF over nodes so that one node failure takes out only one of them.

## Identifiers and metadata

Every resource has a UUID that Kube-VIM assigns, an optional name you choose, and a `metadata`
map for your own tags. Names do not have to be unique; identifiers are.
