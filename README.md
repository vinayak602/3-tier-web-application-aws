# 3-tier-web-application-aws
# 3-Tier Web Application Deployment on AWS

Secure 3-tier web application deployment on AWS using VPC, EC2, ALB, and RDS with network isolation and database connectivity.

## Architecture
- **Tier 1 (Presentation):** Application Load Balancer in Public Subnets
- **Tier 2 (Application):** EC2 instances with Apache in Private Subnets  
- **Tier 3 (Database):** RDS MySQL in Private DB Subnet

## AWS Services Used
VPC, EC2, ALB, RDS, NAT Gateway, Internet Gateway, Security Groups, Route Tables, Target Groups

## Network Design
- VPC CIDR: 10.0.0.0/16
- Public Subnet 1a (10.0.1.0/24) - ALB + NAT Gateway
- Public Subnet 1b (10.0.2.0/24) - ALB + NAT Gateway
- Private App Subnet 1a (10.0.3.0/24) - EC2
- Private App Subnet 1b (10.0.4.0/24) - EC2
- Private DB Subnet - RDS

## Deployment Steps
1. Created custom VPC with 2 public and 2 private subnets across 2 AZs
2. Attached Internet Gateway and created NAT Gateway for private subnet internet access
3. Configured Security Groups:
   - ALB SG: Allow 80/443 from 0.0.0.0/0
   - EC2 SG: Allow 80 from ALB SG only
   - RDS SG: Allow 3306 from EC2 SG only
4. Launched EC2 instances with user-data for web server setup
5. Created Target Group and Application Load Balancer
6. Created RDS MySQL and tested connection from EC2
7. Verified high availability by stopping one EC2 - ALB routed traffic to healthy instance

## Key Learnings
VPC Peering, Subnetting, HA Architecture, Load Balancing, Security Group hardening, RDS connectivity

## Author
Vinayaka Garapatti | Linux | CCNA | AWS | DevOps | Bangalore
GitHub: github.com/vinayak602
