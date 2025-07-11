<h1 align="center">maintainerd</h1>

**maintainerd** is a collection of production-ready, containerized backend services written in Go — designed to be deployed instantly as standalone applications or as part of a high-performance microservices system.

Each service is maintained under its own repository and versioned independently, allowing organizations to pick only what they need.

---

### ⚙️ Overview

The goal of `maintainerd` is to **eliminate redundant backend development** across organizations by offering **ready-to-deploy, configurable services** that handle essential business logic — so teams can focus on their product, not reinventing the backend.

Each module can be:

* Deployed as a **monolith** or **microservice**
* Configured as a **standalone** service or integrated with other modules
* Customized through environment variables or config files

**Current public services include:**

* [`auth`](https://github.com/maintainerd/auth): User authentication, OAuth2, OIDC, and external identity support
* [`core`](https://github.com/maintainerd/core): Main orchestration and REST+gRPC entrypoint
* [`contract`](https://github.com/maintainerd/contract): Shared gRPC/protobuf definitions for all services

---

### 🧩 Microservice Architecture

All `maintainerd` services are built with **inter-service communication and messaging in mind**:

* 🛰 **gRPC** for internal service-to-service communication
* 📬 **RabbitMQ** or **Kafka** for async event-driven communication
* ⚙️ Each service runs as an isolated Docker container, but supports service discovery and orchestration
* 🔗 Common `.proto` contracts are shared via the [`contract`](https://github.com/maintainerd/contract) submodule

---

### 🔐 Current Module: `auth`

A flexible and powerful authentication system supporting:

* ✅ **OIDC** and **OAuth2** protocols
* ✅ **Built-in user management system**
* ✅ **External identity provider integration** (Cognito, Auth0, etc.)
* ✅ **JWT** support with scopes, roles, and metadata
* ✅ REST + gRPC APIs

Use it as:

* A **primary auth system** for your org
* A **bridge to existing identity providers**

---

### 🧠 `core` Service

The gateway and orchestrator for your services:

* Exposes **REST APIs** for client interaction
* Connects to internal modules via **gRPC**
* Integrates with the `auth` module out-of-the-box
* Supports future modules like billing, inventory, and more

---

### 📦 Upcoming Modules

We’re actively expanding the maintained module catalog:

* `billing` – Manage subscriptions, usage, invoicing
* `inventory` – Track assets, stock levels, warehouse activity
* `task-manager` – Projects, task flow, and collaboration tools
* `windows-mgmt` – Tools for managing Windows hosts (RDP, script automation, etc.)

Each module will:

* Be containerized and production-ready
* Integrate seamlessly with existing `maintainerd` services
* Follow a consistent API and config design

---

### 🧰 Features at a Glance

* ✅ Built in **Go** for performance, concurrency, and reliability
* ✅ Fully containerized with **Docker**
* ✅ Plug-and-play architecture with minimal configuration
* ✅ **REST + gRPC APIs** for modern integration
* ✅ Native support for **RabbitMQ** and **Kafka**
* ✅ Secure defaults (TLS, OAuth2, JWT)
* ✅ Production-ready with metrics, health checks, and structured logging

---

### 🚀 Getting Started

**1. Clone any module (e.g. auth):**

```bash
git clone https://github.com/maintainerd/auth.git
cd auth
make build
docker run -p 8080:8080 maintainerd-auth
```

**2. Integrate with `core`**

```bash
git clone https://github.com/maintainerd/core.git
```

Each service comes with its own documentation and Makefile.

---

### 📚 Documentation

> Full docs for setup, deployment, APIs, and architecture coming soon at [maintainerd.dev](https://maintainerd.dev) *(under development)*

In the meantime, see:

* [Wiki](https://github.com/maintainerd/auth/wiki) for auth setup
* [contract](https://github.com/maintainerd/contract) for protobuf definitions

---

### 🤝 Contributing

Want to contribute a module or help improve existing ones?

1. Fork a service repo
2. Create a feature branch
3. Open a pull request

We welcome external contributions, especially for:

* Bug fixes
* Feature ideas
* New maintained modules

---

### 📜 License

MIT License — freely usable for commercial and personal projects.

---

### 🌍 Stay Updated

Watch the [maintainerd organization](https://github.com/maintainerd) to follow all service releases and new module announcements.

---

Let me know if you'd like:

* A matching `README.md` generated
* Badges for Docker Hub, Go Report Card, CI status
* A landing page layout for your [maintainerd.dev](https://maintainerd.dev) in case you want to make it public soon
