# Lacework FortiCNAPP Cloud Costs

## Introduction

This document outlines additional cloud costs when using Lacework FortiCNAPP for AWS and Azure.

## Executive Summary

All costs are monthly estimates in USD.

### AWS

- Agentless Workload Scanning: ~$1.00 per workload per month (at scale, inclusive of ECS compute and snapshot storage)

Additional costs if AWS accounts are in a different region from the Lacework instance (eg. ap-southeast-2 for Sydney, us-east-1 for Virginia, eu-central-1 for Frankfurt, ap-southeast-1 for Singapore):

- Agent Egress: $0.27 per server (EC2) with agent per month
- CloudTrail Egress: $0.45 per account per month for CloudTrail

### Azure

- Agentless Workload Scanning: ~$0.50 per VM per month (at scale, inclusive of storage, compute and NAT gateway)
  - NAT Gateway: $35.00 flat per month

Disclaimer: These are estimates only. Actual costs may vary. Test in your own cloud account to determine actual expenses.

## Lacework Agent

The Lacework agent is installed on EC2 instances and EKS nodes. CPU usage is typically <1%. Data egress is ~100 MB per agent per day.

- Egress cost: 3GB × $0.09/GB = $0.27 per server per month

## AWS Agentless Workload Scanning

An ECS task runs on a regular schedule. Data egress is scan metadata only.

- Cost: ~$1.00 per workload per month (includes ECS compute and snapshot storage)

## AWS Account Inventory

Pulled directly from AWS APIs. No egress cost.

## AWS CloudTrail

Lacework analyzes CloudTrail management events from the S3 bucket.

- Egress cost: 5GB × $0.09/GB = $0.45 per account per month

## AWS Additional Cloudtrails

The first CloudTrail in an account is free. Additional buckets are charged monthly. For trials, point Lacework to your existing organization CloudTrail bucket instead of creating a new one.

## Azure Agentless Workload Scanning

Costs include storage, compute, and NAT gateway.

- Cost: ~$0.50 per VM per month (at scale, inclusive of storage, compute and NAT gateway)
- NAT Gateway: $35.00 flat per month






