# GCP - First 30 Days Plan (Foundation + ACE Prep)

---

## WEEK 1 - Foundations (Core Concepts + First Resources)

### Day 1 (26/03/18) - GCP Overview

### What is GCP

GCP (Google Cloud Platform) is a cloud service provided by Google. 
* Global infrastructure (regions, zones)

**Hands-on**

* Create GCP account
* Create your first project

**Outcome**

* You understand how GCP is structured globally



























<!--
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

# GCP Roadmap - Days 31 to 60 (Architecture Level)

---

## WEEK 5 - Architecture Deep Dive

### Day 31 - Architecture Principles

**Study**

* Well-Architected Framework (GCP version)
* Pillars: reliability, performance, cost, security

**Hands-on**

* Take one of your previous projects and evaluate:

  * What is weak?
  * What would break?

**Outcome**

* You start identifying bad architecture

---

### Day 32 - Design for Reliability

**Study**

* SLI, SLO, SLA
* Error budgets

**Hands-on**

* Define SLOs for your system

**Outcome**

* You think in terms of service quality

---

### Day 33 - High Availability Patterns

**Study**

* Multi-zone vs multi-region
* Active-active vs active-passive

**Hands-on**

* Redesign your app for high availability

**Outcome**

* You design for failure

---

### Day 34 - Disaster Recovery

**Study**

* RTO and RPO
* Backup strategies

**Hands-on**

* Design DR plan for:

  * database
  * application

**Outcome**

* You think about recovery, not just uptime

---

### Day 35 - Performance Optimization

**Study**

* Caching strategies
* CDN usage

**Hands-on**

* Add caching layer (Cloud CDN or Memorystore)

**Outcome**

* You understand performance trade-offs

---

### Day 36 - Cost Optimization

**Study**

* Pricing models
* Preemptible VMs / committed use

**Hands-on**

* Optimize one project for cost

**Outcome**

* You balance performance vs cost

---

### Day 37 - Weekly Review + Architecture Exercise

**Task**

* Design system:

  * highly available
  * cost-efficient
  * scalable

**Outcome**

* You connect all architecture pillars

---

## WEEK 6 - Advanced Networking and Hybrid Cloud

---

### Day 38 - Advanced VPC Design

**Study**

* Custom VPC design
* Subnet strategy

**Hands-on**

* Design production-grade VPC

**Outcome**

* You understand network segmentation deeply

---

### Day 39 - Load Balancing Deep Dive

**Study**

* Global vs regional load balancing
* Layer 4 vs Layer 7

**Hands-on**

* Implement advanced load balancing scenario

**Outcome**

* You choose correct load balancer by use case

---

### Day 40 - Hybrid Connectivity

**Study**

* VPN vs Interconnect
* Latency and throughput considerations

**Outcome**

* You understand hybrid architecture decisions

---

### Day 41 - Identity and Security Architecture

**Study**

* IAM at scale
* Organization policies

**Hands-on**

* Design IAM structure for a company

**Outcome**

* You think in enterprise security terms

---

### Day 42 - Zero Trust and Security Layers

**Study**

* BeyondCorp model
* Defense in depth

**Outcome**

* You understand modern security models

---

### Day 43 - Data Security

**Study**

* Encryption (at rest / in transit)
* Key Management Service (KMS)

**Hands-on**

* Encrypt resources using KMS

**Outcome**

* You design secure data systems

---

### Day 44 - Weekly Review + Scenario Design

**Task**

* Design hybrid architecture:

  * on-prem + GCP

**Outcome**

* You think like enterprise architect

---

## WEEK 7 - Data, Event-Driven and Scalability

---

### Day 45 - Data Architecture

**Study**

* OLTP vs OLAP
* When to use:

  * Cloud SQL
  * Firestore
  * BigQuery

**Outcome**

* You choose the right database

---

### Day 46 - BigQuery Advanced

**Study**

* Partitioning
* Clustering

**Hands-on**

* Optimize queries

**Outcome**

* You think about data performance

---

### Day 47 - Event-Driven Architecture

**Study**

* Pub/Sub patterns
* Event sourcing basics

**Hands-on**

