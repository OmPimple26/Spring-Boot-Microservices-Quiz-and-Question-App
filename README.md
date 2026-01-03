# 📚 Spring-Boot-Microservices-Quiz-and-Question-App
A complete Spring Boot Microservices project with QuizService &amp; QuestionService 📝, Eureka Service Registry 🏷️, and API Gateway 🌐. Features CRUD operations, Feign client communication, and dynamic question fetching. Ideal for learning Microservices, Spring Cloud, Centralized Configuration, Service Discovery and REST APIs 🚀.  

---

## 🏗️ Microservices Architecture

1. **Config Server** (`port: 8888`)
   - Centralized configuration management ⚙️
   - Fetches configs from a separate GitHub repository
   - Provides configuration to all services at startup

  🔗 Config Repository:
  👉 `https://github.com/OmPimple26/Centralized-Spring-Cloud-Config-for-Quiz-and-Question-Microservices-App`

2. **ServiceRegistry (Eureka)** (`port: 8761`)
   - Central service discovery 🏷️
   - Registers QuizService and QuestionService
   - Enables load balancing for microservices

3. **QuizService** (`port: 8081`)
   - Manages quizzes 📝
   - Uses `QuestionClient` to fetch related questions / Uses `Feign Client` to fetch questions from QuestionService
   - CRUD endpoints:
     - `POST /quiz` - Create a quiz
     - `GET /quiz` - Get all quizzes
     - `GET /quiz/{id}` - Get quiz by ID
   - Test endpoint:
     - `GET /quiz-test` - Simple test controller

4. **QuestionService** (`port: 9092` and `port: 8082`)
   - Manages questions ❓
   - Runs multiple instances for load balancing via Eureka ⚖️
   - CRUD endpoints:
     - `POST /question` - Create a question
     - `GET /question` - Get all questions
     - `GET /question/{questionId}` - Get question by ID
     - `GET /question/quiz/{quizId}` - Get questions of a specific quiz

5. **ApiGateway** (`port: 8083`)
   - Single entry point 
   - Routes requests to QuizService & QuestionService 🌐
   - Handles:
     - `/quiz/**` and `/quiz-test/**` → QuizService
     - `/question/**` → QuestionService

---

## 💡 Features
- Centralized configuration using Spring Cloud Config Server
- Fully functional **CRUD operations** for quizzes and questions
- **Feign Client** integration between services
- **Eureka Service Registry** for service discovery
- **Spring Cloud Gateway** for routing
- **MySQL** persistence for both services
- Dynamic retrieval of quiz-related questions
- Scalable & production-style microservices setup

---

## ⚙️ Technologies Used
- Java 21 🟢
- Spring Boot 3.2.5 🌟
- Spring Data JPA & Hibernate
- Spring Cloud Config Server
- Spring Cloud OpenFeign
- Spring Cloud Gateway
- Eureka Server
- MySQL 🐬
- Lombok ✨
- Maven 📦

---

## 📁 Project Structure

