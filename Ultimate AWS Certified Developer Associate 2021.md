# Ultimate AWS Certified Developer Associate 2021

## 13 ECS, ECR & Fargate - Docker in AWS

 - [x] ECS Section Intro
 - [ ] What is Docker?
 - [x] ECS Clusters

   - ECS clusters are logical grouping of EC2 instances
   - EC2 instances run the ECS agent (Docker container)
   - The ECS agent registers the instance to the ECS cluster
   - The EC2 instances run a special AMI, made specifically for ECS

 - [ ] ECS Task Definition

   - Task definitions are metadata in JSON form to tell ECS how to run a docker container
   - It contains crucial information around
     - image name
     - port binding for container and host
     - memory and CPU required
     - environment variables
     - networking info

 - [x] ECS Service

   - ECS services help define how many tasks should run and how they should be run
   - they ensure that the desired number of tasks are running across our fleet of EC2 instances
   - they can be linked to ELB/NLB/ALB if needed

 - [x] ECS Service with Load Balancers
 - [x] ECR Part I

 - ECR is the private Docker image repository of AWS
 - Access is controlled through IAM (permission errors -> policy)
 - AWS CLI v1 login command (output to be executed)
   - `$(aws ecr get-login --no-include-email --region eu-west-1)`
 - AWS CLI v3 login command (pipe)
   - `aws ecr get-login-password --region eu-west-1 | docker login --username AWS -- password-stdin 1234567890.dkr.ecr.eu-west-1.amazonaws.com`
 - Docker push & pull:
   - docker push 1234567890.dkr.ecr.eu-west-1.amazonaws.com/demo:latest
   - docker pull 1234567890.dkr.ecr.eu-west-1.amazonaws.com/demo:latest

 - [x] ECR Part II
 - [x] Fargate

   - ECS cluster: manual CRUD of EC2 instances (infra)
   - Fargate: serverless
     - no EC2 provision required (no more EC2!)
     - we create task definitions, AWS runs our containers
     - change the task number to scale in or out

 - [x] ECS IAM Roles Deep Dive

   - EC2 Instance Profile
     - used by the ECS agent
     - makes API calls to ECS service
     - send container logs to CloudWatch logs
     - pull docker image from ECR

   - ECS Task Role
     - allow each task to have a specific role
     - use differnt roles for the different ECS service you run
     - task role is defined in the task definition

 - [x] ECS Task Placement (only for ECS on EC2)

   - when a task of EC2 type is launched, ECS must determine where to place it, with the constraints of CPU, memory, and available port
   - similarly, when a service sacles in, ECS needs to determine which task to terminate
   - to assist with this, you can define a task placement strategy and task placement constraints
   - only for ECS with EC2, not for Fargate (AWS hanldes task placement)

   ECS Task Placement Process
   - task placement strategies are a best effort
   - when Amazon ECS places tasks, it uses the following process to select container instances:
     1. identify the instances that satifsy the CPU, memory, and port requirements in the task definition
     2. identify the instances that satisfy the task placement constraints
     3. identify the instances that satisfy the task placement strategies
     4. select the instances for task placement
   
   ECS Task Placement Strategies
   - Binpack (cost saving)
     - place tasks based on the least available amount of CPU or memory
     - minimise the number of instances in use
   - Random
     - place the task randomly
   - Spread (high availability)
     - place the task evenly based on the specified value
     - example: instanceId, attribute:ecs.availability-zone
   - Strategies can be mxed

   ECS Task Placement Constraints
   - distinctINstance: place each task on a different container instance
   - memberOf: place task on instances that satisfy an expression
     - Uses the cluster query language (advanced)
   
 - [x] ECS Auto Scaling
   - CPU and RAM is tracked in cloudwatch at the ECS service level
   - **Target Tracking**: target a specific average CloudWatch metric
   - **Step Scaling**: scale based on CloudWatch alarms
   - **Scheduled Scaling**: based on predictable changes
   - ECS service scaling (task level) ≠ EC2 Auto Saling (instance level)
   - Fargate Auto Scaling is much easier to set up (because serverless)

   ECS - Cluster Capacity Provider
   - A capacity provider is used in association with a cluster to determine the infrastructure that a task runs on
     - for ECS and Fargate users, the FARGATE and FARGATE_SPOT capacity providers are added automatically
     - for ECS on EC2, you need to associate the capacity provider with an auto-scaling group
   - When you run a task or a service, you define a capacity provider strategy, to prioritise in which provider to run
   - this allows the capacity provider to automatically provision infrastructure for you

 - [x] ECS Summary + Exam Tips
   - ECS is used to run Docker containers and has 3 flavours
   
     - ECS on EC2 ("Classic"): provision EC2 instances to run containers
       - EC2 instances must be created
       - must configure `/etc/ecs/ecs.config` with the cluster name
       - The EC2 instance must run ECS agent
       - EC2 instances can run multiple containers on the same type:
         - you must not specify a host port (only container port)
         - you should use an ALB with the dynamic port mapping
         - the EC2 instance security group must allow traffic from the ALB on all ports
       - ECS tasks can have IAM Roles to execute actions against AWS
       - Security groups operate at the instance level, not teask level

     - Fargate: ECS serverless, no more EC2 provisioning
       - AWS provisions containers for us and assigns them ENI
       - Fargate containers are provisioned by the container spec (CPU/RAM)
       - Fargate tasks can have IAM roles to execute actions against AWS

     - EKS: managed Kubernetes by AWS

   - ECR stores docker images
     - ECR is tightly integrated with IAM
     - AWS CLI v1 login: `$(aws ecr get-login -no-include-email --region eu-west-1)`
     - AWS CLI v2 login: `aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin 1234567890.dkr.ecr.eu-west-1.amazonaws.com`
     - Docker push & pull
       - `docker push 1234567890.dkr.ecr.eu-west-1.amazonaws.com/demo:latest`
       - `docker pull 1234567890.dkr.ecr.eu-west-1.amazonaws.com/demo:latest`
     - If and EC2 instance or you cannot pull a docker image from ECR, check IAM user or role permission

   - ECS Others
     - ECS integrates with CloudWatch logs
       - need to set up logging at the task definition level
       - each container will have a different log stream
       - the EC2 instance profile needs to have the correct IAM permissions
     - Use IAM task roles for ECS tasks
     - Task placement strategies: binpack, random, spread
     - Service auto scaling with target tracking, step scaling, or scheduled
     - CLuster auto scaling through capacity providers

 - [ ] ECS Quiz
    1. ECS runs docker containers on AWS
    2. Which ECS config must you enable in `/etc/ecs/ecs.config` to allow your ECS tasks to endorse IAM roles?

        `ECS_ENABLE_TASK_IAM_ROLE`

        `ECS_CLUSTER` - this setting helps your EC2 instances register to the correct ECS cluster
        `ECS_AVAILABLE_LOGGING_DRIVERS` - this setting will be used if you want to enable logging to CloudWatch

    3. You are looking to push Docker images into ECR with your AWS CodePipeline and CodeBuild. The last step fails with an authorization issue. What is the issue?

        Any permissions issues against ECR is most likely due to IAM policies

    4. You are looking to run multiple instances of the same application on the same EC2 instance and expose it with a load balancer. The application is available as a Docker container. You should use

        ALB + ECS (uses the dynamic port feature)

    5. You are running a web application on ECS, the Docker image is stored on ECR, and trying to launch two containers of the same type on EC2. The first container starts, but the second one doesn't. You have checked and there's enough CPU and RAM available on the EC2 instance. What's the problem?

        The host port is defined in the task definition.

        To enable random host port, set host port = 0 (or empty), which allows multiple containers of the same type to launch on the same instance

    6. You have started an EC2 instance and it's not registered with the ECS cluster. What's NOT a reason for this issue?

        - [ ] 1. The ECS agent is not running
        - [ ] 2. The AMI used isn't the AWS ECS AMI
        - [ ] 3. The EC2 instance is missing IAM permissions
        - [x] 4. The security groups on the ECS instance are misconfigured

          security groups do not matter when an instance registers with the ECS service

    7. Which commands must be used to pull an image from ECR? (CLI v1)

        ```sh
        $(aws ecr get-login --no-include-email)
        docker pull $ECR_IMAGE_URL
        ```
        
    8. You would like to run 4 ECS services on your ECS cluster, which need access to various services. What is the best practice?

        Create 4 ECS task roles and attach them to the relevant ECS task definition

    9. Which task cluster placement is the MOST cost-efficient?

        binpack (not spread, not random)