* Build event-driven flow

**Outcome**

* You design asynchronous systems

---

### Day 48 - Microservices vs Monolith

**Study**

* Trade-offs

**Outcome**

* You stop blindly choosing microservices

---

### Day 49 - API Design

**Study**

* REST best practices
* API Gateway

**Hands-on**

* Expose API with proper design

**Outcome**

* You design scalable APIs

---

### Day 50 - Scalability Patterns

**Study**

* Horizontal vs vertical scaling
* Stateless design

**Outcome**

* You design systems that grow

---

### Day 51 - Weekly Review + System Design

**Task**

* Design:

  * scalable
  * event-driven system

**Outcome**

* Architecture thinking becomes natural

---

## WEEK 8 - DevOps, SRE and Final Architect Preparation

---

### Day 52 - CI/CD Advanced

**Study**

* Pipeline strategies
* Blue/Green deployment
* Canary releases

**Hands-on**

* Implement advanced deployment

**Outcome**

* You deploy safely

---

### Day 53 - Infrastructure as Code Advanced

**Study**

* Terraform modules
* State management

**Hands-on**

* Modularize your infrastructure

**Outcome**

* You build reusable infra

---

### Day 54 - Observability Deep Dive

**Study**

* Metrics vs logs vs traces

**Hands-on**

* Improve monitoring dashboard

**Outcome**

* You detect problems early

---

### Day 55 - Incident Management

**Study**

* Incident response
* Postmortems

**Outcome**

* You think like SRE

---

### Day 56 - Governance at Scale

**Study**

* Folder structure strategies
* Policy enforcement

**Outcome**

* You design for large organizations

---

### Day 57 - Full Architecture Project

**Project**

* Design and (partially) implement:

  * scalable
  * secure
  * monitored system

**Outcome**

* Portfolio-level architecture

---

### Day 58 - Case Studies

**Study**

* Real-world architectures
* Analyze decisions

**Outcome**

* You learn from real scenarios

---

### Day 59 - Practice Exam (Architect Level)

* Start Professional-level questions

**Outcome**

* You identify gaps

---

### Day 60 - Final Review + Gap Fixing

* Focus on weak areas

**Outcome**

* You are transitioning into architect level

---

# What you achieve after 60 days

At this point, you are no longer just executing tasks.

You are able to:

* Design systems end-to-end
* Make trade-offs (cost vs performance vs reliability)
* Understand enterprise requirements
* Speak like an architect in projects

---

# Important shift (this is critical)

From now on, always think like this:

Not:

* "Which service do I use?"

But:

* "What problem am I solving?"
* "What are the constraints?"
* "What breaks if this fails?"

---

# GCP Roadmap - Days 61 to 90 (Specialist Level)

---

## WEEK 9 - Specialization Direction (You choose your edge)

At this point, you should **lean toward a primary track**.
Given your background, Architecture + DevOps hybrid is the strongest path.

---

### Day 61 - Define Your Specialization

**Task**

* Choose your primary focus:

  * Architecture (recommended)
  * DevOps/SRE
  * Data

**Hands-on**

* Write a 1-page document:

  * “What kind of GCP specialist am I becoming?”

**Outcome**

* Clear professional positioning

---

### Day 62 - Deep Dive: Architecture Decisions

**Study**

* Trade-offs:

  * Cloud Run vs GKE
  * Cloud SQL vs Firestore
  * Pub/Sub vs direct API

**Task**

* Write decision matrix for each

**Outcome**

* You justify decisions, not guess

---

### Day 63 - Multi-Region Design

**Study**

* Global architecture patterns

**Hands-on**

* Design system across 2+ regions

**Outcome**

* You think globally

---

### Day 64 - Disaster Recovery Advanced

**Study**

* DR patterns:

  * Pilot light
  * Warm standby
  * Active-active

**Task**

* Apply to your system

**Outcome**

* You design for worst-case scenarios

---

### Day 65 - Performance at Scale

**Study**

* Bottleneck analysis

**Hands-on**

* Identify scaling limits in your system

**Outcome**

* You understand system limits

---

### Day 66 - Cost vs Performance Trade-offs

