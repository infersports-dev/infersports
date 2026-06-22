# Security Policy

InferSports is a **read-only** odds & scores service. This repository contains only public client
material — an OpenAPI contract, documentation, and agent-integration files. It holds **no
credentials, no data-ingestion code, and no server source**.

## Reporting a vulnerability

Please report suspected security issues privately to **security@infersports.dev**. We aim to
acknowledge within 3 business days. Please do not open a public issue for security reports.

## Scope

- **In scope:** the public API surface at `https://api.infersports.dev` and the contents of this
  repository.
- **Out of scope:** denial-of-service or load testing against the live API, and anything requiring
  access to non-public infrastructure.

## Data handling

The Free tier is keyless and returns only public odds and scores — no personal data is required to
use it. An optional `isk_…` API key is a bearer credential: keep it secret, and rotate it from your
account dashboard if it is exposed.
