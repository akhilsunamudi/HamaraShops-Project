# HamaraShops.ai

> Enterprise Full-Stack Business Platform built with Java 21, Spring Boot Microservices and React.

HamaraShops.ai is a modern full-stack web application developed using a microservices-based backend architecture and a React frontend.

The backend is developed using Java 21, Spring Boot and Spring Cloud, while the frontend is developed using React and Vite.

The project uses an API Gateway for centralized request routing and Netflix Eureka for service discovery in the local environment.

## 👨‍💻 Developer

**Akhil Sunamudi**

## 🚀 Project Overview

HamaraShops.ai contains different modules for managing business-related content and user interactions.

### Major Functionalities

- Products and AI solutions
- Business and industry information
- Career opportunities
- Customer inquiries
- REST API communication
- Centralized API Gateway
- Microservices-based backend
- Service discovery using Eureka
- React-based frontend
- Docker support
- Cloud deployment support

## 🏗️ System Architecture

```text
                         ┌─────────────────────────┐
                         │      React Frontend     │
                         │       React + Vite      │
                         └────────────┬────────────┘
                                      │
                                      │ HTTPS / REST API
                                      ▼
                         ┌─────────────────────────┐
                         │       API Gateway       │
                         │  Spring Cloud Gateway   │
                         │         Port 8080       │
                         └────────────┬────────────┘
                                      │
                  ┌───────────────────┼───────────────────┐
                  │                   │                   │
                  ▼                   ▼                   ▼
        ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
        │ Content Service │ │ Business Service│ │ Contact Service │
        │    Port 8081    │ │    Port 8082    │ │    Port 8083    │
        └─────────────────┘ └─────────────────┘ └─────────────────┘
                                      │
                                      ▼
                         ┌─────────────────────────┐
                         │     Eureka Server       │
                         │    Service Discovery    │
                         │       Port 8761         │
                         └─────────────────────────┘
```

## 📦 Microservices

### 1. API Gateway

**Technology:** Spring Cloud Gateway WebFlux  
**Port:** `8080`

The API Gateway acts as the single entry point between the frontend and backend services.

**Responsibilities:**

- Route frontend requests
- Forward requests to the correct microservice
- Handle CORS configuration
- Manage API paths
- Provide a centralized backend entry point

### 2. Content Service

**Technology:** Spring Boot  
**Port:** `8081`

The Content Service manages application content related to products, solutions, services and case studies.

**Main APIs:**

```text
GET /api/v1/products
GET /api/v1/products/{slug}
GET /api/v1/solutions
GET /api/v1/services
GET /api/v1/case-studies
```

**Responsibilities:**

- Product information
- Product details
- Solutions
- Enterprise services
- Case studies

### 3. Business Service

**Technology:** Spring Boot  
**Port:** `8082`

The Business Service handles business-related information such as industries and career opportunities.

**Main APIs:**

```text
GET /api/v1/industries
GET /api/v1/careers
```

**Responsibilities:**

- Industry information
- Career information
- Business-related content

### 4. Contact Service

**Technology:** Spring Boot  
**Port:** `8083`

The Contact Service manages customer inquiries submitted through the application.

**Main API:**

```text
POST /api/v1/contact/inquire
```

The service receives the inquiry information and returns a tracking or receipt ID.

### 5. Eureka Discovery Server

**Technology:** Spring Cloud Netflix Eureka  
**Port:** `8761`

Eureka is used for service discovery during local development.

Each microservice can register itself with Eureka, allowing services to discover other services.

**Eureka Dashboard:**

```text
http://localhost:8761
```

## 💻 Frontend

The frontend is developed as a modern Single Page Application (SPA) using React.

### Frontend Technologies

- React 19
- Vite
- React Router
- Axios
- Tailwind CSS
- Framer Motion
- Lucide Icons
- Nginx for production

The React frontend communicates with the backend services through REST APIs using the API Gateway.

## 🛠️ Technology Stack

### Backend

| Technology | Version / Usage |
|------------|-----------------|
| Java | 21 |
| Spring Boot | 4.1.0 |
| Spring Cloud | 2025.1.2 |
| Spring Cloud Gateway | WebFlux |
| Netflix Eureka | Service Discovery |
| Maven | 3.9+ |
| REST APIs | Backend Communication |

### Frontend

| Technology | Version / Usage |
|------------|-----------------|
| React | 19.0.0 |
| Vite | 5.4.11 |
| React Router DOM | 7.1.5 |
| Axios | 1.7.9 |
| Tailwind CSS | 3.4.17 |
| Framer Motion | 12.4.3 |
| Lucide Icons | 0.475.0 |

### Deployment

- Docker
- Nginx
- Google Cloud Run
- Google Cloud Build

## 📁 Project Structure

```text
HamaraShops-AI/
│
├── api-gateway/
│   └── Spring Cloud API Gateway
│
├── business-service/
│   └── Industries & Careers Microservice
│
├── contact-service/
│   └── Customer Inquiry Microservice
│
├── content-service/
│   └── Products, Solutions & Services Microservice
│
├── eureka-cloud-server/
│   └── Eureka Service Discovery Server
│
├── frontend/
│   └── React + Vite Application
│
├── .gitignore
│
└── README.md
```

## 🔄 Application Flow

```text
                         USER
                           │
                           ▼
                  ┌─────────────────┐
                  │ React Frontend  │
                  └────────┬────────┘
                           │
                           │ REST API Request
                           ▼
                  ┌─────────────────┐
                  │   API Gateway   │
                  │     :8080       │
                  └────────┬────────┘
                           │
            ┌──────────────┼──────────────┐
            │              │              │
            ▼              ▼              ▼
       Content         Business        Contact
       Service         Service         Service
        :8081           :8082           :8083
```

