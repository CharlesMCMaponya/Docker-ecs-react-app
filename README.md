# 🐳 Dockerized React App with ECS Deployment

This project demonstrates how to containerize a **React** application using **Docker**, test it locally, and prepare for deployment to **AWS ECS Fargate** using **Terraform**.

---

## 📂 Project Structure

docker-ecs-react-app/
├── app/ # React app (built using Create React App)
│ ├── Dockerfile
│ ├── package.json
│ ├── public/
│ ├── src/
│ └── ...
├── terraform/ # (Coming Soon) Terraform configs for AWS ECS + ECR
├── screenshots/ # Project screenshots
└── README.md # This file

---

## 🧱 Built With

- ⚛️ React (via Create React App)
- 🐳 Docker
- ☁️ AWS ECR (Elastic Container Registry)
- 🚀 AWS ECS (Elastic Container Service, Fargate)
- 📜 Terraform (Infrastructure as Code — coming soon)

---

## 🐳 Docker Workflow

### 🔨 Build Docker Image

```bash
docker build -t react-docker-app .
Run Container Locally
docker run -d -p 3000:80 --name react-docker-container react-docker-app
Visit: http://localhost:3000

☁️ Push to AWS ECR
Step 1: Create Repository
aws ecr create-repository --repository-name react-docker-app --region us-east-1

Step 2: Authenticate Docker
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 188252831771.dkr.ecr.us-east-1.amazonaws.com

tep 3: Tag Docker Image
docker tag react-docker-app:latest 188252831771.dkr.ecr.us-east-1.amazonaws.com/react-docker-app:latest

 Step 4: Push to ECR
 docker push 188252831771.dkr.ecr.us-east-1.amazonaws.com/react-docker-app:latest

Screenshots
All screenshots are saved in the screenshots/ folder:

✅ Docker image build complete

✅ Container running

✅ ECR image successfully pushed

✅ Project folder view

👤 Author
Mosehla Charles Maponya

License
MIT – Free to use and modify.




