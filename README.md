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

## 🚀 How to Run
1. Clone the repository
```bash
git clone https://github.com/<your-username>/spring-boot-microservices-quiz.git
```

2. Start MySQL databases for quizzes and questions

3. Run ServiceRegistry

4. Run QuizService and QuestionService

5. Run ApiGateway

6. Access APIs via http://localhost:8083

---

## 📫 Contact

For queries or contributions, feel free to open an issue or pull request. Enjoy building and learning Microservices! 🎉
