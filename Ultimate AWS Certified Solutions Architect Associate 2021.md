# Ultimate AWS Certified Solutions Architect Associate 2020

- [Ultimate AWS Certified Solutions Architect Associate 2020](#ultimate-aws-certified-solutions-architect-associate-2020)
  - [1. Introduction - AWS Certified Solutions Architect Associate](#1-introduction---aws-certified-solutions-architect-associate)
  - [2. Code & Slides Download](#2-code--slides-download)
  - [3. (***DONE***) "AWS Fundamentals: IAM & EC2"](#3-done-aws-fundamentals-iam--ec2)
  - [4. (***DONE***) "High Availability and Scalability: ELB & ASG"](#4-done-high-availability-and-scalability-elb--asg)
  - [5. (***DONE***) EC2 Storage - EBS & EFS](#5-done-ec2-storage---ebs--efs)
  - [6. (***WIP***) "AWS Fundamentals: RDS + Aurora + ElastiCache"](#6-wip-aws-fundamentals-rds--aurora--elasticache)
  - [7. (***DONE***) Route 53](#7-done-route-53)
  - [8. (***DONE***) Classic Solutions Architecture Discussions](#8-done-classic-solutions-architecture-discussions)
  - [9. (***DONE***) Amazon S3 Introduction](#9-done-amazon-s3-introduction)
  - [10. (***DONE***) AWS CLI, SDK, IAM Roles & Policies](#10-done-aws-cli-sdk-iam-roles--policies)
  - [11. Advanced Amazon S3 & Athena](#11-advanced-amazon-s3--athena)
  - [12. (***DONE***) CloudFront & AWS Global Accelerator](#12-done-cloudfront--aws-global-accelerator)
  - [13. AWS Storage Extras](#13-aws-storage-extras)
  - [14. "Decoupling applications: SQS, SNS, Kinesis, Active MQ"](#14-decoupling-applications-sqs-sns-kinesis-active-mq)
  - [15. (***DONE***)Serverless Overviews from a Solution Architect Perspective](#15-doneserverless-overviews-from-a-solution-architect-perspective)
  - [16. (***WIP***) Serverless Solution Architecture Discussions](#16-wip-serverless-solution-architecture-discussions)
  - [17. (***DONE***) Databases in AWS](#17-done-databases-in-aws)
  - [18. "AWS Monitoring & Audit: CloudWatch, CloudTrail & Config"](#18-aws-monitoring--audit-cloudwatch-cloudtrail--config)
  - [19. Identity and Access Management (IAM) - Advanced](#19-identity-and-access-management-iam---advanced)
  - [20. "AWS Security & Encryption: KMS, SSM Parameter Store, CloudHSM, Shield,](#20-aws-security--encryption-kms-ssm-parameter-store-cloudhsm-shield)
  - [21. Networking - VPC](#21-networking---vpc)
  - [22. Disaster Recovery & Migrations](#22-disaster-recovery--migrations)
  - [23. More Solution Architectures](#23-more-solution-architectures)
  - [24. Other Services](#24-other-services)
  - [25. WhitePapers and Architectures - AWS Certified Solutions Architect Associate](#25-whitepapers-and-architectures---aws-certified-solutions-architect-associate)
  - [26. Preparing for the Exam + Practice Exam - AWS Certified Solutions](#26-preparing-for-the-exam--practice-exam---aws-certified-solutions)
  - [27. Congratulations - AWS Certified Solutions Architect Associate](#27-congratulations---aws-certified-solutions-architect-associate)

## 1. Introduction - AWS Certified Solutions Architect Associate

 - [ ] Course Introduction - AWS Certified Solutions Architect Associate
 - [ ] "PLEASE READ: Lectures you can skip if you took a course from me before"
 - [ ] Creating an AWS Account
 - [ ] AWS Account Activation Troubleshooting
 - [ ] AWS Budget Setup
 - [ ] Important Message
 - [ ] About your instructor
 - [ ] How to read an AWS Bill

## 2. Code & Slides Download

 - [ ] Slides and Code Download

## 3. (***DONE***) "AWS Fundamentals: IAM & EC2"

 - [x] AWS Fundamentals - Section Introduction
 - [x] AWS Regions and AZs
 - [x] IAM Introduction
   
    - **User** (a physical person)
    - **Group** (functions/team, contains users)
    - **Role** (for machine/application, for internal usage with AWS resources)

    Remember:

    - one IAM **User** per PHYSICAL PERSON
    - one IAM **Role** per application
    - IAM credentials **SHOULD NEVER BE SHARED**
    - **NEVER PUT IAM CREDENTIALS IN CODE**
    - **NEVER COMMIT IAM CREDENTIALS**
    - **NEVER USE ROOT ACCOUNT**
    - **NEVER USE ROOT IAM CREDENTIALS**

 - [x] IAM Hands On
 - [x] About the EC2 Console Changes
 - [x] EC2 Introduction

    - Renting virtual machines (EC2)
    - Storing data on virtual drives (EBS)
    - Distributing load across machiens (ELB)
    - Scaling the services using an auto-scaling group (ASG)

 - [] SSH Overview
 - [ ] How to SSH using Linux or Mac
 - [ ] How to SSH using Windows
 - [ ] How to SSH using Windows 10
 - [ ] SSH Troubleshooting
 - [x] EC2 Instance Connect
 - [x] Introduction to Security Groups
 - [x] Security Groups Deep Dive

    - Security groups are acting as a firewall on EC2 instances
    - They regulate:
      - access to ports
      - authorised IP ranges - IPv4 and IPv6
      - Control of inbound network (from other to the instance)
      - Control of outbound network (from the instance to other)

    Security Groups Good to Know
    
    - Can be attached to multiple instances
    - locked down to a region/VPC combination (need to recreate to use outside)
    - live outside the EC2 - if traffic is blocked, the EC2 instance won't see it
    - goot to maintain one dedicated security grouop for SSH access
    - if application is not accessible (time out), it's a 

 - [x] Private vs Public vs Elastic IP

    Public IP
      
      - means the machine can be identified on the internet
      - must be unique across the whole web (not two machines can have the same public IP)
      - can be geo-located easily

    Private IP

      - means the machine can only be identified on a private network only
      - must be unique across the private network, but
      - 2 different private networks (e.g., 2 companies) can have the same IPs
      - Machines connect to internet using a NAT + internet gateway (a proxy)
      - only a specific range of IP can be used as private IPs

    Elastic IPs

      - only 5 Elastic IPs per AWS account (can request more)
      - overall, try to avoid using Elastic IP as
        - they often reflect poor architectural decisions. Instead,
        - use a random public IP and register a DNS name to it (Route53), or
        - use a load balancer

 - [ ] Private vs Public vs Elastic IP Hands On
 - [x] Install Apache on EC2
 - [x] EC2 User Data

    - EC2 user data script is used to bootstrap an EC2 instance
    - Bootstrapping means launching commands when a machine starts
    - The EC2 user data script is only run once at the instance first start
    - EC2 user data is used to automate boot tasks such as:
      - Install updates
      - Install software
      - Download common files from internet
      - Anything
    - EC2 user data script runs with root user

 - [x] IAM & EC2 Mid Way Quiz

    - 'ap-southeast-1a' is an availability zone. Anything that ends with a letter is an AZ
    - Availability Zones are in isolated data centres - this helps guarantee that multi AZ won't all fail at once (due to a meteorological disaster for example). Read more here: https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html
    - "Organisations" does not exist in IAM
    - IAM is a global service (encompasses all regions)
    - An IAM user can belong to multiple groups
    - This is best practice when you have a big organisation: create multiple IAM users and grouops, and assign policies to groups. New users will be added to groups
    - Never share your IAM credentials. If your colleagues need access to AWS they'll need their own account
    - You pay for an EC2 instance compute component only when it's in 'running' state
    - You are getting a permission error exception when trying to SSH into your Linux Instance because the key is missing permissions `chmod 0400`
    - You are getting a network timeout when trying to SSH into your EC2 instance becuase your security groups are misconfigured. 
        
        **Any timeout errors (not just in SSH but also HTTP for example) means a misconfiguration of your security groups.**
    - When a security group is created, the default behavior is to deny all traffic inbound and allow all traffic outbound
    - Security groups can reference IP address, CIDR block and Security group, but not a DNS name

 - [x] EC2 Instances Launch Types

    - On demand instances: short workload, predictable pricing, good for elastic workload
      - pay for what you use (billing per second, after the first minute)
      - highest cost but no upfront payment
      - no long term commitment
      - Recommended for short-term and un-interrupted workloads, in which you cannot predict how the application will behave
    - Reserved: (min 1yr)
      - Reserved instances: long workloads
        - up to 75% discount compared to on demand
        - pay upfront for what you use with long term commitment
        - reservation period can be 1 or 3 years
        - reserve a specific instance type
        - recommended for steady state usage applications (think **database**)
      - convertible reserved instances: long workloads with flexible instances
        - can change the EC2 instance type
        - up to 54% discount
      - Scheduled Reserved instances: example - every Thu between 3 and 7pm
        - launch within time window you reserve
        - when you require a fraction of day/week/month
    - Spot instances: short workloads, for cheap, can lose instances (less reliable)
      - up to 90% discount
      - can lose the EC2 instance any time if max price is less than the current spot price
      - the most cost-efficient instances in AWS
      - Useful for workloads that are resilient to failure, such as batch jobs, data analysis and image processing etc.
      - not good for critical jobs or databases
      - great combo: reserved instances for baseline + on demand & spot for peaks
    - Decicated instances: no other customers will share your hardware
      - instances running on hardware that's dedicated to you
      - may share hardware with other instance in same account
      - no control over instance placement (can move hardware after stop/start)
    - Dedicated hosts: book an entire physical server, control instance placement
      - Physical dedicated EC2 server for your use
      - full control of EC2 instance placement
      - visibility into the underlying sockets/physical cores of the hardware
      - allocated for your account for a 3 year period reservation
      - more expensive
      - useful for software that have complicated licensing model (BYOL - Bring Your Own License), or
      - for companies that have strong regulatory or compliance needs

    Characteristic | Dedicated Instances | Dedicated Hosts
    - | :-: | :-:
    Enables the use of dedicated physical servers | ✅ | ✅
    Per instance billing (subject to a $2 per region fee) | ✅ | 
    Per host billing | | ✅
    Visibility of sockets, cores, host ID | | ✅
    Affinity between a host and instance | | ✅
    Targeted instance placement | | ✅
    Automatic instance placement | ✅ | ✅
    Add capacity using an allocation request | | ✅

    Which host is right for me?

    - On demand: coming and staying in resort whenever we like, we pay the full price
    - Reserved: like planning ahead and if we plan to stay for a long time, we may get a good discount
    - Spot instances: the hotel allows people to bid for the empty rooms and the highest bidder keeps the rooms. You can get kicked out at any time
    - Dedicated hosts: we book an entire building of the resort

 - [x] Spot Instances & Spot Fleet

    - up to 90% discount compared to on demand
    - 2 strategies:
      1. max spot price
         - get the spot instance while current spot price < max spot price
         - hourly spot price varies based on offer and capacity
         - if current spot price > max spot price, 2 minutes grace period to **stop or terminate** the spot instance
      2. spot block
         - 'block' spot instance buring a specified time frame (1 to 6 hours) without interruptions
         - in rare situations, the spot instance may be reclaimed
    - Use case: batch job, data analysis or workloads that are resilient to failures
    - Not great for critical applications or databases
    - How to terminate spot instances?
      
      [Spot request](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/spot-requests.html)
        - max spot price
        - desired number of spot instances
        - launch specification
        - request type: one time | persistent
        - valid from, valid until

      You can only cancel spot instance requests that are open, active or disabled.

      Cancelling a sport request does not terminate the spot instances.

      However, you must first cancel a spot request, and then terminate the associated spot instances.
    
    - Spot fleets = set of spot instances + (optional) on demand instances
      - try to meet the target capacity with price constraints
        - define possible launch pools: instance type (e.g., m5.large), OS, AZ
        - can have multiple launch pools for the fleet to choose
        - stops launching instances when reaching capacity or max cost
      - Strategies to allocate spot instances:
        1. lowestPrice: from the pool with the lowest price (cost optimisation, short workload)
        2. diversified: distributed across all pools (great for availability, long workloads)
        3. capacityOptimized: pool with the optimal capacity for the number of instances

      **Spot fleets allow us to automatically request spot instances with the lowest price.**
    
 - [ ] EC2 Instances Launch Types Hands On
 - [x] EC2 Instance Types Deep Dive

    https://www.ec2instances.info

    - R: applications that need a lot of RAM - in-memory caches
    - C: applications that need good CPU -  compute/databases
    - M: applications that are balanced (think "medium") - general / web app
    - I: applications that need good local I/O (instance storage) - databases
    - G: applications that need a GPU

    - T2/T3: burstable instances (up to a capacity)
    - T2/T3 - unlimited: unlimited burst

 - [x] EC2 AMIs

    - Advantages:
      - pre-install packages needed
      - faster boot time (no need for ec2 user data)
      - machine comes configured with monitoring/enterprise software
      - secrity concerns - control over the machines in the network
      - control of maintenance and updates of AMIs over time
      - Active Directory integration out of the box
      - install your app ahead of time (for faster deploys when auto-scaling)
      - using others' AMI that is optimised for runing an app, DB, etc.
    - **AMIs are built for a specific AWS region!**

 - [ ] EC2 AMI Hands On
 - [x] Cross Account AMI Copy

    https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/CopyingAMIs.html

    - can share an AMI with another AWS account
    - sharing an AMI does not affect the ownership of the AMI
    - if you copy an AMI, you own the target AMI in your account
    - to copy an AMI shared from another AWS account, the owner of the source AMI must grant you read permissions ofr the storage that backs the AMI, either the associated EBS snapshot (for an Amazon EBS-backed AMI) or an associated S3 bucket (for an instance store-backed AMI)
    - **Limits**
      - cannot copy an encrypted AMI shared from another account. Instead, if the underlying snapshot and encryption key are shared with you, you can copy the snapshot while re-encrypting it with your own key. You own the copied snapshot, and can register it as a new AMI
      - cannot copy a shared AMI with an associated billingProduct code. This includes Windows AMIs and AMIs from the AWS Marketplace. To copy a shared AMI with a billingProduct code, launch an EC2 instance in your account using the shared AMI and then create an AMI from the instance

 - [x] EC2 Placement Groups

    - placement groups control how the ec2 instances are placed within AWS
    - a placement group can have one of the three strategies below:
      1. *cluster* - cluster instances are in one low latency gorup in a single AZ
         - same rack, same AZ, low latency, 10Gbps network
         - Pros: great network (10Gbps bandwidth between instances)
         - Cons: if the rack fails, all instances fails at the same time
         - Use cases:
           - big data job that needs to complete fast
           - applications tha need extremely low latency and high network throughput
      2. *spread* - spread instances are placed across underlying hardware (max 7 instances er group per AZ) - critical applications
         - each ec2 instance is on different hardware
         - Pros: span across AZ; reduced risk of simultaneous failure; ec2 instances are on different physical hardware
         - Cons: limited to 7 instances per AZ per placement group
         - Use cases:
           - applications that need to maimise high availability
           - critical applications where each instance must be isolated from failure from each otherf
      4. *partition* - partition instances are placed across many different partitions (which rely on different sets of racks) within an AZ. Scales to hundreds of ec2 instances per group (Hadoop, Cassandra, Kafka)
         - up to 7 partitions per AZ
         - up to hundreds of EC2 instnaces
         - The instances in a partition do not share racks with the instances in the other partitions
         - A partition failure can affect many EC2 but won't affect other partitions
         - EC2 instances get access to the partition info as metadata
         - Use cases: big data - HDFS, HBase, Cassandra, Kafka

 - [x] Elastic Network Interfaces (ENI) with Hands On

    - logical component in a VPC that represents a **virtual network card**
    - can have the following attributes:
      - primary private IPv4, one or more seecondary IPv4
      - 1 elastic IP (IPv4) perprivate IPv4
      - 1 public IPv4
      - 1 or more security groups
      - a MAC address
    - ENI can be independently created and attached to an ec2 instance on the fly, especially for failover
    - bound to a specific AZ

 - [x] ENI - Extra Reading

    https://aws.amazon.com/blogs/aws/new-elastic-network-interfaces-in-the-virtual-private-cloud/

 - [x] EC2 Hibernate

    - in-memory state is preserved (RAM)
    - boot faster (OS not stopped / restarte)
    - RAM state is written to a file in the root EBS volume
      - the root EBS volume must be encrypted
    - Use cases:
      - long-running process
      - saving the RAM state
      - services that take time to initialise

 - [ ] EC2 Hibernate - Hands On
 - [x] EC2 for the Solution Architect

    - EC2 instance are billed by the second, t2.micro is free tier (monthly quota of free hours)
    - SSH for Linux / MacOS / Windows 10, Putty for Windows in general
    - SSH is on port 22, lock down the security group to your IP
    - Timeout error → security groups settings
    - Permission error on the SSH key → `chmod 0400`
    - security groups can reference other security groups instead of IP ranges (popular exam question)
    - Know the difference between Private, Public and Elastic IP
    - customise and EC2 instance at boot time using EC2 user data
    - 4 EC2 launch modes:
      - on demand
      - reserved
      - spot instances
      - dedicated hosts (licensing, underlying hardware such sockets)
    - basic instance types: R, C, M, I, G, T2/T3
    - ceate AMIs to pre-install software on EC2 → faster boot
    - AMI can be copied across regions and accounts
    - EC2 placement groups: cluster, spread

 - [x] EC2 Final Quiz

    - Cluster placement groups places your instances next to each other giving you high performance computing and networking
    - Reserved instances allow you to save cost as you know in advance that the instance will be a up for a full year
    - An AMI created for a region can only be seen in that region
    - AMI is region locked and the same ID cannot be used across regions
    - dedicated hosts for licensing requirement - the vendor license bills you based on the physical cores and underlying network socket visibility
    - Creating an AMI after installing the applications allows you to start more EC2 instances directly from that AMI, hence bypassing the need to install the application (as it's already installed)
    - scheduled reserved instance: to run a critical workload of three hours on Monday weekly; maximize the **cost savings** while ensuring the **application stability**?

## 4. (***DONE***) "High Availability and Scalability: ELB & ASG"

 - [x] High Availability and Scalability

    - Scalability means an application / system can handle greater loads by adapting
    - 2 kinds of scalability:
      - vertical scalability
      - horizonal scalability (elasticity)
    - scalability is linked but different to high availability

    Vertical Scalability (scale up/down):
    - increase the size of the instance: t2.micro → t2.large
    - common for non-distributed systems, e.g., database
    - RDS, ElstiCache can scale vertically
    - can vertically scale up to hardware limit

    Horizontal Scalability (scale out/in):
    - increase the number of instances
    - for distributed systems/applications, e.g., web app
    - EC2 are easy to scale horizontally: ASG, load balancer

    High Availability
    - usually linked to horizontal scalability
    - application runs in >= 2 data centres (AZ)
    - the goal is to survive a data centre loss
    - passive high availability, e.g., RDS multi AZ
    - active high availability - horizontal scaling
    - ASG multi AZ, load balancer multi AZ

 - [x] Elastic Load Balancing (ELB) Overview

    - spread load across multiple downstream instances
    - expose a single point of access (DNS) to your application
    - seamlessly handle failures of downstream instances
    - do regular health checks to your instances
    - provie SSL termination (HTTPS) for your websites
    - enforce tickiness with cookies
    - high availability across zones
    - separate publice traffic from private traffic

    3 types of Elastic load balancer (ELB) on AWS

    - Classic load balancer: http, https, tcp
    - Application load balancer (ALB): http, https, websocket
    - Network load balancer (NLB): TCP, TLS (secure TCP) & UDP
    - ELB can be internal (private) or external (public)

    Good to know
    
    - LBs can scale but not instantaneously - contact AWS for a 'warm-up'
    - Troubleshooting
      - 4xx erros are client induced
      - 5xx errors are application induced
      - LB errors 503 means at capacity or no registered target
      - If LB cannot connect to your application, check the security group settings
    - Monitoring
      - DLB access logs will log all access requests (can debug per request)
      - CloudWatch metrics will give you aggregate statistics, e.g., connection count)

 - [x] Classic Load Balancer (CLB) with Hands On

    - supports TCP (layer 4), HTTP & HTTPS (layer 7)
    - health check are TCP or HTTP based
    - fixed hostname

 - [x] Application Load Balancer (ALB) with Hands On

    - ALB is layer 7 only (HTTP)
    - can distribute load to
      - multiple HTTP applications across machines (target groups)
      - multiple applicatins on the same machine (e.g., containers)
    - supports HTTP/2 and WebSocket
    - supports redirects (from HTTP to HTTPS for example)
    - routing table to different target groups:
      - routing based on path in URL: example.com/*users* & example.com/*posts*
      - routing based on hostname in URL: one.example.com & two.example.com
      - routing based on query string, headers: example.com/users?id=123&order=false
    - ALB is a great fit for micro services and container-based application (Docker and ECS)
    - port mapping feature to redirect to a dynamic port in ECS
    - Comparision: 1 CLB per application vs 1 ALB per many applications

    Target Groups
    - EC2 instances (ASG) - HTTP
    - ECS tasks - HTTP
    - Lambda functions - HTTP request is tranlsated into a JSON event
    - IP Addresses - mut be private IPs
    - ALB can route to multiple target groups

    Good to know
    - fixed hostname
    - application servers don't see the IP of the client directly
      - client IP is inserted in the header X-Forwarded-For
      - client port - X-Forwarded-Port and client proto - X-Forwarded-Proto

 - [x] Network Load Balancer (NLB) with Hands On

    - NLB is layer 4
      - forward TCP & UDP traffic to your instances
      - handle millions of request per second
      - less latency ~100ms (vs 400 ms for ALB)
    - NLB has **one static IP per AZ**, and supports assigning Elastic IP
      - 2 entry points
      - useful for whitelising specific IP
    - NLB is used for extreme performance, TCP or UDP traffic
    - NLB is not free tier
    - NLBs do not have associated security groups

 - [x] Elastic Load Balancer - Stickiness

    - stickiness: the same client is always redirected to the same instance behind a load balancer
    - works for CLB & ALB
    - The cookies used for stickiness has an expiration date you configure
    - Use case: ensure the user doesn't lose his session data
    - Enabling stickiness may bring imbalance to the load over the backend EC2 instances

 - [x] Elastic Load Balancer - Cross Zone Load Balancing

    - CLB: disabled by default; no charges for inter AZ data if enabled
    - ALB: always on (cannot be disabled); no charges for inter AZ data
    - NLB: disabled by default; if enabled, the inter AZ data is chargeable

 - [x] Elastic Load Balancer - SSL Certificates

    - the LB uses an X.509 cert (SSL/TLS server cert)
    - certs are managed in ACM (AWS Certificate Manager)
    - alternatively, we can upload our own certs
    - HTTPS listener:
      - must specify a default cert
      - can add an optional list of certs to support multiple domains
      - clients can use SNI (server name indication) to specify the target hostname
      - ability to specify a security policy to support older versions of SSL/TLS (legacy clients)

    Server Name Indication (SNI)

    - SNI allows loading multiple SSL certs onto one web server (to serve multiple websites)
    - it's a newer protocol and requires the client to indicate the hostname of the target server in the iniital SSL handshake
    - the web server will then find the correct cert, or return the default one
    - only works for ALB & NLB (newer generation), CloudFront
    - not supported by CLB (older gen)

    SSL certs for ELBs

    - CLB: one SSL cert per CLB; must use multiple CLB for multiple hostname with multiple SSL certs
    - ALB: supports multiple listners with multiple SSL certs; uses SNI
    - NLB: supports multiple listners with multiple SSL certs; uses SNI

 - [x] Elastic Load Balancer - Connection Draining

    - Feature naming:
      - CLB: connection draining
      - target group: deregistration delay (ALB & NLB)
    - Connection draining refers to the time to complete "in-flight requests" while the instance is being de-registered or unhealthy
    - Stops sending new requests to the instance which is de-registering
    - can be 1 to 3600 sec, default is 300 sec
    - can be disabled (set value to 0)
    - set to a low value if the requests are expected to be short

 - [x] Auto Scaling Groups (ASG) Overview

    - scale in/out to match decreased/increased load
    - ensure min/max number of running instances
    - auto register new instances to a LB

    ASG attributes

    - launch config
      - AMI + instance type
      - ec2 user data
      - EBS volumes
      - security Groups
      - ssh key pair
    - min/max/initial size
    - network + subnets info
    - LB info
    - scaling policies

    Scaling Policies
    - auto scaling alarms
      - scale in/out based on CloudWatch alarms
      - an alarm monitors a metric, e.g., average CPU usage
      - metrics are computed for the overall ASG instances
    - auto scaling new rules
      - directly managed by EC2, e.g.,
        - target avg cpu usage,
        - number of requests on the ELB per instance
        - avg network in/out
      - easier to set up
    - auto scaling custom metric
      - custom metric example: number of connected users
      1. send custom metric from application on EC2 to cloudwatch (PutMetric API)
      2. create cloudwatch alarm to react to low/high values
      3. use cloudwatch alarm as the scaling policy for ASG

    Brain Dump

    - scaling policies can be based on cpu, network, custom metrics or a schedule
    - ASGs use launch configurations or launch templates (newer)
    - to update an ASG, you must provide a new launch configuration/template; the underlying EC2 will be replaced over time
    - IAM roles attached to an ASG will get assigned to the underlying EC2 instances
    - ASG is free; you only pay for the underlying resources being launched
    - having instances under an ASG means that if they are terminated for whatever reason, the ASG will automatically create new ones as a replacement
    - ASG can terminate instances marked as unhealthy by an LB and hence replace them

 - [x] Auto Scaling Groups Hands On

    - launch template (newer) allows spot fleet, while launch configuration allows 1 instance type

 - [x] Auto Scaling Groups - Scaling Policies

    - target tracking scaling
      - Most simple and easy to set up
      - e.g., keep avg ASG CPU ~40%
    - simple/step scaling
      - when a cloudwatch alarm is triggered, e.g., CPU > 70%, add 2 units
      - when a cloudwatch alarm is triggered, e.g., CPU < 30%, remove 1 unit
    - scheduled actions
      - anticipate a scaling based on know usage patterns
      - e.g., increase the min size to 10 at 5pm on Fridays

    [Scaling Cooldown](https://docs.aws.amazon.com/autoscaling/ec2/userguide/Cooldown.html)
    - the cooldown period ensures the ASG doesn't launch or terminate additional instances before the previous scaling activity takes effect
    - in addtion to default cooldown for ASG, we can create cooldowns that apply to a specific simple scaling policy
    - a scaling-specific cooldown period overrides the default cooldown period
    - one common use for scaling-specific cooldowns is with a scale-in policy;  scale-in policy terminates instances based on a specific criteria or metric, because the policy terminates instances, Amazon EC2 auto scaling needs less time to determine whether to terminate addtional instances
    - if the default cooldown period of 300 seconds is too long - you can reduce costs by applying a scaling-specific cooldown period of 180 seconds to the scale-in policy
    - if the application is scaling up/down multiple times each hour, modify the ASG cooldown timers and the cloudwatch alarm period that triggers the scale in 

 - [x] Auto Scaling Groups - for Solutions Architects

    ASG default termination policy
     
      1. find the AZ with most instances
      2. if there are multiple instances in the AZ, delete the one with the oldest launch config
    - ASG tries to balance the number of instances across AZ by default

    [ASG Lifecycle Hooks](https://docs.aws.amazon.com/autoscaling/ec2/userguide/lifecycle-hooks.html)
    
    - kicks in during the instance launch
    - perform extra steps before instance goes in service (pending state)
    - perform actions before instance termination (terminating state)

    ASG launch template vs launch configuration
    
    - both can define:
      - AMI, instance type, a key pair, security groups, and other parameters for EC2 launch (tags, ec2 user data)
    - Launch configuration (legacy)
      - must be re-created every time
    - Launch Template (newer)
      - versioned
      - create parameters subsets (partial configuration for re-use and inheritance)
      - provision using on demnad, spot instance or a mix
      - can use T2 unlimited burst
      - AWS recommended going forward

 - [x] Fundamentals 2 Quiz

    1. Load balancers provide a static DNS name we can use in our application, because AWS wants your load balancer to be accessible using a static endpoint, even if the underlying AWS infrastructure changes
    2. Stickiness ensures traffic is sent to the same backend instance for a client. This helps maintaining session data
    3. The X-Forwarded-For header contains client IP; this header is created by your load balancer and passed on to your backend application
    4. Health checks ensure your ELB won't send traffic to unhealthy (crashed) instances
    5. NLB handles millions of requests per second with low latency; NLB provides the highest performance if your application needs it
    6. ALB supports http, https and websocket; use a NLB (Network Load Balancer) to support TCP instead
    7. The application load balancer can route to different target groups based on hostname, request path and source IP, but not geography.
    8. The capacity of your ASG cannot go over the maximum capacity you have allocated during scale out events
    9. Because ASG has been configured to leverage the ALB health checks, unhealthy instances will be terminated
    10. The metric "requests per minute" is not an AWS metric, hence it needs to be a custom metric in CloudWatch. We then can build an alarm to scale an ASG
    11. Vertical scalability refer to increasing the size of an instance
    12. Horizontal scalability refers to increasing the number of instances (e.g., scaling out an ASG)
    13. Network Load Balancers expose a public static IP, whereas an Application or Classic Load Balancer exposes a static DNS (URL); an elastic IP usually reflects poor architecural decision/design
    14. This is the most secure way of ensuring only the ALB can access the EC2 instances. Referencing by security groups in rules is an extremely powerful rule and many questions at the exam rely on it. Make sure you fully master the concepts behind it!
    15. SNI (Server Name Indication) is a feature allowing you to expose multiple SSL certs if the client supports it. Read more here: https://aws.amazon.com/blogs/aws/new-application-load-balancer-sni/
    16. Make sure you remember the Default Termination Policy for ASG. It tries to balance across AZ first, and then delete based on the age of the launch configuration
    17. ALB target groups can be EC2 instances, IP addresses and Lambda functions
    18. Cross zone load balancing distributes the traffic across all the available EC2 instances
    19. ALB's Server Name Indication (SNI) choose the right SSL certificate for the clients when there are multiple target groups based on hostname rules
    20. Target tracking scaling policy ensures the average number of connections to EC2 does not go over the expected number

## 5. (***DONE***) EC2 Storage - EBS & EFS

**EBS volumes are created for a specific AZ and can only be attached to one EC2 instance at a time. This will not help make our application stateles.**

 - [x] EBS Intro

    - EBS volumes are network drives (i.e., not physical)
      - communicate over the network with EC2 instances -> latency
      - can be detached from and attached to EC2 instances quickly
    - AZ locked
      - an EBS volume in us-east-1a cannot be attached to EC2 instances in us-east-1b
      - can only move the snapshot of a EBS volume across AZs
    - EBS volumes have provisioned capacity (size in GBs and IOPS)
      - billing based on the provisioned capacity
      - capacity can be increased over time

    EBS Volume Types

    - EBS volumes come in 4 types:
      - GP2 (SSD): general purpose SSD volume, balance between price and performance
      - IOS (SSD): highest-performance SSD volume for critical, low-latency and/or high-throughput workloads (DB etc.)
      - ST1 (HDD): low cost HDD volume designed for frequently accessed, throughput intensive workloads
      - SC1 (HDD): lowest cost HDD volume designed for less frequently accessed workloads
    - EBS volumes are characterised in size/throughput/IOPS (I/O ops per sec)
    - When in doube, always refer to the latest AWS docs
    - Only GP2 and IOI can be used as boot volume

 - [ ] EBS Intro Hands On
 - [x] EBS Volume Types Deep Dive

    [Solid state drives (SSD)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html#solid-state-drives)

    GP2
    
    - recommended for most workload
    - system boot volume
    - virtual desktops
    - low-latency interactive apps
    - dev and test environments
    - 1GB - 16 TB
    - small gp2 volumes can burst IOPS to 3000
    - max IOPS is 16000
    - 3 IOPS per GB -> max IOPS at 5334 GB

    IOI

    - critical applications that required sustained IOPS performance, or more than 16000 IOPS per volume (gp2 lmit)
    - Use case: large DB workloads, e.g., MongoDB, Cassandra, SQL Server, MySQL, PostgreSQL, Oracle
    - 4 GB - 16 TB
    - IOPS is provisioned (PIOPS): 100 - 64000 (Nitro instances) else max 32000 (other instances)
    - max ratio of provisioned IOPS to requested volume size (GB) is 50:1

    [Hard disk drives (HDD)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html#hard-disk-drives)

    ST1 (throughput optimised HDD)

    - streaming workloads requiring consistent, fast throughput at a low price
    - bit data, data warehousing, log processing
    - Apache Kafka
    - cannot be a boot volume
    - 125 GB - 16 TB
    - max IOPS: 500
    - max throughput: 500 MB/s - can burst

    SC1 (code HDD)

    - throughput-oriented storage for large volumes of data that is infrequently accessed
    - scenarios where the lowest storage cost is important
    - cannot be a boot volume
    - 125 GB - 16 TB
    - max IOPS: 250
    - max throughput of 250 MB/s - can burst

    Summary

    - gp2: general purpose volumes (cheap)
      - 3 IOPS/GB, min 100 IOPS, burst to 3000 IOPS, max 16000 IOPS
      - 1 GB - 16 TB, +1 TB = +3000 IOPS
    - io1: provisioned IOPS (expensive)
      - min 100 IOPS, max 64000 IOPS (Nitro) or 32000 (other)
      - 4 GB - 16 TB; size of volume and IOPS are independent
    - st1: throughput optimised HDD
      - 125 GB - 16 TB, 500 MB/s throughput
    - sc1: cold hdd, infrequently accessed data
      - 125 GB - 16 TB, 250 MB/s throughput

 - [x] "EBS Operation: Snapshots"

    - incremental - only backup changed blocks
    - EBS backups use IO and shouldn't be run while the application has heavy traffic
    - snapshots are stored in S3 (but the S3 buckets are not visible)
    - not neccessary to detach volume to take snapshot, but recommended
    - max 100,000 snapshots per AWS account
    - can copy snapshots across AZ/region
    - can create AMI from snapshots
    - EBS volumes restored by snapshots need to be pre-warmed (using `fio` or `dd` command to read the entire volume)
    - snapshots can be automated using Amazon Data Lifecycle Manager (Lifecycle Policy)

 - [x] "EBS Operation: Volume Migration"

    - EBS volumes are AZ locked
    - to migrate to a different AZ/region:
      - snapshot the volume
      - (optional) copy the volume to a different region
      - create a volume from the snapshot in the AZ of your choice

 - [x] "EBS Operation: Volume Encryption"

    - when we create an encrypted EBS volume,
      - data at rest is encrypted inside the volume
      - all the data in flight moving between the instance and the volume is encrypted
      - all snapshots are encrypted
      - all volumes created from the snapshot are encrypted
    - Encryption and decryption are handled transparently (no operation)
    - Encrytion has minimal impact on latency
    - EBS encryption leverages keys from KMS (AES-256)
    - copying an unecnrypted snapshot allows encryption
    - snapshots of encrypted volumes are encrypted

    Encrypt an EBS Volume

    - create an EBS snapshot of the unencrypted volume
    - encrypt the EBS snapshot (using copy)
    - create new EBS volume from the encrypted snapshot - the new EBS volume will also be encrypted
    - attached the new encrypted volume to the original instance

 - [x] EBS vs Instance Store

    - EC2 instances with no root EBS volume -> instance store
    - instance store is physically attached to the EC2 instance (EBS is a network drive)
    - instance store is an ephemeral storage
    - Pros
      - better I/O performance
      - good for buffer/cache/scratch data/temporary content
      - data survives reboot
    - Cons
      - is lost on stop/termination
      - cannot be resized
      - backup can only be done by user (not managed by AWS)

    [Amazon EC2 instance store](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html)

    - physical disk attached to the physical server of the EC2 instance
    - very high IOPS (because physical)
    - (may change over time) disks up to 7.5 TB, stripped to reach 30 TB
    - block storage (just EBS), is a file system
    - cannot change size once provisioned
    - risk of data loss if hardware fails (make sure to have redundancy - replicate the data)

 - [x] EBS RAID configurations

    - EBS is already redundant storage (replicated within an AZ)
    - to increase IOPS to 100,000 IOPS; to mirror EBS volumes
      - mount volumes in parallel in RAID settings
    - RAID must be supported by the OS
    - [RAID options](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/raid-config.html#raid-config-options)
      - RAID 0
      - RAID 1
      - RAID 5 (not recommended for AWS)
      - RAID 6 (not recommended for AWS)

    RAID 0 (only increase performance)

    - combining 2 or more volumes and getting the total disk space and I/O
    - but one disk fails, all disks failed
    - Uses cases
      - an application that needs high IOPS but not fault-tolerance
      - A DB that has replication already built-in
    - this can achieve a very big disk with very high IOPS (sum of the disk size, sum of the disk IOPS)
    - e.g.,
      - two 500 GB EBS IO1 volumes, each provisioned with 4000 IOPS ->
      - 1000 GB RAID 0 array with a bandwidth of 8000 IOPS and a throughput of 1000 MB/s

    RAID 1 (only increase fault tolerance)

    - RAID 1 = mirroring a volume to another
    - if one disk failes, our logical volume is still working
    - we have to send the data to two EBS volumes at the same time (2x network)
    - Use cases
      - an application that needs volume fault tolerance
      - an application that you need to service disks
    - e.g.,
      - two 500 GB EBS IO1 volumes with 4000 provisioned IOPS each ->
      - a 500 GB RAID 1 array (a logical volume) with a bandwidth of 4000 IOPS and a throughput of 500 MB/s

 - [x] EFS Overview (Elastic File System)

    - Managed NFS (network file system) that can be mounted on many EC2
    - EFS works across AZs/regions
    - highly available, highly scalable; expensive (3x gp2), pay per use
    - Use cases: content management, web content serving, data sharing, WordPress
    - NFSv4.1 protocol
    - access controlled by IAM security group
    - compatible with Linux based AMI (not Windows)
    - encryption at rest using KMS
    - POSIX file system (~Linux) that has a standard file API
    - file system scales automatically, pay per use, no capacity planning

    Performance & Storage Classes

    - EFS Scale
      - 1000s of concurrent NFS clients, > 10 GB/s throughput
      - grow to petabyte-scale network file system automatically
    - Performance mode (set at EFS creation time)
      - general purpose (default): latency-sensitive use cases (web server, CMS, etc.)
      - max I/O - higher latency, throughput, highly parallel (big data, media processing)
    - Storage tiers (lifecycle management feature - move file after N days)
      - standard: for frequently accessed files
      - infrequent access (EFS-IA): cost to retrieve fiels, lower price to store

 - [x] EFS Hands On

    - install [amazon-efs-utility](https://docs.aws.amazon.com/efs/latest/ug/using-amazon-efs-utils.html) on EC2 instances to attach EFS

 - [x] EBS & EFS - Section Cleanup
 - [x] EFS vs EBS

    EBS

    - attached to one EC2 instance at a time
    - AZ locked
    - gp2: I/O increases as disk size increases (max 16000 IOPS, 5334 GB)
    - IO1: can increase I/O independently (max 64000 IOPS for Nitro instances, or 32000 for others)
    - to migrate EBS across AZ
      - taka snapshot
      - restore snapshot to target AZ
      - EBS backups use I/O - should not run during heavy application traffic
    - by default, root EBS volumes of instances get terminated together with instance termination - can be disabled

    EFS

    - mount to 100s of instances across AZ
    - EFS share websit files (WordPress)
    - only for Linux instances (POSIX)
    - higher price point than EBS
    - can leverage EFS-IA for cost savings

    EFS vs EBS vs Instance Store
    - EFS (managed NFS, mounts to 100s of ec2, pay per use)
    - EBS (network drive, mounts to 1 ec2, RAID 0 & RAID 1, capacity planning)
    - instance store (physical drive, physically attached, ephemeral, highest IOPS)

 - [x] EC2 Data Management - EBS & EFS Quiz

    1. EBS volumes are AZ locked. EBS Volumes are created for a specific AZ. It is possible to migrate them between different AZ through backup and restore
    2. EBS IOPS peaks at 16,000 IOPS. or equivalent 5334 GB. Increase in volume size beyond 5334 GB will not increase IOPS further
    3. RAID 0 leverage EBS volumes in parallel to linearly increase performance, while accepting greater failure risks. See https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/raid-config.html
    4. RAID 1 will mirror data and allow instances to not be affected if an EBS volume enrirely fails. See https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/raid-config.html
    5. EFS is a network file system (NFS) and allows to mount the same file system on EC2 instances that are in different AZ
    6. Instance Store provide the best disk performance compared to EBS and EFS
    7. You are running a high-performance database that requires an IOPS of 210,000 for its underlying filesystem. What do you recommend?

        Use an **instance store**, instead of EBS gp2 drive / EBS io1 drive / EFS.

        Is running a DB on EC2 instance store possible? It is possible to run a database on EC2. It is also possible to use instance store, but there are some considerations to have. The data will be lost if the instance is stopped, but it can be restarted without problems. One can also set up a replication mechanism on another EC2 instance with instance store to have a standby copy. One can also have back-up mechanisms. It's all up to how you want to set up your architecture to validate your requirements. In this case, it's around IOPS, and we build an architecture of replication and back up around it

## 6. (***WIP***) "AWS Fundamentals: RDS + Aurora + ElastiCache"

 - [ ] AWS RDS Overview
 - [ ] RDS Read Replicas vs Multi AZ
 - [ ] AWS RDS Hands On
 - [ ] RDS Encryption + Security
 - [ ] Aurora Overview
 - [ ] Aurora Hands On
 - [ ] ElastiCache Overview
 - [ ] ElastiCache Hands On
 - [ ] ElastiCache for Solution Architect
 - [x] RDS / Aurora / ElastiCache Quiz

    1. In this question, we consider a disaster to be an entire Availability Zone going down. In which case Multi-AZ will help. If we want to plan against an entire region going down, backups and replication across regions would help.
    2. Be very careful with the way you read questions at the exam. Here, the question is asking which solution is NOT adapted to this problem. ElastiCache and RDS Read Replicas do indeed help with scaling reads.
    3. Read Replicas have asynchronous replication and therefore it's likely our users will only observe eventual consistency
    4. Read Replicas add new endpoints for databases to read from and therefore we must change our application to have the list of these endpoints in order to balance the read load and connect to the databases
        
        Multi AZ keeps the same connection string regardless of which database is up. Read Replicas imply we need to reference them individually in our application as each read replica will have its own DNS name
    5. Multi AZ ensure the Redis cluster will always be available
    6. Storing Session Data in ElastiCache is a common pattern to ensuring different instances can retrieve your user's state if needed.
    7. Read Replicas will help as our analytics application can now perform queries against it, and these queries won't impact the main production database.
    8. PostgreSQL on RDS does not support TDE (Transparent Data Encryption)
    9. Oracle on RDS does not support IAM authentication
    10. Global Databases allow you to have cross region replication
    11. Use Redis Auth to force users to enter their password - enhance the security of the Redis cache
    12. Your company has a production Node.js application that is using RDS MySQL 5.6 as its data backend. A new application programmed in Java will perform some heavy analytics workload to create a dashboard, on a regular hourly basis. You want to the final solution to minimize costs and have minimal disruption on the production application, what should you do?

        Create a read replica in the same AZ and run the analytics workload on the replica database - this will minimize cost because the data won't have to move across AZ
    13. read replica in different region (DR) to mitigate a regional outage; multi AZ to achieve high availability
    14. You are managing a PostgreSQL database and for security reasons, you would like to ensure users are authenticated using short-lived credentials. What do you suggest doing?

        Use PostgreSQL for RDS and authenticate using a token obtained through the RDS service. In this case, IAM is leveraged to obtain the RDS service token, so this is the IAM authentication use case.
    15. An application is running in production, using an Aurora database as its backend. Your development team would like to run a version of the application in a scaled-down application, but still, be able to perform some heavy workload on a need-basis. Most of the time, the application will be unused. Your CIO has tasked you with helping the team while minimizing costs. What do you suggest?

        Use Aurora serverless.

 - [x] List of Ports to be familiar with

## 7. (***DONE***) Route 53

 - [x] Route 53 Overview

    - Route 53 is a managed DNS
    - DNS is a collection of rules and records which helps clients understand how to reach a server through its domain name
    - 4 most common record types:
      - A: hostname to IPv4
      - AAAA: hostname to IPv6
      - CNAME: hostname to hostname
      - Alias: hostname to AWS resource
    - can use public domain names (own or buy) or private domain names (resolved with a VPC)
    - features
      - load balancing (through DNS - client load balancing)
      - health check (limited)
      - routing policy: simple, failover, geolocation, latency, weighted, multi value
    - $0.50 monthly per hosted zone

 - [x] Route 53 Hands On

    - `nslookup` (win)/`dig` (MacOS)

 - [x] Route 53 - EC2 Setup
 - [x] Route 53 - TTL
 - [x] Route 53 CNAME vs Alias

    - AWS resouces (e.g., load balancer, cloudfront, etc.) expose an AWS hostname: *.${aws_region}.*.amazonaws.com
    - application domain name/hostname directs to aws resouce: app.mydomain.com
    - CNAME
      - points a hostname to any other hostname: app.mydomain.com -> *.*.com
      - **only for non root domain**
    - Alias:
      - points a hostname to an AWS resource (app.mydomain.com -> *.amazonaws.com)
      - **works for both root and non root domain (mydomain.com vs app.mydomain.com)**
      - free of charge
      - native health check

 - [x] Routing Policy - Simple

    - redirect to a single resource
    - cannot attach health check
    - if multiple values are returned, a random one is chosen by the client

 - [x] Routing Policy - Weighted

    - distribute % requests to endpoints
    - use cases
      - test 1% of traffic on the new app version
      - split traffic between regions
    - can attach health checks

 - [x] Routing Policy - Latency

    - redirects to the server with the lowest latency
    - latency is evaluated in terms of user to designated AWS region
      - e.g., Germany may be directed to the US (if lowest latency)

 - [x] Route 53 Health Checks

    - have X health checks failed -> unhealthy (default 3)
    - have X health checks passed -> healthy (default 3)
    - default health check interval: 30 seconds (can set to 10s at a higher cost)
      - about 15 health checkers will check the endpoint health
      - one request every 2 seconds on average
    - http, https and tcp health checks (no ssl verification)
    - possibility of integrating the health check with CloudWatch
    - health checks can be linked to Route53 DNS queries

 - [x] Routing Policy - Failover

    - mandatory health check for the primary record

 - [x] Routing Policy - Geolocation

    - different from latency routing policy
    - routing based on user location
      - specific country go to specific IP
    - should create a default record (for no location match)

 - [x] Routing Policy - Multi Value

    - route traffic to multiple resources
    - can attach health check (improve over simple routing policy)
    - up to 8 healthy records are returned for each multi value query
    - multi value is not a substitute for having an ELB

 - [x] 3rd Party Domains & Route 53

    - a domain name registrar is an organisation that manages the reservation of internet domain names
    - famous names:
      - GoDaddy
      - Google Domains
      - ... etc.
    - Route 53 is a domain name registrar
    - Domain registrar != DNS

    3rd party registrar with AWS Route 53
    - if you buy a domain on 3rd party registrar/website, you can still use Route 53
      1. create a hosted zone in Route 53
      2. update NS records on 3rd party website to use Route 53 name servers
    - Domain registrar != DNS
    - but each domain registrar usually comes with some DNS features

 - [x] Section Cleanup
 - [x] Route 53 Quiz

    1. The DNS protocol does not allow you to create a CNAME record for the top node of a DNS namespace (mycoolcompany.com), also known as the zone apex
    2. Weighted allows you to redirect a part of the traffic based on a weight (hence a percentage). It's common to use to send a part of a traffic to a new application you're deploying
    3. DNS records have a TTL (Time to Live) in order for clients to know for how long to caches these values and not overload the DNS with DNS requests. TTL should be set to strike a balance between how long the value should be cached vs how much pressure should go on the DNS
    4. Latency will evaluate the latency results and help your users get a DNS response that will minimize their latency (e.g. response time)
    5. You have a legal requirement that only people in a specific country should be able to access your website. Geolocation Route 53 record can achieve this
    6. Private hosted zones are meant to be used for internal network queries and are not publicly accessible. Public Hosted Zones are meant to be used for people requesting your website through the public internet. Finally, NS records must be updated on the 3rd party registrar.

## 8. (***DONE***) Classic Solutions Architecture Discussions

 - [x] Solutions Architecture Discussions Overview
 - [x] WhatsTheTime.com

    stateless web app

    - public vs private IP and EC2 instances
    - Elastic IP vs Route 53 vs load balancers
    - maintaining EC2 instances manually vs Auto Scaling Groups (ASG)
    - multi AZ to survive disasters
    - ELB health checks
    - security group rules
    - reservation of capacity for cost saving when possible
    - 5 pillars for application architecture:
      - cost (reserve capacity for cost saving)
      - performance (vertical scaling, ELB, auto-scaling group)
      - reliability (Route 53,multi-AZ for the ELB and the ASG)
      - security (security group to link the load balancer to the EC2 instances securely)
      - operation excellence (manual process → fully automated with ASG)

 - [x] MyClothes.com

    stateful web app

    3-tier architecture for web app (client, web, DB)

    - ELB sticky sessions
    - web clients for storing cookies and making our web app stateless
    - ElastiCache
      - for stroing sessions (alternative: DynamoDB)
      - for caching data from RDS
      - multi AZ
    - RDS
      - for storing user data
      - read replicas for scaling reads
      - multi AZ for disaster recovery
      - tight security with security groups referencing each other
    
    **EBS volumes are created for a specific AZ and can only be attached to one EC2 instance at a time. This will not help make our application stateles.**

 - [x] MyWordPress.com

    - Aurora DB to have easy multi-AZ and read replicas
    - storing data in EBS (single instance application), vs
    - storing data in EFS (distributed application)

 - [x] Instantiating applications quickly

    - EC2 instances:
      - **Use a Golden AMI**: install the applications, OS dependencies etc. beforehand
      - **Bootstrap using User Data**: for dynamic configuration, use User Data scripts
      - **Hybird**: mix Golden AMI and User Data (Elastic Beanstalk)
    - RDS DB:
      - Restore from a snapshot: the DB will have schemas and data ready
    - EBS Volumes:
      - Restore from a snapshot: the disk will already be formatted and have data

 - [x] Beanstalk Overview

    - managed service
      - instance configuration and OS is handled by beanstalk
      - deployment strategy is configurable but performed by ElasticBeanStalk
    - Just the application code is the responsibility of the developer
    - 3 architecture models
      - single instance deployment: good for development
      - LB + ASG: great for production or pre-prod web applications
      - ASG only: greate for non-web apps in production (workers etc.)
    - has 3 components
      - application
      - application version: each deployment gets assigned a version
      - environment name (dev, test, prod...): free naming
    - deploy application versions to environments and can promote application versions to the next environment
    - rollback feature to previous application version
    - ful control over lifecycle of environments
    - support many languages/platforms: Go, Java SE, Java with Tomcat, .NET on Windows Server with IIS, node.js, PHP, Python, Ruby, Packer Builder, single container/multi container/preconfigured docker
    - write your own custom platform (advanced)

 - [x] Beanstalk Hands On
 - [x] Solutions Architecture Discussions - Classic

    1. Reserving 2 instnances is the way to save costs further as we will run 2 EC2 instances no matter what.
    2. EBS volumes are created for a specific AZ and can only be attached to one EC2 instance at a time. This will not help make our application stateles
    3. EFS is a network file system (NFS) and allows to mount the same file system to 100s of EC2 instances. Publishing software updates their allow each EC2 instance to access them.
    4. Golden AMI are a standard in making sure you snapshot a state after an application installation so that future instances can boot up from that AMI quickly.
    5. I am creating an application and would like for it to be running with minimal cost in a development environment with Elastic Beanstalk. I should run it in single instance mode which will create one EC2 instance and one Elastic IP.
    6. Golden AMI are a standard in making sure save the state after the installation or pulling dependencies so that future instances can boot up from that AMI quickly.

## 9. (***DONE***) Amazon S3 Introduction

 - [x] Amazon S3 - Section Introduction
 - [x] S3 Buckets and Objects
    
    Buckets
    
    - buckets must have globally unique name
    - buckets are region locked
    - Naming convention
      - no uppercase
      - no underscore
      - 3-63 characters long
      - not an IP
      - must start with lowercase letter or number
    
    Objects

    - objects have a key
    - the key is the full path, e.g., s3://my-bucket/my_folder/my_file.txt
    - the key = prefix + object name
      - prefix = "my_folder/"
      - object name = my_file.txt
    - no "directory" concept in buckets (though UI presents as folders and files)
    - just keys with very long names that contain slashes ("/")
    - object values are the content of the body
      - max object size is 5TB (5000GB)
      - if a file is larger than 5GB, must use multi-part upload
    - metadata (list of text key/value pairs - system or user metadata)
    - tags (unicode key/value pairs - up to 10) - useful for security/lifecycle
    - version ID (if versioning is enabled)

 - [ ] S3 Buckets and Objects - Hands On
 - [x] S3 Versioning

    - versioning is enabled at the bucket level
    - same key overwrite will increment the version: 1, 2, 3...
    - best practice to version buckets
      - protect against unintended deletes (restore to a version)
      - easy roll back to previous version
    - any files prior to versioning enabled will have version "null"
    - suspending versioning does not delete the previous versions
 
 - [x] S3 Versioning - Hands On
 - [x] S3 Encryption

    - 4 encrytion methods
      - SSE-S3: encrypts S3 objects using keys handled and managed by AWS
        - server side encryption
        - AES-256 encryption type
        - must set header: "x-amz-server-side-encryption":"AES256"
      - SSE-KMS: leverage AWS Key Management Service to manage encryption keys
        - server side encryption
        - pros: user control + audit trail
        - server side encryption
        - must set header: "x-amz-server-side-encryption":"aws:kms"
        - AWS manage the encryption keys but you have full control of the key rotation policy
      - SSE-C: we manage keys, AWS encrypts the S3 objects
        - S3 doesn't store the encryption keys
        - HTTPS only
        - encryption key must be provided in HTTP headers in every HTTP request
      - client side encryption
        - client library, e.g., Amazon S3 encryption client
        - client must encrypt data themselves while sending/retrieving data from S3
        - user must manage keys and encryption cycle

    Encryption in transit (SSL/TLS)
    - Amazon S3 exposes
      - HTTP end point: not encrypted
      - HTTPS end point: encryption in flight
    - HTTPS is mandatory for SSE-C
    - Encryption in flight is also called SSL/TLS

 - [x] S3 Encryption - Hands On

    - SSE-C can only be done programatically (e.g., aws cli) as we need to specify the encryption key

 - [x] S3 Security & Bucket Policies

    - user based: IAM policies - which api calls should be allowed for a specific user from IAM console
    - resource based
      - bucket policies - bucket wide rules form the S3 console; allows cross account
        - json based
          - Resouces: buckets and objects
          - Action: set of API to allow or deny
          - Effect: allow/deny
          - Principal: the account or user to apply to
        - use S3 policy to
          - grant public access to the bucket
          - force objects to be encrypted at upload
          - grant access to another account (cross account)
        - bucket setting to block public access
          - can be set at account level
        - other
          - networking: supports VPC endpoints (for instances in the VPC without internet traffic)
          - logging and audit: access logs can be stored in another S3 bucket; API calls can be logged in AWS CloudTrail
          - user security: MFA delete - MFA required to delete objects in versioned buckets; pre-signed URLs - URLs that are valid only for a limited time, e.g., premium video service for logged in users
      - object access control list (ACL) - finer grain
      - bucket access control list (ACL) - less common
    - an IAM principal can access an S3 object if
      - the user IAM permissions allow it, OR the resouces policy ALLOWS it
      - AND there's no explicit DENY

 - [x] S3 Bucket Policies Hands On

    - AWS policy generator
    - use * to represent any object - https://docs.aws.amazon.com/AmazonS3/latest/dev/s3-arn-format.html
    - [How to Prevent Upload of Unencrypted Objects to Amazon S3](https://aws.amazon.com/blogs/security/how-to-prevent-uploads-of-unencrypted-objects-to-amazon-s3/)

 - [x] S3 Websites

    - S3 can host static websites (accessible on wwww)
    - URL will be
      - `${bucket-name}.s3-website-${aws-region}.amazonaws.com`
      - `${bucket-name}.s3-website.${aws-region}.amazonaws.com`
    - 403 forbidden error -> bucket policy must allow public reads
      1. disable block public access (bucket settings)
      2. create a bucket policy to allow public access (s3:GetObject) to specific/all resources

 - [x] S3 CORS

    S3: [Cross-origin resource sharing (CORS)](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html)
    - an origin is a scheme (protocol), a host (domain) plus a port
      - e.g., https://www.example.com (implied port is 443 for https, 80 for http)
    - browser based mechanism to allow requests to other origins while visiting the main origin
    - same origin: **https://www.example.com**/app1 & **http://www.example.com**/app2
    - different origin: https://**www**.example.com & https://**other**.example.com
    - the requests won't be fulfilled unless the other origin allows for the requests, using CORS headers (e.g., Access-Control-Allow-Origin)

    S3 CORS
    - if a client want to make a cross-origin request on our S3 buckegt, we need to enable the correct CORS headers (***popular exam question***)
    - can allow for specific origins or for * (all origins)

 - [x] S3 CORS Hands On

    - [How do I configure CORS on my bucket?](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html#how-do-i-enable-cors)

 - [x] [S3 Consistency Model](https://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html#ConsistencyModel)

    - Read after write consistency for PUT of new objects
      - PUT 200 -> GET 200: as soon as a new object is written, we can retrieve it
      - this is true except a GET before PUT (e.g., to see if object already existed)
        - GET 404 -> PUT 200 -> GET 404: eventually consistent
    - Eventual Consistency for DELETE and PUT of existing objects
      - PUT 200 -> PUT 200 -> GET 200 (might be older version): if we read an object after update (PUT), we might get older version
      - DELETE 200 -> GET 200: if we dlete an object, we might still be able to retrieve it for a short time
    - **NOTE**: there is no way to request "strong consistency"

 - [x] AWS S3 Quiz

    1. Use Multi Part to upload any file bigger than 5GB; Multi Part Upload is also recommended as soon as the file is over 100MB
    2. Bucket names must be globally unique
    3. You've added files in your bucket and then enabled versioning. The files you've already added will have version as "null"
    4. SSE-C allows full control over the encryption keys, but let AWS do the encryption. 
        
        SSE-S3 and SSE-KMS let got of control over the encryption keys. Client side encryption means encryption is done manually by the user
    5. With SSE-KMS you let AWS manage the encryption keys but you have full control of the key rotation policy
    6. With Client Side Encryption you perform the encryption yourself and send the encrypted data to AWS directly. AWS does not know your encryption keys and cannot decrypt your data.
    7. Explicit DENY in an IAM policy will take precedence over a bucket policy permission
    8. Cross-origin resource sharing (CORS) defines a way for client web applications that are loaded in one domain to interact with resources in a different domain. To learn more about CORS, go here: https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html
        
        If the bucket policy was wrong, the files wouldn't load in either browser

## 10. (***DONE***) AWS CLI, SDK, IAM Roles & Policies

 - [x] Developing on AWS Introduction
 - [ ] AWS CLI Setup on Windows
 - [x] AWS CLI Setup on Mac OS X
 - [ ] AWS CLI Setup on Linux
 - [x] AWS CLI Configuration
 - [x] AWS CLI on EC2
 - [x] AWS CLI Practice with S3
 - [x] IAM Roles and Policies Hands On (An EC2 instance can only have one IAM Role attached at any point of time)
 - [x] AWS Policy Simulator
 - [x] AWS EC2 Instance Metadata (link-local address within AWS: http://169.254.169.254/latest/meta-data)
 - [x] AWS SDK Overview
 - [x] CLI & SDK Quiz

## 11. Advanced Amazon S3 & Athena

 - [ ] S3 MFA Delete
 - [ ] S3 MFA Delete Hands On
 - [ ] S3 Access Logs
 - [ ] S3 Access Logs - Hands On
 - [ ] S3 Replication (Cross Region and Same Region)
 - [ ] S3 Replication - Hands On
 - [ ] S3 Pre-signed URLs
 - [ ] S3 Pre-signed URLs - Hands On
 - [ ] S3 Storage Classes + Glacier
 - [ ] S3 Storage Classes + Glacier - Hands On
 - [ ] S3 Lifecycle Rules
 - [ ] S3 Lifecycle Rules - Hands On
 - [ ] S3 Performance
 - [ ] S3 Select & Glacier Select
 - [ ] S3 Event Notifications
 - [ ] S3 Event Notifications - Hands On
 - [ ] Athena Overview
 - [ ] Athena Hands On
 - [ ] S3 Lock Policies & Glacier Vault Lock
 - [ ] S3 Advanced & Athena - Quiz

## 12. (***DONE***) CloudFront & AWS Global Accelerator

 - [x] CloudFront Overview

    - Content Delivery Network (CDN)
    - improves read performance, content is cached at the edge
    - 216 point of presence globally (edge locations)
    - DDoS protection, integration with Shield, AWS Web Application Firewall
    - can expose external HTTPS and can talk to internal HTTPS backends

    CloudFront Origins
    - S3
      - For distributing files and caching them at the edge
      - enhanced security with cloudfront Origin Access Identity (OAI)
      - CloudFront can be used as an ingress (to upload files to S3)
    - Custom Origin (HTTP)
      - application load balancer
      - ec2 instance
      - S3 website (must enable the bucket as a static S3 website)
      - Any HTTP backend you want

    CloudFront Geo Restriction
    - restrict who can access your distribution
      - **whitelist**: allow users to access content only if they are in one of the countries on a list of approved countries
      - **blacklist**: prevent users from accessing the content if they are in one of the countries on a blacklist of banned countries
    - the 'country' is determined using a 3rd party Geo-IP database
    - use case: copyright laws to contol access content

    CloudFront vs S3 cross region replication
    - CloudFront
      - global edge network
      - Files are cahced for a TTL (maybe a day)
    - S3 cross region replication
      - must be set up for each region you want replication to happen
      - Files are updated in near real-time
      - read only
      - great for dynamic contet that needs to be availalbe at low-latency in few region

 - [x] CloudFront with S3 - Hands On (Use policy to only allow Origin Access Identity (OAI) to access private S3 files)

    - S3; cloudfront distribution; origin access identity
    - use bucket policy to limit S3 access to only the origin access identity
    - without bucket policy S3 objects must be public (both bucket settings and object level)
    - aws cloudfront redirect to S3 (307 temporary redirect) - DNS might take a few hours to sync
 
 - [x] CloudFront Signed URL / Cookies (one signed URL per file; one signed cookie for many files)
 - [x] AWS Global Accelerator - Overview (2 Static IPs + ALB)
 - [x] AWS Global Accelerator - Hands On
 - [x] CloudFront & AWS Global Accelerator Quiz

## 13. AWS Storage Extras

 - [ ] Snowball Overview
 - [ ] Snowball Hands On
 - [ ] Storage Gateway Overview
 - [ ] Storage Gateway - File Gateway Hardware Appliance
 - [ ] Storage Gateway Hands On
 - [ ] Amazon FSx - Overview
 - [ ] Amazon FSx - Hands On
 - [ ] All AWS Storage Options Compared
 - [ ] AWS Storage Extras - Quiz

## 14. "Decoupling applications: SQS, SNS, Kinesis, Active MQ"

 - [ ] Introduction to Messaging
 - [ ] Amazon SQS - Standard Queues Overview
 - [ ] SQS - Standard Queue Hands On
 - [ ] SQS - Message Visibility Timeout
 - [ ] SQS - Dead Letter Queues
 - [ ] SQS - Delay Queues
 - [ ] SQS - FIFO Queues
 - [ ] SQS + Auto Scaling Group
 - [ ] Amazon SNS - Overview
 - [ ] SNS - Hands On
 - [ ] SNS and SQS -  Fan Out Pattern
 - [ ] Kinesis Data Streams Overview
 - [ ] Kinesis Data Streams Hands On
 - [ ] Kinesis Firehose & Kinesis Data Analytics
 - [ ] Data Ordering for Kinesis vs SQS FIFO
 - [ ] SQS vs SNS vs Kinesis
 - [ ] Amazon MQ
 - [ ] Messaging and Integration Quiz

## 15. (***DONE***)Serverless Overviews from a Solution Architect Perspective

 - [x] About the Serverless Section
 - [x] Serverless Introduction
 - [x] Lambda Overview

    EC2
    - virtual servers in cloud
    - limited by RAM and CPU
    - continuously running
    - scaling means intervention to add/remove servers

    Lambda
    - virtual functions - no servers to manage
    - limited by time (max 15min) - short execution
    - run on demand
    - scaling is automated
    - docker is not for Lambda; it's for ECS/Fargate
    - use cases
      - event trigger, e.g., new upload event in S3 trigger
      - serverless CRON job

    Pricing
    - https://aws.amazon.com/lambda/pricing
    - pay per call
    - pay per duration

 - [x] Lambda Hands-On

    - handler is specified as the function entry
    - lambda execution role has the permission to create cloudwatch logs

 - [x] Lambda Limits (per region)

    Execution
    - memory: 128 - 3008 MB (64 MB increments)
    - maximum execution time: 900 seconds (15min)
    - environment variables (4kb)
    - disk capacity in the function container (/tmp): 512 MB
    - concurrency executions: 1000 (request to increase)

    Deployment
    - lambda function deployment size (compressed .zip): 50 MB
    - size of uncompressed deployment (code + dependencies): 250 MB
    - can use the /tmp directory to load other files at startup
    - size of environment variables: 4 KB

 - [x] Lambda@Edge
 - [x] DynamoDB Overview

    - fully managed, highly available with replication across 3 AZ
    - NoSQL database - not a relational database
    - scales to massive workloads, distributed database
    - millions of requests per seconds, trillions of row, 100s of TB of storage
    - fast and consistent in performance (low latency on retrieval)
    - integrated with IAM for security, authorisation and administration
    - enables event driven programming with DynamoDB streams
    - low cost and auto scaling capabilities

    Basics
    - made of tables (no need to create DB, start right away with tables)
    - each table has primary key (must be decided at creation time)
    - each table can have an infinite number of items (= rows)
    - each item has attributes (can be added over time - can be null)
    - max size of an item is 400 KB
    - data types
      - scalar types: string, number, binary, boolean, null
      - document types: list, map
      - set types: string set, number set, binary set

    Provisioned throughput
    - table must have provisioned read and write capacity units
    - **Read Capacity Units** (RCU): throughput for reads ($0.00013 per RCU)
      - 1 RCU = 1 strongly consistent read of 4 KB per second
      - 1 RCU = 2 eventually consistent read of 4 KB per second
    - **Write Capacity Units** (WCU): throughput for writes ($0.00065 per WCU)
      - 1 WCU = 1 write of 1 KB per second
    - option to set up auto-scaling of throughput to meet demand
    - throughput can be exceeded temporarily using 'burst credit'
    - if burst credit are empty, you will get a 'ProvisionedThroughputException'
    - it's then advised to do an exponential back-off retry

 - [x] DynamoDB Hands-On
 - [x] DynamoDB Advanced Features

    DAX = DynamoDB Accelerator
    - seamless cache for DynamoDB, no application rewrite
    - writes go through DAX to DynamoDB
    - micro second latency for cached reads & queries
    - solves the hot key problem (too many reads)
    - 5 minutes TTL for cache by default
    - up to 10 nodes in the cluster
    - multi AZ (3 nodes minimum recommended for production)
    - secure (encryption at rest with KMS, VPC, IAM, CloudTrail..)

    DynamoDB Streams
    - changes in DynamoDB (create, update, delete) can end up in a DynamoDB Stream
    - this stream can be read by AWS Lambda which can:
      - react to changes in real time (welcome email to new users)
      - Analytics
      - create derivative tables / views
      - insert into ElasticSearch
    - cross region replication must use DynamoDB Streams
    - Stream has 24 hours of data retention

    New Features
    - Transactions
      - 'all or nothing' type of operation
      - coordinated insert, update and delete across multiple tables
      - up to 10 unique items or up to 4 MB of data
    - On Demand
      - no capacity planning needed (WCU/RCU) -scales automatically
      - 2.5 times more expensive than provisioned capacity (use with care)
      - helpful when spikes are un-predictable or the application is very low throughput

    Security & Others
    - Security
      - VPC endpoints available to access DynamoDB without internet
      - access fully controlled by IAM
      - encryption at rest using KMS
      - encryption in transit using SSL/TLS
    - Backup and restore
      - point in time restore like RDS
      - no performance impact
    - Global Tables (cross region replication)
      - multi region, fully replicated, high performance
      - active-active replication, many regions
      - must enable DynamoDB streams
      - Useful for low latency, DR purposes
    - Amazon DMS can be used to migrate to DynamoDB (from Mongo, Oracle, MySQL, S3, etc.)
    - local DynamoDB instance for development purposes

 - [x] API Gateway Overview

    - AWS Lambda + API Gateway: no infra
    - support WebSocket Protocol
    - handle API versioning (v1, v2...)
    - handle different environments (dev, test, prod...)
    - handle security (authentication and authorization)
    - create API keys, handle request throttling
    - swagger/open API import to quicklyu define APIs
    - transform and validate requests and responses
    - generate SDK and API specifications
    - cache API responses

    Integrations
    - Lambda Function
      - invoke Lambda function
      - easy way to expose REST api backed by AWS Lambda
    - HTTP
      - expose HTTP endpoints in the backend
      - e.g., internal HTTP api on premise, ALB etc.
      - Why? add rate limiting, caching, user authentications, API keys, etc.
    - AWS services
      - expose any AWS api through the API Gateway
      - e.g., start an AWS Step Function workflow, post a message to SQS
      - Why? add authentication, deploy publicly, rate control, etc.

    Endpoint Types
    - edge-optimised (default): for global clients
      - requests are routed through the CloudFront Edge locations (improves latency)
      - the API Gateway still lives in only one region
    - Regional
      - for clients within the same region
      - can manually combine with CloudFront (more control over the caching strategies and the distribution)
    - Private
      - can only be accessed from your VPC using an interface VPC endpoint (ENI)
      - use a resource policy to define access

 - [x] API Gateway Basics Hands-On
 - [x] API Gateway Security

    IAM permissions
    - create an IAM policy authorisation and attach to User/Role
    - API Gateway verifies IAM permissions passed by the calling application
    - good to provide access within your own infra
    - leverages 'Sig v4' capability where IAM credentials are in headers

    Lambda Authoriser (formerly Custom Authoriser)
    - uses AWS Lambda to validate the token in header being passed
    - option to cache result of authentication
    - helps to use OAuth/SAML/3rd party type of authentication
    - Lambda must return an IAM policy for the user

    Cognito User Pools
    - Cognito fully manages user lifecycle
    - API gateway verifies identity automatically from AWS Cognito
    - No custom implementation required
    - Cognito only helps with authentication, not authorisation

    Summary
    - IAM
      - for users/roles within AWS account
      - authentication + authorisation
      - leverage Sig v4
    - Custom Authorizer
      - great for 3rd party tokens
      - very flexible in terms of what IAM policy is returned
      - authentication + authorisation
      - pay per Lambda invocation
    - Cognito User Pool
      - manage your own user pool (can be backed by Facebook, Goole login, etc.)
      - No need to write any custom code
      - must implement authorisation in the backend

 - [x] AWS Cognito Overview

    - Cognito user pool
      - sign in functionality for app users
      - integrate with API Gateway
      - create a serverless DB of user for mobile apps
      - simple login: username or email / password
      - can verify email/phone number and add MFA
      - can enable federated identities (FB, Google, SAML, etc.)
      - returns a JSON Web Token (JWT)
      - can integrate with API Gateway for authentication
    - Cognito identity pools (federated identity)
      - provide AWS credentials to users so they can access AWS resources directly
      - integrate with Cognito user pool as an identity provider
      - Goal
        - provide direct access to AWS resources from client side
      - How
        - log in to federated identity provider - or remain anonymous
        - get temporary AWS credentials back from the Federated Identity Pool
        - these credentials come with a pre-defined IAM policy stating their permissions
      - e.g.,
        - provide (temporary) access to write to S3 bucket using Facebook login
    - Cognito Sync
      - synchronise data from device to Cognito
      - may be deprecated and replaced by AppSync
      - store preference, config, state of app
      - cross device synchronisation (iOS, android, etc.)
      - offline capability (synchronisation when back online)
      - requires federated identity pool in Cognito (not user pool)
      - store data in datasets (up to 1 MB)
      - sync up to 20 datasets

 - [x] Serverless Application Model (SAM) Overview

    - framework for developing and deploying serverless applications
    - all the configuration is in YAML
      - Lambda, dynamoDB, API Gateway, Cognito User Pools
    - SAM can run Lambda, API Gateway, DynamoDB locally
    - SAM can use CodeDeploy to deploy Lambda functions

 - [x] Serverless Quiz

    1. Lambda max timeout is 15 minutes
    2. Environment variables allow for your Lambda to have dynamic variables from within
    3. DynamoDB is a serverless service and as such we don't provision an instance type for our database. We just say how much RCU and WCU we require for our table (or auto scaling)
    4. RCU and WCU are decoupled in DynamoDB - can be adjusted independently
    5. A DynamoDB Accelerator (DAX) cluster is a cache that fronts your DynamoDB tables and caches the most frequently read values. They help offload the heavy reads on hot keys off of DynamoDB itself, hence preventing the ProvisionedThroughputExceededException
    6. DynamoDB streams allow Lambda to receive events in real time, e.g., send welcome email to new users
    7. Lambda is serverless...
    8. Cognito User Pools directly integration with Facebook Logins
    9. WCU & RCU with autoscaling works best for smooth sustained usage (capacity planning for provisioned usage); on demand

## 16. (***WIP***) Serverless Solution Architecture Discussions

 - [x] "Mobile Application: MyTodoList"

    Requirements
    - expose as rest api with https
    - serverless architecture
    - users directly interact with their own folder in S3
    - users authenticate through a managed serverless service
    - users can write and read to-dos, but they mostly read them
    - DB should scale and have high read throughput

    REST API layer
    - mobile client <-(rest https)-> API Gateway <-invoke-> lambda <-query-> DynamoDB

      ```plantuml
      @startuml
      skinparam componentStyle rectangle
      [client] <-> [API Gateway]:HTTPS REST
      [API Gateway] <-> [Lambda]:invoke
      [Lambda] <-> [DynamoDB]:query
      @enduml
      ```

    - mobile client <-authenticate-> Cognito <-verify authentication-> API Gateway
    
      ```plantuml
      @startuml
      skinparam componentStyle rectangle
      [client] <-> [API Gateway]:HTTPS REST
      [API Gateway] <-> [Lambda]:invoke
      [Lambda] <-> [DynamoDB]:query
      [client] <-down-> [Cognito]:authenticate
      [Cognito] <-> [API Gateway]:verify authentication
      @enduml
      ```

    - mobile client <-store/retrieve files (permissions)-> S3
      - mobile client <-authenticate-> Cognito <-generate temp credentials-> AWS STS

      ```plantuml
      @startuml
      skinparam componentStyle rectangle
      [client] <-> [API Gateway]:HTTPS REST
      [API Gateway] <-> [Lambda]:invoke
      [Lambda] <-> [DynamoDB]:query
      [client] <-down-> [Cognito]:authenticate
      [Cognito] <-> [API Gateway]:verify authentication
      [Cognito] <-down-> [STS]:generate temp credentials
      [client] <-> [S3]:store/retrieve files based on permissions
      @enduml
      ```      

    High read throughput, static data
    - DAX (caching layer) before DynamoDB
    - API Gateway: caching of responses
    
    ```plantuml
    @startuml
    skinparam componentStyle rectangle
    [client] <-> [API Gateway]:HTTPS REST
    [API Gateway] <-> [API Gateway]:caching responses
    [API Gateway] <-down-> [Lambda]:invoke
    [Lambda] <-> [DAX (caching layer)]:query/read
    [client] <-down-> [Cognito]:authenticate
    [Cognito] <-> [API Gateway]:verify authentication
    [Cognito] <-down-> [STS]:generate temp credentials
    [client] <-> [S3]:store/retrieve files based on permissions
    [DAX (caching layer)] <-> [DynamoDB]
    @enduml
    ```      

    Summary
    - serverless rest api: https, API Gateway, Lambda, DynamoDB
    - use Cognito to generate temporary credentials with STS to access S3 bucket with restricted policy
      - app users can directly access AWS resources this way
      - pattern can be applied to DynamoDB, Lambda...
    - DAX: caching the reads on DynamoDB
    - API Gateway: caching responses
    - security for authentication and authorisation with Cognito and STS

 - [x] "Serverless Website: MyBlog.com"

    Requirements
    - website scale globally
    - blogs are rarely written, but often read
    - some of the website is purely static files, the rest is a dynamic REST API
    - implement caching where possible
    - newly subscribed users receive a welcome email
    - photos uploaded to the blog should have thumbnail generated automatically

    Serving static content globally and securely
    - user welcome email flow

      ```plantuml
      @startuml
      skinparam componentStyle rectangle
      [client] <-up-> [CloudFront]:interact with edge locations
      [CloudFront] <-> [S3]:bucket policy only \n authorise access from OAI
      [client] <-> [API Gateway]: HTTPS REST
      [API Gateway] <-> [Lambda 1]:invoke
      [Lambda 1] <-> [DAX (caching layer)]:query/read
      [DAX (caching layer)] <-> [DynamoDB (global tables)]
      [DynamoDB (global tables)] -down-> [DynamoDB Stream]:stream changes for new users
      [DynamoDB Stream] -left-> [Lambda 2]:invoke
      [Lambda 2] -left-> [SES]:SDK to send welcome email \n (Lambda 2 with correct \n IAM Role and Permissions)
      @enduml
      ```
      
    - thumbnail generation flow

      ```plantuml
      @startuml
      skinparam componentStyle rectangle
      [client] <-up-> [CloudFront 1]:interact with edge locations
      [CloudFront 1] <-> [S3 Bucket 1]:bucket policy only \n authorise access from OAI
      [client] <-> [API Gateway]: HTTPS REST
      [API Gateway] <-> [Lambda 1]:invoke
      [Lambda 1] <-> [DAX (caching layer)]:query/read
      [DAX (caching layer)] <-> [DynamoDB (global tables)]
      [client] <.down.> [S3 Bucket 2]:direct upload; or
      [client] <-down-> [CloudFront 2]:upload photos \n S3 transfer acceleration
      [CloudFront 2] <-> [S3 Bucket 2]:bucket policy only \n authorise access from OAI
      [S3 Bucket 2] -> [Lambda 2]:trigger
      [Lambda 2] -> [S3 Bucket 2/3...]:thumbnail
      [S3 Bucket 2/3...] .> [SQS/SNS/...]: optional
      @enduml
      ```

    Summary
    - static content distributed through CloudFront with S3
    - public serverless rest api without Cognito
    - DynamoDB global table
      - alternatively, Aurora global table
    - DynamoDB streams to trigger Lambda function
    - lambda function had an IAM role with SES permission
    - SES (Simple Email Service) sends emails in a serverless way
    - S3 can trigger SQS/SNS/Lambda to notify events

 - [x] MicroServices Architecture

    - services interact with each other directly using a REST API
    - each micro service may have its own design
    - leaner development lifecycle for each service

    Microservices Environment
    - pending UML

    Discussion
    - each micro service may have its own design
    - synchronous: API Gateway, Load Balancers
    - asynchronous: SQS, Kinesis, SNS, Lambda triggers (S3)
    - challenges with microservices
      - repeated overhead for creating each new microservice
      - issues with optimising server density/utilisation
      - complexity of running multiple versions of multiple microservices simultaneously
      - proliferation of client-side code (frontend) requirements to integrate with many separate services
    - some challenges are solved by serverless patterns
      - API Gateway, Lambda scale automatically and pay per usage
      - easily clone API, reproduce environments
      - generated client SDK through Swagger integration for the API Gateway

 - [x] Distributing Paid Content

    - users to buy online videos
    - each video can be bought by many customers
    - only distribute videos to premium/paid users
    - a DB of premium/paid users
    - short-lived video links for paid users
    - global application
    - fully serverless
 
    Architecture
    - pending UML

    Fully serverless solution
    - Cognito for authentication
    - DynamoDB for storing premium/paid users
    - 2 serverless applications
      - premium user registration
      - CloudFront signed URL generator
    - content is stored in S3 (serverless and scalable)
    - CloudFront with OAI for security (users cannot bypass)
    - CloudFront signed URL prevents unauthorised users
    - S3 signed URL are not efficient for global access

 - [x] Software updates distribution

    Requirements
    - application running on EC2 distributes software updates once in a while
    - costly to distribute new software update in mass over the network
    - without application change, how to optimise cost and CPU?

    Why CloudFront?
    - no change to application architecture
    - cache software update files at the edge
      - software update files are static (never changing)
    - EC2 is not serverless, but CloudFront is and can scale automatically
    - cost saving as ASG won't scale as much
    - cost saving in availability and network bandwidth etc.
    - easy way to make an existing application more scalable and cheaper

 - [x] Big Data Ingestion Pipeline

    Fully serverless solution requirements
    - serverless ingestiong pipeline
    - collect data in real time
    - transform data
    - query the transformed data using SQL
    - store query reports/results in S3
    - load data into a warehouse and create dashboards

    Big data ingestion pipeline
    - pending UML

    Summary
    - IoT Core harvests/collects data from IoT devices
    - Kinesis collects real-time data
    - Firehose deliver data to S3 in near real-time (every 1min at highest frequency)
    - Lambda transform data in Firehose
    - S3 triggers notification to SQS
    - Lambda can subscribe to SQS
      - alternatively connect S3 directly with Lambda
    - Athena is a serverless SQL service and results are stored in S3
    - reporting bucket contains analysed data and can be used by reporting tool such as AWS QuickSight, Redshift etc.

 - [x] Serverless Architectures Quiz

    1. API Gateway + AWS Lambda = fully serverless REST API
    2. Lambda does not have an out of the box caching feature (it's often paired with API gateway for that)
      API Gateway can cache responses
      DynamoDB can have DAX
    3. Cognito + STS federate mobile user login and generate temporary credentials for direct access to S3 bucket folders
    4. CloudFront can distribute static contentin S3 globally (multiple regions)
    5. DynamoDB Streams enable DynamoDB to get a changelog and use that changelog to replicate data across regions; required for DynamoDB global table
    6. Lambda can read DynamoDB stream but cannot store messags in SQS -> Lambda IAM execution role missing permissions
    7. SQS allows you to retain messages for days and process them later, while we take down our EC2 instances
    8. CloudFront signed URL has security including IP restriction
    9. CloudFront can be used in front of an ELB to cache static content, optimise network costs and reduce server load
    10. Kinesis Data Streams delivers big data streams in real time to multiple consuming applications with replay features

## 17. (***DONE***) Databases in AWS

 - [x] Choosing the right database

    Questions to ask for the right DB choice:
    - Read-heavy, write-heavy or balanced workload? Throughput needs? Will it change over time, or does it scale or fluctuate during the day?
    - How much data to store and for how long? Will it grow? Average object size? How are they accessed?
    - Data durability? Source of truth for the data?
    - Latency requirements? Concurrent users?
    - Data model? How will you query the data? Joins? Structured? Semi-Structured?
    - Strong schema? More flexibility? eporting? Search? RBDMS / NoSQL?
    - License costs? Switch to Cloud Native DB such as Auronra?

    DB types:
    - RDBMS (= SQL / OLTP); RDS, Aurora - gresat for joins
    - NoSQL DB: DynamoDB (~JSON), ElastiCache (key value pairs), Neptune (graphs) - no joins, no SQL
    - Object Store: S3 (for big objects) / Glacier (for backups / archives)
    - Data Warehouse (= SQL Analytics / BI): Redshift (OLAP), Athena (query data in S3)
    - Search: ElasticSearch (JSON) -free text, unstructured searches
    - Graphs: Neptune - displays relationships between data

 - [x] RDS

    - Managed PostgreSQL / MySQL / Oracle / SQL Server
    - Must provision an EC2 instance & EBS Volume type and size
    - Support for Read Replicas and Multi AZ (disaster recovery)
    - Security through IAM, Security Grouops, KMS, SSL in transit
    - Backup / Snapshot / Point in time restore feature
    - Managed and Schedule maintenance
    - Monitoring through CloudWatch

    **Use case**: Store relational datasets (RDBMS / OLTP), perform SQL queries, transactional inserts/update/delete is available

    RDS for Solutions Architect (5 pillars of architecture)
    - **Operations**: small downtime when failover happens, when maintenance happens, scalingi n read replicas / EC2 instance / restore EBS implies manual intervention, application changes
    - **Security**: AWS responsible for OS security, we are responsible for setting up KMS, security groups, IAM policies, authorising users in DB, using SSL
    - **Reliability**: Multi AZ feature, failover in case of failures
    - **Performance**: depends on EC2 instance type, EBS volume type, ability to add Read Replicase, Doesn't auto-scale
    - **Cost**: Pay per hour based on provisioned EC2 and EBS

 - [x] Aurora (Enterprise-grade RDS)

    - Compatible API for PostgreSQL / MySQL
    - Data is held in 6 replicas, across 3 AZ
    - Auto healing capability
    - Multi AZ, Auto Scaling Read Replicas
    - Read Replicas can be Global
    - Aurora DB can be Global for DR or latency purposes
    - Auto scaling of storage from 10GB to 64TB
    - Define EC2 instance type for aurora instances
    - Same security / monitoring / maintenance features  as RDS
    - "Aurora Serverless" option

    **Use case**: same as RDS, but with less maintenance / more flexibility / more performance

    Aurora for Solutions Architect
    - **Operations**: less operations, auto scaling storage
    - **Security**: AWS responsible for OS security, we are responsible for setting up KMS security groups, IAM policies, authorising users in DB, using SSl
    - **Reliability**: Multi AZ, highly available, possibly more than RDS, Aurora Serverless option
    - **Performance**: 5x performance (according to AWS) due to architectural optimisations, Up to 15 Read Replicas (only 5 for RDS)
    - **Cost**: Pay per hour based on EC2 and storage usage. Possibly lower costs compared to Enterprise grade databases such as Oracle

 - [x] ElastiCache

    - Managed Redis / Memcached (similar offering as RDS, but for caches)
    - In-memory data store, sub-millisecond latency
    - Must provision and EC2 instance type
    - Support for Clustering (Redis) and Multi AZ, Read Replicas (sharding)
    - Security through IAM, Security Groups, KMS, Redis Auth
    - Backup / Snapshot / Point in time restore feature
    - Managed and Scheduled maintenance
    - Monitroing through CloudWatch

    **Use case**: Key/Value store, frequent reads, less writes, cache results for DB queries, store session data for websites, cannot use SQL

    - **Operations**: same as RDS
    - **Security**: AWS responsible for OS security, we are responsible for setting KMS, security groups, IAM policies, users (Redis Auth), using SSL
    - **Reliability**: Clustering, Multi AZ
    - **Performance**: Sub-millisecond performance, in memory, read replicas for sharding, very popular cache option
    - **Cost**: Pay per hour based on EC2 and storage usage

 - [x] DynamoDB

    - AWS proprietary technology, managed NoSQL database
    - Serverless, provisioned capacity, auto scaling, on demand capacity (Nov 2018)
    - Can replace ElastiCache as a key/value store (storing session data for example)
    - Highly Available, Multi AZ by default, Read and Writes are decoupled, DAX (Amazon DynamoDB Accelerator) for read cache
    - Reads can be eventually consistent or strongly consistent
    - Security, authentication and authorisation is done through IAM
    - DynamoDB Streams to integrate with AWS Lambda
    - Backup/restore feautre, Global Table feature
    - Monitoring through CloudWatch
    - Can only query on primary key, sort key or indexes (downside)

    **Use case**: Serverless applications development (small documents 100s KB), distributed serverless cache, doesn't have SQL query language available, has transactions capability from Nov 2018

    - **Operations**: no perations needed, auto scaling capability, serverless
    - **Security**: full security through IAM policies, KMS encryption, SSL in flight
    - **Reliability**: Multi AZ, Backups
    - **Performance**: single digit millisecond performance, DAX for caching reads, performance doesn't degrade if your application scales
    - **Cost**: pay per provisioned capacity and storage usage (no need to guess in advance any capacity - can use auto scaling)

 - [x] S3

    - S3 is a key/value store for objects
    - Great for big objects, not so great for small objects
    - Serverless, scales infinitely, max object size is 5TB
    - Eventual consistency for overwrites and deletes
    - Tiers: S3 Standard, S3 IA, S3 One Zone IA, Glacier for backups
    - Features: Versioning, Encryption, Cross Region Replication, etc...
    - Security: IAM, Bucket Policies, ACL
    - Encryption: SSE-S3, SSE-KMS, SSE-C, client side encryption, SSL in transit

    **Use case**: static files, key value store for big files, webiste hosting

    - **Operations**: no perations needed
    - **Security**: IAM, Bucket Policcies, ACL, Encryption (Server/Client), SSL
    - **Reliability**: 99.999999999% durability / 99.99% availability, Multi AZ, CRR (Cross-Region Replication)
    - **Performance**: scales to thousands of read/write per second, transfer acceleration / multi-part for big files
    - **Cost**: pay per storage usage, network cost, requests number

 - [x] Athena

    - Fully Serverless database with SQL capabilities
    - Used to query data in S3
    - Pay per query
    - output results back to S3
    - Secured through IAM

    **Use case**: one time SQL queries, serverless queries on S3, log analytics

    - **Operations**: no operations needed, serverless
    - **Security**: IAM + S3 security
    - **Reliability**: managed service, uses Presto engine, highly available
    - **Performance**: queries scale based on data size
    - **Cost**: pay per query / per TB of data scanned, serverless

 - [x] Redshift

    - Redshift is based on PostgreSQL, but it's not used for OLTP
    - It's OLAP - online analytical processing (analytics and data warehousing)
    - 10x better performance than other data warehouses, scale to PBs of data
    - Columnar storage of data (instead of row based)
    - Massively Parallel Query Execution (MPP), highly available
    - Pay as you go based on the instances provisioned
    - Has a SQL interface for performing the queries
    - BI tools such as AWS Quicksight or Tableau integrate with it
    - Data is loaded from S3, DynamoDB, DMS and other DBs
    - From 1 node to 128 nodes, up to 160GB per node
    - Leader node: for query planning, results aggregation
    - Compute node: for performing the queries, send results to leader
    - Redshift Spectrum: perform queries directly against S3 (no need to load)
    - Backup & Resotre, Security VPC / IAM / KMS, Monitoring
    - Redshift Enhanced VPC Routing: COPY / UNLOAD goes through VPC
    - Redshift - Snapshots & DR
      - Snapshots are point-in-time backups of a cluster, stored internally in S3
      - Snapshots are incremental (only what has changed is saved)
      - You can restore a snapshot into a **new cluster**
      - Automated: every 8 hours every 5GB, or on a schedule. Set retention
      - Manual: snapshot is retained until you delete it
    - Redshift Spectrum
      - Query data that is already in S3 without loading it
      - **Must have Redshift cluster available to start the query**
      - The query is then submitted to thousands of Redshift Spectrum nodes


    **Use case**: 
    
    - **Operations**: similar to RDS
    - **Security**: IAM, VPC, KMS, SSL (similar to RDS)
    - **Reliability**: highly available, auto healing features
    - **Performance**: 10x performance vs other data warehousing, compression
    - **Cost**: pay per node provisioned, 1/10th of the cost vs other warehouses

    **Remember: Redshift = Analytics / BI / Data Warehouse**

 - [x] Neptune

    - Fully managed **graph** database
    - When do we use Graphs?
      - High relationship data
      - Social Networking: User fiends with Users, replied to comment on post of user and likes other comments
      - Knowledge graphs (Wikipedia)
      - Highly available across 3 AZ, with up to 15 read replicas
      - Point-in-time recovery, continuous backup to Amazon S3
      - Support for KMS encryption at rest + HTTPS

    **Use case**: Graph DB
    
    - **Operations**: similar to RDS
    - **Security**: IAM, VPC, KMS, SSL (similar to RDS) + IAM Authentication
    - **Reliability**: Multi-AZ, clustering
    - **Performance**: best suited for graphs clustering to improve performance
    - **Cost**: pay per node provisioned (similar to RDS)

    **Remember: Neptune = Graphs**

 - [x] ElasticSearch

    - Example: In DynomoDB, you can only find by primary key or indexes
    - With ElasticSearch, you can **search any field**, even partially matches
    - It's common to use ElasticSearch as complement to another database
    - ElasticSearch also has some usage for Big Data applications
    - You can provision a cluster of instances
    - Built-in integrations: Amazon Kinesis Data Firehose, AWS IoT, and Amazon CloudWatch Logs for data ingestion
    - Security through Cognito & IAM, KMS encryption, SSL & VPC
    - Comes iwth Kibana (visualisatio) & Logstash (log ingestion) - ELK stack

    **Use case**: search any field
    
    - **Operations**: similar to RDS
    - **Security**: Cognito, IAM, VPC, KMS, SSL
    - **Reliability**: Mult-AZ, clustering
    - **Performance**: based on ElasticSearch project (open source), PB scale
    - **Cost**: pay per node provisioned (similar to RDS)

    **Remember: ElasticSearch = Search / Indexing**

 - [x] Databases Quiz

## 18. "AWS Monitoring & Audit: CloudWatch, CloudTrail & Config"

 - [ ] AWS Monitoring - Section Introduction
 - [ ] AWS CloudWatch Metrics
 - [ ] AWS CloudWatch Dashboards
 - [ ] AWS CloudWatch Logs
 - [ ] CloudWatch Agent & CloudWatch Logs Agent
 - [ ] AWS CloudWatch Alarms
 - [ ] EC2 Instance Recovery with CloudWatch Alarms
 - [ ] AWS CloudWatch Events
 - [ ] AWS CloudTrail
 - [ ] AWS Config - Overview
 - [ ] AWS Config - Hands On
 - [ ] CloudTrail vs CloudWatch vs Config
 - [ ] Monitoring Quiz

## 19. Identity and Access Management (IAM) - Advanced

 - [ ] Security Token Service (STS) Overview
 - [ ] Identity Federation & Cognito
 - [ ] Directory Services - Overview
 - [ ] Organizations - Overview
 - [ ] Organizations - Hands On
 - [ ] IAM - Advanced
 - [ ] IAM - Policy Evaluation Logic
 - [ ] Resource Access Manager (RAM)
 - [ ] AWS Single Sign On (SSO) - Overview
 - [ ] AWS Single Sign On (SSO) - Hands On
 - [ ] Identity and Access Management (IAM) - Advanced - Quiz

## 20. "AWS Security & Encryption: KMS, SSM Parameter Store, CloudHSM, Shield,

 - [ ] AWS Security - Section Introduction
 - [ ] Encryption 101
 - [ ] KMS Overview
 - [ ] KMS Hands On w/ CLI
 - [ ] SSM Parameter Store Overview
 - [ ] SSM Parameter Store Hands On (CLI)
 - [ ] SSM Parameter Store Hands On (AWS Lambda)
 - [ ] AWS Secrets Manager - Overview
 - [ ] AWS Secrets Manager - Hands On
 - [ ] CloudHSM
 - [ ] Shield - DDoS Protection
 - [ ] Web Application Firewall (WAF)
 - [ ] WAF & Shield - Hands On
 - [ ] Shared Responsibility Model
 - [ ] Security & Encryption Quiz

## 21. Networking - VPC

 - [ ] Section Introduction
 - [ ] CIDR, Private vs Public IP
 - [ ] Default VPC Overview
 - [ ] VPC Overview and Hands On
 - [ ] Subnet Overview and Hands On
 - [ ] Internet Gateways & Route Tables
 - [ ] NAT Instances
 - [ ] NAT Gateways
 - [ ] DNS Resolution Options & Route 53 Private Zones
 - [ ] NACL & Security Groups
 - [ ] VPC Peering
 - [ ] VPC Endpoints
 - [ ] VPC Flow Logs + Athena
 - [ ] Bastion Hosts
 - [ ] Site to Site VPN, Virtual Private Gateway & Customer Gateway
 - [ ] Direct Connect & Direct Connect Gateway
 - [ ] Egress Only Internet Gateway
 - [ ] AWS PrivateLink - VPC Endpoint Services
 - [ ] AWS ClassicLink
 - [ ] VPN CloudHub
 - [ ] Transit Gateway
 - [ ] VPC Section Summary
 - [ ] Section Cleanup
 - [ ] VPC Quiz
 - [ ] Networking Costs in AWS

## 22. Disaster Recovery & Migrations

 - [ ] Disaster Recovery in AWS
 - [ ] Database Migration Service (DMS)
 - [ ] Database Migration Service (DMS) - Hands On
 - [ ] On-Premises Strategies with AWS
 - [ ] DataSync - Overview
 - [ ] Transferring Large Datasets into AWS
 - [ ] Disaster Recovery Quiz

## 23. More Solution Architectures

 - [ ] Event Processing in AWS
 - [ ] Caching Strategies in AWS
 - [ ] Blocking an IP Address in AWS
 - [ ] High Performance Computing (HPC) on AWS
 - [ ] EC2 Instance High Availability
 - [ ] Bastion Host High Availability
 - [ ] More Solution Architectures - Quiz

## 24. Other Services

 - [ ] Other Services Section Introduction
 - [ ] CICD Introduction
 - [ ] CloudFormation Intro
 - [ ] CloudFormation Hands-On
 - [ ] CloudFormation - Extras
 - [ ] ECS Introduction
 - [ ] ECS - Extras
 - [ ] EKS - Overview
 - [ ] Step Functions & SWF
 - [ ] EMR
 - [ ] AWS Glue
 - [ ] OpsWorks
 - [ ] ElasticTranscoder
 - [ ] AWS Workspaces
 - [ ] AppSync
 - [ ] "Other Services: Cheat Sheet"
 - [ ] "Other Services: Quiz"

## 25. WhitePapers and Architectures - AWS Certified Solutions Architect Associate

 - [ ] WhitePaper Section Introduction
 - [ ] Well Architected Framework Overview + Well Architected Tool
 - [ ] "1st pillar: Operational Excellence"
 - [ ] "2nd pillar: Security"
 - [ ] "3rd pillar: Reliability"
 - [ ] "4th pillar: Performance Efficiency"
 - [ ] "5th pillar: Cost Optimization"
 - [ ] AWS Trusted Advisor Overview + Hands-On
 - [ ] Examples of Architecture - AWS Certified Solutions Architect Associate
 - [ ] WhitePaper Quiz

## 26. Preparing for the Exam + Practice Exam - AWS Certified Solutions

 - [ ] Exam Preparation - Section Introduction
 - [ ] State of Learning Checkpoint - AWS Certified Solutions Architect Associate
 - [ ] Exam Tips - AWS Certified Solutions Architect Associate
 - [ ] Exam Walkthrough and Signup
 - [ ] Save 50% on your AWS Exam Cost!
 - [ ] Get an Extra 30 Minutes on your AWS Exam - Non Native English Speakers only
 - [ ] Practice Exam - AWS Certified Solutions Architect Associate

## 27. Congratulations - AWS Certified Solutions Architect Associate

 - [ ] Congratulations - AWS Certified Solutions Architect Associate
 - [ ] THANK YOU!
 - [ ] "Bonus Lecture: Special discounts for my other courses"
