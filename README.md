# Distributed HRMS

Human Resources Management System based on a
distributed microservices architecture.

## Technologies

- Frontend: React
- Backend: Spring Boot
- Recruitment Backend: Laravel
- Messaging: Apache Kafka
- Database: PostgreSQL
- Authentication: Keycloak
- Containerization: Docker
- CI/CD: GitHub Actions

## Architecture

The system contains five independent services:

1. Employee Service
2. Leave Service
3. Payroll Service
4. Notification Service
5. Recruitment Service

The services communicate using REST APIs and
asynchronous events through Apache Kafka.

## Project Structure

- backend/: Spring Boot services
- recruitment-service/: Laravel service
- frontend/: React application
- infrastructure/: Docker, Kafka, Keycloak and Nginx
- docs/: Project documentation
