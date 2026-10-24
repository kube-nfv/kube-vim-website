---
title: Standards
weight: 7
description: How the Kube-VIM API builds on the ETSI NFV IFA and SOL specifications, what it adds, and what it leaves out.
---

The Kube-VIM API is not a home-grown design. It is built on the ETSI NFV-MANO specifications,
the industry standard for managing virtualized network functions, and aligned with them. Any
orchestrator that works with the ETSI model will find familiar resources and operations;
[OSM](https://osm.etsi.org) is a validated integration.

## The specifications

ETSI NFV-MANO splits management into three roles: the **NFVO** orchestrates network services,
the **VNFM** manages the lifecycle of each network function, and the **VIM** manages the
compute, network and storage underneath. Kube-VIM is a VIM. The NFVO reaches it over the
**Or-Vi** reference point and the VNFM over **Vi-Vnfm**.

Two families of specifications describe those reference points:

- **ETSI IFA** defines the information model: the resources, their attributes and their
  operations. [IFA 005](https://www.etsi.org/deliver/etsi_gs/nfv-ifa/001_099/005/05.04.01_60/gs_nfv-ifa005v050401p.pdf)
  covers Or-Vi and [IFA 006](https://www.etsi.org/deliver/etsi_gs/nfv-ifa/001_099/006/05.04.01_60/gs_nfv-ifa006v050401p.pdf)
  covers Vi-Vnfm. Kube-VIM uses version 5.4.1.
- **ETSI SOL** defines protocols. [SOL 013](https://www.etsi.org/deliver/etsi_gs/NFV-SOL/001_099/013/05.04.01_60/gs_NFV-SOL013v050401p.pdf)
  sets the common rules for ETSI REST APIs: paths, errors, filtering, paging and
  authorization.

ETSI publishes the model for Or-Vi and Vi-Vnfm but no REST protocol for them, so every VIM API
is a mapping of IFA onto a protocol. Kube-VIM maps it onto gRPC and REST, following SOL 013.
No ETSI programme certifies Or-Vi or Vi-Vnfm implementations.

## What comes from ETSI

- **The interfaces.** One API for each IFA management interface: software images, compute
  flavours, compute, networks and storage.
- **The resources and their attributes,** under IFA's names: `numVirtualCpu`,
  `virtualMemSize`, `segmentationId`, `operationalState` and so on.
- **The operations:** allocate, query, update and terminate; operate (start, stop, pause,
  reboot), scale and migrate; attach and detach storage; snapshots.
- **Or-Vi and Vi-Vnfm** share the same interfaces in IFA, so they share the same APIs in
  Kube-VIM, told apart by OAuth 2.0 scopes.
- **The REST conventions** of SOL 013: `/{api}/v1/` paths, problem documents for errors, the
  filter syntax, paging with the `Link` header, `201 Created` with `Location`, and OAuth 2.0.

## How the API presents the model

IFA describes information, not an API, so Kube-VIM presents it the way modern APIs are built:

- Allocate, Query and Terminate become Create, Get, List and Delete; one query operation is
  split into reading one resource and listing many.
- Identifiers are named after their resource (`computeId`, `networkId`) everywhere they appear.
- Values IFA leaves as free text, such as image status or compute operation, are typed
  enumerations.
- Sizes are Kubernetes quantities such as `"10Gi"`, not numbers with an implied unit.
- An update changes only the fields it carries.
- Snapshots and placement groups are resources you can list and read back; in IFA they can
  only be created.

## Extensions

What Kube-VIM adds, mostly where Kubernetes infrastructure offers more than IFA describes:

- **Every resource:** a `metadata` map and a name, flavours and subnets included.
- **Images:** import from HTTP, S3, a container registry, an upload, or a Glance or local
  catalog; import up front or on first use; progress and failure reasons; firmware (BIOS, EFI,
  secure boot) and boot disk bus.
- **Flavours:** hugepages and guest CPU topology.
- **Networks:** provider networks by name, realised as Kube-VIM decides; dual-stack networks with one IPv4 and one IPv6 subnet; MTU and DNS
  servers.
- **Compute:** placement groups (together or apart, per node or zone, required or preferred);
  creating a VM stopped and resuming it after a pause; interface names, NIC models and address
  assignment; the guest PCI address, guest interface name and host PCI address of each
  interface; a management interface on every VM; failure reasons and a restart-needed flag;
  deleting a VM together with its volumes.
- **Storage:** Kubernetes storage classes, and moving a volume to another class.

## Left out

IFA features with nothing behind them on Kubernetes yet. Each can be added later without
breaking clients.

- **Everywhere:** reservations, quotas, location constraints and resource groups; per-tenant
  visibility of images, flavours and networks; per-request affinity rules and network or
  storage affinity groups (placement groups replace them).
- **Images:** checksums.
- **Flavours:** CPU clock, CPU oversubscription, CPU power states, static CPU pinning rules,
  RDMA storage, acceleration capabilities, and network interfaces inside the flavour (they are
  given when the VM is created).
- **Networks:** standalone ports and trunks, network bandwidth and QoS, connected networks,
  more than one subnet per IP version.
- **Compute:** changing an interface in place (remove it and add a new one), offline
  migration and picking the target host, suspend to disk, certificate data, disk mount points.
- **Storage:** storage flavours and object storage.
- **Other ETSI interfaces:** change notifications, capacity and resource information, fault and
  performance management, reservations and quotas. They would come as separate APIs.

## Anuket

> This section is being written. It will cover alignment with the Anuket infrastructure
> profiles.
