<h1 align="center">🚀 Node.js CI/CD Pipeline Using Jenkins & AWS EC2</h1>

<p align="center">
  <b>Automated deployment of a Node.js application using Jenkins, GitHub, and AWS EC2.</b><br>
  <i>Designed for efficient Continuous Integration and Continuous Deployment (CI/CD).</i>
</p>

---

## 🧭 Table of Contents
- [📘 Overview](#-overview)
- [🧩 Architecture](#-architecture)
- [⚙️ Technologies Used](#️-technologies-used)
- [🖥️ Setup Steps](#️-setup-steps)
- [📂 Project Structure](#-project-structure)
- [✅ Result](#-result)
- [🧠 Key Learnings](#-key-learnings)
- [👨‍💻 Author](#-author)
- [🏷️ Tags](#-tags)

---

## 📘 Overview
This project demonstrates a **CI/CD pipeline** for a **Node.js application** hosted on **AWS EC2** instances using **Jenkins**.  
It automates code deployment every time a developer pushes updates to GitHub, ensuring a smooth and repeatable deployment process.

> 🧠 The main goal is to achieve **Continuous Integration and Continuous Deployment** using open-source DevOps tools.

---

## 🧩 Architecture
```
GitHub → Jenkins Server → Deployment Server (Node.js + PM2)
```

- **GitHub:** Stores the application source code and Jenkinsfile.  
- **Jenkins Server:** Automates build, test, and deployment stages.  
- **Deployment EC2:** Hosts the running Node.js application managed by PM2.

<p align="center">
  <img src="https://user-images.githubusercontent.com/91388754/169044722-6b89486b-3b6f-4978-8a0f-30ac2c4e4c1f.png" alt="Architecture Diagram" width="600"/>
</p>

---

## ⚙️ Technologies Used
| Tool / Service | Purpose |
|----------------|----------|
| **AWS EC2** | Hosting Jenkins and Node.js application |
| **Node.js** | Backend runtime for the application |
| **npm** | Package management |
| **PM2** | Process manager for running Node.js apps |
| **Jenkins** | CI/CD automation server |
| **GitHub** | Source code and Jenkinsfile storage |
| **Webhook** | Automates Jenkins builds on code push |

---

## 🖥️ Setup Steps

### 🔹 Step 1: Launch EC2 Instances
- Launch **two EC2 instances**:
  - `Jenkins Server`
  - `Deployment Server`

### 🔹 Step 2: Configure Deployment Server
```bash
sudo apt update
sudo apt install nodejs -y
sudo apt install npm -y
sudo npm install -g pm2
```
PM2 ensures the app keeps running continuously even after reboots.

### 🔹 Step 3: Push Code to GitHub
- Create a new **GitHub repository**.
- Add all your project files including `app.js` and `Jenkinsfile`.
- Commit and push the code to GitHub.

### 🔹 Step 4: Configure Jenkins Server
1. Install Jenkins on another EC2 instance.  
2. Access Jenkins via:
   ```
   http://<jenkins-server-public-ip>:8080
   ```
3. Install required plugins:
   - Git Plugin
   - Pipeline Plugin
   - SSH Agent Plugin  
4. Create **credentials** in Jenkins for:
   - GitHub (if private)
   - Deployment server (SSH key)

### 🔹 Step 5: Create Jenkins Pipeline
1. Create a new **Pipeline job** in Jenkins.  
2. Choose **"Pipeline script from SCM"**.  
3. Enter your **GitHub repository URL**.  
4. Save the configuration.

### 🔹 Step 6: Run the Pipeline
- Click **Build Now** in Jenkins.  
- Jenkins will:
  - Pull the latest code from GitHub.
  - SSH into the Deployment Server.
  - Deploy and start the Node.js app using PM2.

### 🔹 Step 7: Add GitHub Webhook
- Go to **GitHub → Settings → Webhooks → Add Webhook**
- Use this URL:
  ```
  http://<jenkins-server-public-ip>:8080/github-webhook/
  ```
- Set **Content type**: `application/json`
- Choose event: **Just the push event**

Now Jenkins will automatically build and deploy whenever new code is pushed!

---

## 📂 Project Structure
```
.
├── app.js
├── package.json
├── Jenkinsfile
├── README.md
└── other source files
```

---

## ✅ Result
🎉 The CI/CD pipeline works as follows:
1. Code is pushed to GitHub.  
2. Jenkins automatically triggers a build via webhook.  
3. The Node.js app is deployed to the EC2 deployment server.  
4. PM2 ensures continuous uptime of the application.

> 💡 Achieved a fully automated **end-to-end CI/CD process** using Jenkins and AWS.

---

## 🧠 Key Learnings
- Setting up Jenkins on AWS EC2.
- Automating deployments using GitHub webhooks.
- Managing Node.js processes with PM2.
- Securely using SSH for remote deployment.
- Building an efficient DevOps workflow using open-source tools.

---

## 👨‍💻 Author
**Ganesh Jadhav**  
🌐 [LinkedIn](https://www.linkedin.com/in/iam-ganeshjadhav)  
📧 iamganeshjadhav@gmail.com  

---

## 🏷️ Tags
`AWS` `Jenkins` `Node.js` `CI/CD` `DevOps` `PM2` `GitHub` `EC2` `Automation`

---

<p align="center">
  💡 <b>“Build. Test. Deploy. Automate — That’s the DevOps way.”</b> 💡
</p>
