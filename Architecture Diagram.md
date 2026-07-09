# AWS Secrets Manager for Secure Credential Storage

## Overview

This project demonstrates how to securely store and manage sensitive credentials such as **database usernames**, **passwords**, **API keys**, and **application secrets** using **AWS Secrets Manager**.

The solution eliminates hardcoded credentials, enables automated secret rotation, and provides secure access through IAM policies, significantly improving cloud security and compliance.

---

# Architecture Diagram

```mermaid
flowchart TD

A[Application / Lambda / EC2]

A --> B[AWS Secrets Manager]

B --> C[Database Credentials]

B --> D[API Keys]

B --> E[Application Secrets]

C --> F[Amazon RDS]

B --> G[Automatic Rotation]

G --> H[AWS Lambda Rotation Function]

H --> F

A --> I[IAM Role / IAM Policy]

I --> B
```

---

# High-Level Architecture

```text
Application / EC2 / Lambda
          │
          ▼
IAM Role / IAM Policy
          │
          ▼
AWS Secrets Manager
          │
 ┌────────┼─────────┐
 │        │         │
 ▼        ▼         ▼
DB Credentials API Keys App Secrets
          │
          ▼
Amazon RDS
          │
          ▼
Automatic Secret Rotation
          │
          ▼
Lambda Function
```

---

# Solution Workflow

```mermaid
flowchart LR

A[Create Secret]

A --> B[Store Credentials]

B --> C[Assign IAM Permissions]

C --> D[Application Requests Secret]

D --> E[Secrets Manager]

E --> F[Returns Secret Securely]

F --> G[Application Connects to Database]
```
