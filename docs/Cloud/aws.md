# AWS - Amazon Web Services

If anyone is interested in developing this way, you should check out a framework called "Serverless".  For AWS, Serverless still uses CloudFormation under the hood, but automates the entire process you see in this video.  This allows you to focus more on your code and I highly recommend it.  Thanks for the vid-

Terraform jest to open-source freamwork który potrafi zastąpić cloudformation i jest uniwersalny na przestrzeni wszystkich cloud providerów.

## TODO

AWS CodeBuild – For building, testing, and packaging the application. Only used if you choose to build from source. Supported languages are Node.js and Python.
AWS Fargate & AWS ECS – Used for the underlying managed container orchestration platform.
AWS Auto Scaling – Makes sure that the application scales based on the number of concurrent requests.
AWS Elastic Load Balancing – Makes sure that the load is evenly distributed amongst the different instances of the service.
Amazon CloudWatch – Used for storing App Runner Logs (events, deployments, and application) and metrics.
AWS Certificate Manager – Used to provide out-of-the-box SSL/TLS certificates for the service endpoint.
AWS KMS – Used to encrypt copies of the source repository and service logs.

## AWS Lambda

- Cloudflare domain configuration
<https://support.cloudflare.com/hc/en-us/articles/360037983412-Configuring-an-Amazon-Web-Services-static-site-to-use-Cloudflare>

- Caching data with redis
<https://medium.com/swlh/setting-up-aws-lambda-functions-with-redis-cache-and-mongodb-7f0363c97165>

- Telegram bot
<https://github.com/telegraf/telegraf>

- Create real node.js server on lambda
<https://github.com/vendia/serverless-express>

- Web crawler
<https://aws.amazon.com/blogs/architecture/scaling-up-a-serverless-web-crawler-and-search-engine/>
<https://github.com/alixaxel/chrome-aws-lambda>
<https://github.com/aws-samples/aws-step-functions-kendra-web-crawler-search-engine/tree/d534a054bbcdf62dc52703d72d79fa31fd08bf61>

## AWS Serverless

Users: Amazon Cognito

?? Amazon Lightsail

Possible run docker container like a serverless using `Amazon App Runner` or `AWS fragate` or `AWS ECS` or `AWS `

## Create project and deploy

Run command: `copilot init` and choose and one items:

```sh
Request-Driven Web Service  (App Runner)
Load Balanced Web Service   (Internet to ECS on Fargate)
Backend Service             (ECS on Fargate)
Worker Service              (Events to SQS to ECS on Fargate)
Scheduled Job               (Scheduled event to State Machine to Fargate)
```

`Request-Driven Web Service`

An AWS App Runner service that autoscales your instances based on incoming traffic and scales down to a baseline instance when there's no traffic. This option is more cost effective for HTTP services with sudden bursts in request volumes or low request volumes.

Unlike ECS, App Runner services are not connected by default to a VPC. In order to route egress traffic through a VPC, you can configure the network field in the manifest.

`Load Balanced Web Service`

An ECS Service running tasks on Fargate with an Application Load Balancer, a Network Load Balancer or both, as ingress. This option is suitable for HTTP or TCP services with steady request volumes that need to access resources in a VPC or require advanced configuration.

Note that an Application Load Balancer is an environment-level resource, and is shared by all Load Balanced Web Services within the environment. To learn more, go here. In contrast, a Network Load Balancer is a service-level resource, and hence is not shared across services.

Below is a diagram for a Load Balanced Web Service that involves an Application Load Balancer only.

`Backend Service`

If you want a service that can't be accessed externally, but only from other services within your application, you can create a Backend Service.

## You can create a new project for many different ways:

1. Use `AWS Copilot`

