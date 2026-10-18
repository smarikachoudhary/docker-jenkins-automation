# Docker + Jenkins Automation Project

## Project Objective
Automate the build and deployment of a website using Jenkins and Docker. Every time the pipeline runs, Jenkins pulls the code from GitHub, builds a Docker image and runs the container automatically.

## Tools Used
- Jenkins
- Docker
- GitHub
- AWS EC2 (Ubuntu 26.04, t3.small)
- Nginx (inside the container)

## Features
- Pull code from GitHub
- Build Docker image
- Run container automatically

## Project Files
| File | Purpose |
|---|---|
| `index.html` | The website |
| `Dockerfile` | Builds an Nginx image that contains the website |
| `Jenkinsfile` | Pipeline with 3 stages: Pull Code, Build Docker Image, Run Container |

## Pipeline (Jenkinsfile)
1. **Pull Code from GitHub**: `checkout scm`
2. **Build Docker Image**: `docker build -t my-web-app .`
3. **Run Container**: `docker run -d --name my-web-container -p 80:80 my-web-app`

## Steps Performed
1. Launched an Ubuntu EC2 instance (t3.small) with ports 22, 80 and 8080 open
2. Installed Docker and Jenkins on the server
3. Fixed the Jenkins node going offline by lowering the free disk/temp space threshold
4. Created a Jenkins pipeline using "Pipeline script from SCM" pointing to this repository (branch `main`)
5. Ran **Build Now**: all 3 stages passed
6. Opened the EC2 public IP in the browser and the website was served from the Docker container
7. Terminated the EC2 instance after the demo

## Screenshots

### 1. EC2 instance launch settings
![EC2 launch](Screenshot%202026-10-18%20132931.png)

### 2. Security group (ports 22, 80, 8080)
![Security group](Screenshot%202026-10-18%20135517.png)

### 3. Jenkins installed and running
![Jenkins installed](Screenshot%202026-10-18%20135001.png)

### 4. Jenkins node online
![Node online](Screenshot%202026-10-18%20141207.png)

### 5. Pipeline created
![Pipeline created](Screenshot%202026-10-18%20141813.png)

### 6. Build successful (Console Output)
![Build success](Screenshot%202026-10-18%20142144.png)

### 7. Container running (docker ps)
![docker ps](Screenshot%202026-10-18%20142412.png)

### 8. Website live
![Website](Screenshot%202026-10-18%20142517.png)

### 9. EC2 instance terminated
![Terminated](Screenshot%202026-10-18%20142720.png)
## Learning Outcomes
- CI/CD pipeline basics with Jenkins
- Docker image build and container run
- Pipeline as code using a Jenkinsfile
- Deploying a website automatically from GitHub

## Author
Smarika Choudhary
