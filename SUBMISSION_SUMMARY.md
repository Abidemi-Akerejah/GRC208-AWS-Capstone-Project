# GRC208 AWS Capstone - Student Submission

## Student Information
- **Name**: Abidemi Zainab Akerejah
- **Student ID**: GRC25/10323
- **Course**: GRC208 - Governance, Risk, and Compliance Capstone
- **Instructor**: Aminu Idris
- **Submission Date**: 2/04/2026
- **AWS Account ID**: 211125455591
- **Region**: us-east-1
- **Environment**: AWS Academy Learner Lab

---

## Task Completed

### Configuration
- [x] Created `.env` file with 12 environment variables
- [x] Verified database endpoint, bucket names, Lambda ARN

### Monitoring & Compliance
- [x] Created CloudWatch alarm: `grc-lambda-errors`
- [x] Created CloudWatch alarm: `grc-rds-high-cpu`
- [x] Enabled CloudTrail trail: `grc-trail` with S3 logging
- [x] Created EventBridge rule: `grc-compliance-check` (hourly)

### Backup & Recovery
- [x] Created RDS snapshot: `grc-capstone-snapshot-20260329` (Status: available)

### Testing & Validation
- [x] Executed `test_cases.py`
- [x] **Result: 22/22 tests PASSED** 

### Infrastructure Verified
- [x] 4 S3 buckets confirmed
- [x] Lambda function `grc-compliance-monitor` deployed
- [x] RDS instance `grc-capstone-db` status: available
- [x] CloudWatch alarms active
- [x] EventBridge rule enabled