[Example](https://github.com/aws-samples/aws-copilot-sample-service)
[Docs](https://aws.github.io/copilot-cli/docs/overview/)

New project from AWS which is creating/managing serverless services.

- https://aws.amazon.com/blogs/containers/introducing-aws-copilot/
- https://aws.amazon.com/blogs/containers/automatically-deploying-your-container-application-with-aws-copilot/

Create and deploy project using: https://aws.amazon.com/getting-started/guides/deploy-webapp-copilot/module-one/

```sh
copilot init
copilot env init --name env_name_test --profile default --app copilot-project-name
copilot deploy
```

1. Use `AWS CDK`

- https://docs.aws.amazon.com/AmazonECS/latest/developerguide/tutorial-ecs-web-server-cdk.html#ecs-web-server-cdk-step-1

3. Use `AWS SAM`

Example:

```js
import * as ec2 from "aws-cdk-lib/aws-ec2";
import * as ecs from "aws-cdk-lib/aws-ecs";
import * as ecs_patterns from "aws-cdk-lib/aws-ecs-patterns";

const vpc = new ec2.Vpc(this, "MyVpc", {
    maxAzs: 3 // Default is all AZs in region
  });

const cluster = new ecs.Cluster(this, "MyCluster", {
    vpc: vpc
});

// Create a load-balanced Fargate service and make it public
new ecs_patterns.ApplicationLoadBalancedFargateService(this, "MyFargateService", {
    cluster: cluster, // Required
    cpu: 512, // Default is 256
    desiredCount: 6, // Default is 1
    taskImageOptions: { image: ecs.ContainerImage.fromRegistry("amazon/amazon-ecs-sample") },
    memoryLimitMiB: 2048, // Default is 512
    publicLoadBalancer: true // Default is false
});
```

## Serverless Framework vs AWS Serverless Application Model (SAM)

SAM on the other hand is an abstraction layer specifically for AWS using not only FaaS but also DynamoDB for storage and API Gateway for creating a serverless HTTP endpoint.

The biggest difference is that Serverless is written to deploy FaaS (Function as a Service) functions to different providers.

https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-cli-command-reference-sam-local-start-lambda.html
https://stackoverflow.com/questions/52228361/whats-the-difference-between-aws-sam-serverless-application-model-and-serverl

## How to prepaire and access to EC2 instances

0. Create Amazon Linux 2 AMI instance
1. Update systemu during the creation

```sh
#!/bin/bash
yum update -y
yum install git -y
```

2. Generate new ssh key and download it

```sh
chmod 400 key-pair-name.pem
```

3. Use ssh to log in

```sh
ssh ec2-user@ip_address -i key-pair-name.pem
```

4. [Configure AWS CLI user](#how-to-change-aws-cli-user)

## How to change AWS CLI user

```sh
aws configure
```

and provide AWS Access Key ID and AWS Secrect Access Key.

## How to create DynamoDB table

After running AWS Configure, create a DynamoDB table using the following command:

```sh
aws dynamodb create-table --table-name ProductCatalog --attribute-definitions \
AttributeName=Id,AttributeType=N --key-schema \
AttributeName=Id,KeyType=HASH \
--provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5
```

## How to populate the table

```sh
aws dynamodb batch-write-item --request-items file://items.json
```

## How to query Dynamodb from EC2 command line

```sh
aws dynamodb get-item --table-name ProductCatalog --region us-east-1  --key '{"Id":{"N":"403"}}'
```

## AWS Issues

➜  aws aws cloudformation validate-template --template-body e2e-scrapping.yaml
An error occurred (InvalidClientTokenId) when calling the ValidateTemplate operation: The security token included in the request is invalid.
= problem with account settings you have to type was configuration
and set up https://console.aws.amazon.com/iam/home?#/security_credentials Access keys

➜  aws aws cloudformation validate-template --template-body e2e-scrapping.yaml
An error occurred (ValidationError) when calling the ValidateTemplate operation: Template format error: unsupported structure.
There is not file before file path aws cloudformation validate-template --template-body file://e2e-scrapping.yaml

➜  aws aws cloudformation validate-template --template-body e2e-scrapping.yaml
An error occurred (ValidationError) when calling the ValidateTemplate operation: Invalid templ
ate resource property 'AvailabilityZone'
Wrong name of, this is correct one: AvailabilityZone: us-east-1a

➜  aws aws cloudformation validate-template --template-body e2e-scrapping.yaml
An error occurred (ValidationError) when calling the ValidateTemplate operation: Template form
at error: YAML not well-formed. (line 28, column 16)

aws cloudformation deploy --template-file e2e-scrapping.yaml --stack-name new-stack-2
An error occurred (ValidationError) when calling the CreateChangeSet operation: Parameters: [KeyName] must have values
You must remove file: from command before file name

aws cloudformation deploy --template-file e2e-scrapping.yaml --stack-name new-stack-2
An error occurred (ValidationError) when calling the CreateChangeSet operation: Parameters: [KeyName] must have values
You should add required parameters and below command is correct:
aws cloudformation deploy --template-file e2e-scrapping.yaml --stack-name new-stack-2 --parameter-overrides KeyName=my-key-pair

One or more parameter values were invalid: Number of attributes in KeySchema does not exactly match number of attributes defined in AttributeDefinitions (Service: AmazonDynamoDBv2; Status Code: 400; Error Code: ValidationException; Request ID:
https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_CreateTable.html
https://stackoverflow.com/questions/47385177/serverless-framework-dynamo-db-table-resource-definition-with-sort-key
Problem with too much number of columns. We should add only required columns in AttributeDefinitions, same as declared in KeySchema.

aws cloudformation deploy --template-file e2e-scrapping.yaml --stack-name new-stack-7 --parameter-overrides KeyName=my-key-pair
The requested configuration is currently not supported. Please check the documentation for supported configurations. (Service: AmazonEC2; Status Code: 400; Error Code: Unsupported; Request ID: d8a167ea-fa11-4c80-a27d-3a8d2002717b; Proxy: null)
EC2 instance in configuration didn’t have declared InstanceType: "t2.micro"
and ImageId: "ami-0db9040eb3ab74509"

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/replacing-lost-key-pair.html

node.js
import dotenv from 'dotenv';
SyntaxError: Cannot use import statement outside a module
- add "type": "module” to package.json

AWS COMMANDS

- create new pair key
aws ec2 create-key-pair --key-name my-key-pair --query "KeyMaterial" --output text > my-key-pair.pem
aws ec2 create-key-pair --key-name MyKeyPair --query 'KeyMaterial' --output text > MyKeyPair.pem

- remove cloudformation stack
aws cloudformation delete-stack --stack-name new-stack-7

- czy komenda update tworzy nowe elementy jeśli nie istnieją - tak tworzy i dodaje tyle te dane wprowadzone w update

NICE TO KNOW
- In DynamoDB, you use the UpdateItem action to modify a single item. (If you want to modify multiple items, you must use multiple UpdateItem operations.)
- UpdateItem - Edits an existing item's attributes, or adds a new item to the table if it does not already exist.
- AWS does not permit to modify it in a single update request more info was found in the following answers: updating-a-json-array-in-aws-dynamodb.
- I could not find any answer to query and update the JSON-array. I think this may be AWS profitable motive to not allow those features. Changing attendees from [] to {}. This allows me the flexibility to query particular attendeeId and change the entire JSON associated with that.

## Usefull libraries/links

[aws-sdk-js-v3](https://github.com/aws/aws-sdk-js-v3)

[@aws-sdk/lib-storage](https://github.com/aws/aws-sdk-js-v3/tree/main/lib/lib-storage)

[@aws-sdk/lib-dynamodb](https://github.com/aws/aws-sdk-js-v3/tree/main/lib/lib-dynamodb)
