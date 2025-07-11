<p align="center">
  <img width="150" height="150" alt="logo" src="https://github.com/user-attachments/assets/3545c8ef-fe74-42c4-890e-0becf4f5ae2f" />
</p>

<h1 align="center">Maintainerd</h1>

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

* Each service runs as an **independent microservice**
* Services communicate via **gRPC** and **RabbitMQ/Kafka**
* Each service can use:

  * Its **own database** (`DB_MODE = standalone`)
  * A **shared database** (`DB_MODE = shared`) using **table prefixes** to avoid naming conflicts
* Ideal for distributed, decoupled deployments

#### 🧱 `APP_MODE = mono`

* Deploy multiple services **together in a single container/app**
* Services **share a single database**, reducing duplicated data like `users`, `organizations`, etc.
* Enables tight integration and direct table access between services
* Best for hybrid or gradual microservice adoption

#### 🛡️ Table Prefixing with `DB_TABLE_PREFIX`

To support shared databases without table conflicts:

* Services support a configurable **`DB_TABLE_PREFIX`** variable
* Tables will be named like `auth_users`, `billing_invoices`, etc.
* Prevents name clashes when:

  * Using `DB_MODE = shared`
  * Deploying into a pre-existing database
  * Connecting multiple services to the same schema

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

* ✅ **gRPC** for direct inter-service calls
* ✅ **RabbitMQ** and **Kafka** for event-driven messaging
* ✅ Shared protobuf contracts via [`contract`](https://github.com/maintainerd/contract)
* ✅ Container-ready for Docker/Kubernetes

---

### 📦 Upcoming Modules

We’re actively expanding the ecosystem with more reusable backend components:

* `billing` – Manage payments, subscriptions, invoices
* `inventory` – Products, stock, warehouse tracking
* `task-manager` – Projects, issues, tasks
* `windows-mgmt` – Windows endpoint scripting and automation
* ...more coming soon!

All future modules will:

* Be independently deployable
* Support `mono` and `micro` modes
* Follow consistent APIs and deployment conventions

---

### ✅ Features

* ⚡ Written in **Go** for performance
* 🐳 Fully containerized with Docker
* 🔗 REST + gRPC APIs
* 🔄 Pub/Sub messaging support
* 🔐 Secure by default (JWT, OAuth2)
* 🧠 Configurable via `APP_MODE`, `DB_MODE`, `DB_TABLE_PREFIX`

---

### 🚀 Quick Start

**1. Clone a service (e.g., `auth`):**

```bash
git clone https://github.com/maintainerd/auth.git
cd auth
make build
docker run -p 8080:8080 maintainerd-auth
```

**2. Set your environment variables:**

```env
# Choose between microservice mode or hybrid-monolith mode
APP_MODE=micro         # or mono

# Database mode (micro only)
DB_MODE=standalone     # or shared

# Optional table prefix (for shared DB or name collision prevention)
DB_TABLE_PREFIX=auth_
```

These environment variables ensure flexible deployment in any environment — from isolated containers to tightly integrated backends.

---

### 📚 Documentation

> Full setup guides and architecture docs are coming soon on [maintainerd.dev](https://maintainerd.dev)

For now:

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