```
├── .vscode/
│   ├── launch.json
│   └── settings.json
├── ApiGateway/
│   ├── .mvn/
│   │   └── wrapper/
│   │       └── maven-wrapper.properties
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/
│   │   │   │       └── gateway/
│   │   │   │           └── ApiGatewayApplication.java
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   └── test/
│   │       └── java/
│   │           └── com/
│   │               └── gateway/
│   │                   └── ApiGatewayApplicationTests.java
│   ├── .gitattributes
│   ├── .gitignore
│   ├── mvnw
│   ├── mvnw.cmd
│   └── pom.xml
├── ConfigServer/
│   ├── .mvn/
│   │   └── wrapper/
│   │       └── maven-wrapper.properties
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/
│   │   │   │       └── config/
│   │   │   │           └── ConfigServer/
│   │   │   │               └── ConfigServerApplication.java
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   └── test/
│   │       └── java/
│   │           └── com/
│   │               └── config/
│   │                   └── ConfigServer/
│   │                       └── ConfigServerApplicationTests.java
│   ├── .gitattributes
│   ├── .gitignore
│   ├── mvnw
│   ├── mvnw.cmd
│   └── pom.xml
├── QuestionService/
│   ├── .mvn/
│   │   └── wrapper/
│   │       └── maven-wrapper.properties
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/
│   │   │   │       └── question/
│   │   │   │           ├── controllers/
│   │   │   │           │   └── QuestionController.java
│   │   │   │           ├── entities/
│   │   │   │           │   └── Question.java
│   │   │   │           ├── repositories/
│   │   │   │           │   └── QuestionRepository.java
│   │   │   │           ├── services/
│   │   │   │           │   ├── impl/
│   │   │   │           │   │   └── QuestionServiceImpl.java
│   │   │   │           │   └── QuestionService.java
│   │   │   │           └── QuestionServiceApplication.java
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   └── test/
│   │       └── java/
│   │           └── com/
│   │               └── question/
│   │                   └── QuestionServiceApplicationTests.java
│   ├── .gitattributes
│   ├── .gitignore
│   ├── mvnw
│   ├── mvnw.cmd
│   └── pom.xml
├── QuizService/
│   ├── .mvn/
│   │   └── wrapper/
│   │       └── maven-wrapper.properties
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/
│   │   │   │       └── quiz/
│   │   │   │           ├── controllers/
│   │   │   │           │   ├── QuizController.java
│   │   │   │           │   └── TestController.java
│   │   │   │           ├── entities/
│   │   │   │           │   ├── Question.java
│   │   │   │           │   └── Quiz.java
│   │   │   │           ├── repositories/
│   │   │   │           │   └── QuizRepository.java
│   │   │   │           ├── services/
│   │   │   │           │   ├── impl/
│   │   │   │           │   │   └── QuizServiceImpl.java
│   │   │   │           │   ├── QuestionClient.java
│   │   │   │           │   └── QuizService.java
│   │   │   │           └── QuizServiceApplication.java
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   └── test/
│   │       └── java/
│   │           └── com/
│   │               └── quiz/
│   │                   └── QuizServiceApplicationTests.java
│   ├── .gitattributes
│   ├── .gitignore
│   ├── mvnw
│   ├── mvnw.cmd
│   └── pom.xml
├── ServiceRegistry/
│   ├── .mvn/
│   │   └── wrapper/
│   │       └── maven-wrapper.properties
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/
│   │   │   │       └── registry/
│   │   │   │           └── ServiceRegistryApplication.java
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   └── test/
│   │       └── java/
│   │           └── com/
│   │               └── registry/
│   │                   └── ServiceRegistryApplicationTests.java
│   ├── .gitattributes
│   ├── .gitignore
│   ├── mvnw
│   ├── mvnw.cmd
│   └── pom.xml
├── .gitignore
├── LICENSE
└── README.md

```

---

## 🚀 How to Run
1. Clone the repository
```
git clone https://github.com/OmPimple26/Spring-Boot-Microservices-Quiz-and-Question-App.git
git clone https://github.com/OmPimple26/Centralized-Spring-Cloud-Config-for-Quiz-and-Question-Microservices-App.git
```

2. Start MySQL server and create databases for quizzes and questions
```
CREATE DATABASE quizdb;
CREATE DATABASE questionsdb;
```

3️. Run services in this exact order

- ServiceRegistry (Eureka Server)
- ConfigServer
- QuestionService
- QuizService
- ApiGateway

4️. Access APIs

- API Gateway → ```http://localhost:8083```
- Eureka Dashboard → ```http://localhost:8761```
- Config Server → ```http://localhost:8888```
  
---

## 📸 Screenshots

### 🧩 Quiz Application – Microservices Architecture Diagram
<img width="1724" height="952" alt="Quiz-Application Microservices Application Diagram" src="https://github.com/user-attachments/assets/7d2fc419-c107-4d38-b58e-ae3c1fafe454" />

### 🏷️ Eureka Service Registry – Registered Services Overview
<img width="1890" height="865" alt="Spring-Eureka-Dashboard-4" src="https://github.com/user-attachments/assets/641eff45-b801-4bfa-a41f-d8b433109ab8" />

### 🔌 Eureka Server – Microservices Instance Details
<img width="1890" height="859" alt="Spring-Eureka-Dashboard-5" src="https://github.com/user-attachments/assets/a7807db1-22e7-46b5-8d93-222f2b9ff7ef" />

### 📡 Eureka Dashboard – QuizService & QuestionService Status
<img width="1896" height="823" alt="Spring-Eureka-Dashboard-6" src="https://github.com/user-attachments/assets/909fa05d-1dbf-43b3-9041-9259ee4cd83f" />

---

## 📫 Contact & Contribution

Feel free to:

- Open an issue 🐞

- Submit a pull request 🔁

- Fork and enhance the project ⭐

Happy Learning & Building Microservices! 🎉🔥
