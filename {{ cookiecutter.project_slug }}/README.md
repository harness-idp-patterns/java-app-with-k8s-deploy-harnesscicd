# {{ cookiecutter.project_name }}

{{ cookiecutter.description }}

## Overview

This is a Spring Boot application created using the Harness Internal Developer Platform (IDP). It provides a simple REST API with health check endpoints and is containerized for deployment to Kubernetes.

## Development

### Prerequisites

- Java 11 or higher  
- Maven 3.6 or higher  
- Docker (for local container testing)  
- Kubernetes CLI (`kubectl`) for deployment verification  

### Building the Application

To build the application locally:

```bash
mvn clean package
```

To run the tests:

```bash
mvn test
```

To run the application locally:

```bash
mvn spring-boot:run
```

The application will be available at [http://localhost:8080](http://localhost:8080)

---

## API Endpoints

| Method | Endpoint | Description |
|---------|-----------|-------------|
| GET | `/` | Returns a greeting message and timestamp |
| GET | `/health` | Health check endpoint (returns status "UP" when service is healthy) |

---

## Docker

### Building the Docker Image

```bash
docker build -t {{ cookiecutter.docker_registry }}/{{ cookiecutter.docker_image_name }}:latest .
```

### Running the Docker Container

```bash
docker run -p 8080:8080 {{ cookiecutter.docker_registry }}/{{ cookiecutter.docker_image_name }}:latest
```

---

## Deployment

This application is automatically deployed to Kubernetes using Harness CD.

### Kubernetes Resources

| Resource | Name |
|-----------|------|
| Deployment | {{ cookiecutter.project_slug }} |
| Service | {{ cookiecutter.project_slug }} |

Access URL: The application will be accessible via the LoadBalancer service.

### Viewing Deployment Status

```bash
kubectl get deployments {{ cookiecutter.project_slug }}
kubectl get pods -l app={{ cookiecutter.project_slug }}
kubectl get service {{ cookiecutter.project_slug }}
```

---

## CI/CD Pipeline

This application uses Harness CI/CD pipelines for automated building, testing, and deployment:

1. **Build and Push Stage** – Compiles the code and runs unit tests; Builds and pushes the Docker image.  
3. **Deploy Stage** – Deploys the application to Kubernetes  

---

## Customization

To customize this application for your needs:

- Update the application code in `src/main/java/{{ cookiecutter.package_path }}/`  
- Modify the API endpoints in `HelloController.java`  
- Add additional dependencies to `pom.xml` as needed  
- Update Kubernetes resource requirements in `kubernetes/deployment.yaml`  

---

## Support

For questions or issues, please contact the **Platform Engineering Team**.
