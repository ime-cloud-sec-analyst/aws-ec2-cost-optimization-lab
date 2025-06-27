AWS EC2 Cost Optimization Lab 💰☁️

This lab demonstrates how to analyze and optimize AWS EC2 instance costs using the AWS Pricing Calculator. It walks through the before-and-after impact of right-sizing an EC2 instance running a Café web application.

🧪 Lab Objective

Identify underutilized AWS EC2 resources

Uninstall a decommissioned local MariaDB database

Resize EC2 instance from t3.small to t3.micro

Reduce Amazon EBS volume from 40 GB to 20 GB

Use AWS CLI and AWS Pricing Calculator to analyze potential cost savings

🏗️ Lab Environment

Region: US West (Oregon)

EC2 Instance Before Optimization:

Type: t3.small

Storage: 40 GB (20 GB used by local database)

Pricing: On-Demand, 100% utilization

Amazon RDS Instance:

Type: db.t3.micro

Engine: MariaDB

Storage: 20 GB

📉 Before Optimization Estimate

EC2 + EBS + RDS Estimated Monthly Cost: $35.60

Total Annual Cost: $427.20

✅ CSV export available in the repository under /exports
📸 Step-by-step screenshots are located in the /images folder

🔧 Optimization Steps

Task 1: Optimize the EC2 Environment

SSH into CafeInstance

sudo systemctl stop mariadb
sudo yum -y remove mariadb-server

SSH into CLI Host and run the following AWS CLI commands:

aws ec2 stop-instances --instance-ids <Instance-ID>
aws ec2 modify-instance-attribute --instance-id <Instance-ID> --instance-type '{"Value": "t3.micro"}'
aws ec2 start-instances --instance-ids <Instance-ID>

Task 2: Estimate Costs with AWS Pricing Calculator

✔️ After Optimization:

EC2: t3.micro, 20 GB EBS

RDS: unchanged

Estimated Monthly Cost: $25.18

Annual Cost: $302.16

💡 Monthly Savings: $10.42
💡 Annual Savings: $125.04

🖼️ Screenshots & Exports

All evidence of lab execution is included:

/images: screenshots for each major step

/exports: pre- and post-optimization cost estimate CSVs

🚀 Key Takeaways

Use AWS CLI to manage and optimize EC2 infrastructure

Understand the financial impact of right-sizing resources

Apply AWS Pricing Calculator for service cost forecasting

🔗 Useful Links

AWS Pricing Calculator

AWS EC2 Pricing

AWS RDS Pricing

AWS EBS Pricing

🙏 Author

Ime BenAWS Cloud Practitioner & Security AnalystGitHub: ime-cloud-sec-analyst

📅 Date Completed: June 27, 2025

📢 Share & Connect

If you found this helpful:

⭐ Star the repository

📝 Share your feedback

📣 Post your learning with #AWSLearning #CloudOptimization

