# 🚀 GCP Roadmap - From Zero to Specialist

## PHASE 1 - Fundamentals (Solid Foundation)

Goal: understand **how GCP works internally**

### Core concepts

* Resource hierarchy:

  * Organization
  * Folder
  * Project
* Billing and cost control
* IAM (Identity and Access Management)
* Regions, zones, and latency

### Core services

* Compute:

  * Compute Engine (VMs)
* Storage:

  * Cloud Storage (buckets, storage classes)
* Networking:

  * VPC (subnets, firewall rules)

### Practical goal

* Create a GCP project
* Launch a VM
* Create a bucket and upload files
* Configure basic networking

---

## PHASE 2 - Core Cloud (You start “working” with GCP)

Goal: move from basics to real-world usage

### Advanced compute

* GKE (Kubernetes on GCP)
* Cloud Run (serverless containers)
* App Engine

### Data

* Cloud SQL
* Firestore
* BigQuery (**very important**)

### Integration & events

* Pub/Sub
* Cloud Functions

### Security

* Advanced IAM
* Service Accounts
* Secret Manager

### Practical goal

* Deploy an application:

  * API + database
* Build a simple event pipeline with Pub/Sub
* Use BigQuery for analytics

---

## PHASE 3 - Architecture & Best Practices

Goal: start thinking like an architect

### Cloud architecture

* High Availability (HA)
* Fault Tolerance
* Horizontal scalability
* Multi-region design

### Advanced networking

* VPC Peering
* Shared VPC
* Load Balancing
* Cloud CDN

### Hybrid connectivity

* VPN
* Interconnect
* Concepts like:

  * Network overlap
  * BGP (dynamic routing)

### Practical goal

* Design a resilient system
* Build a multi-tier architecture (frontend + backend + DB)
* Simulate failure and failover

---

## PHASE 4 - DevOps & Automation (Where you stand out)

Goal: operate at scale

### CI/CD

* Cloud Build
* Artifact Registry

### Infrastructure as Code

* Terraform (**ESSENTIAL**)
* Deployment Manager

### Observability

* Cloud Logging
* Cloud Monitoring
* Error Reporting

### SRE mindset

* SLI / SLO / SLA
* Incident management

### Practical goal

* Build a full pipeline:

  * build → deploy automatically
* Monitor an application with alerts

---

## PHASE 5 - Security, Governance & Costs (Enterprise level)

Goal: think like a large organization

### Security

* VPC Service Controls
* Organization Policies
* Cloud Armor

### FinOps

* Billing export
* Cost optimization
* Rightsizing

### Compliance

* PCI
* Auditing (Cloud Audit Logs)

### Practical goal

* Build a secure environment with restrictions
* Optimize the cost of an existing architecture

---

## PHASE 6 - Specialization (Become a true expert)

### Option 1 - Architecture (Recommended for you)

* Complex solution design
* Multi-cloud / hybrid environments
* Disaster Recovery (DR)

Certification:

* **Professional Cloud Architect**

---

### Option 2 - DevOps / SRE

* Heavy automation
* Deep observability
* Resilience engineering

Certification:

* **Professional Cloud DevOps Engineer**

---

### Option 3 - Data / AI

* Advanced BigQuery
* Dataflow
* Machine Learning

Certification:

* **Professional Data Engineer**

---

# Recommended certification order

1. **Associate Cloud Engineer**
2. **Professional Cloud Architect**
3. (Optional later)

   * DevOps Engineer
   * Data Engineer

---

# How to study (realistic strategy)

### Ideal cycle

1. Study theory (brief)
2. Practice (a lot)
3. Build real projects
4. Document everything (this is a huge differentiator)

---

# Projects that will make you stand out

* A system with:

  * API (Cloud Run)
  * Database (Cloud SQL)
  * Cache (Memorystore)
* Data pipeline with BigQuery
* 100% infrastructure via Terraform
* Highly available multi-region system

---

# GCP - First 30 Days Plan (Foundation + ACE Prep)

---

## WEEK 1 - Foundations (Core Concepts + First Resources)

### Day 1 - GCP Overview

**Study**

* What is GCP
* Global infrastructure (regions, zones)

**Hands-on**

* Create GCP account
* Create your first project

**Outcome**

* You understand how GCP is structured globally

---

### Day 2 - Resource Hierarchy

**Study**

* Organization, Folder, Project
* Billing basics

**Hands-on**

* Link billing account
* Create 2–3 projects (for testing separation)

**Outcome**

* You understand how companies organize GCP

---

### Day 3 - IAM Basics

**Study**

* IAM roles (Owner, Editor, Viewer)
* Principle of least privilege

**Hands-on**

* Create a new user (or service account)
* Assign roles

**Outcome**

* You understand access control

---

### Day 4 - Compute Engine (VMs)

**Study**

* VM basics
* Machine types

