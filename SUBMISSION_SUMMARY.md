# GRC208 AWS Capstone - Student Submission

- **Name**: Abidemi Zainab Akerejah
- **Student ID**: GRC25/10323
- **Course**: GRC208 - Governance, Risk, and Compliance Capstone
- **Instructor**: Aminu Idris ,AMPN, CCNA, CompTIA Security+, CEH, OSCP, CISSP
- **Submission Date**: 02/04/2026
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


## Project Manifest Completion Status

### Core Infrastructure Tasks (Completed)
- [x] Read and understood project documentation
- [x] Verified architecture via AWS CLI commands
- [x] Deployed network and database CloudFormation stacks
- [x] Configured environment variables (.env)
- [x] Set up monitoring (CloudWatch alarms, CloudTrail, EventBridge)
- [x] Created RDS snapshot for disaster recovery
- [x] Executed test suite: 22/22 tests PASSED

### Application-Level Tasks (Learner Lab Limitations)

#### Load Sample Data
- **Attempted**: `mysql -h $DB_ENDPOINT -u grcadmin -p grcdb < sample_data.sql`
- **Result**: Connection timeout
- **Cause**: RDS deployed in private subnet (security best practice)
- **Understanding**: This is intentional design; application components (Lambda) in same VPC can connect
- **Impact**: Sample data pre-loaded by lab; compliance logic validated via unit tests instead

#### Access GRC Application / Review Compliance Status / Generate Reports
- **Status**: Frontend deployment not executed
- **Cause**: grc-dashboard.jsx requires build step + hosting (beyond Learner Lab scope)
- **Understanding**: Infrastructure supports frontend deployment; Lambda provides backend API
- **Verification**: Backend compliance logic validated via 22 passing unit tests
- **Future Work**: Deploy frontend to S3 + CloudFront for full user experience

### Learning Outcomes
Despite application-level limitations, core GRC competencies demonstrated:
1. Cloud infrastructure design for compliance workloads
2. AWS native monitoring and audit logging configuration
3. Disaster recovery planning (RDS snapshots)
4. Infrastructure-as-Code understanding (CloudFormation)
5. Security best practices (private subnets, IAM roles, encryption)
6. Professional documentation of constraints and mitigations
