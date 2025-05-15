# Lacework FortiCNAPP AWS Costs

## Introduction

When Lacework FortiCNAPP is integrated with AWS, it is helpful to understand any costs associated with the integration. This document outlines the potential additional AWS costs associated with the integration.

## Executive Summary of AWS Costs

All costs are based on an estimated monthly basis in USD.

- Agent Egress: $0.27 per server (EC2) with agent per month
- Agentless Storage: $1.00 per server (EC2) per month for S3 Local snapshot storage
- Agentless Compute: $15.00 per month (ECS Task for snapshot/scan)
- CloudTrail Egress: $0.45 per account per month for CloudTrail

## Lacework Agent

The Lacework agent is a minimal footprint agent is installed on AWS EC2 instances including EKS nodes. CPU usage is typically <1% depending on workload. Data egress is outbound only, typically 100 MB per agent per day. 

- Egress cost estimation: 1GB × $0.09/GB = $0.27 per server (EC2) with agent per month.

## AWS Agentless Workload Scanning

The Lacework Agentless Workload Scanning is an ECS task scheduled to run on a regular basis. Data egress is scan metadata only. There are two sources of cost for this service:

- ECS Task cost estimation: ~$15.00 of compute per month
- S3 for Local snapshot storage cost estimation: ~$1.00 per server (EC2) per month

## AWS Account Inventory

The AWS Account Inventory configuration for compliance reports is pulled directly from AWS APIs, so there is no egress cost.

## AWS CloudTrail

Lacework analyzes AWS CloudTrail management events from the CloudTrail S3 bucket. The egress cost is based on the size of the CloudTrail logs.

- CloudTrail egress cost estimation: 5GB at $0.09/GB = $0.45 per account per month

## AWS Additional Cloudtrails

AWS provides the first CloudTrail in an account for free. Additional CloudTrail buckets are charged per month. For a Lacework trial, a new CloudTrail bucket may be created, which is not free. It is recommended instead to point Lacework to the existing organization CloudTrail bucket.