**Hands-on**

* Create a VM
* SSH into it

**Outcome**

* You can run workloads in GCP

---

### Day 5 - Storage

**Study**

* Cloud Storage
* Storage classes

**Hands-on**

* Create bucket
* Upload/download files

**Outcome**

* You understand object storage

---

### Day 6 - Networking Basics

**Study**

* VPC
* Subnets
* Firewall rules

**Hands-on**

* Create custom VPC
* Open SSH/HTTP ports

**Outcome**

* You understand how traffic flows

---

### Day 7 - Review + Mini Project

**Project**

* VM + Web Server + Storage

**Hands-on**

* Deploy a simple web server on VM
* Store static files in bucket

**Outcome**

* First working architecture

---

## 🗓️ WEEK 2 - Core Services (Real Usage)

---

### Day 8 - Cloud Run (Serverless)

**Study**

* What is serverless
* When to use Cloud Run

**Hands-on**

* Deploy a containerized app

**Outcome**

* You understand modern deployment

---

### Day 9 - App Engine vs Cloud Run

**Study**

* Differences and use cases

**Hands-on**

* Deploy simple app on App Engine

**Outcome**

* You can compare services

---

### Day 10 - Cloud SQL

**Study**

* Managed databases

**Hands-on**

* Create instance
* Connect from VM or app

**Outcome**

* You understand managed DB

---

### Day 11 - Firestore

**Study**

* NoSQL basics

**Hands-on**

* Create database
* Insert/query data

**Outcome**

* You understand NoSQL in GCP

---

### Day 12 - BigQuery

**Study**

* Data warehouse concept

**Hands-on**

* Run SQL queries on public dataset

**Outcome**

* You understand analytics layer

---

### Day 13 - Pub/Sub

**Study**

* Event-driven architecture

**Hands-on**

* Create topic + subscription
* Send/receive messages

**Outcome**

* You understand async systems

---

### Day 14 - Review + Mini Project

**Project**

* API + DB + Messaging

**Hands-on**

* App → Pub/Sub → Consumer → DB

**Outcome**

* You understand event-driven flow

---

## 🗓️ WEEK 3 - Architecture + Networking

---

### Day 15 - Load Balancing

**Study**

* Types of load balancers

**Hands-on**

* Create HTTP Load Balancer

**Outcome**

* You understand scaling entry point

---

### Day 16 - Auto Scaling

**Study**

* Instance groups

**Hands-on**

* Create managed instance group

**Outcome**

* You understand elasticity

---

### Day 17 - Advanced Networking

**Study**

* VPC Peering
* Shared VPC

**Hands-on**

* Connect two VPCs

**Outcome**

* You understand network segmentation

---

### Day 18 - Hybrid Connectivity (Conceptual)

**Study**

* VPN
* Interconnect
* BGP basics

**Outcome**

* You understand enterprise networking

---

### Day 19 - High Availability

**Study**

* Multi-zone vs multi-region

**Hands-on**

* Deploy app across zones

**Outcome**

* You understand resilience

---

### Day 20 - Review + Architecture Design

**Task**

* Design system:

  * scalable
  * fault tolerant

**Outcome**

* Thinking like architect starts here

---

### Day 21 - Practice Tests (Light)

**Study**

* Start ACE sample questions

**Outcome**

* Identify weak points

---

## 🗓️ WEEK 4 - DevOps + Final Preparation

---

### Day 22 - Cloud Build (CI/CD)

**Study**

* CI/CD basics

**Hands-on**

* Create simple pipeline

**Outcome**

* You understand automation

---

### Day 23 - Terraform (Intro)

**Study**

* IaC concepts

**Hands-on**

* Create VM using Terraform

**Outcome**

* You start automating infra

---

### Day 24 - Monitoring & Logging

**Study**

* Cloud Monitoring
* Logging

**Hands-on**

* Create alert

**Outcome**

* You understand observability

---

### Day 25 - IAM Advanced

**Study**

* Custom roles
* Service accounts deeper

**Outcome**

* Security maturity increases

---

### Day 26 - Cost Management

**Study**

* Billing reports
* Budgets

**Hands-on**

* Set budget alert

**Outcome**

* You avoid real-world mistakes

---

### Day 27 - Full Project

**Project**

* Cloud Run + DB + Pub/Sub + Monitoring

**Outcome**

* End-to-end system

---

### Day 28 - Full Review

* Go over weak topics

---

### Day 29 - Practice Exam (Full)

* Simulate real exam

---

### Day 30 - Final Prep

* Light review
* Focus on:

  * IAM
  * Networking
  * Use cases

---

# 🧠 What you’ll achieve in 30 days

If you follow this seriously:

[x] Solid GCP foundation
[x] Real hands-on experience
[x] Ready (or very close) for **ACE certification**
[x] Already thinking beyond junior level

---




























