# Text-to-Speech Converter

## Overview

The Text-to-Speech Converter is a serverless application built on AWS that converts text files into speech audio files using Amazon Polly. It leverages AWS Lambda functions to process uploaded text files from an S3 bucket and generate corresponding MP3 audio files.

## Features

- Automatic conversion of text files to speech audio using Amazon Polly.
- Integration with AWS S3 for file storage and event-driven triggers.
- Scalable and cost-effective serverless architecture.

## Project Structure

text-to-speech-converter/

├── lambda_function.py # Lambda function code.

├── README.md # Project overview and usage guide.

└── requirements.txt # Python dependencies.


## Setup Instructions

1. Clone the repository to your local machine.
2. Set up an AWS account and configure AWS CLI with appropriate credentials.
3. Deploy the Lambda function using AWS SAM or manually via the AWS Management Console.
4. Configure IAM roles and permissions to allow access to necessary AWS services (S3, Polly).
5. Configure S3 event notifications to trigger the Lambda function upon file uploads.
6. Upload text files to the designated S3 bucket to initiate the conversion process.

## Usage Guide

- Upload text files to the designated S3 bucket manually or programmatically.
- Monitor the Lambda function execution in the AWS Management Console or CloudWatch logs.
- Retrieve synthesized speech audio files from the output S3 bucket after conversion is completed.

## Configurable Options

- Source Bucket: You can specify the source S3 bucket from which text files will be retrieved for conversion to speech. This parameter is configurable in the lambda_handler function under the variable source_bucket.

- Destination Bucket: You can specify the destination S3 bucket where the synthesized speech audio files will be stored after conversion. This parameter is configurable in the lambda_handler function under the variable destination_bucket.

- Output Format: The output format of the synthesized speech can be customized. Currently, the function is set to generate MP3 audio files (OutputFormat='mp3'). However, you can modify this parameter to generate speech in other formats supported by Amazon Polly.

- Voice Selection: You can choose the voice used for speech synthesis by specifying the VoiceId parameter in the synthesize_speech function.

## Dependencies

- Python 3.x
- boto3
- AWS CLI

## Issues Encountered

### Access Denied Error

**Description:** Access Denied error occurred when the Lambda function lacked sufficient permissions to access or write to the S3 bucket.

**Solution:** Adjusted IAM roles and permissions to grant the necessary access to the Lambda function.

### KeyError: 'Records'

**Description:** KeyError: 'Records' error occurred when the Lambda function was triggered by an event without the expected 'Records' field.

**Solution:** Implemented graceful handling to prevent function crashes in such cases.

### Timeout Error

**Description:** Timeout error occurred when the Lambda function timed out before completing the text-to-speech conversion, especially for larger text files.

**Solution:** Increased the timeout configuration to allow for longer processing times.

### Malformed or Missing Parameters

**Description:** Malformed or missing parameters led to errors during execution, such as incorrect bucket names or file keys.

**Solution:** Ensured that all required parameters were correctly provided to the Lambda function.

# Contributing Guidelines

Thank you for considering contributing to the Text-to-Speech Converter project! Contributions from developers like you help improve and grow the project. Below are some guidelines to help you get started:

## Bug Reports

If you encounter any bugs or unexpected behavior while using the Text-to-Speech Converter, please submit a detailed bug report. Include information such as:

- Description of the issue
- Steps to reproduce the issue
- Expected behavior
- Actual behavior
- Any error messages or screenshots

You can submit bug reports by [opening an issue](https://github.com/CodedbyChino/Text-to-Speech-Converter-/blob/main/ISSUES.md) in the GitHub repository.

## Feature Requests

If you have ideas for new features or improvements to the Text-to-Speech Converter, we'd love to hear from you! Please submit a feature request with the following details:

- Description of the feature or enhancement
- Justification for the feature (optional)
- Any relevant use cases or examples

You can submit feature requests by [opening an issue](https://github.com/CodedbyChino/Text-to-Speech-Converter-/blob/main/ISSUES.md) in the GitHub repository.

## Pull Requests

We welcome contributions in the form of pull requests (PRs) to improve the Text-to-Speech Converter. Before submitting a PR, please ensure the following:

- Fork the repository and create a new branch for your changes.
- Write clear and concise commit messages.
- Test your changes thoroughly to ensure they work as expected.
- Include documentation updates if necessary.
- Follow the [code style guidelines](https://github.com/CodedbyChino/Text-to-Speech-Converter-/blob/main/CodeStyleGuidelines.md) of the project.

Once your changes are ready, submit a pull request against the `main` branch of the repository. We'll review your changes and merge them if they align with the project goals and standards.

## Code Style Guidelines

To maintain consistency and readability in the codebase, we follow certain code style guidelines. Please refer to the [Code Style Guidelines](https://github.com/CodedbyChino/Text-to-Speech-Converter-/blob/main/CodeStyleGuidelines.md) document for more details.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
