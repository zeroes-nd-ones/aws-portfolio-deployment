# Portfolio Website - Deployed on AWS EC2

Personal portfolio website deployed on AWS EC2 with nginx.

## Live Demo
**http://13.57.236.83**

## Architecture
```
Local Machine (HTML/CSS)
        ↓
    SCP transfer
        ↓
AWS EC2 (t2.micro, Ubuntu 22.04)
        ↓
  Nginx Web Server (port 80)
        ↓
   Public Internet
```

## Technologies Used
- AWS EC2 (t2.micro - Free Tier)
- Ubuntu 22.04
- Nginx
- HTML/CSS
- Git & GitHub
- AWS CLI

## Deployment Steps

### 1. Launch EC2 Instance
- AMI: Ubuntu 22.04
- Instance type: t2.micro (free tier)
- Security Group: Allow SSH (22), HTTP (80)

### 2. SSH Into Server
```bash
chmod 400 your-key.pem
ssh -i your-key.pem ubuntu@<ec2-ip>
```

### 3. Install Nginx
```bash
sudo apt update
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

### 4. Deploy Website
```bash
# From local machine
scp -i your-key.pem index.html ubuntu@<ec2-ip>:/home/ubuntu/

# On EC2
sudo cp /home/ubuntu/index.html /var/www/html/
```

## What I Learned
- AWS EC2 setup and management
- Security groups and networking
- SSH and SCP file transfers
- Nginx web server configuration
- Cloud deployment workflow
- AWS CLI usage

## Next Steps (Coming Soon)
- Dockerize the application
- Add CI/CD pipeline (GitHub Actions)
- Provision infrastructure with Terraform
- Add HTTPS with Let's Encrypt
- Deploy to Kubernetes
