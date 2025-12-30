# 📚 Spring-Boot-Microservices-Quiz-and-Question-App
A complete Spring Boot Microservices project with QuizService &amp; QuestionService 📝, Eureka Service Registry 🏷️, and API Gateway 🌐. Features CRUD operations, Feign client communication, and dynamic question fetching. Ideal for learning Microservices, Spring Cloud, and REST APIs 🚀.

---

## 🏗️ Microservices Architecture

1. **QuizService** (`port: 8081`)
   - Manages quizzes 📝
   - Uses `QuestionClient` to fetch related questions
   - CRUD endpoints:
     - `POST /quiz` - Create a quiz
     - `GET /quiz` - Get all quizzes
     - `GET /quiz/{id}` - Get quiz by ID
   - Test endpoint:
     - `GET /quiz-test` - Simple test controller

2. **QuestionService** (`port: 9092` and `port: 8082`)
   - Manages questions ❓
   - Runs multiple instances for load balancing via Eureka ⚖️
   - CRUD endpoints:
     - `POST /question` - Create a question
     - `GET /question` - Get all questions
     - `GET /question/{questionId}` - Get question by ID
     - `GET /question/quiz/{quizId}` - Get questions of a specific quiz

3. **ServiceRegistry (Eureka)** (`port: 8761`)
   - Central service discovery 🏷️
   - Registers QuizService and QuestionService
   - Enables load balancing for microservices

4. **ApiGateway** (`port: 8083`)
   - Routes requests to QuizService & QuestionService 🌐
   - Handles:
     - `/quiz/**` and `/quiz-test/**` → QuizService
     - `/question/**` → QuestionService

---

## 💡 Features
- Fully functional **CRUD operations** for quizzes and questions
- **Feign Client** integration between services
- **Eureka Service Registry** for service discovery
- **Spring Cloud Gateway** for routing
- **MySQL** persistence for both services
- Dynamic retrieval of quiz-related questions

---

## ⚙️ Technologies Used
- Java 21 🟢
- Spring Boot 3.x 🌟
- Spring Data JPA & Hibernate
- Spring Cloud OpenFeign
- Spring Cloud Gateway
- Eureka Server
- MySQL 🐬
- Lombok ✨

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
```

2. Start MySQL databases for quizzes and questions

3. Run ServiceRegistry

4. Run QuizService and QuestionService

5. Run ApiGateway

6. Access APIs via ```http://localhost:8083```

---

## 📸 Screenshots

### 🧩 Quiz Application – Microservices Architecture Diagram
<img width="1724" height="952" alt="Quiz-Application Microservices Application Diagram" src="https://github.com/user-attachments/assets/7d2fc419-c107-4d38-b58e-ae3c1fafe454" />

### 🏷️ Eureka Service Registry – Registered Services Overview
<img width="1896" height="856" alt="Spring-Eureka-Dashboard-1" src="https://github.com/user-attachments/assets/5e18dbcd-d51a-4bb5-b233-b243539cd8ab" />

### 🔌 Eureka Server – Microservices Instance Details
<img width="1895" height="859" alt="Spring-Eureka-Dashboard-2" src="https://github.com/user-attachments/assets/dd58494c-83e0-4e59-802a-5c3b6c5b5a9a" />

### 📡 Eureka Dashboard – QuizService & QuestionService Status
<img width="1896" height="832" alt="Spring-Eureka-Dashboard-3" src="https://github.com/user-attachments/assets/eab490e4-7d40-4849-ba43-a89a03c59aa1" />

---

## 📫 Contact

For queries or contributions, feel free to open an issue or pull request. Enjoy building and learning Microservices! 🎉
