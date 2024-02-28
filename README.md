# DVWA on Kubernetes with GitLab CI/CD

This repository demonstrates deploying Damn Vulnerable Web Application (DVWA) on a local Kubernetes cluster using Minikube and showcasing three attack surfaces. Additionally, it includes GitLab CI/CD integration for automated deployment.

## Setup

1. **Start Minikube:**
    ```bash
    minikube start
    ```

2. **Deploy DVWA:**
    ```bash
    kubectl apply -f dvwa-deployment.yaml -f dvwa-service.yaml
    ```

3. **Expose DVWA:**
    - Get Minikube IP: `minikube ip`
    - Access DVWA in a browser using Minikube IP and NodePort.

4. **Showcase Attack Surfaces:**
    - Follow the steps mentioned in the README to demonstrate SQL Injection, XSS, and Command Injection vulnerabilities.

This guide provides step-by-step instructions to showcase and demo three attack surfaces present in the Damn Vulnerable Web Application (DVWA) running on a local Kubernetes cluster.

## 1. SQL Injection

1. **Access DVWA Login Page:**
   - Navigate to the DVWA login page using the provided URL.

2. **Perform SQL Injection:**
   - In the Username field, input: `admin' OR '1'='1' --`.
   - Demonstrate successful login with the injected SQL.

## 2. XSS (Cross-Site Scripting)

1. **Access DVWA XSS Page:**
   - Navigate to the DVWA XSS page.

2. **Inject XSS Payload:**
   - Enter `<script>alert('XSS');</script>` in the input field.
   - Show the alert box indicating XSS vulnerability.

## 3. Command Injection

1. **Access DVWA Command Execution Page:**
   - Navigate to the DVWA Command Execution page.

2. **Execute Command Injection:**
   - In the IP field, enter `127.0.0.1; ls`.
   - Showcase the command execution result.

## GitLab CI/CD Integration

1. **Create `.gitlab-ci.yml`:**
    ```yaml
    stages:
      - deploy
    
    deploy_dvwa:
      stage: deploy
      script:
        - kubectl apply -f deployment.yaml -f service.yaml
    ```

2. **Commit and Push:**
    - Commit your changes and push to your GitLab repository.

3. **Monitor CI/CD Pipeline:**
    - Visit your GitLab project's CI/CD section to monitor the pipeline.
    - Ensure the deployment job is successful.


