# docker-nginx-multi-site-setup
# 🚀 Multi-Website Deployment using Docker & Nginx on Ubuntu Server

## 📌 Project Description

This project demonstrates deploying multiple websites using **Docker containers** with **Nginx** on an **Ubuntu Server** environment.  
Each website is hosted inside a separate container and exposed using different ports.

---

## 🖥️ Environment

- OS: Ubuntu Server  
- Containerization: Docker  
- Web Server: Nginx  

---

## 🧱 Implementation Steps

### 1. Pull Nginx Image

```bash
docker pull nginx
```
2. Create and Run Containers
 ```bash
   docker run -d --name pratiksha.com -p 80:80 -v /home/ubuntu/pratiksha.com:/usr/share/nginx/html nginx
```
 ```bash
   docker run -d --name aws.com -p 90:80 -v /home/ubuntu/aws.com:/usr/share/nginx/html nginx
 ```
 ```bash
   docker run -d --name learn-devops.com -p 8080:80 -v /home/ubuntu/learn-devops.com:/usr/share/nginx/html nginx
 ```
3. Verify Running Containers
    ```bash
   docker ps
     ```
4. Access Containers
    ```bash
    docker exec -it pratiksha.com bash
    docker exec -it aws.com bash
    docker exec -it learn-devops.com bash
     ```
5. Create Website Content
🔹 Pratiksha Website
    ```bash
cd /usr/share/nginx/html/
echo "Hello I am Pratiksha lavand" > index.html
     ```
🔹 AWS Website
    ```bash
cd /usr/share/nginx/html/
echo "Welcome Amazon Web Services(AWS)" > index.html
     ```
🔹 Learn DevOps Website
    ```bash
cd /usr/share/nginx/html/
echo "Hello This is my Learn-devops page" > index.html
     ```
6. Modify Nginx Configuration
    ```bash
cd /etc/nginx/conf.d/
nano default.conf
     ```
📄 default.conf (Final Config)
    ```bash
    # Pratiksha Website
server {
    listen 80;
    server_name pratiksha.com;

    location / {
        root /usr/share/nginx/html/site1;
        index index.html;
    }
}

# AWS Website
server {
    listen 80;
    server_name aws.com;

    location / {
        root /usr/share/nginx/html/site2;
        index index.html;
    }
}

# Learn DevOps Website
server {
    listen 80;
    server_name learn-devops.com;

    location / {
        root /usr/share/nginx/html/site3;
        index index.html;
    }
}
    ```
    
🌐 Application Access
http://<Server-IP> → Pratiksha Website
http://<Server-IP>:90 → AWS Website
http://<Server-IP>:8080 → Learn DevOps Website

🛠️ Key Concepts Used
Docker container deployment
Port mapping
Volume mounting
Nginx configuration
Linux command-line operations

📊 Outcome
Successfully deployed 3 independent websites
Each container serves custom content
Multiple applications hosted on a single Ubuntu server

👩‍💻 Author

Pratiksha Lavand
Aspiring Cloud & DevOps Engineer
