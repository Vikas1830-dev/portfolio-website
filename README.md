# 🚀 Portfolio Website Deployment using AWS S3 & GitHub Actions  

This repository contains the source code and deployment setup for my **personal portfolio website** hosted on **AWS S3** with **GitHub Actions CI/CD**.  

## 🌟 Features  
✅ Static Website (HTML, CSS, JavaScript)  
✅ AWS S3 Hosting with Public Access  
✅ Automated CI/CD Pipeline via GitHub Actions  
✅ Secure AWS IAM & Secret Management  
✅ Route 53 for Custom Domain (Optional)  

## 🛠 Tech Stack  
🔹 **Frontend** → HTML, CSS, JavaScript  
🔹 **Cloud** → AWS S3, IAM, Route 53, CloudFront  
🔹 **CI/CD** → GitHub Actions  
🔹 **Version Control** → Git & GitHub  

## 🚀 Deployment Process  
### 1️⃣ **Clone the Repository**  
```bash

 git clone [GitHub Repository Link Here]
cd portfolio-website


2️⃣ Setup AWS S3 Bucket
Create an S3 bucket (example: vikas-portfolio-website1)
Enable Static Website Hosting
Set Public Read Access with this policy:
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::vikas-portfolio-website1/*"
        }
    ]
}

3️⃣ Setup GitHub Actions CI/CD
Go to GitHub Repository → Settings → Secrets

Add AWS Credentials:

AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
Create .github/workflows/deploy.yml and paste:

yaml
Copy
Edit
name: Deploy to S3

on:
  push:
    branches:
      - master

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Configure AWS Credentials
        uses: aws-actions/configure-aws-credentials@v2
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: eu-north-1

      - name: Sync files to S3
        run: |
          aws s3 sync . s3://vikas-portfolio-website1 --delete


4️⃣ Commit & Push Changes
bash
Copy
Edit
git add .
git commit -m "Deploy portfolio to S3"
git push origin master

5️⃣ Check Your Website
Open AWS S3 Static Website Hosting URL
Example:
arduino
Copy
Edit
http://vikas-portfolio-website1.s3-website-eu-north-1.amazonaws.com/
📌 Contributing
Feel free to fork this repo, raise issues, or submit pull requests! 😊

🔗 [Live Portfolio Website:http://vikas-portfolio-website1.s3-website.eu-north-1.amazonaws.com/]
🔗 GitHub Repository:(https://github.com/Vikas1830-dev/portfolio-website)]

#AWS #DevOps #GitHubActions #CICD #PortfolioWebsite
---
