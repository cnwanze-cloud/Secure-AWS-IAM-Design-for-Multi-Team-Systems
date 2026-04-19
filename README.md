# Secure-AWS-IAM-Design-for-Multi-Team-Systems
Built a secure AWS IAM system that eliminates over-permissioned access by enforcing least privilege across developers, DevOps, QA, finance, and interns.

---

## Project Scenario
A growing tech company, **CloudNova Solutions**, is building a cloud-based application hosted on AWS. The company has multiple teams:

- **Developers** – Build and deploy applications  
- **QA/Test Engineers** – Test applications  
- **DevOps Engineers** – Manage infrastructure  
- **Finance Team** – View billing only  
- **Interns** – Limited read-only access  

The company previously faced **security risks due to overly permissive access**, including developers having admin rights.

---

## Project Objective
Design and implement a secure Identity and Access Management (IAM) structure that enforces:

- Least privilege access  
- Role-Based Access Control (RBAC)  
- Separation of duties  
- Secure authentication policies  

---

## AWS Services Used
- Amazon S3  
- Amazon EC2  
- AWS IAM  
- IAM Users  
- IAM Groups  
- IAM Roles  
- IAM Policies  
- IAM Policy Simulator  

---

## Security Requirements

### Developers
- Full access to:
  - EC2  
  - S3 (read/write)  
- No access to IAM or Billing  

---

### QA/Test Engineers
- Read-only access to:
  - EC2  
  - CloudWatch Logs  
- Ability to start/stop test instances  

---

### DevOps Engineers
- Full administrative access to:
  - EC2  
  - S3  
  - CloudWatch  
- No billing access  

---

### Finance Team
- Access only to:
  - Billing Dashboard  
- No access to compute or storage services  

---

### Interns
- Read-only access to:
  - S3 buckets   

---

## IAM Architecture Design
<img width="974" height="437" alt="image" src="https://github.com/user-attachments/assets/cfc7e9f3-42d2-44d8-88f3-ea144e4f3de5" />


---

## Project Outcome
This project demonstrates how to:

- Design secure IAM architecture for real-world organizations  
- Prevent over-permissioning and security breaches  
- Implement structured access control across multiple teams  
- Apply AWS best practices in identity and access management

---

## Step-by-Step Implementation

### 1. Create an S3 Bucket
- Create a bucket for application storage  
- Configure appropriate access settings  
<img width="962" height="299" alt="image" src="https://github.com/user-attachments/assets/38dad3ec-43e4-4b4c-b949-bc0bf11ab6cd" />

---

### 2. Create IAM Groups
Create the following groups:
- Developers  
- QA-Engineers  
- DevOps  
- Finance  
- Interns  
<img width="961" height="401" alt="image" src="https://github.com/user-attachments/assets/656a428f-f8c6-4069-bb90-1b34f9dc786e" />

---

### 3. Create Custom IAM Policies
Define policies based on each team’s access requirements:

- Restrict access using least privilege principle    
<img width="959" height="426" alt="image" src="https://github.com/user-attachments/assets/54156d3b-4dfb-4cf9-b10b-0fd7c2986a27" />

---

### 4. Attach Policies to Groups
- Attach the appropriate policy to each IAM group  
<img width="798" height="414" alt="image" src="https://github.com/user-attachments/assets/425507a3-29b9-45e7-bfc6-5b1ddc7af8ca" />

---

### 5. Create IAM Users
- Create users, and assign to their respective IAM groups  
<img width="962" height="470" alt="image" src="https://github.com/user-attachments/assets/0b474bcf-a234-49d3-ae5d-36e546fc5750" />

---

### 6. Enable Multi-Factor Authentication (MFA)
- Configure Virtual MFA for all users  
<img width="959" height="465" alt="image" src="https://github.com/user-attachments/assets/04e894e9-e257-4212-980b-e72d78c8e11b" />

### 7. Set Password Policy
- Minimum 1 uppercase letter  
- Minimum 1 lowercase letter  
- Minimum 1 number  
- Minimum 1 special character  
- Enable password expiration  
<img width="962" height="438" alt="image" src="https://github.com/user-attachments/assets/eac7e1ef-fb0a-4f1d-9cf9-8f1ab69d7d37" />

---

### 8. Create IAM Role for EC2
- Create a role with appropriate permissions  
- Attach role to an EC2 instance  
<img width="960" height="300" alt="image" src="https://github.com/user-attachments/assets/8d51995b-d995-4ff5-8ff1-18d4949bc04b" />
<img width="963" height="150" alt="image" src="https://github.com/user-attachments/assets/233d7d48-32ee-42bb-8906-d7a902ef3ed8" />
<img width="954" height="471" alt="image" src="https://github.com/user-attachments/assets/0643db03-63e2-4516-ba84-b2991798cb33" />


### 9. Test EC2 Role
- Verify instance can access allowed AWS services  
- Ensure no unintended permissions are granted  
<img width="960" height="350" alt="image" src="https://github.com/user-attachments/assets/32dd710d-f30f-46be-994f-34e486fd9828" />
<img width="968" height="139" alt="image" src="https://github.com/user-attachments/assets/cfabbae3-2b0e-4ff0-98c0-046aec4fca63" />
<img width="963" height="343" alt="image" src="https://github.com/user-attachments/assets/3a100b88-236e-4312-97d6-2f9f5b3a3a0e" />

---

### 10. Test User Groups Permissions (IAM Policy Simulator)
- Simulate user/group permissions  
- Validate:
  - Allowed actions  
  - Denied actions  
- Confirm enforcement of least privilege  
<img width="1006" height="513" alt="image" src="https://github.com/user-attachments/assets/379f5c50-2db6-402b-860f-47c55148bc0a" />
<img width="973" height="484" alt="image" src="https://github.com/user-attachments/assets/8a406524-0689-40cf-8a0d-08c3c354420c" />
<img width="962" height="166" alt="image" src="https://github.com/user-attachments/assets/55b23d85-483f-439a-a153-75771fee9e8a" />

---

