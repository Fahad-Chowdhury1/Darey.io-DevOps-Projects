# <p align="center"> Shell Scripting Journey into Cloud Computing

### Introduction
In this part of my project i will hypoethetically act as the "achitect" of this project. I am tasked with specifically explaining what i think the requirement is rather than writing out an actual code at the moment. This is common DevOps practice whereby you define the logic and scope before touching the CLI. 

Based on the docoument provided to me within the project, The core objective is to create a Bash automation script for "DataWise Solutions." This script will allow an e-commerce client to instantly deploy a standardized data science environment on AWS without manual configuration in the AWS Console.

### Core Infrastructure Components
The script is responsible for provisioning two main types of resources:

- Amazon EC2: Virtual servers to handle the heavy computational tasks (machine learning models and data processing).

- Amazon S3: Scalable storage buckets to hold the client’s customer interaction datasets.


### Technical Requirements

- <b>Functions:</b> Creating separate blocks of code for create_ec2, create_s3, and check_status to keep the script organized.

- <b>Arrays:</b> Storing the IDs or names of created resources in a list so the script can track or delete them easily later.

- <b>Environment Variables:</b> Keeping sensitive data such as the AWS_ACCESS_KEY and global settings in this instance the region outside the main logic for security.

- <b>CLI Arguments:</b> Allowing the user to pass data when running the script for example  "./setup.sh t2.micro my-data-bucket" to make it flexible.

- <b>Error Handling:</b> Adding logic to detect if a command fails (e.g., if a bucket name is already taken) and exiting gracefully with a helpful message.

### Success Criteria
The requirement is met if the script can take a few user inputs and successfully output a ready to use EC2 instance and S3 bucket, while handling any AWS service errors that might occur during the process.