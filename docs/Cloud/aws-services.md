# AWS Services

?? Amazon Lightsail
?? Amazon Route 53
?? AWS Secrets Manager
?? AWS Step Functions
?? Amazon CloudFront
?? Amazon CloudWatch
?? Amazon ElastiCache - Redis

## By names

https://aws.amazon.com/products/compute/

### Amazon Elastic Container Service (ECS)

> Run containerized applications or build microservices

### Amazon Amazon Elastic Kubernetes Service (EKS)

> Manage containers with Kubernetes

### AWS Fargate

> Run containers without managing servers

If you want a truly serverless website with zero idle costs you’ll have to implement it using API:

- Put your frontend files (HTML, CSS, JS) in S3
- Load your dynamic content through API
- Implement the dynamic functionality in Lambda functions
- Use API gateway to call the Lambdas
- The DB can be Aurora Serverless or DynamoDB On-Demand


<https://serverfault.com/questions/951429/aws-fargate-service-scale-to-zero>

### Amazon Elastic Compute Cloud (EC2)

> Run containers with server-level control

### Amazon EC2 Spot Instances

> Run fault-tolerant workloads for up to 90 percent off

### AWS Copilot

> Quickly launch and manage containerized applications

### Amazon Elastic Container Registry (ECR)

> Share and deploy container software, publicly or privately

### AWS App Mesh

> Application-level networking for all your services

### AWS Cloud Map

> Cloud resource discovery service

### AWS Lambda

> Package and deploy Lambda functions as container images

### AWS App Runner

> Build and run containerized applications on a fully managed service

> App Runner does not allow you to scale to zero instances. You will always have a single instance running and will be charged for the allocated resources.
> Open ticket <https://github.com/aws/apprunner-roadmap/issues/9>

> Alternative: https://cloud.google.com/run

App Runner is optimized for request/response application (e.g. web servers, api services).

Scale to zero is really important for small projects that don’t need 24/7 compute running, and especially contractor work. Besides that microservices that don’t need to be running all the time, and side projects where someone wants a full container and is willing to deal with cold starts (like lambda but not being constrained to API gateway or lambda utilities in the container).

It scales to just $0.007 per GB/hour if the application is idle as far as I can tell, no vCPU cost. Or there is a PauseService API call to eliminate that cost too. If you had a batch job, you could call ResumeService at the start and PauseService at the end?

Yeah but that’s still $5/month more than cloud run, and if I’m using such a heavily managed service I wouldn’t want to automate pausing and resuming myself (with batch it would be fine but for an api it would be very difficult)

What should happen when a request is made when instances are zero? Yeah, basically a cold start similar to lambda. That’s how cloud run does it.

You can configure the minimum "provisioned" containers which stay active (paying for mem only, not CPU) - except you can only set that to >= 1.

Apart from smaller projects, scale to zero would be super useful for development workflows. Imagine many developers deploying code branches for testing. Right now, they would have to consciously deprovision the service when they are not working on it.

Aurora Serverless can only be accessed from within VPC via private IP. AppRunner does not support VPC integration yet.

Our company usecase: we want our applications to be serverless, but we don't really want to change our development model to lambda one. We want to build traditional microservices, which could handle more than one request at a time, but we also want our dev and staging environment cost less when it is not used.

Actually scratch that above statement! Pricing is convoluted / misleading. I was mistaken when reading the post that there is a $0.064 per hour compute charge (Fargate pricing is about $0.04048 per hour in comparison and that was behind my 50% more expensive comment).

App runner now supports resources inside your private VPC (https://aws.amazon.com/blogs/containers/deep-dive-on-aws-app-runner-vpc-networking/)

App Runner only supports the blue/green deployment model, so other options like rolling, canary or traffic split are not an option right now.

### Amazon Lightsail

> Run simple containerized applications for a fixed, monthly price

### AWS App2Container

> Containerize and migrate existing applications

### Amazon ECS Anywhere

> Run containers on customer-managed infrastructure

### Amazon EKS Anywhere

> Create and operate Kubernetes clusters on your own infrastructure

### AWS Proton

> Automated management for container and serverless deployments

### Red Hat OpenShift Service on AWS (ROSA)

> A fully managed, turnkey app platform

### Amazon EKS Distro

> Run the Kubernetes distribution that powers Amazon EKS

## Usefull links

<https://nathanpeck.com/concurrency-compared-lambda-fargate-app-runner/>
<https://aws.amazon.com/containers/?sc_ichannel=ha&sc_icampaign=acq_awsblogsb&sc_icontent=containers-resources>
