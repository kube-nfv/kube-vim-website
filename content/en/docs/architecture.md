---
title: Architecture
weight: 2
description: The vim and gateway components, the KRM controller model, and bundled dependencies.
---

Kube-VIM ships as two Kubernetes Deployments: **vim**, the gRPC server that
exposes the ETSI reference points, and **gateway**, a
gRPC-Gateway reverse proxy that exposes REST/OpenAPI bindings.

> This page is being written. It will cover the vim and gateway components, the
> stateless KRM controller model, the bundled dependencies (KubeVirt, CDI,
> Kube-OVN, Multus), and key design decisions such as per-edge VIMs and the
> managed management network.
