Here’s a **brief and concise version** of your `README.md`:

---

# 🚀 Brain Tasks App – CI/CD on AWS

This project demonstrates CI/CD for a simple Node.js app using AWS **ECR, EKS, CodeBuild, CodeDeploy**, and **CodePipeline**.

---

## 🧠 App Overview

* Node.js HTTP server returns:
  `Hello from Brain Tasks App! 234`
* Runs on: `http://localhost:3000`

---

## ⚙️ Setup

```bash
git clone https://github.com/Vennilavan12/Brain-Tasks-App.git
cd Brain-Tasks-App
node server.js
```

---

## 🐳 Docker

### Dockerfile

```dockerfile
FROM node:14
WORKDIR /app
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]
```

### Build & Run

```bash
docker build -t brain-tasks-app .
docker run -p 3000:3000 brain-tasks-app
```

---

## ☁️ AWS Deployment

### ECR

```bash
aws ecr create-repository --repository-name brain-tasks-app
aws ecr get-login-password | docker login --username AWS --password-stdin <account>.dkr.ecr.<region>.amazonaws.com
docker tag brain-tasks-app:latest <account>.dkr.ecr.<region>.amazonaws.com/brain-tasks-app
docker push <account>.dkr.ecr.<region>.amazonaws.com/brain-tasks-app
```

### Kubernetes (EKS)

* Create EKS Cluster
* Apply `deployment.yaml` and `service.yaml`

Deployed URL:
**[http://a0d42432a62a64bceaa8d7d9702b85e4-768409516.ap-south-1.elb.amazonaws.com](http://a0d42432a62a64bceaa8d7d9702b85e4-768409516.ap-south-1.elb.amazonaws.com)**

---

## 🏗️ CodeBuild

### `buildspec.yml`

Builds and pushes Docker image to ECR.

---

## 🚀 CodeDeploy

### `appspec.yml`

Used to deploy app to EKS.

---

## 🔁 CodePipeline

* **Source**: GitHub
* **Build**: CodeBuild
* **Deploy**: CodeDeploy or Lambda

---

## 🔍 Monitoring

* Use **CloudWatch Logs** for:

  * Build Logs
  * Deployment Logs
  * App Logs

---

## ✅ Version Control

```bash
git init
git remote add origin https://github.com/<your-username>/<repo>.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

---

Let me know if you'd like this saved as a file or formatted for PDF export.
