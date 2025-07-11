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
* Configured as a **standalone** service or integrated with others
* Customized through environment variables and config files

---

### 🧱 Architecture Modes

`maintainerd` supports two flexible deployment modes:

#### 🧩 `APP_MODE = micro`

* Each service runs as an **independent microservice**
* Services communicate via **gRPC**, **RabbitMQ**, or **Kafka**
* Organizations can choose:

  * A **separate database per service**, or
  * A **shared database across services**
* To prevent table name collisions in a shared DB, set the `DB_TABLE_PREFIX` environment variable (e.g., `auth_`, `billing_`)

> This allows services to run independently while still being flexible enough to integrate into existing systems with shared schemas.

#### 🧱 `APP_MODE = mono`

* Multiple services run in a **single app/container**
* Services **share one database**, avoiding duplication of common tables like `users`, `organizations`, etc.
* Enables direct cross-service queries and tight integration
* Ideal for hybrid deployments or simpler self-hosted stacks

#### 🛡️ Table Prefixing with `DB_TABLE_PREFIX`

To support shared databases without table conflicts:

* Prefix all tables with a unique string per service
* e.g., `auth_users`, `core_services`, `billing_invoices`
* Recommended for both shared microservice deployments and mono mode

---

### 🧩 Current Modules

#### ✅ [`auth`](https://github.com/maintainerd/auth)

Authentication & Authorization Service
A fully featured authentication system with support for:

* **OIDC**, **OAuth2**, and custom flows
* **External Identity Providers** (e.g., Cognito, Auth0)
* **Built-in User System**
* **JWT-based auth**, role-based access, and metadata

> Can be used independently or integrated into `core` or other services.

#### 🧠 [`core`](https://github.com/maintainerd/core)

The **central API** for managing your organization and service configurations.

* Stores **organization data**, service settings, enabled/attached modules
* Acts as the **main API backend** for the frontend web portal
* Communicates with other services to configure them automatically
* Optional but **highly recommended** for managing all services in one place
* Other services can still operate independently without `core`

> Think of it as the **system controller and admin panel API**, not an orchestrator.

---

### 🧰 Microservice Communication

* ✅ **gRPC** for internal communication
* ✅ **RabbitMQ** / **Kafka** for event-driven architecture
* ✅ Shared protobuf contracts via [`contract`](https://github.com/maintainerd/contract)
* ✅ Designed for container orchestration platforms (Docker, Kubernetes, etc.)

---

### 📦 Upcoming Modules

More modules are in development, designed to cover frequently reimplemented backend logic:

* `billing` – Subscriptions, invoices, usage tracking
* `inventory` – Stock management, suppliers, warehousing
* `task-manager` – Projects, issues, and collaboration tools
* `windows-mgmt` – Windows system scripting, RDP sessions, and automation
* ...more soon

Each one will:

* Follow the same architecture principles
* Be distributed as a Docker image
* Support both `micro` and `mono` deployment modes

---

### ✅ Features

* ⚡ Written in **Go** for high performance
* 🐳 Distributed via Docker containers
* 🔗 REST + gRPC APIs
* 🔄 Pub/Sub with RabbitMQ or Kafka
* 🔐 Secure defaults (JWT, OAuth2, HTTPS)
* 🧠 Smart table prefixing via `DB_TABLE_PREFIX`
* 🧩 Modular and configurable by environment variables

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
# Choose between microservice or monolith mode
APP_MODE=micro         # or mono

# Optional table prefix to avoid name collisions
DB_TABLE_PREFIX=auth_
```

---

### 📚 Documentation

> Full setup guides and architecture docs are coming soon on [maintainerd.dev](https://maintainerd.dev)

In the meantime:

* [`auth` Wiki](https://github.com/maintainerd/auth/wiki)
* [`contract`](https://github.com/maintainerd/contract) for shared protobufs

---

### 🤝 Contributing

Want to contribute a new module or improve an existing one?

1. Fork a service
2. Create a feature branch
3. Submit a PR

We welcome:

* New reusable modules
* Performance and security improvements
* Better developer tooling and DX enhancements

---

### 📜 License

MIT License — free to use in commercial and personal projects.

---

### 🌍 Stay Updated

* Follow the [maintainerd GitHub org](https://github.com/maintainerd)
* Star your favorite modules
* Join the discussions and contribute ideas
