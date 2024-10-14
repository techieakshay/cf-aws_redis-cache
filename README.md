# AWS CloudFormation - Redis Cluster Deployment

This CloudFormation template creates an **Amazon Redis Cluster** with the following components:
- **Redis Cluster**: Hosts your redis db.
- **Security Group**: Secures access to the cluster instances.
- **Replication Group**: Replication instances for the data.


## Architecture
The stack consists of:
1. **Redis Cluster**: An empty redis db cluster.
2. **Security Group**: Allows access only to the necessary ports.

## Prerequisites
- AWS CLI or access to AWS Console.
- IAM permissions to create ECS, EC2, RedisDb, and related resources.

## Deployment Instructions

### 1. Deploy the CloudFormation Stack

#### Using AWS Console
1. Navigate to the [AWS CloudFormation Console](https://console.aws.amazon.com/cloudformation/).
2. Click on **Create Stack** and choose **With new resources (standard)**.
3. Upload the CloudFormation template (e.g., `cftemplate.json`) or provide the template URL.
4. Provide the necessary parameters if you want to override.
5. Click **Next**, configure stack options as needed, and proceed to **Create Stack**.

#### Using AWS CLI
You can also create the stack using the AWS CLI:
```bash

aws cloudformation create-stack --stack-name apprediscluster --template-body file://cftemplate.json --capabilities CAPABILITY_NAMED_IAM --profile  my-profile 

- If you want to override the parameters from commandline, use below syntax
aws cloudformation create-stack --stack-name apprediscluster  --parameters ParameterKey=CacheClusterId,ParameterValue=app-cache-cluster \
               ParameterKey=CacheNodeType,ParameterValue=t2.micro \
               ParameterKey=Port,ParameterValue=6524 --template-body file://cftemplate.json --capabilities CAPABILITY_NAMED_IAM --profile  my-profile 


