# Node.js App Deployment using Jenkins and CI/CD pipeline 

## Overview

This project demonstrate how to deploy a **Node.js applicatin** using **Jenkins** with a fully automated software delivery.

---

## Tools and Technologies
- **Node.js**- Application framework
- **Git and GitHub** - Source code management
- **Jenkins** - CI/CD automation server
- **AWS EC2/Local Server** - Deployment envrionment

---

## CI/Cd Pipeline Flow:
Developer pushes code to GitHub --> Jenkins pulls code --> Install Dependencies (npm install) --> Run Tests --> Buils Application --> Deploy using PM2 --> Live Application

---

## Architecture Diagram

![](./img/Node.js%20deployment.png)
 
---

## Steps to deploy App using Jenkins:

### Step 1: Launch EC2 Instances

1. Jenkins Server 
2. Node-App server
   - Install nodejs,npm and pm2 

   ![](./img/Screenshot%201.png)


- Add port 8080 in security group
- Add port 22 and 3000 in security group

   ![](./img/Screenshot%202.png)

### Step 2: Create Repository on GitHub
- Create a repository on GitHUb with name : **Node-App-CLCD-Project**

![](./img/Screenshot%203.png)

### Step 3: Add Credentials

**Manage Jenkins → Credentials → System → Gobal**

- Create new credentails
    - scope:Global
    - id:Node-app-key
    - description:Node-app-key
    - username:ubuntu
    
![](./img/Screenshot%204.png)

### Step 4: Create a Pipeline Job

1. from Jenkins Dashboard → Click "New Item"
2. Enter job name:Node-app-deploy-CICD → select **Pipeline** → click OK

![](./img/Screenshot%205.png)

3. In this Pipeline configuration:
 - Enable trigger:GitHub hook trigger for GITScm polling
 - Choose Defination: Pipeline script from SCM
 - SCM:Git
 - Repository: https://github.com/Abhinandan-58/Node-app-deploy-CICD-project.git
 - Branch:main
 - Script Path:Your-jenkinfile-name

 ![](./img/Screenshot%206.png)

### Step 5: Create Jenkinfile 

In your Node.js project root directory, create a filr named jenkinfile with the following code:

![](./img/Screenshot%207.png)

### Step 6: Push Jenkinfile to GitHub

- After creating the jenkinsfile, push it to your repository so jenkins can access it.

         git init 
         git add.
         git commit -m ""
         git push -u origin main

- After pushing the Jenkinsfile and code to GitHub, Jenkins will automatically pull the latest code, build the app, and deploy it to the server using the pipeline steps.

![](./img/Screenshot%208.png)

### Step 7: Verify Deployment

Once the pipeline completes successfully:
- Visit your app in browser:
       http://<your-server-ip>:3000


![](./img/Screenshot%209.png)

---
## Conclusion
 
 This project demonstrate how Jenkins automates the **Node.js CI/CD workflow** — from code commit to live deployment - improving efficency,consistency and reliability of releases.
 It's a simple yet powerful setup for real-world Devops practices.

   
