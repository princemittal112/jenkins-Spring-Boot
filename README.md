
[jenkins-s3-java.pdf](https://github.com/user-attachments/files/21197114/jenkins-s3-java.pdf)

# 🚀 Spring Boot CI/CD Pipeline with Jenkins, Ansible & AWS

This project demonstrates a complete CI/CD pipeline using **Jenkins**, **Ansible**, and **AWS services** including **S3** and **EC2** to deploy a Spring Boot application.

---

## 🧰 Tech Stack

- **Jenkins** – CI/CD pipeline automation
- **Ansible** – Deployment to EC2 instance
- **AWS S3** – Artifact (JAR) storage
- **AWS EC2** – Hosting the Spring Boot app
- **Nginx** – Reverse proxy to forward port 80 to 8081
- **Spring Boot** – Sample Java backend application

---

## 📁 Project Structure

<img width="199" height="107" alt="Screenshot 2025-07-12 at 9 17 49 PM" src="https://github.com/user-attachments/assets/774ede02-fad6-4eb3-b364-915483cd55da" />

---

## 🔄 CI/CD Workflow

1. **Clone GitHub Repo** via Jenkins.
2. **Build JAR** using `./mvnw clean package -DskipTests`.
3. **Upload to S3** using AWS CLI.
4. **Ansible Playbook** pulls the JAR from S3 to EC2 and runs it.
5. **Nginx** configured to proxy port 80 → 8081 (Spring Boot).

---

## 🔐 Fixes & Enhancements

- ✅ Replaced Ansible `copy` with `amazon.aws.aws_s3` to pull JAR from S3
- ✅ Attached IAM Role with S3 access to EC2
- ✅ Avoided Jenkins port conflict by setting Spring Boot to run on `8081`
- ✅ Jenkins runs on `localhost:9090`

---

## 🌐 URLs

| Component       | URL                              |
|----------------|-----------------------------------|
| Jenkins (Local) | `http://localhost:9090/`         |
| Spring Boot App | `http://<EC2-IP>/`               |
| Custom Domain   | `http://princespringboot.com/`   |

---

## 🛠 Required IAM Role (EC2)

Attach a role with the following permission:
```json
{
  "Effect": "Allow",
  "Action": "s3:*",
  "Resource": "*"
}


