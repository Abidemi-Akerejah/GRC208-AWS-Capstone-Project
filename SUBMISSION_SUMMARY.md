# GRC208 AWS Capstone - Student Submission

- **Name**: Abidemi Zainab Akerejah
- **Student ID**: GRC25/10323
- **Course**: GRC208 - Governance, Risk, and Compliance Capstone
- **Instructor**: Aminu Idris ,AMPN, CCNA, CompTIA Security+, CEH, OSCP, CISSP
- **Submission Date**: 03/04/2026
## AWS Environment
- **Account Type**: Personal AWS Free Tier Account
- **Account ID**: 768499314195
- **Region**: us-east-1

## Infrastructure Deployed 
| Resource | Status | Details |
|----------|--------|---------|
| Network Stack |  CREATE_COMPLETE | VPC, subnets, security groups |
| S3 Buckets |  4 Created | evidence, reports, config, cloudtrail |
| DynamoDB Tables |  3 Created | controls, risk, compliance |
| RDS Database | Available | MySQL 8.0.44, db.t3.micro |
| Lambda Function |  Active | grc-compliance-monitor |
| CloudWatch Alarms |  3 Active | billing, lambda-errors, rds-cpu |
| CloudTrail |  Logging Enabled | grc-trail → S3 |
| EventBridge Rule |  ENABLED | hourly compliance checks |
| RDS Snapshot |  Available | manual backup |

## Validation Results 
Ran 22 tests in 0.028s
OK


## Compliance Requirements
- [x] $10 billing alert configured
- [x] All services within AWS Free Tier limits
- [x] Evidence screenshots captured in `evidence/` folder

### Lifecycle Management Note

AWS notified me that RDS MySQL 8.0 reaches end of standard support on July 31, 2026. 
Evidence can be found in the evidence folder

**Production Recommendation:**
- Schedule major version upgrade (MySQL 8.4 or 9.0) before July 2026
- Test upgrade in staging environment using RDS snapshots
- Consider Blue/Green deployments for minimal downtime
- Budget for Extended Support only if business requirements delay upgrade

This demonstrates proactive lifecycle governance — a core GRC competency.
