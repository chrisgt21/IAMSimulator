# IAMSimulator
This repo will have details on how to run the AWS IAM simulator. This docker container will run simulations against your AWS environment and provide a report, detailing which IAM resources have potential elevated access. 

## Getting Started
In order to start using this Docker container, you will need to create a docker image locally and copy a config file. 

1. Pull down repository locally
2. Edit the config.json file to target your environment
    - At least one user, role, or group must be defined
    - At least one service must be defined
    - AWS Account number must be specified
    - S3 Bucket name must be specified to share findings
3. Build the docker image 

`docker build . -t CUSTOM_NAME`

4. Run the docker container
    - If you are running this container on an AWS instance (EC2, ECS, etc), no credentials need to be specified. If this container is not running within AWS, the environment variables must be set to gain access. 

`docker run CUSTOM_NAME`

`docker run -e AWS_ACCESS_KEY={AWS_ACCESS_KEY} -e AWS_SECRET_ACCESS_KEY={AWS_SECRET_KEY} CUSTOM_NAME`

5. Check the S3 bucket you specified in the config file for the findings