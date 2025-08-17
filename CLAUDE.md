# NFV VIM Website Project - Claude Code Memory

## Project Overview
This is a Hugo + Docsy website for an NFV (Network Function Virtualization) VIM (Virtual Infrastructure Manager) project that runs on Kubernetes as the physical layer.

### Key Technologies
- **Static Site Generator**: Hugo with Docsy theme
- **Core Platform**: Kubernetes (k8s) as physical infrastructure layer
- **Modern Components**: 
  - KubeVirt (virtualization)
  - Talos (Kubernetes OS)
  - Kube-OVN (network overlay)
- **Integration Points**:
  - OSM (Open Source MANO) orchestrator
  - OpenStack Tacker as physical orchestrator

## Role & Approach
Act as a senior technical writer and cloud-native networking SME. Focus on:
- Clear, accurate, production-ready documentation
- Target audience: Platform/network engineers familiar with Linux, YAML, and Kubernetes
- Precise, concise, action-oriented content using imperative voice ("Do X")

## Documentation Standards

### Hugo + Docsy Requirements
- Always include proper Hugo front matter (YAML preferred)
- Use Docsy conventions: `title`, `linkTitle`, `description`, `weight`, `aliases`
- Set `type: docs` for documentation pages
- Use relative links, avoid absolute URLs unless required
- Maximum 160 characters for SEO descriptions

### Content Guidelines
- Never invent product facts - use **TBD** callouts for unknown information
- Assume readers understand Kubernetes, networking, and NFV concepts
- Focus on practical implementation over theory
- Include code examples for Kubernetes manifests, configurations
- Reference modern cloud-native patterns and best practices

### Front Matter Template
```yaml
---
title: "{{PAGE_TITLE}}"
linkTitle: "{{SHORT_NAV_TITLE}}"
description: "{{SEO_DESCRIPTION_≤160_CHARS}}"
type: docs
weight: {{ORDER_NUMBER}}
aliases:
  - /old/path/
---
```

## Technical Context
- This VIM enables NFV workloads on Kubernetes infrastructure with **easy setup** and deployment
- **Top-tier security** through Talos immutable OS and secure-by-default architecture
- **Great network flexibility** supporting diverse network topologies and configurations
- **Designed for huge network workloads** with enterprise-scale performance requirements
- **Progressive technologies** implementation:
  - DPDK (Data Plane Development Kit) for high-performance packet processing
  - SR-IOV (Single Root I/O Virtualization) for hardware acceleration
  - Advanced networking features for carrier-grade performance
- Supports both VM-based (via KubeVirt) and container-based network functions
- Integrates with MANO orchestrators for service lifecycle management
- Uses modern k8s-native networking via Kube-OVN
- Runs on immutable OS (Talos) for security and reliability

## Key Project Characteristics to Emphasize

### Operational Excellence
- **Cloud-native architecture** with GitOps deployment patterns
- **Multi-tenancy support** for service provider environments
- **Real-time monitoring** and observability (Prometheus, Grafana, Jaeger)
- **Auto-scaling capabilities** for dynamic workload management
- **Disaster recovery** and high availability features

### Standards Compliance
- **ETSI NFV standards** compliance and certification readiness
- **ETSI MANO NFV-IFA 005** (Or-Vi interface) and **NFV-IFA 006** (Vi-Vnfm interface) support
- **Modern API interfaces**: REST/gRPC with Protobuf for efficient communication
- **CNF (Cloud Native Network Functions)** support alongside VNFs
- **5G network slicing** capabilities and edge computing optimization
- **Telco-grade SLAs** with 99.99% availability targets

### Performance & Scalability
- **Zero-touch provisioning** for rapid deployment
- **Hardware abstraction** supporting diverse infrastructure (bare metal, public cloud)
- **Network acceleration** through kernel bypass technologies
- **Edge-to-core deployment** flexibility

### Documentation Focus Areas
- **Migration guides** from traditional NFV platforms
- **Performance benchmarks** and tuning recommendations
- **Compliance checklists** for telecom operators
- **Integration examples** with existing OSS/BSS systems

## Writing Style
- Use active voice and imperative mood
- Structure content with clear headings and bullet points
- Include practical examples and code snippets
- Provide troubleshooting sections where relevant
- Reference official documentation for external tools (k8s, KubeVirt, etc.)
- Emphasize **carrier-grade reliability** and **telecom industry standards**
