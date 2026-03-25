# Step 1: Create IAM Role
Go to AWS Console → IAM
Click Roles → Create role

- Select:
- Trusted entity: AWS service
- Use case: EC2
- Click Next
  
# Step 2: Attach Policy
Search and select:
- AmazonS3ReadOnlyAccess

Click Next
# Step 3: Name the Role
EC2-S3-Read-Role

Click Create role
# Step 4: Launch EC2 Instance
Go to EC2 → Launch instance

Configure:
- Name: Amazon-Linux
- AMI: Amazon Linux
- Instance type: t3.micro
- Key pair: create/select
Click Launch instance

# Step 5: Attach IAM Role to EC2
Select your instance
Click:
Actions → Security → Modify IAM role

Choose:
EC2-S3-Read-Role

Click Update IAM role

# Step 6: Connect to EC2
ssh -i your-key.pem ec2-user@your-public-ip

# Step 7: Test S3 Access
aws s3 ls

# Install AWS CLI (if needed)

sudo yum install aws-cli -y

# Fix Key Permission

chmod 400 your-key.pem

# Important Concept

- No access keys used
-  EC2 uses temporary credentials via IAM Role
- Secure method (recommended)

# Final Result

IAM Role created
Role attached to EC2
S3 accessed successfully
