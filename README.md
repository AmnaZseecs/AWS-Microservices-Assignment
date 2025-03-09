
# 🚀 AWS Microservices Assignment

This repository contains an implementation of breaking a **monolithic application** into **microservices** and deploying them using **AWS services** such as **ECS (Elastic Container Service), Docker, and EC2**.

## 📌 Project Overview
This project demonstrates:
- **Containerizing a Monolithic Application** using **Docker**.
- **Breaking it into Microservices** and deploying them to **Amazon ECS**.
- **Using an Application Load Balancer (ALB)** for routing traffic between microservices.

## 🛠 Technologies Used
- **Node.js** with **Koa.js** (backend framework)
- **Docker** (for containerization)
- **AWS ECS (EC2 launch type)** (for microservices deployment)
- **Amazon ECR** (Elastic Container Registry for storing images)
- **Application Load Balancer (ALB)** (for request routing)

## 🏗️ Project Structure
```
📦 AWS-Microservices-Assignment
├── 📜 Dockerfile          # Docker configuration for containerizing services
├── 📜 package.json        # Project dependencies
├── 📜 package-lock.json   # Dependency lock file
├── 📜 server.js           # Main application logic
├── 📜 db.json             # Sample dataset for Subjects API
├── 📜 rule.json           # ALB path-based routing configuration
├── 📜 .gitignore          # Files to exclude from Git tracking
└── 📜 README.md           # This documentation file
```

## 🔥 Setup Instructions
To run this project locally:

### **1️⃣ Install Dependencies**
```sh
npm install
```

### **2️⃣ Run the Application**
```sh
npm start
```
It should start the server on **port 3000**.

### **3️⃣ Test the Endpoints**
- **Get all subjects:** `http://localhost:3000/api/subjects`
- **Get a specific subject:** `http://localhost:3000/api/subjects/:subjectId`

---

## 🐳 Docker Instructions
### **1️⃣ Build Docker Image**
```sh
docker build -t my-microservice .
```

### **2️⃣ Run the Container**
```sh
docker run -p 3000:3000 my-microservice
```
Now, the API should be accessible at `http://localhost:3000`.

---

## ☁️ AWS Deployment
### **1️⃣ Push Docker Image to Amazon ECR**
```sh
aws ecr get-login-password --region <your-region> | docker login --username AWS --password-stdin <your-ecr-repository-url>
docker tag my-microservice <your-ecr-repository-url>:latest
docker push <your-ecr-repository-url>:latest
```

### **2️⃣ Deploy to AWS ECS**
```sh
copilot svc deploy --name subjects-service
```

---

## 🛣️ ALB Path-Based Routing
The following ALB listener rules are configured in `rule.json`:
- **Subjects API:** `/api/subjects*` → routes traffic to `subjects-service`

### **Sample ALB URLs (Replace with actual values)**
```sh
http://dummy-lb-720579266.us-east-1.elb.amazonaws.com/api/subjects
```

---

## 🔧 Troubleshooting
### **Common Issues & Solutions**
| Problem | Solution |
|---------|----------|
| ECS task failed to start | Check IAM permissions for `AmazonECSTaskExecutionRole` |
| ALB not routing requests | Verify ALB listener rules in `rule.json` |
| Docker image not found in ECR | Ensure you pushed the correct image to ECR |

---

## 🏆 Learning Outcomes
- **Learned AWS ECS & ECR deployments.**
- **Gained experience in containerizing microservices using Docker.**
- **Implemented path-based routing using AWS ALB.**

---



## 🎯 Next Steps
- ✅ Improve security using **IAM roles & policies**.
- ✅ Automate deployments using **CI/CD pipelines**.
- ✅ Migrate to **AWS Fargate** for serverless microservices.

---

## ⭐ Contributions & Feedback
Feel free to **fork** this repo, **submit pull requests**, or **raise issues** if you have improvements or questions! 😊

---

## 📜 License
This project is **MIT licensed**. See the [LICENSE](LICENSE) file for details.
```

---

