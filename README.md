# 🌐 Cloudformation-CICD: Automated Static Website Deployment

Welcome to **CloudFormation-CICD**, an automated static website deployment pipeline built with AWS S3, CloudFormation, and GitHub Actions. This project eliminates manual deployments and enables seamless, error-free updates from GitHub to your live site.

---

## 🔧 Tech Stack

- **AWS S3** – Static website hosting
- **AWS CloudFormation** – Infrastructure as Code (IaC)
- **GitHub Actions** – CI/CD pipeline for automation
- **Route 53** – Custom domain DNS (optional)
- **HTML/CSS/JS** – Static content

---

## 📁 Project Structure

```
cloudformation-cicd/
├── website/                # Static website files
│   ├── index.html
│   ├── css/
│   └── js/
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Actions workflow
├── infrastructure/
│   └── template.yaml       # CloudFormation template for S3
└── README.md               # Project documentation
```

---

## 🚀 How It Works

1. Push code to `main` branch on GitHub.
2. GitHub Actions triggers the `deploy.yml` workflow.
3. Website files are uploaded to S3.
4. S3 serves the site as a static website.
5. (Optional) Domain `waseem-syed.click` maps to S3 endpoint.

---

## 🏗️ Infrastructure Setup

CloudFormation provisions:

- S3 bucket `waseem-portfolio-website-bucket`
- Static website hosting
- Public bucket policy
- Index and error documents configuration

---

## ✅ GitHub Actions Workflow

**Trigger**: On push to `main`  
**Steps**:
- Checkout source code  
- Configure AWS credentials  
- Run `aws s3 sync` to upload content  
- (Optional) Notify on success/failure

---

## 🔐 AWS Credentials Setup

Create GitHub Secrets:

| Key                | Value                        |
|-------------------|------------------------------|
| `AWS_ACCESS_KEY_ID`     | Your AWS Access Key ID         |
| `AWS_SECRET_ACCESS_KEY` | Your AWS Secret Access Key     |
| `AWS_REGION`            | `eu-west-2` (London region)    |

---

## 🌍 Custom Domain Setup (Optional)

You can point your domain `waseem-syed.click` to this website by:

1. Creating a Route 53 Hosted Zone
2. Updating your domain registrar's nameservers
3. Adding an **A Record (Alias)** to S3 static endpoint
4. (Optional) Add CloudFront + HTTPS via ACM

---

## 🧪 Testing Checklist

- [x] `index.html` loads correctly from S3
- [x] GitHub Actions deploys on every push
- [x] Deployment logs show success
- [x] Domain `waseem-syed.click` accessible
- [x] Public access to website is confirmed

---

## 🛠️ Commands Reference

```bash
# Sync website files to S3 manually
aws s3 sync website/ s3://waseem-portfolio-website-bucket --delete

# Deploy CloudFormation template
aws cloudformation deploy \
  --template-file infrastructure/template.yaml \
  --stack-name cloudpipe-s3-static-site \
  --capabilities CAPABILITY_NAMED_IAM

# Delete stack (clean-up)
aws cloudformation delete-stack --stack-name cloudpipe-s3-static-site
```

---

## 📌 Future Enhancements

- ✅ Domain configuration (Route 53 & SSL)
- ⏳ Add CloudFront distribution for global CDN
- ⏳ Monitor deployment status with Slack/email
- ⏳ Enable versioning and logging in S3

---

## ✨ Author

**Waseem Syed**  
🔗 Medium: [@waseem.syed465](https://medium.com/@waseem.syed465)  
🌍 Website: [waseem-syed.click](http://waseem-syed.click)

---

