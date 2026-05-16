<div align="center">

# 💪 AI-Powered Fitness Platform

### Smart Fitness Platform — Microservices Architecture

> A full-scale, cloud-native fitness management platform built using **Spring Boot microservices**. Demonstrates distributed systems design, event-driven communication, secure authentication, and modern DevOps practices.

<br/>

<img src="https://img.shields.io/badge/Java-17+-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white"/>
<img src="https://img.shields.io/badge/Spring_Boot-3.2-6DB33F?style=for-the-badge&logo=springboot&logoColor=white"/>
<img src="https://img.shields.io/badge/Apache_Kafka-3.x-231F20?style=for-the-badge&logo=apachekafka&logoColor=white"/>
<img src="https://img.shields.io/badge/Keycloak-OAuth2-4A4A55?style=for-the-badge&logo=keycloak&logoColor=white"/>
<img src="https://img.shields.io/badge/MongoDB-6.0-47A248?style=for-the-badge&logo=mongodb&logoColor=white"/>
<img src="https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/>
<img src="https://img.shields.io/badge/Docker-Compose-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
<img src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge"/>

<br/><br/>

</div>

---

## 📌 Repository Description

> **AI-Powered Fitness Platform** is a microservices-based fitness management platform built using **Java 17**, **Spring Boot 3.2**, and secure distributed architecture. The system features multiple independent services communicating via **API Gateway** and **Apache Kafka**, with full **OAuth2 authentication using Keycloak**, database integration, and **Docker Compose** orchestration.

---

## 📦 Microservices

| # | Service | Port | Responsibility | Key Tech |
|---|---------|------|----------------|----------|
| 1 | **API Gateway** | 8080 | Single entry point, request routing | API Gateway |
| 2 | **Eureka Server** | 8761 | Service discovery & registration | Eureka |
| 3 | **Auth Service** | 8081 | Login, signup, OAuth2 security | Keycloak, OAuth2 |
| 4 | **User Service** | 8082 | User profiles and health details | MySQL |
| 5 | **Workout Service** | 8083 | Workout plans and activity tracking | MongoDB |
| 6 | **Nutrition Service** | 8084 | Diet and nutrition records | MongoDB |
| 7 | **AI Recommendation Service** | 8085 | AI-based workout and diet suggestions | Google API |
| 8 | **Notification Service** | 8086 | Event-based notifications | Kafka |

------

## 🛠 Tech Stack

<table>
<tr><td><strong>Core</strong></td><td>Java 17, Spring Boot 3.2, Maven</td></tr>
<tr><td><strong>Microservices</strong></td><td>API Gateway, Eureka Server</td></tr>
<tr><td><strong>Security</strong></td><td>Keycloak, OAuth2</td></tr>
<tr><td><strong>Messaging</strong></td><td>Apache Kafka (async events)</td></tr>
<tr><td><strong>Persistence</strong></td><td>MongoDB, MySQL</td></tr>
<tr><td><strong>Frontend</strong></td><td>React.js</td></tr>
<tr><td><strong>DevOps</strong></td><td>Docker, Docker Compose</td></tr>
<tr><td><strong>Tools</strong></td><td>Postman, IntelliJ IDEA, Google API Key</td></tr>
</table>

---

## 🗃 Database Design

Each service owns its own database schema:

```text
 user_db
 └── users              (id, name, email, password, role)

 workout_db
 └── workouts           (id, user_id, type, duration, calories)

 nutrition_db
 └── meals              (id, user_id, food_name, calories, protein, carbs, fats)

 ai_db
 └── recommendations    (id, user_id, workout_plan, meal_plan)

 notification_db
 └── notifications      (id, user_id, message, status)
```

---

## 🌐 Service URLs

| Portal | URL |
|--------|-----|
| 🔀 API Gateway | http://localhost:8080 |
| 🗂 Eureka Dashboard | http://localhost:8761 |
| 📋 Auth Service | http://localhost:8081 |
| 📋 Workout Service | http://localhost:8083 |
| 📋 Nutrition Service | http://localhost:8084 |

---

## 🔐 Authentication & Authorization

### Roles

| Role | Permissions |
|------|-------------|
| `USER` | Manage workouts, nutrition, AI suggestions |
| `ADMIN` | Full platform access |

### Auth Flow

```bash
# 1. Register
curl -X POST http://localhost:8080/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John Doe",
    "email": "john@example.com",
    "password": "Secure@1234"
  }'

# 2. Login → receive token
curl -X POST http://localhost:8080/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"john@example.com","password":"Secure@1234"}'

# 3. Use token in requests
curl http://localhost:8080/api/workouts \
  -H "Authorization: Bearer <your_token>"
```

---

## 📖 API Documentation

### Core Endpoints

#### Workouts
```text
GET    /api/workouts              → Get user workouts
POST   /api/workouts              → Create workout
PUT    /api/workouts/{id}         → Update workout
DELETE /api/workouts/{id}         → Delete workout
```

#### Nutrition
```text
GET    /api/nutrition             → Get meal records
POST   /api/nutrition             → Add meal entry
PUT    /api/nutrition/{id}        → Update meal
DELETE /api/nutrition/{id}        → Delete meal
```

#### AI Recommendations
```text
GET    /api/ai/workout-plan       → AI workout plan
GET    /api/ai/diet-plan          → AI diet plan
```

---

## 🧪 Testing

```bash
# Run all unit tests
mvn test

# Run tests for specific service
cd auth-service && mvn test
cd workout-service && mvn test
cd nutrition-service && mvn test
cd ai-service && mvn test
```

**Test coverage includes:**
- ✅ `AuthServiceTest`
- ✅ `WorkoutServiceTest`
- ✅ `NutritionServiceTest`
- ✅ `AiServiceTest`

---

## 🏛 Architecture Patterns

| Pattern | Implementation |
|---------|----------------|
| **Microservices** | Independent services |
| **API Gateway** | Central entry point |
| **Event-Driven** | Kafka communication |
| **Service Discovery** | Eureka |
| **DTO Pattern** | Request/Response DTOs |
| **Repository Pattern** | Spring Data repositories |

---

## 🔭 Observability

```bash
# Health check
curl http://localhost:808X/actuator/health
```

---

## 🤝 Contributing

1. Fork the repository  
2. Create your branch: `git checkout -b feature/your-feature`  
3. Commit your changes: `git commit -m 'feat: add your feature'`  
4. Push to the branch: `git push origin feature/your-feature`  
5. Open a Pull Request  
