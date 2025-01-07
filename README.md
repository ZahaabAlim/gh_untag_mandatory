## AWS Resource Monitoring and Reporting Automation

## Overview

This project automates the monitoring and reporting of AWS resources (S3 buckets, Lambda functions, and DynamoDB tables) to ensure they have the required tags. It uses Terraform to set up the necessary infrastructure and AWS Lambda functions to generate and publish CSV reports. Additionally, a GitHub Actions workflow is included to automate the execution of the script and upload the reports.

## Project Components

### Terraform Configuration

The Terraform configuration sets up the following AWS resources:

- **SNS Topic**: For publishing messages.
- **SQS Queues**: For storing messages for Lambda functions.
- **IAM Roles and Policies**: For granting necessary permissions to Lambda functions.
- **Lambda Functions**: For scraping EC2 and Cost Explorer data and generating reports.
- **EventBridge Rule**: For scheduling the Lambda functions.

### Lambda Functions

1. **Cost Explorer Scraper Lambda**:
   - Queries AWS Cost Explorer for cost and usage data.
   - Generates a CSV report and publishes it to an SNS topic.

2. **EC2 Scraper Lambda**:
   - Retrieves EC2 instance data from all regions.
   - Generates a CSV report and publishes it to an SNS topic.

3. **Untagged Resources Checker**:
   - Checks S3 buckets, Lambda functions, and DynamoDB tables for missing mandatory tags.
   - Generates CSV reports listing untagged resources.

### GitHub Actions Workflow

The GitHub Actions workflow automates the execution of the untagged resources checker script and uploads the generated reports as artifacts.

## Setup Instructions

### Prerequisites

- AWS account with necessary permissions.
- Terraform installed.
- Python 3.10 installed.
- GitHub repository with secrets for AWS credentials.

### Terraform Setup

1. Clone the repository.
2. Navigate to the Terraform directory.
3. Initialize Terraform:
   ```sh
   terraform init
   ```
4. Apply the Terraform configuration:
   ```sh
   terraform apply
   ```

### Lambda Functions Deployment

1. Ensure the Lambda function code (`ec2_scraper.py`, `cost_explorer_scrapper.py`, `untag.py`) is in the repository.
2. Terraform will automatically package and deploy the Lambda functions.

### GitHub Actions Workflow

1. Add AWS credentials to the GitHub repository secrets (`AWS_ACCESS_KEY`, `AWS_SECRET_ACCESS_KEY`).
2. The workflow will run on every push to the repository, executing the untagged resources checker script and uploading the reports.

## Usage

- The Lambda functions will run as scheduled by the EventBridge rule and generate reports.
- The GitHub Actions workflow will check for untagged resources and upload reports on every push.

## Contributing

Feel free to open issues or submit pull requests if you have any improvements or bug fixes.

