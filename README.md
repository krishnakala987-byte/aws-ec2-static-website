# README.md

# AWS EC2 Static Website Deployment

This project demonstrates how to deploy a static website on an AWS EC2 instance using Apache (httpd). It covers GitHub setup, EC2 configuration, and hosting a website using a public IP.

## Topics Covered
- Git & GitHub basics
- Repository structure management
- AWS EC2 setup
- SSH connection
- Apache (httpd) installation
- Static website deployment

## Projects
- AWS EC2 Static Website Hosting


---

# DETAILED_NOTES.md

# AWS EC2 Static Website Deployment - Detailed Notes

## 1. Introduction

This project is about deploying a static website on an AWS EC2 instance using Apache (httpd).

In simple terms:
- We store our website code on GitHub
- We create a virtual server (EC2)
- We install a web server (Apache)
- We copy our website files into the server
- Then we access it using a public IP

Real-world analogy:
GitHub is storage, EC2 is a rented computer, Apache is the software that shows your website to users.

---

## 2. Core Concepts

### GitHub Repository
- A place to store your project code
- Contains files like:
  - index.html
  - images/
  - assets/

### Repository Structure
Clean structure is important:

```
project/
 ├── index.html
 ├── images/
 ├── assets/
 └── README.md
```

### Static Website
- HTML, CSS, images only
- No backend

### EC2
- Virtual server on AWS

### Apache (httpd)
- Web server
- Serves files from:
```
/var/www/html
```

### Security Groups
- Firewall for EC2
- Allows:
  - Port 22 (SSH)
  - Port 80 (HTTP)

---

## 3. Important Commands

### Git Commands

```
git init
git add .
git commit -m "initial commit"
git push origin main
```

If README exists:
```
git pull origin main --rebase
```

---

### EC2 Commands

```
ssh -i key.pem ec2-user@<public-ip>
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
git clone <repo-url>
sudo cp -r * /var/www/html/
```

---

## 4. Step-by-Step Implementation

1. Create GitHub repo
2. Upload:
   - index.html
   - images/
   - assets/

3. Maintain structure:
```
images/bg.jpg
```

4. Launch EC2:
   - Region: ap-south-1
   - Instance: t2.micro
   - Enable public IP

5. Security group:
   - SSH (22)
   - HTTP (80)

6. Connect:
```
ssh -i key.pem ec2-user@<public-ip>
```

7. Install Apache:
```
sudo yum install httpd -y
```

8. Start Apache:
```
sudo systemctl start httpd
```

9. Clone repo:
```
git clone <repo-url>
cd <repo-name>
```

10. Copy files:
```
sudo cp -r * /var/www/html/
```

11. Open browser → Public IP

---

## 5. Problems & Troubleshooting

Problem: Image upload not working  
Cause: Used "Create new file"  
Solution: Use "Upload files"

Problem: Folder not created  
Cause: Wrong naming  
Solution: Use:
```
images/bg.jpg
```

Problem: .DS_Store confusion  
Cause: Seen in mentor repo  
Solution:
- Not needed
- Ignore it

Problem: Git push error due to README  
Solution:
```
git pull origin main --rebase
```

---

## 6. Mistakes & Things to Remember

- Do not upload .DS_Store
- Keep clean structure
- Always verify image paths
- Understand commands, don’t copy blindly
- Use correct upload method

---

## 7. Quick Revision

- GitHub → stores code
- EC2 → server
- Apache → serves website
- /var/www/html → web root
- Public IP → access website
- Port 80 → must be open

Flow:
GitHub → EC2 → Apache → Browser
