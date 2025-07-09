# 🐳 Dockerized React App with ECS Deployment

This project demonstrates how to containerize a **React** application using **Docker**, test it locally, and prepare for deployment to **AWS ECS Fargate** using **Terraform**.

---

## 📂 Project Structure

```
docker-ecs-react-app/
├── app/                    # React app (built using Create React App)
│   ├── Dockerfile
│   ├── package.json
│   ├── public/
│   ├── src/
│   └── ...
├── terraform/              # (Coming Soon) Terraform configs for AWS ECS + ECR
├── screenshots/            # Project screenshots
└── README.md               # This file
```

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
```

### 🏃 Run Container Locally
```bash
docker run -d -p 3000:80 --name react-docker-container react-docker-app
```
Visit: http://localhost:3000

---

## ☁️ Push to AWS ECR

### Step 1: Create Repository
```bash
aws ecr create-repository --repository-name react-docker-app --region us-east-1
```

### Step 2: Authenticate Docker
```bash
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 188252831771.dkr.ecr.us-east-1.amazonaws.com
```

### Step 3: Tag Docker Image
```bash
docker tag react-docker-app:latest 188252831771.dkr.ecr.us-east-1.amazonaws.com/react-docker-app:latest
```

### Step 4: Push to ECR
```bash
docker push 188252831771.dkr.ecr.us-east-1.amazonaws.com/react-docker-app:latest
```

---

## 🧹 Git Repository Cleanup

### Problem: Large File in Git History
During development, a large screenshot file (`screenshots/docker-build-success.png.jpg`) was accidentally committed, causing issues with repository size and push operations.

### Solution: Using git-filter-repo
**Step 1:** Install git-filter-repo
```bash
pip install git-filter-repo
```

**Step 2:** Remove the large file from Git history
```bash
git filter-repo --path screenshots/docker-build-success.png.jpg --invert-paths --force
```

**Step 3:** Re-add remote and push cleaned repository
```bash
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push origin main --force
```

### ⚠️ Important Notes:
- This **permanently removes** the file from Git history
- Always backup your repository before running cleanup commands
- The `--force` flag is needed when working on your original repository
- `git-filter-repo` removes remotes for safety - you need to add them back

---

## 📸 Screenshots

All screenshots are saved in the `screenshots/` folder:

✅ Container running successfully  
✅ ECR image successfully pushed  
✅ Project folder view  

---

## 👤 Author

**Mosehla Charles Maponya**

---

## 📄 License

MIT – Free to use and modify.