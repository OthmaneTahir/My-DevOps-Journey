<div align="center">

# 📘 00 — What is DevOps & How to Start

![Phase](https://img.shields.io/badge/Phase-1-blue?style=flat-square)
![Topic](https://img.shields.io/badge/Topic-Fundamentals-green?style=flat-square)
![Level](https://img.shields.io/badge/Level-Beginner-yellow?style=flat-square)

</div>

---

## 🌟 What is DevOps?

**DevOps** is a culture, mindset, and set of practices that bring **Development (Dev)** and **Operations (Ops)** teams together to build, test, release, and maintain software faster, more reliably, and with fewer errors.

> 🎯 **The main goal of DevOps:**
> Deliver high-quality software to users as quickly, safely, and reliably as possible.

---

## 🔢 Software Versioning

Applications are usually versioned using **Semantic Versioning (SemVer)**.

```
v1.0.2
```

| Segment | Name | Meaning |
|:-------:|------|---------|
| 🟥 `1` | **Major** | Breaking changes or major releases (new framework, architecture changes, incompatible API changes) |
| 🟨 `0` | **Minor** | New features that remain compatible with previous versions |
| 🟩 `2` | **Patch** | Bug fixes, security fixes, and small improvements |

Example progression:

```
v1.0.0 → v1.1.0 → v1.1.1 → v2.0.0
```

---

## 🔄 The Software Development Lifecycle

Modern software is continuously improved through a cycle like this:

```
💡 Idea
   ↓
👨‍💻 Develop
   ↓
🧪 Test
   ↓
🏗️ Build
   ↓
🚀 Deploy
   ↓
📊 Monitor & Observe
   ↓
📝 Collect Feedback
   ↓
💡 New Idea
```

This loop repeats throughout the life of an application.

Delivering new versions continuously is known as **Continuous Delivery (CD)**, while automatically releasing every validated change to production is called **Continuous Deployment**.

DevOps helps make this cycle:

- ⚡ Faster
- 🛡️ More reliable
- 🐛 Less error-prone
- 🤖 Highly automated

---

## 🧩 Problems DevOps Solves

### 1️⃣ Lack of Collaboration

Traditionally, developers and operations teams worked separately.

- 👨‍💻 Developers focused on creating new features.
- 🖥️ Operations focused on keeping servers stable and available.

This separation often caused poor communication and slower software releases.

> DevOps encourages both teams to collaborate throughout the entire software lifecycle.

---

### 2️⃣ Different Objectives

Developers usually want to release new features quickly. Operations teams want maximum stability and minimum downtime.

**Example:**
Developers release **v2.5** of an application. The new version consumes more CPU and memory than expected. Servers become overloaded. Operations now has to investigate, scale infrastructure, or roll back the release.

Instead of conflicting goals, DevOps aligns everyone around one common objective:

> 🎯 Deliver valuable software quickly **without sacrificing reliability.**

---

### 3️⃣ Security 🔐

Security is another important part of software delivery. Before an application is deployed, security teams verify things such as:

- 🛡️ Vulnerabilities
- 🔑 Secrets management
- 👤 Permissions
- 📋 Compliance
- ⚙️ Secure configurations

Integrating security throughout the DevOps lifecycle is called:

> ### 🔒 DevSecOps

Security becomes everyone's responsibility instead of being added only at the end.

---

### 4️⃣ Testing 🧪

Software must be tested before release. Common types of testing include:

- ✅ Unit Testing
- 🔗 Integration Testing
- 🧭 End-to-End (E2E) Testing
- 📈 Performance Testing
- 🛡️ Security Testing
- 👥 User Acceptance Testing (UAT)

Many tests can be automated, but some scenarios still require manual testing. Automation significantly reduces the time needed for software releases.

---

### 5️⃣ Manual Work 🐌

Manual operations are slow and error-prone. Examples include:

- Deploying applications manually
- Running scripts manually
- Creating servers manually
- Configuring Jenkins jobs manually
- Managing users and permissions manually

**Problems with manual work:**

| ❌ Problem | Impact |
|-----------|--------|
| Slow deployments | Delays releases |
| Human errors | Increases risk |
| Difficult knowledge sharing | Creates silos |
| Poor traceability | Hard to audit |
| Hard to reproduce environments | Inconsistent results |
| Difficult disaster recovery | Longer downtime |

> DevOps replaces repetitive manual work with **automation**.

---

## 🔁 CI/CD

CI/CD is one of the core concepts of DevOps.

### 🟦 Continuous Integration (CI)

Developers frequently merge code into a shared Git repository. Each change automatically triggers:

- 🏗️ Build
- 🧪 Automated tests
- 📏 Code quality checks
- 📦 Packaging

This allows problems to be detected early.

### 🟩 Continuous Delivery (CD)

After a successful build, the application is automatically prepared for deployment. Deployments become:

- 🔁 Repeatable
- 🛡️ Reliable
- ⚡ Fast

The final deployment to production may still require **manual approval**.

### 🟥 Continuous Deployment

Continuous Deployment goes one step further. Every successful change that passes all automated checks is deployed **automatically** to production.

---

## 👷 What Does a DevOps Engineer Do?

A DevOps engineer usually does **not** build the application's business logic. Instead, they **automate everything around the application**.

A DevOps engineer understands:

- 🐧 How developers work
- 🌿 Git workflows
- 🏗️ Build systems
- 🧪 Automated testing
- 🖥️ Infrastructure
- 🚀 Deployment
- 📊 Monitoring
- 🔐 Security
- 🤖 Automation

---

## 🎓 Skills Needed to Become a DevOps Engineer

### 1. 🐧 Linux

Linux is one of the most important skills. You should be comfortable with:

- File system
- Permissions
- Services
- Processes
- Networking
- Bash commands

---

### 2. 🌐 Networking & Security

Understand networking fundamentals such as:

- IP Addressing
- DNS
- HTTP / HTTPS
- SSH
- Firewalls
- Reverse Proxies
- Load Balancers
- SSL/TLS

---

### 3. 📦 Containers

Containers package applications with all their dependencies. The most widely used container platform is:

> **🐳 Docker** — considered a must-have DevOps skill.

---

### 4. 🔁 CI/CD Tools

CI/CD platforms automate software delivery. Popular tools include:

- Jenkins
- GitHub Actions
- GitLab CI/CD
- Azure DevOps Pipelines

**Typical pipeline:**

```
👨‍💻 Developer
      ↓
🌿 Git Repository
      ↓
🏗️ Build
      ↓
🧪 Automated Tests
      ↓
📦 Package Application
      ↓
🐳 Create Docker Image
      ↓
📤 Push Image to Registry
      ↓
🚀 Deploy
      ↓
🔔 Notify Team
```

---

### 5. 🗄️ Artifact Repositories

Build artifacts and Docker images are stored in repositories such as:

- Nexus Repository
- Docker Hub
- GitHub Container Registry (GHCR)
- Amazon ECR

---

### 6. ☁️ Cloud Computing

Modern applications are commonly deployed in the cloud. Popular cloud providers include:

- ![AWS](https://img.shields.io/badge/-AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white) Amazon Web Services
- ![Azure](https://img.shields.io/badge/-Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white) Microsoft Azure
- ![GCP](https://img.shields.io/badge/-GCP-4285F4?style=flat-square&logo=googlecloud&logoColor=white) Google Cloud Platform

> You do not need to master every cloud service — focus on the services commonly used in DevOps.

---

### 7. ⚓ Container Orchestration

Running one container is easy. Running hundreds or thousands requires orchestration.

> The industry standard is **Kubernetes** ☸️ — by far the most in-demand skill.

Other orchestration tools include:

- Docker Swarm
- Nomad

---

### 8. 📊 Monitoring & Observability

After deployment, applications must be monitored. Monitoring helps detect:

- Performance issues
- Errors
- Downtime
- Resource usage

Popular tools include:

- Prometheus
- Grafana
- Nagios

Observability often includes: **Metrics · Logs · Traces**

---

### 9. 🏗️ Infrastructure as Code (IaC)

Instead of manually creating servers and networks, infrastructure is defined as code.

**Provisioning:**
- Terraform

**Configuration Management:**
- Ansible
- Puppet
- Chef

Infrastructure becomes:

- ♻️ Reproducible
- 🌿 Version-controlled
- 🤖 Automated

---

### 10. 📝 Scripting

Automation is a core responsibility of DevOps engineers. Common scripting languages:

- Bash
- Python
- Go (increasingly common)
- PowerShell (especially on Windows)

Scripts automate repetitive daily tasks.

---

### 11. 🌿 Version Control

Almost everything in DevOps is stored as code:

- Infrastructure
- CI/CD pipelines
- Kubernetes manifests
- Dockerfiles
- Scripts

Version control systems include: **Git · GitHub · GitLab · Bitbucket**

> Git is an essential skill for every DevOps engineer.

---

## 🔄 Typical DevOps Workflow

```
👨‍💻 Developer
      ↓
🌿 Git
      ↓
🔁 Continuous Integration
      ↓
🏗️ Build
      ↓
🧪 Automated Testing
      ↓
📦 Package
      ↓
🐳 Docker Image
      ↓
🗄️ Artifact Repository
      ↓
🚀 Deploy
      ↓
☸️ Kubernetes
      ↓
📊 Monitoring
      ↓
📝 Feedback
```

---

## ⚖️ DevOps vs Site Reliability Engineering (SRE)

Although they are closely related, DevOps and SRE are not the same.

| | DevOps | SRE |
|---|--------|-----|
| **Focus** | Culture & practices for collaboration, automation, and delivery | Applying software engineering principles to operations |
| **Origin** | Grew from industry practice | Pioneered by Google |
| **Key concerns** | Communication, CI/CD, automation | Reliability, SLOs, error budgets, incident response, reducing toil |

In many companies, DevOps engineers build and automate delivery platforms, while SREs ensure production systems remain highly reliable. The responsibilities may overlap depending on the organization.

---

## ✅ Key Takeaways

- 🧠 DevOps is about **people, processes, and automation** — not just tools.
- 🤝 Collaboration between Development, Operations, QA, and Security is essential.
- 🔁 CI/CD enables fast and reliable software delivery.
- 🎓 Linux, Git, Networking, Docker, Kubernetes, Cloud, IaC, Monitoring, and Scripting are foundational DevOps skills.
- 🤖 Automation reduces manual work, minimizes errors, and improves consistency.
- 🎯 The ultimate goal is to deliver reliable software to users **quickly, safely, and continuously**.

---

<div align="center">

⬅️ [Back to README](../README.md)

</div>
