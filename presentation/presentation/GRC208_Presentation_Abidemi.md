# GRC208 AWS Capstone Project
## Governance, Risk, and Compliance Platform on AWS

| Field | Value |
|-------|-------|
| **Student** | Abidemi Zainab Akerejah |
| **Student ID** | GRC/2025/10323 |
| **Instructor** | Aminu Idris, AMPN, CCNA, CompTIA Security+, CEH, OSCP, CISSP |
| **Course** | GRC208 - Governance, Risk, and Compliance Capstone |
| **Submission Date** | April 2026 |
| **AWS Account** | `768499314195` (Personal Free Tier) |
| **Region** | `us-east-1` |
| **Repository** | [github.com/Abidemi-Akerejah/GRC208-AWS-Capstone-Project](https://github.com/Abidemi-Akerejah/GRC208-AWS-Capstone-Project) |

---

## Executive Summary

A cloud-based GRC (Governance, Risk, Compliance) platform deployed on AWS that automates compliance monitoring, risk assessment, and audit logging using native AWS services.

### Deployment Status: COMPLETE

---

## System Architecture
Internet
↓


[Public Subnet]
↓


Application Load Balancer → Lambda (grc-compliance-monitor)
↓


[Private Subnet]
↓



RDS MySQL (grc-capstone-db) ✓ available
↓


S3 Buckets (evidence, reports, config, cloudtrail-logs) ✓

↓

CloudWatch + CloudTrail + EventBridge + AWS Config ✓


### Key Design Principles

| Principle | Implementation |
|-----------|---------------|
| 🔐 Security | Private subnets for RDS, least-privilege IAM roles |
| ⚡ Scalability | Serverless Lambda functions, PAY_PER_REQUEST DynamoDB |
| 📝 Auditability | CloudTrail logs all API calls to S3 |
| 🤖 Automation | EventBridge triggers hourly compliance checks |
| 💾 Recovery | RDS manual snapshots + S3 versioning |

---

## Deployed Infrastructure

### Core Components (All Verified via AWS CLI)

| Component | Resource Name | Status | Verification Command |
|-----------|--------------|--------|---------------------|
| **Network Stack** | `grc-capstone-network-stack` |  `CREATE_COMPLETE` | `aws cloudformation describe-stacks --stack-name grc-capstone-network-stack` |
| **RDS Database** | `grc-capstone-db` | ] `available` | `aws rds describe-db-instances --db-instance-identifier grc-capstone-db --query "DBInstances[0].DBInstanceStatus"` |
| **S3 Buckets** | 4 buckets with `grc-*` prefix | ] Created | `aws s3 ls \| grep grc-` |
| **DynamoDB Tables** | `grc-capstone-controls`, `grc-capstone-risk`, `grc-capstone-compliance` | ] Created | `aws dynamodb list-tables --query "TableNames[?contains(@, 'grc-capstone')]"` |
| **Lambda Function** | `grc-compliance-monitor` | ] `Active` | `aws lambda get-function --function-name grc-compliance-monitor --query "Configuration.State"` |
| **CloudWatch Alarms** | `grc-lambda-errors`, `grc-rds-high-cpu`, `grc-capstone-billing-alert-10` |  Active | `aws cloudwatch describe-alarms --query "MetricAlarms[?contains(AlarmName, 'grc-')].AlarmName"` |
| **CloudTrail** | `grc-trail` |  Logging: `true` | `aws cloudtrail describe-trails --query "trailList[0].{Name:Name,Logging:IsLogging}"` |
| **EventBridge Rule** | `grc-compliance-check` |  `ENABLED`, `rate(1 hour)` | `aws events describe-rule --name grc-compliance-check --query "{Name:Name,State:State}"` |
| **RDS Snapshot** | `grc-capstone-snapshot` |  `available` | `aws rds describe-db-snapshots --snapshot-type manual --query "DBSnapshots[0].{ID:DBSnapshotIdentifier,Status:Status}"` |
| **AWS Config** | `default` recorder |  Enabled, resources discovering | `aws configservice describe-configuration-recorder-status --query "ConfigurationRecordersStatus[0].{Recording:recording,LastStatus:lastStatus}"` |

### Configuration Management

- `.env` file with 12 environment variables (force-added to Git for submission)
- All CLI commands documented in `evidence/` folder
- Infrastructure as Code via CloudFormation (network stack) + manual deployment (database stack)

---

### Validation Results: 22/22 Tests PASSED

$ python3 test_cases.py
Ran 22 tests in 0.028s
OK

Services Verified:
CloudWatch + CloudTrail + EventBridge + AWS Config ✓

Test Categories Validated:
• Compliance Monitoring (3 tests):
Validate compliance percentage calculation, report generation, non-compliant rule detection
• Risk Assessment (3 tests):
Verify risk level classification, matrix scoring, risk score calculation
• Data Validation (4 tests):
Confirm asset classification, control ID format, criticality level, risk status validation
• Database Operations (3 tests):
Test compliance snapshot, control record, risk register data structures
• Framework Mapping (2 tests):
Validate framework control count and version format
• Audit Logging (3 tests):
Verify audit log action types, entity types, entry structure
• Report Generation (2 tests):
Test compliance and risk report content requirements
• Integration Workflows (2 tests):
Validate compliance-to-risk and control-to-audit end-to-end logic
