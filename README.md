# LAB-12--ACESS-S3-FROM-INSTANCE-USING-IAM-ROLE-
you can access s3 bucket list in ec2 

## EC2 IAM Role – Access S3 from Instance

### What you will learn
- Create IAM Role for EC2  
- Attach S3 Read Access policy  
- Assign role to EC2 instance  
- Access S3 using AWS CLI without credentials  

---

### Step 1: Create IAM Role
- Go to AWS Console → IAM  
- Click **Roles → Create role**  
- Select:
  - Trusted entity: **AWS service**
  - Use case: **EC2**
- Click **Next**

---

### Step 2: Attach Policy
- Search and select:
  - **AmazonS3ReadOnlyAccess**
- Click **Next**

---

### Step 3: Name the Role
- Role name: `EC2-S3-Read-Role`
- Click **Create role**

---

### Step 4: Launch EC2 Instance
- Go to EC2 → **Launch instance**
- Configure:
  - Name: `Amazon-Linux`
  - AMI: Amazon Linux  
  - Instance type: `t3.micro`
  - Key pair: create/select  
- Launch instance  

---

### Step 5: Attach IAM Role to EC2
- Select your instance  
- Click **Actions → Security → Modify IAM role**
- Choose:
  - `EC2-S3-Read-Role`
- Click **Update IAM role**

---

### Step 6: Connect to EC2
Use Command Prompt / Git Bash:

```bash
ssh -i your-key.pem ec2-user@your-public-ip
```

---

### Step 7: Test S3 Access
Run:

```bash
aws s3 ls
```

👉 This will list all S3 buckets  

---

### Important Concept
- No access keys used  
- EC2 gets temporary credentials via IAM Role  
- More secure than storing keys  

---

### Common Issues
- `aws command not found` → install AWS CLI  
- No output → check IAM role attached  
- Permission denied → check key pair  

---

### Final Result
- IAM Role created  
- Role attached to EC2  
- Successfully accessed S3 using CLI  

