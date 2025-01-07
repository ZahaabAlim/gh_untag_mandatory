
# Checking of Untagged Resources

This project is designed to help you identify AWS resources (S3 buckets, Lambda functions, and DynamoDB tables) that are missing mandatory tags. It uses a Python script to scan your AWS environment and generate reports, which are then uploaded as artifacts using GitHub Actions.

## Features

- **Automated Identification**: The script automatically identifies AWS resources that do not have the specified mandatory tags.
- **Report Generation**: It generates CSV reports for each type of resource (S3, Lambda, and DynamoDB) that are missing the mandatory tags.
- **Continuous Monitoring**: The GitHub Actions workflow ensures that the check is performed every time there is a push to the repository, providing continuous monitoring.

## How to Use

### Setup

1. **Clone the Repository**: Start by cloning the repository to your local machine.

2. **Install Dependencies**: Install the necessary Python dependencies using pip.

3. **Configure AWS Credentials**: Ensure your AWS credentials are configured properly. You can do this using the AWS CLI.

### Running the Script Locally

1. **Execute the Script**: Run the Python script to check for untagged resources in your AWS environment.
2. **Review Reports**: The script will generate CSV reports for S3, Lambda, and DynamoDB resources that are missing the mandatory tags. These reports will be saved in the repository directory.

### Using GitHub Actions

1. **Push to Repository**: The GitHub Actions workflow is triggered on every push to the repository.
2. **Automated Steps**: The workflow will:
   - Checkout the repository
   - Set up Python
   - Install dependencies
   - Configure AWS credentials
   - Run the script
   - Upload the generated reports as artifacts

3. **Access Reports**: After the workflow runs, you can download the reports from the GitHub Actions artifacts section.

## Contributing

Contributions are welcome! If you have any improvements or bug fixes, please open an issue or submit a pull request.

