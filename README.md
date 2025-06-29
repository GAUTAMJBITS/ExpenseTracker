# ExpenseTracker
React-Native + SpringBoot Microservices


---

## ⚙️ Tech Stack

### 🖥️ Backend (Microservices)
- Spring Boot
- MongoDB
- Apache Kafka
- Kong API Gateway
- Eureka (optional for discovery)

### 📱 Frontend
- React Native (or Flutter)

### 🧪 DevOps
- Docker
- GitHub Actions / Jenkins (optional CI/CD)
- Prometheus + Grafana (monitoring)
- ELK / Loki (centralized logging)

---

## 🚀 Features

### ✅ Functional Requirements
- **User Authentication**
  - Email/password login with JWT token issuance
- **Expense Management**
  - Add, update, delete, and view categorized expenses
- **User Profile**
  - View and update user details
- **API Gateway**
  - Centralized routing, rate limiting, authentication
- **Event Communication**
  - Kafka-based event-driven architecture

### 🛡️ Non-Functional Requirements
- High scalability and availability
- Secure API communication (HTTPS, JWT)
- Centralized monitoring and logging
- Modular and independently deployable services

---

## 🧪 Microservices

| Service         | Port | Responsibilities                         |
|-----------------|------|------------------------------------------|
| Auth Service    | 8081 | Register/Login, JWT generation           |
| User Service    | 8082 | Profile management                       |
| Expense Service | 8083 | Expense CRUD operations                  |
| DS Service      | 8084 | Intermediate data transformation layer   |

---

## 🔄 Kafka Topics

| Event Type         | Topic Name           |
|--------------------|----------------------|
| User Registration  | `user_created`       |
| Login Event        | `login_success`      |
| Expense Added      | `expense_added`      |

---

```bash

![ET HLD](https://github.com/user-attachments/assets/33baf7a5-e24d-4198-b2b0-16210f600715)

```



## 🧪 Running Locally

```bash
# Step 1: Clone the repository
git clone https://github.com/GAUTAMJBITS/ExpenseTracker.git
cd expense-tracker-microservices

# Step 2: Start required services
docker-compose up -d  # (includes MongoDB, Kafka, Kong, services)

# Step 3: Access services
Kong Gateway: http://localhost:8000
```

---
# Software Requirements Specification (SRS)
---


# 1. Introduction
1.1 Purpose
The purpose of this document is to define the software requirements for a Mobile-first Expense Tracker Application that allows users to record, view, and manage personal expenses securely. The system is built using microservices, supporting scalability and modular deployment.
1.2 Scope
The application consists of:
- A mobile frontend
- A backend built using Spring Boot microservices:
  - Auth Service
  - User Service
  - Expense Service
  - DS (Data Sync) Service
- API Gateway using Kong
- Event-driven communication using Apache Kafka
- MongoDB for data storage
1.3 Definitions
- API Gateway: Kong gateway managing all API traffic
- Kafka: Message broker for asynchronous communication
- JWT: JSON Web Tokens for stateless authentication
2. Overall Description
2.1 Product Perspective
This application is a standalone system comprising modular microservices. It is designed to run in a containerized environment (e.g., Docker/Kubernetes).
2.2 User Classes
- End Users: Interact via mobile app to manage expenses
- Admin: May be added later for system monitoring
2.3 Operating Environment
Mobile App: Android/iOS
Backend: Spring Boot Microservices
Databases: MongoDB (NoSQL)
Broker: Apache Kafka
Gateway: Kong
Hosting: Cloud-native (AWS/GCP) or local Docker
3. Functional Requirements
FR-1: Users can register using email/password
FR-2: Auth service issues JWT tokens
FR-3: Kong validates tokens before routing requests
FR-4: Users can add/edit/delete expenses
FR-5: Users can view expenses by date/category
FR-6: Expense service stores data in MongoDB
FR-7: User service manages user info (name, email)
FR-8: User data is stored in user-service DB
FR-9: Auth service produces login/registration events
FR-10: Expense and User services consume relevant Kafka topics
FR-11: Kong handles routing, rate limiting, logging
4. Non-Functional Requirements
NFR-1: Average API response time < 300ms
NFR-2: Should handle 1000+ concurrent users
NFR-3: Services must scale independently
NFR-4: Kafka supports event-driven scaling
NFR-5: All APIs use HTTPS
NFR-6: JWT tokens used for secure access
NFR-7: Input validation to prevent XSS/SQLi
NFR-8: Modular microservice design
NFR-9: Version-controlled APIs (v1, v2)
NFR-10: Centralized logging with ELK/Loki
NFR-11: Metrics exposed to Prometheus
5. System Architecture (HLD Overview)
Components:
- Mobile App
- Kong Gateway
- Auth Service → MongoDB
- User Service → MongoDB
- Expense Service → MongoDB
- DS Service
- Kafka Broker
6. External Interfaces
6.1 API Interface
RESTful APIs over HTTP
Swagger/OpenAPI documentation for each service
6.2 Database Interface
MongoDB accessed via Spring Data Mongo
6.3 Messaging Interface
Kafka topics for user_created, login_success, expense_added
7. Assumptions and Dependencies
Docker environment is available
Kong gateway is pre-configured
Kafka and MongoDB are up and running
Mobile app is available and follows API contract
