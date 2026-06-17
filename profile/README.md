<p align="center">
  <img width="96" height="96" alt="Maintainerd logo" src="https://maintainerd.github.io/assets/maintainerd-mark.svg" />
</p>

<h1 align="center">Maintainerd</h1>

<p align="center">
  <strong>Open-source, self-hostable cloud services for app teams.</strong>
</p>

<p align="center">
  Maintainerd gives developers cloud-style product and platform services they can inspect, run, and own themselves.
  Use each service standalone, or connect them through <strong>M9d-Core</strong> for a shared control plane.
</p>

<p align="center">
  <a href="https://maintainerd.github.io/">Website</a>
  |
  <a href="https://github.com/maintainerd">GitHub</a>
  |
  <a href="https://github.com/maintainerd/maintainerd-auth">M9d-Auth</a>
</p>

---

## What Maintainerd Is

Maintainerd is an open-source ecosystem of reusable services that teams repeatedly rebuild when creating modern applications. It is closer to a self-hostable cloud product suite than a traditional deployment tool.

Maintainerd does not try to be AWS, Google Cloud, or a VM provider. You bring your own infrastructure, Docker host, Kubernetes cluster, database engine, or cloud account. Maintainerd provides the product and platform services that can run on top of that environment.

Each service is designed to be:

- Standalone first, so teams can adopt only what they need.
- Self-hostable, so organizations keep control of runtime, data, and deployment.
- Open source, so developers can inspect, extend, and contribute.
- Ecosystem-ready, so services can connect through M9d-Core when a shared control plane is useful.

## How The Ecosystem Fits Together

M9d-Core is the control plane for the Maintainerd ecosystem. It manages tenants, registered services, health, topology, and high-level operations. It does not directly provision infrastructure. Provisioning and runtime work belong to provider services such as M9d-Docker, M9d-Kubernetes, M9d-Database, and M9d-Domains.

The model is simple:

- Use one Maintainerd service by itself when you only need that product.
- Connect multiple services through M9d-Core when you want shared visibility and control.
- Plug into existing infrastructure instead of replacing your cloud, database, or orchestration platform.

## Service Catalog

### In Development

| Service | Status | Purpose |
| --- | --- | --- |
| [M9d-Auth](https://github.com/maintainerd/maintainerd-auth) | Ongoing development. No public release yet. Estimated first release: `v0.1.0` around July 14, 2026. | Identity and access management. Includes the auth backend, an admin/developer console, and a public identity interface for login, OAuth2, MFA, consent, account flows, permissions, and policies. |

### Planned And Idea-Stage Services

| Area | Services |
| --- | --- |
| Control plane | M9d-Core, M9d-Domains, M9d-Docker, M9d-Kubernetes, M9d-Database |
| Identity and security | M9d-Auth, M9d-Secret, M9d-Gateway |
| Application products | M9d-Storage, M9d-Drive, M9d-Messaging, M9d-CMS |
| Operations and business | M9d-Workflow, M9d-Jobs, M9d-Observability, M9d-Billing, M9d-Project, M9d-Support |

These services are not all built yet. The catalog represents the direction of Maintainerd: commonly repeated product and platform capabilities that should be reusable, self-hostable, and able to work together when needed.

## Current Focus

The first service under active development is M9d-Auth.

M9d-Auth is the IAM foundation for Maintainerd. It owns authentication, authorization, permissions, policies, identity providers, OAuth2/OIDC flows, developer-facing management, and public-facing identity experiences. It has no public release yet; the estimated first release is `v0.1.0` around July 14, 2026.

The Auth product is split into focused parts:

- `maintainerd-auth`: backend service.
- `maintainerd-auth-console`: admin and developer management console.
- `maintainerd-auth-identity`: public identity interface for login, OAuth2, account, MFA, and consent flows.

## Deployment Philosophy

Maintainerd services are distributed as containers and are designed to run on infrastructure you control.

Example:

```bash
docker pull maintainerd/maintainerd-auth
```

Future services will follow the same approach:

```bash
docker pull maintainerd/maintainerd-core
docker pull maintainerd/maintainerd-docker
docker pull maintainerd/maintainerd-kubernetes
```

## Contributing

Maintainerd is early and open to contributors who care about reusable application infrastructure, self-hostable products, identity, control planes, and developer experience.

Useful ways to contribute:

- Improve M9d-Auth and its console.
- Help define clear service boundaries.
- Build SDKs, examples, and deployment templates.
- Review security, identity, and authorization behavior.
- Discuss planned services and real-world use cases.

## Links

- Website: https://maintainerd.github.io/
- Organization: https://github.com/maintainerd
- Current service in development: https://github.com/maintainerd/maintainerd-auth
