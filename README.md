# Cookiecutter Spring Boot Template

This is a Cookiecutter template for bootstrapping a Spring Boot microservice with:

- Java 17 + Maven
- Dockerfile for containerization
- Kubernetes manifests for deployment to EKS

## Usage

Install Cookiecutter:

```bash
pip install cookiecutter
```

Generate your new project:

```bash
cookiecutter gh:harness-idp-sandbox/java-app-with-k8s-deploy-harnesscicd
```

You’ll be prompted to enter values like:

- project_name
- project_slug
- package_name
- group_id

Then cd into your generated project and follow the README instructions to build, push, and deploy.