**Task**

* Create 3 versions of the same system:

  * cheapest
  * balanced
  * high performance

**Outcome**

* You think like a business

---

### Day 67 - Weekly Review + Architecture Defense

**Task**

* Present (even if just written):

  * Your system design
  * Why you chose each service

**Outcome**

* You defend your architecture

---

## WEEK 10 - Real-World Scenarios

---

### Day 68 - E-commerce Architecture

**Task**

* Design:

  * high traffic
  * payment system
  * inventory

**Focus**

* scalability
* reliability

---

### Day 69 - Streaming / Event System

**Task**

* Design:

  * real-time data processing

**Focus**

* Pub/Sub
* BigQuery

---

### Day 70 - Enterprise Migration

**Task**

* Migrate:

  * on-prem → GCP

**Focus**

* hybrid connectivity
* risk reduction

---

### Day 71 - SaaS Multi-Tenant System

**Task**

* Design SaaS platform

**Focus**

* isolation
* scaling
* billing

---

### Day 72 - Security-Critical System

**Task**

* Design system with:

  * strict access control
  * audit requirements

**Focus**

* IAM
* encryption
* logging

---

### Day 73 - Failure Scenario Drill

**Task**

* Simulate failures:

  * region down
  * database crash

**Outcome**

* You react like an SRE

---

### Day 74 - Weekly Review

**Task**

* Revisit all designs
* Improve weak areas

**Outcome**

* Iterative improvement mindset

---

## WEEK 11 - Certification + Interview Level Thinking

---

### Day 75 - Professional Exam Strategy

**Study**

* Question patterns:

  * “most cost-effective”
  * “most scalable”
  * “least operational overhead”

**Outcome**

* You learn how questions are framed

---

### Day 76 - Practice Exam (Full)

**Task**

* Simulate real exam

**Outcome**

* Identify gaps

---

### Day 77 - Deep Review of Mistakes

**Task**

* Analyze every wrong answer:

  * Why wrong?
  * What concept missing?

**Outcome**

* Rapid improvement

---

### Day 78 - Weak Areas Focus

**Study**

* Focus only on weak topics

**Outcome**

* Close knowledge gaps

---

### Day 79 - Second Practice Exam

**Task**

* Re-test

**Outcome**

* Measure progress

---

### Day 80 - Architecture Whiteboard Practice

**Task**

* Explain system out loud:

  * like in an interview

**Outcome**

* Communication skill improves

---

### Day 81 - Weekly Review

* Light review + consolidation

---

## WEEK 12 - Final Transformation

---

### Day 82 - Build Your Portfolio Project

**Task**

* Final project:

  * well-architected
  * documented
  * partially implemented

**Outcome**

* Real-world proof of skill

---

### Day 83 - Documentation (Critical)

**Task**

* Write:

  * architecture decisions
  * diagrams
  * trade-offs

**Outcome**

* You stand out professionally

---

### Day 84 - Mock Interview

**Task**

* Answer questions like:

  * “Why did you choose this architecture?”
  * “What happens if this fails?”

**Outcome**

* Interview readiness

---

### Day 85 - Final Cost Optimization Pass

**Task**

* Review your system:

  * reduce unnecessary cost

**Outcome**

* Business awareness

---

### Day 86 - Security Review

**Task**

* Review:

  * IAM
  * network
  * data protection

**Outcome**

* Enterprise-level thinking

---

### Day 87 - Final Practice Exam

**Task**

* Full simulation

---

### Day 88 - Light Review

* No heavy study
* Focus on clarity

---

### Day 89 - Mental Preparation

* Review key patterns:

  * scalability
  * reliability
  * cost

---

### Day 90 - Ready for Certification

At this point, you should be ready for:

* Professional Cloud Architect
  or
* Very strong performance in real-world scenarios

---

# What you become after 90 days

If you followed this seriously, you are now:

* Capable of designing production-grade systems
* Able to justify decisions clearly
* Comfortable with enterprise scenarios
* Ready for high-level interviews

---

# Final mindset shift

At expert level, everything becomes about trade-offs:

* There is no “best service”
* Only the best decision for a context

-->