### Example Product Request

```text
React Frontend
      ↓
API Gateway
      ↓
Content Service
      ↓
Product Data
      ↓
API Gateway
      ↓
React Frontend
      ↓
User
```

## 🌐 API Reference

| Microservice | Method | Endpoint | Description |
|--------------|--------|----------|-------------|
| Content Service | GET | `/api/v1/products` | Get product list |
| Content Service | GET | `/api/v1/products/{slug}` | Get product details |
| Content Service | GET | `/api/v1/solutions` | Get solutions |
| Content Service | GET | `/api/v1/services` | Get services |
| Content Service | GET | `/api/v1/case-studies` | Get case studies |
| Business Service | GET | `/api/v1/industries` | Get industries |
| Business Service | GET | `/api/v1/careers` | Get career opportunities |
| Contact Service | POST | `/api/v1/contact/inquire` | Submit customer inquiry |

## ⚙️ Local Development Setup

### Prerequisites

Before running the project, install:

- JDK 21 or later
- Node.js 20 or later
- npm 10 or later
- Maven 3.9 or later
- Git

### 1. Clone the Repository

```bash
git clone https://github.com/akhilsunamudi/HamaraShops-Project.git
cd HamaraShops-Project
```

### 2. Start Eureka Server

Open a terminal:

```bash
cd eureka-cloud-server
mvn spring-boot:run
```

Eureka Dashboard:

```text
http://localhost:8761
```

### 3. Start Content Service

Open another terminal:

```bash
cd content-service
mvn spring-boot:run
```

Runs on:

```text
http://localhost:8081
```

### 4. Start Business Service

Open another terminal:

```bash
cd business-service
mvn spring-boot:run
```

Runs on:

```text
http://localhost:8082
```

### 5. Start Contact Service

Open another terminal:

```bash
cd contact-service
mvn spring-boot:run
```

Runs on:

```text
http://localhost:8083
```

### 6. Start API Gateway

Open another terminal:

```bash
cd api-gateway
mvn spring-boot:run
```

Runs on:

```text
http://localhost:8080
```

### 7. Start Frontend

Open another terminal:

```bash
cd frontend
npm install
npm run dev
```

Frontend:

```text
http://localhost:5173
```

## 🐳 Docker Support

The project includes Docker support for packaging services into containers.

### Build API Gateway

```bash
docker build -t hamarashops/api-gateway:latest ./api-gateway
```

### Build Frontend

```bash
docker build -t hamarashops/frontend:latest ./frontend
```

## ☁️ Cloud Deployment

The application is designed to support container-based cloud deployment.

```text
                    Source Code
                         │
                         ▼
                    Docker Build
                         │
                         ▼
                 Google Cloud Build
                         │
                         ▼
                  Container Image
                         │
                         ▼
                  Google Cloud Run
                         │
        ┌────────────────┼────────────────┐
        │                │                │
        ▼                ▼                ▼
    Frontend        API Gateway       Microservices
```

The backend services can be deployed independently as separate Cloud Run services.

## 🔀 Application Profiles

### Local Profile

```text
SPRING_PROFILES_ACTIVE=local
```

The local profile is designed to work with Eureka service discovery.

### Cloud Profile

```text
SPRING_PROFILES_ACTIVE=cloud
```

The cloud profile is designed for cloud deployment where services can communicate using their deployed service endpoints.

## ✨ Key Features

- Microservices-based architecture
- Centralized API Gateway
- Eureka service discovery
- REST API communication
- React Single Page Application
- Responsive frontend
- Axios-based API communication
- Docker support
- Cloud deployment support
- Separate local and cloud profiles

## 📊 Why Microservices?

Instead of creating one large backend application, HamaraShops.ai separates the application into multiple independent services.

```text
                 HamaraShops.ai
                       │
        ┌──────────────┼──────────────┐
        │              │              │
        ▼              ▼              ▼
 Content Service  Business Service  Contact Service
        │              │              │
        ▼              ▼              ▼
 Products          Industries       Inquiries
 Solutions         Careers          Contact Forms
 Services
```

Each service has its own responsibility, making the application easier to maintain, test, update and deploy.

## 🧪 API Testing

The REST APIs can be tested using Postman or directly through the frontend application.

Example:

```text
GET http://localhost:8080/api/v1/products
```

The request is received by the API Gateway and forwarded to the Content Service.

Contact API:

```text
POST http://localhost:8080/api/v1/contact/inquire
```

## 🔐 CORS & API Communication

The project includes centralized API communication and CORS configuration.

```text
React Frontend
      │
      │ HTTP / HTTPS
      ▼
API Gateway
      │
      ▼
Backend Microservice
```

## 📌 Project Status

HamaraShops.ai has been developed as a full-stack microservices application with:

- React frontend
- Spring Boot backend
- Spring Cloud
- API Gateway
- Eureka service discovery
- REST APIs
- Docker support
- Cloud deployment support

## 👨‍💻 Developer

**Akhil Sunamudi**

Full Stack Java Developer

### Technologies

Java • Spring Boot • Spring Cloud • Microservices • REST APIs • React • Vite • Axios • Docker • Google Cloud • Git • GitHub

## 📄 License

This project is distributed under the MIT License.

See the `LICENSE` file for more information.

---

# ⭐ HamaraShops.ai

A full-stack microservices platform built using modern Java, Spring Boot, Spring Cloud and React technologies.

**Developed by Akhil Sunamudi**
