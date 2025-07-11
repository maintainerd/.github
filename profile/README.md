<p align="center">
  <img width="150" height="150" alt="logo" src="https://github.com/user-attachments/assets/3545c8ef-fe74-42c4-890e-0becf4f5ae2f" />
</p>

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

---

### 🧱 Architecture Modes

`maintainerd` supports two high-level application modes:

#### 🧩 `APP_MODE = micro`

* Each service runs as an **independent microservice**.
* Services communicate via **gRPC** and **RabbitMQ/Kafka**.
* Each service can use:

  * Its **own database** (`DB_MODE = standalone`), or
  * A **shared database** (`DB_MODE = shared`) using **table prefixes** to avoid naming conflicts.
* Suitable for scalable, modular deployments.

#### 🧱 `APP_MODE = mono`

* Deploy multiple services **together in a single container/app**.
* Services **share a single database**, eliminating data duplication (e.g., shared `users`, `organization`, etc.).
* Allows cross-service queries and tight integration.
* Useful for hybrid monolith-microservice deployments — perfect for medium-scale orgs or those migrating gradually.

#### 🛡️ Table Prefixing

To support shared databases without table collisions:

* All services support a configurable **table prefix**.
* This is useful when:

  * Deploying multiple services into the same schema
  * Avoiding name conflicts with existing organizational tables
  * Running in `DB_MODE = shared` (only supported in `micro` mode)

---

### 🧩 Current Modules

#### ✅ [`auth`](https://github.com/maintainerd/auth)

Authentication & Authorization Service
A fully featured authentication system with support for:

* **OIDC**, **OAuth2**, and custom flows
* **External Identity Providers**: Connect to Cognito, Auth0, etc.
* **Internal User System**: Use `maintainerd-auth`'s built-in database
* **JWT-based access control**, roles, and metadata

> Can serve as your **primary auth system** or integrate with external providers.

#### 🧠 [`core`](https://github.com/maintainerd/core)

Acts as the central orchestrator and API gateway for all modules:

* Exposes unified REST + gRPC APIs
* Handles coordination across services like `auth`
* Can be deployed in `mono` or `micro` mode

---

### 🧰 Microservice Communication

* ✅ **gRPC** for direct inter-service requests
* ✅ **RabbitMQ** and **Kafka** for event-driven architecture
* ✅ Optional shared protobuf contracts via [`contract`](https://github.com/maintainerd/contract)
* ✅ Compatible with container orchestration (Docker, Kubernetes)

---

### 📦 Upcoming Modules

We’re actively expanding the ecosystem with more reusable backend components:

* `billing` – Manage payments, subscriptions, invoices
* `inventory` – Products, stocks, warehousing
* `task-manager` – Projects, issues, tasks
* `windows-mgmt` – Windows endpoint scripting and automation
* ...more coming soon!

All future modules:

* Will be deployable as standalone microservices
* Will support both `mono` and `micro` modes
* Will follow consistent APIs and architecture

---

### ✅ Features

* ⚡ Written in **Go** for performance
* 🐳 Distributed via Docker images
* 🔗 REST + gRPC APIs
* 🎯 Pluggable into existing systems
* 🔐 Secure by default (JWT, OAuth2)
* 🧠 Designed for reusability, modularity, and extensibility
* 🛠 Supports `APP_MODE` and `DB_MODE` for flexible deployments

---

### 🚀 Quick Start

**1. Clone a service (e.g., `auth`):**

```bash
git clone https://github.com/maintainerd/auth.git
cd auth
make build
docker run -p 8080:8080 maintainerd-auth
```

**2. Choose your mode (via env):**

```env
APP_MODE=micro       # or mono
DB_MODE=standalone   # or shared (micro only)
TABLE_PREFIX=auth_
```

---

### 📚 Documentation

> Full setup guides and architecture docs are coming soon on [maintainerd.dev](https://maintainerd.dev)

Until then:

* [`auth` Wiki](https://github.com/maintainerd/auth/wiki)
* [`contract`](https://github.com/maintainerd/contract) for shared protobufs

---

### 🤝 Contributing

Want to contribute a new service or help improve existing ones?

1. Fork a module repo
2. Create a feature branch
3. Submit a PR

We welcome:

* New modules (e.g., HR, CRM, support, chat)
* Bug fixes & security patches
* Performance improvements

---

### 📜 License

MIT License — use freely for commercial and personal projects.

---

### 🌍 Stay Updated

* Watch the [GitHub org](https://github.com/maintainerd)
* Star and follow modules you use
* Open issues or discussions to request new modules
