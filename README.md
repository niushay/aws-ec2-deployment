# Continuous Deployment On AWS EC2

This repository contains a YAML file that enables continuous deployment on AWS EC2 using GitHub Actions. The workflow defined in the YAML file automatically builds and deploys a Docker image to an AWS EC2 server whenever a push is made to the main branch or a pull request is created targeting the main branch.

## Workflow Overview

1. When a push or pull request is made to the main branch of your project repository, GitHub Actions triggers the defined workflow.

2. The workflow checks out the code from the repository.

3. AWS credentials are configured using the provided access key and secret key.

4. The workflow logs in to Docker Hub using the provided Docker Hub username and token.

5. The Docker image is built and pushed to Docker Hub.

6. The workflow connects to your AWS EC2 server via SSH using the provided private key.

7. The latest Docker image is pulled on the EC2 server.

8. The Docker container is run on the EC2 server, deploying the latest changes to your application.

## Prerequisites

Before using this workflow, ensure that you have the following set up:

- An AWS EC2 server running and accessible via SSH.
- Dockerfile: A Dockerfile in your project repository that defines the necessary steps to build your application's Docker image.
- Docker Hub account: You need an account on Docker Hub to store and access your Docker images.
- AWS access key and secret key: Obtain the access key and secret key from your AWS account with sufficient permissions to deploy on EC2.

## Usage

To enable continuous deployment for your project, follow these steps:

1. Copy the contents of the provided `.github/workflows/pipeline.yml` file and create a new file named `pipeline.yml` in your project repository's `.github/workflows/` directory.

2. Commit and push the `pipeline.yml` file to your GitHub repository.

3. In your GitHub repository settings, navigate to "Secrets" and create the following repository secrets:

   - `AWS_ACCESS_KEY_ID`: The AWS access key ID.
   - `AWS_SECRET_ACCESS_KEY`: The AWS secret access key.
   - `DOCKERHUB_TOKEN`: The token or password for your Docker Hub account.
   - `PRIVATE_KEY`: The private key required to SSH into your EC2 server.

4. Save the secrets.

From now on, every push to the main branch or pull request targeting the main branch will trigger the continuous deployment workflow. The workflow will build the Docker image, push it to Docker Hub, and deploy it to your AWS EC2 server automatically.

## Customize the Workflow

You can customize the workflow to fit your specific requirements. For example, you can modify the AWS region, Docker image tags, or add additional steps as needed.

Refer to the GitHub Actions documentation for more details on customization options: [GitHub Actions Workflow Syntax](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvement, feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
