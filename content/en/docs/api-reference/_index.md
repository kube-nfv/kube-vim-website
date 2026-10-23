---
title: API Reference
weight: 6
description: The Kube-VIM API over gRPC and REST, its conventions, and the Go and Python clients.
---

Kube-VIM serves one API per ETSI management interface. Each is defined in Protocol Buffers,
served over gRPC, and exposed as a REST API with an OpenAPI 3.1 schema by the Kube-VIM
gateway. Orchestrators (NFVO, the Or-Vi reference point) and VNF managers (VNFM, Vi-Vnfm) use
the same APIs; what each may do is set by the OAuth 2.0 scopes in its token.

The [REST reference](rest/) lists every operation, field and error.

## The APIs

| API | REST prefix | gRPC service | What it manages |
| --- | --- | --- | --- |
| Software image | `/image/v1` | `kubenfv.kubevim.image.v1.ImageService` | VM images and their import |
| Compute flavour | `/flavour/v1` | `kubenfv.kubevim.flavour.v1.FlavourService` | CPU, memory and disk sizes for VMs |
| Network | `/network/v1` | `kubenfv.kubevim.network.v1.NetworkService` | Networks and their IPv4 and IPv6 subnets |
| Compute | `/compute/v1` | `kubenfv.kubevim.compute.v1.ComputeService` | VMs, their snapshots, and placement groups |
| Storage | `/storage/v1` | `kubenfv.kubevim.storage.v1.StorageService` | Volumes and their snapshots |

## Conventions

The APIs share one set of rules, so learning one teaches you the others.

**Methods.** Every resource has Create, Get, List, Update and Delete. Actions that are not
plain reads or writes have their own endpoint on the resource:

```text
POST /compute/v1/computes/{compute_id}/operate      start, stop, pause, resume, reboot
POST /compute/v1/computes/{compute_id}/scale        move to another flavour
POST /compute/v1/computes/{compute_id}/migrate      live migration
POST /compute/v1/computes/{compute_id}/attachVolume
POST /storage/v1/volumes/{volume_id}/scale          grow a volume
```

**Identifiers** are UUIDs that Kube-VIM assigns. They stay the same for the life of the
resource, through migration, scaling and snapshot reverts.

**Responses.** Create answers `201 Created` with the new resource and a `Location` header.
Delete answers `204 No Content`. Long-running work, such as an image import or a VM start,
continues after the call returns: poll the resource with Get and watch its status.

**Updates** change only the fields you send. Every resource that has an Update can change its
name and `metadata`; a VM can also gain or lose network interfaces.

**Metadata.** Every resource has one `metadata` map for your own tags. An update merges keys
into it. Keys under `kubevim.kubenfv.io/` are set by Kube-VIM.

**Lists** return a JSON array. Narrow them with an ETSI filter expression:

```text
GET /compute/v1/computes?filter=(eq,computeName,router-1)
```

When a list is paged, the `Link` response header holds the URL of the next page.

**Validation.** Kube-VIM checks every request against the rules in the API definition. A field
that this Kube-VIM does not support yet is rejected with an error, never silently ignored.

## Errors

REST errors are `application/problem+json` documents (RFC 9457). The `type` field says what
went wrong; `status` and `detail` give the HTTP status and a readable message.

```json
{
  "type": "https://kubevim.kubenfv.io/problems/resource-in-use",
  "title": "Conflict",
  "status": 409,
  "detail": "network is used by compute router-1"
}
```

| Type (after `/problems/`) | Status | Meaning |
| --- | --- | --- |
| `validation-failed` | 422 | The request breaks a validation rule |
| `unsupported-field` | 422 | The request sets a field this Kube-VIM does not support yet |
| `invalid-filter` | 400 | The filter expression is not valid |
| `not-found` | 404 | The resource, or one the request refers to, does not exist |
| `resource-in-use` | 409 | The resource cannot be deleted while others use it |
| `invalid-state` | 409 | The resource is not in a state that allows the operation |
| `not-implemented` | 501 | The operation is not implemented yet |
| `backend-unavailable` | 503 | Kubernetes or a component Kube-VIM depends on cannot be reached |
| `internal` | 500 | Anything else |

Over gRPC, the same reason is in a `google.rpc.ErrorInfo` detail with domain
`kubevim.kubenfv.io`. Authentication and authorization failures (401, 403) carry no
Kube-VIM type.

## Authentication and scopes

Every request carries an OAuth 2.0 access token: `Authorization: Bearer <token>`. See
[Authentication](/docs/guides/authentication/) for setting it up.

Each operation needs one scope, named `<api>:v1:<permission>`:

| API | Scopes |
| --- | --- |
| Software image | `image:v1:add`, `query`, `update`, `delete` |
| Compute flavour | `flavour:v1:create`, `query`, `delete` |
| Network | `network:v1:allocate`, `query`, `update`, `terminate` |
| Compute | `compute:v1:allocate`, `query`, `update`, `terminate`, `operate`, `scale`, `migrate` |
| Storage | `storage:v1:allocate`, `query`, `update`, `terminate`, `operate`, `scale`, `migrate` |

A typical setup grants an orchestrator every scope, and a VNF manager every scope except
adding, updating and deleting images, which matches the ETSI split between Or-Vi and Vi-Vnfm.

## Clients

**Python.** Install `kubevim-client` from PyPI:

```python
import kubevim_client
from kubevim_client import ComputeServiceApi, CreateComputeRequest

config = kubevim_client.Configuration(host="https://kubevim.example.com", access_token=token)
with kubevim_client.ApiClient(config) as client:
    compute = ComputeServiceApi(client).create_compute(CreateComputeRequest.from_dict({
        "compute": {"computeName": "router-1", "flavourId": flavour_id, "imageId": image_id},
        "networkInterfaces": [{"name": "data0", "networkId": network_id}],
    }))
    print(compute.compute_id, compute.running_state)
```

Errors raise `kubevim_client.exceptions.ApiException`, with the HTTP status and the problem
document. Values a newer Kube-VIM adds to an enum read as `UNKNOWN_DEFAULT_OPEN_API` instead
of breaking your code.

**Go.** The module `github.com/kube-nfv/kube-vim-api` has the gRPC clients and types, one
package per API:

```go
import computev1 "github.com/kube-nfv/kube-vim-api/pkg/apis/compute/v1"

ctx = metadata.AppendToOutgoingContext(ctx, "authorization", "Bearer "+token)
resp, err := computev1.NewComputeServiceClient(conn).ListComputes(ctx, &computev1.ListComputesRequest{
	Filter: "(eq,computeName,router-1)",
})
```

**Anything else.** Generate a client from the OpenAPI schema: one document per API and a
combined `kubevim.openapi.json` are attached to each
[kube-vim-api release](https://github.com/kube-nfv/kube-vim-api/releases).

## Versions

The major version is part of every REST path and gRPC package (`v1`). Within a major version,
changes only add operations, fields and enum values, so existing clients keep working. The
API and its clients share one release number.
