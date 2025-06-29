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

![ET HLD](https://github.com/user-attachments/assets/33baf7a5-e24d-4198-b2b0-16210f600715)





## 🧪 Running Locally

```bash
# Step 1: Clone the repository
git clone https://github.com/GAUTAMJBITS/ExpenseTracker.git
cd expense-tracker-microservices

# Step 2: Start required services
docker-compose up -d  # (includes MongoDB, Kafka, Kong, services)

# Step 3: Access services
Kong Gateway: http://localhost:8000
