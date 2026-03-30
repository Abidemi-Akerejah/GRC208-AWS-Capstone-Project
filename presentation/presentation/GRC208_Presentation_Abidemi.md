# GRC208 AWS Capstone Project
## Governance, Risk, and Compliance Platform on AWS

**Student**: Abidemi Zainab Akerejah  
**Student ID**: GRC25/10323  
**Instructor**: Aminu Idris  
**Date**: 02/04/2026  
**AWS Account**: 211125455591 | 
**Region**: us-east-1

 Repository: https://github.com/Abidemi-Akerejah/GRC208-AWS-Capstone-Project

 ## Deployment

 A cloud-based GRC (Governance, Risk, Compliance) platform on AWS

### Core Components:

• Infrastructure: VPC, RDS MySQL, S3 buckets, Lambda functions

• Monitoring: CloudWatch alarms for Lambda & RDS

• Audit: CloudTrail logging to S3

• Automation: EventBridge scheduled compliance checks

• Backup: RDS manual snapshot for disaster recovery


### Validation:
• 22/22 automated tests PASSED 

• All infrastructure verified via AWS CLI

• Configuration documented in .env file


## The Challenge: Complexity in Governance, Risk, and Compliance

🔴 Compliance requirements are extensive:

• ISO 27001, NIST CSF, SOC 2, PCI DSS, HIPAA, GDPR

🔴 Manual compliance checks are:

• Time-consuming

• Error-prone

• Hard to audit


🔴 Organizations need:

• Automated monitoring

• Audit trails

• Scalable, secure infrastructure


## Solution:
Leverage AWS native services to build an automated, auditable GRC platform.

## System Architecture

Internet
   ↓
[Public Subnet]

   ↓
Application Load Balancer → Lambda (grc-compliance-monitor)

                              ↓
                    [Private Subnet]
                    
                              ↓
                    RDS MySQL (grc-capstone-db)
                    
                              ↓
                    S3 Buckets (evidence, reports, logs)
                    
                              ↓
              CloudWatch + CloudTrail + EventBridge
              

### Key Design Principles:

• Security: Private subnets for database

• Scalability: Serverless Lambda functions

• Auditability: CloudTrail logs all API calls

• Automation: EventBridge triggers hourly checks


## Services and Contributions

| Service | Configuration | Purpose |
|---------|-----------------|---------|
| **CloudWatch** | 2 alarms created | Monitor Lambda errors, RDS CPU |
| **CloudTrail** | grc-trail enabled | Audit all AWS API calls |
| **EventBridge** | Hourly rule: grc-compliance-check | Automate compliance checks |
| **RDS** | Manual snapshot created | Disaster recovery backup |
| **S3** | 4 buckets verified | Secure storage for evidence/logs |
| **Lambda** | grc-compliance-monitor verified | Serverless compliance logic |
| **CloudFormation** | 2 stacks: CREATE_COMPLETE | Infrastructure as Code |

### All verified via AWS CLI commands 

## Key Commands Executed

