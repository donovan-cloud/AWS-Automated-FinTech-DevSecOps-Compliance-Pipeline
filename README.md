# AWS Automated FinTech DevSecOps Compliance Pipeline

## Business Value
Manual security audits block deployment speed. This project implements a zero-trust automated gatekeeper that scans Infrastructure as Code (IaC) for critical compliance and security violations on every code commit. It guarantees 100% compliance before cloud infrastructure hits production, preventing costly data leaks and audit failures.

## Technical Architecture
- **Source Control:** AWS CodeCommit / GitHub Integration
- **Orchestration:** AWS CodePipeline
- **Execution Environment:** AWS CodeBuild
- **Compliance Tooling:** Checkov SAST Framework (Static Application Security Testing)
- **Target Infrastructure:** Secured Amazon S3 Tiers

## Automated Remediation Logs

### 1. Pipeline Blocks Compliance Failure
When an insecure, unencrypted S3 bucket configuration was committed, the Checkov static analysis stage immediately flagged the vulnerability (`CKV_AWS_145`) and safely aborted the build.

![Compliance Failure Verification](failed_build_log.jpg)

### 2. Pipeline Succeeds Post-Remediation
After updating the infrastructure code to enforce high-grade KMS encryption, block public access blocks, and activate bucket versioning, the pipeline configuration successfully cleared the compliance check and marked the build green.

![Successful Compliance Pass](successful_pipeline.jpg)
