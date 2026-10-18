---
title: Authentication
weight: 5
description: Require OAuth 2.0 access tokens from API clients, using any OIDC provider.
---

Kube-VIM can require an OAuth 2.0 access token on every API request, as ETSI GS NFV-SOL 013
asks of NFV-MANO APIs. Clients such as OSM get a token from your identity provider with the
client credentials grant and send it as `Authorization: Bearer <token>`. Kube-VIM checks
the token's signature, issuer, audience and expiry against the provider's published keys.

Any provider that issues JWT access tokens and supports OIDC discovery works: Keycloak,
Dex, Okta, Microsoft Entra ID and others. Authentication is off by default.

## Before you start

Turn on TLS for both components first, so tokens never cross the network in the clear:
set `vim.tls.secretName` and `gateway.tls.secretName` to `kubernetes.io/tls` Secrets.

In your identity provider, create a client for each API consumer (for example `osm-ro`)
that can use the client credentials grant, and make sure its access tokens carry the
audience you choose for Kube-VIM, such as `kube-vim`. In Keycloak this takes an audience
mapper on the client.

## Enable it

```yaml
vim:
  auth:
    enabled: true
    issuer: https://idp.example.com/realms/nfv
    audience: kube-vim
    # Secret with ca.crt, if the provider's certificate is not publicly trusted
    issuerCASecretName: idp-ca
```

Kube-VIM refuses to start with authentication on but TLS off. If Kube-VIM and its clients
only talk inside one cluster, you can accept plaintext with
`vim.auth.allowInsecureTransport: true`.

## Check it

```bash
curl -i https://kube-vim-gateway/vivnfm/v5/images
# HTTP/1.1 401 Unauthorized
# Www-Authenticate: Bearer realm="kube-vim"

curl -i -H "Authorization: Bearer $TOKEN" https://kube-vim-gateway/vivnfm/v5/images
# HTTP/1.1 200 OK
```

An expired or wrong token returns 401 with `error="invalid_token"`. Kube-VIM logs every
request with the client that sent it.

## Limits

Any valid token gets full access, including the admin API, so give each Kube-VIM its own
audience. Per-operation scopes and certificate-bound tokens (RFC 8705) are planned.