```bash
# 1. Verify infrastructure stacks
aws cloudformation describe-stacks --stack-name grc-capstone-network-stack
# Result: CREATE_COMPLETE ✅

# 2. Create CloudWatch alarms
aws cloudwatch put-metric-alarm --alarm-name "grc-lambda-errors" ...

# 3. Enable CloudTrail audit logging
aws cloudtrail create-trail --name grc-trail --s3-bucket-name ...

# 4. Create EventBridge automation rule
aws events put-rule --name grc-compliance-check --schedule-expression "rate(1 hour)"

# 5. Create RDS backup snapshot
aws rds create-db-snapshot --db-instance-identifier grc-capstone-db ...

# 6. Run validation tests
python3 test_cases.py
# Result: Ran 22 tests in 0.001s - OK ✅

---

### Test Results - 
## Validation: 22/22 Tests PASSED ✅


### Test Categories Passed:
Compliance Monitoring (3 tests)  
Risk Assessment (3 tests)  
Data Validation (4 tests)  
Database Operations (3 tests)  
Framework Mapping (2 tests)  
Integration Workflows (3 tests)  
Additional Validation (4 tests)  

### Why This Matters:
• Confirms backend compliance logic works correctly  
• Validates risk calculations and data structures  
• Provides confidence in the platform's core functionality
## Monitoring Dashboard (Conceptual)

### CloudWatch Alarms:
grc-lambda-errors  
   → Alerts if compliance Lambda function fails  
   → Threshold: 1 error in 5 minutes  

grc-rds-high-cpu  
   → Alerts if database CPU > 80%  
   → Threshold: 2 consecutive periods  

### EventBridge Automation:
grc-compliance-check  
   → Schedule: rate(1 hour)  
   → Target: grc-compliance-monitor Lambda  
   → Purpose: Automated hourly compliance validation  

### CloudTrail Audit:
grc-trail  
   → Logs: All AWS API calls  
   → Destination: S3 bucket grc-cloudtrail-logs-*  
   → Purpose: Compliance audit trail

## Challenges Encountered in Learner Lab

| Challenge | Cause | My Response |
|-----------|-------|------------|
| **AWS Config Delivery Channel** | LabRole lacks `config:PutDeliveryChannel` permission | Documented as Learner Lab constraint; architecture designed for Config integration in production |
| **Direct MySQL Connection** | RDS in private subnet (security design) | Explained as intentional security; Lambda has VPC access for application connectivity |
| **Frontend Dashboard Access** | Requires build + hosting beyond lab scope | Focused on backend validation; 22 tests confirm logic works |

### Key Learning:
Understanding constraints is part of real-world cloud engineering. Professional documentation of limitations demonstrates maturity.

## Technical Skills Gained

✅ AWS CLI proficiency  
✅ CloudFormation stack verification  
✅ CloudWatch alarm configuration  
✅ CloudTrail audit logging setup  
✅ EventBridge automation rules  
✅ RDS snapshot management  
✅ IAM role and permission understanding  

## GRC Concepts Mastered

✅ How AWS services enable compliance automation  
✅ Importance of audit trails (CloudTrail)  
✅ Monitoring for anomalies (CloudWatch)  
✅ Disaster recovery planning (RDS snapshots)  
✅ Security by design (private subnets, least privilege)  

## Professional Skills

✅ Documenting limitations honestly  
✅ Validating work with automated tests  
✅ Presenting technical work clearly  
✅ Working within environment constraints

## Submission Evidence Included

### In GitHub Repository:
 SUBMISSION_SUMMARY.md  
   → My personal work summary with checkboxes  

 evidence/cli_outputs.txt  
   → Raw AWS CLI command outputs observed during lab  

 evidence/DEPLOYMENT lab session screenshots.pdf  
   → Visual proof from my active lab session  

### Key Verification Commands (All Executed):
```bash
aws s3 ls | grep grc                    # 4 buckets confirmed
aws lambda list-functions --query ...   # grc-compliance-monitor verified
aws cloudwatch describe-alarms ...      # 2 alarms active
aws rds describe-db-snapshots ...       # Snapshot: available
python3 test_cases.py                   # 22/22 PASSED


---

### Key Takeaways 

Successfully:
• Configured monitoring, logging, and automation for GRC workloads  
• Validated deployment with 22/22 passing tests  
• Documented infrastructure limitations professionally  
• Demonstrated understanding of AWS security best practices  

This project prepares me to:
• Design compliant cloud architectures  
• Implement automated compliance monitoring  
• Document and communicate technical constraints  
• Continue learning AWS GRC services  


## Thank You!

Questions?

🔗 GitHub Repository:  
https://github.com/Abidemi-Akerejah/GRC208-AWS-Capstone-Project

Abidemi Zainab Akerejah 
Student ID: GRC25/10323
