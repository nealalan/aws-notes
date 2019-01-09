# [nealalan.github.io](https://nealalan.github.io)/[aws-notes](https://nealalan.github.io/aws-notes)

## TOC
  - [AWS Well-Architected Framework](https://nealalan.github.io/aws-notes/#aws-well-architected-framework-june-2018-version)
  - [AWS Disaster Recovery Whitepaper](https://nealalan.github.io/aws-notes/#disaster-recovery-whitepaper-2014)
  - [AWS Services Summary Cheat Sheet](https://nealalan.github.io/aws-notes/#aws-services-summary-cheat-sheet)


# [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/) (June 2018 version)

## Good Design Principles
- Stop guessing your capacity needs
- Test systems at production scale
- Automate to make architectural experimentation easier
- Allow for evolutionary architectures
- Drive architectures using data
- Improve through game days

## The Five Pillars of the Well-Architected Framework
1. OPS: Operational Excellence
2. SEC: Security
3. REL: Reliability
4. PERF: Performance Efficiency
5. COST: Cost Optimization

## 1) OPS: Operational Excellence ([Whitepaper](https://d1.awsstatic.com/whitepapers/architecture/AWS-Operational-Excellence-Pillar.pdf))

### Design Principles for Operational Excellence
- Perform operations as code 
  - limit human error and enable consistent responses to events
  - define your entire workload (applications, infrastructure, etc.) as code and update it with code
- Annotate documentation
  - Annotated documentation can be used by humans and systems
  - Use annotations as an input to your operations code.
- Make frequent, small, reversible changes
  - Design workloads to allow components to be updated regularly to increase the flow of beneficial changes into your workload
  - Make changes in small increments that can be reversed if they fail to aid in the identification and resolution of issues 
- Refine operations procedures frequently
  - As you evolve your workload, evolve your procedures appropriately
- Anticipate failure
- Learn from all operational failures (lessons learned)

### 3 Areas: 1) PREPARE
- Operational Priorities
  - teams need to have a shared understanding of your entire workload, their role in it, and shared business goals 
  - use the resources provided by AWS Support 
  - [AWS Knowledge Center](https://aws.amazon.com/premiumsupport/knowledge-center/)
  - [AWS Discussion Forms](https://forums.aws.amazon.com/)
  - [AWS Support Center](https://console.aws.amazon.com/support/home)
  - [AWS Cloud Compliance](https://aws.amazon.com/compliance/) - regulatory or compliance requirements 
  - [AWS Trusted Advisor]() - core set of checks that recommend optimizations for your environment
- Design for Operations
  - [AWS CloudFormation](https://aws.amazon.com/cloudformation/) - create version-controlled templates
  ![](https://d1.awsstatic.com/CloudFormation%20Assets/howitworks.c316d3856638c6c9786e49011bad660d57687259.png?raw=true)
  - [AWS Developer Tools]() - Set up CI/CD pipelines using: 
    - AWS CodeCommit, AWS CodeBuild, AWS CodePipeline, AWS CodeDeploy, AWS CodeStar
  ![](https://github.com/nealalan/aws-notes/blob/master/images/d4e2416aad5d988fc47322190319a1d3780478ef.png?raw=true)
  - apply metadata using tags
  - capture logs in Amazon CloudWatch from:
    - AWS CloudTrail, AWS Lambda, VPC Flow Logs, CloudWatch Events, Amazon CloudWatch Logs API
  - use this log information to create a system-wide view of your operational status
    - CloudWatch Dashboards or third-party tools
  - [AWS X-Ray](https://aws.amazon.com/xray/) traces user requests as they travel through your entire application
  ![](https://github.com/nealalan/aws-notes/blob/master/images/product-page-diagram_AWS-X-Ray_how-it-works.2922edd4bfe011e997dbf32fdf8bd520bcbc85fb.png?raw=true)
- Operational Readiness
  - use a consistent process (including checklists) to know when you are ready to go live
  - test your procedures, failure scenarios, and the success of your responses (Game Days)
  - create temporary parallel environments, which lowers the risk, effort, and cost of experimentation and testing
  - script procedures on your instances using [AWS Systems Manager](https://aws.amazon.com/systems-manager/) Run Command, Systems Manager Automation, and use AWS Lambda to script responses to events across AWS service 
  ![](https://github.com/nealalan/aws-notes/blob/master/images/product-page-diagram-AWS-Systems-Manager_how-it-works.2e7c5d550e833eed0f49fb8dc1872de23b09d183.png?raw=true)
  - Automate your responses by triggering these scripts using CloudWatch Events
  - making baselines using [AWS Config](https://aws.amazon.com/config/)
  ![](https://github.com/nealalan/aws-notes/blob/master/images/product-page-diagram-Config_how-it-works.bd28728a9066c55d7ee69c0a655109001462e25b.png?raw=true)

### 3 Areas: 2) OPERATE
- Understanding Operational Health
  - implement CloudWatch Dashboards with business and technical viewpoints to make informed decisions
  - CloudWatch Logs 
    - define baseline metrics to establish normal operating patterns
    - ingest into Amazon ES (Elasticsearch Service)
    - use the built-in support for Kibana to create dashboards and visualizations of your operational health
  - [Amazon Elastisearch Service](https://aws.amazon.com/elasticsearch-service/) makes it easy to deploy, secure, operate, and scale Elasticsearch for log analytics, and application monitoring.
  ![](https://github.com/nealalan/aws-notes/blob/master/images/How%20AES%20works_final.2e3ac88fbb9910d7c401d0748556db0c91c97b33.png?raw=true)
  - [AWS Personal Health Dashboard](https://aws.amazon.com/premiumsupport/technology/personal-health-dashboard/) provides alerts and remediation guidance **when AWS is experiencing events that may impact you**
  - [AWS Service Health Dashboard](https://status.aws.amazon.com/) provides up-to-the-minute information **on AWS service availability**
- Responding to Events
  - anticipate operational events, both planned (for example, sales promotions, deployments, and failure tests) and unplanned (for example, surges in utilization and component failures)
  - automate the execution of runbook and playbook actions on AWS.
  - create CloudWatch rules to trigger responses through CloudWatch targets:
    - Lambda functions, Amazon SNS topics, Amazon EC2 ECS tasks, AWS Systems Manager Automation
  - create CloudWatch alarms to perform one or more actions:
    - Amazon EC2 actions, Auto Scaling actions, send a notification to an Amazon SNS topic. 
    - custom actions in response to an alarm, invoke Lambda through Amazon SNS notification. 
    - Use Amazon SNS to publish event notifications and escalation messages to keep people informed
  - third-party systems through the AWS service APIs and SDKs
    - New Relic, Splunk, Loggly, SumoLogic, and Datadog.
  - Amazon Elastisearch Service
  - [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) / [Amazon CloudWatch Events](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/CWE_GettingStarted.html)
  ![](https://github.com/nealalan/aws-notes/blob/master/images/product-page-diagram_Cloudwatch_v4.55c15d1cc086395cbd5ad279a2f1fc37e8452e77.png?raw=true)
  - [Amazon SNS](https://aws.amazon.com/sns/)
  ![](https://github.com/nealalan/aws-notes/blob/master/images/product-page-diagram_SNS_how-it-works_1.53a464980bf0d5a868b141e9a8b2acf12abc503f.png?raw=true)
  - Auto Scaling for elasticity

### 3 Areas: 3) EVOLVE
- Learning from Experience
  - Amazon QuickSight is a business analytics service that makes it easy to build visualizations, perform ad-hoc analysis, and quickly get insights from your data
  - Amazon Athena is a serverless interactive query service that makes it easy to analyze data in Amazon S3
  - Amazon CloudWatch is used for the collection of logs and metrics and the creation of dashboards
- Share Learnings
  - AWS IAM - enables you to manage the sharing of resources within and across accounts
  - AWS CodeCommit provides a version-controlled repository for your operations as code
  - AWS Lambda enables the definition of operational procedures as code that can be shared across accounts
  - Amazon Machine Images (AMIs) are predefined operating system templates
  
### Best Practices 
- OPS 1: What factors drive your operational priorities?
  - Evaluate Business needs
  - Evaluate compliance requirements
  - Evaluate risk
- OPS 2: How do you design your workload to enable operability?
  - Share design standards
  - Design for cloud operations
  - Provide insights into workload behavior
  - Provide insights into customer behavior
  - Implement practices that reduce defects, ease remediation and improve flow
  - Mitigate deployment risks
- OPS 3: How do you know that you are ready to support a workload?
  - Continuous improvement culture
  - Share understanding of the value to the business
  - Ensure personnel capability
  - Documented accessible governance and guidance
  - Use checklists
  - Use playbooks
  - Practice recovery
- OPS 4: What factors drive your understanding of operational health?
  - Define expected business and customer outcomes
  - Identify success metrics
  - Identify workload metrics
  - Identify ops metrics
  - Established baselines
  - Collect and analyze metrics
  - Validate indights
  - Business-level view of ops
- OPS 5: How do you manage operational events?
  - Determine priority of operational events based on business impact
  - Processes for event, incident, and problem management
  - Process per alert
  - ID decision makers
  - Define escalation paths
  - Push notifications
  - Communicate status through dashboards
  - Process for root cause analysis
- OPS 6: How do you evolve operations?
  - frequent small improvements; providing safe environments and time to experiment, develop, and test improvements; and environments in which learning from failures is encouraged
  - Process for Continuous Improvement
  - Define drivers for improvement
  - Implement feedback loops
  - Document and share lessons learned
  - Perform ops metrics reviews

### Key Services
- [AWS CloudFormation](https://aws.amazon.com/cloudformation/) = essential to Ops Excellence
- Amazon QuickSight is a business analytics service that makes it easy to build visualizations, perform ad-hoc analysis, and quickly get insights from your data.
- Amazon Athena is a serverless interactive query service that makes it easy to analyze data in Amazon S3
- Amazon S3 can be used for collection and archival retention of logs
- Amazon CloudWatch is used for the collection of logs and metrics and the creation of dashboards.

## 2) SEC: Security

### Design principles for Security

- Implement a strong identity foundation
  - principle of least privilege
  - enforce separation of duties
  - centralize privilege mgmt
  - eliminate reliance on long-term credentials
- Enable traceability
  - monitor, alert and audit actions and changes in real time
  - integrate logs and metrics with systems to auto respond
- Apply security at all layers
  - defense-in-depth
  - apply to all layers (edge, VPC, subnet, load balancer, every instance, OS, apps)
- **Automate** security best practices
- **Protect** data in transit 
- **Protect** data at rest
- Keep people away from data
- **Prepare** for security events

### Best Practices
- SEC 1: How do you manage credentials for your workload?
  - Enforce use of MFA, PW reqs
  - Rotate creds regularly
  - Audit creds periodically
  - Use centralized identity provider
- SEC 2: How do you control human access to services?
  - Creds are not shared
  - User life-cycle managed
  - Min privileges
  - Clearly defined access req
  - Grant access via roles or federation
- SEC 3: How do you control programmatic access to services?
  - Creds are not shared
  - Dynamic auth
  - Min privileges
  - Clearly defined access req
- SEC 4: How are you aware of security events in your workload?
  - Logging enables where avail
  - Analyze AWS CloudTrail
  - Analyze logs centrally
  - Monitoring and alerting for key metrics and events
  - AWS marketplace or APN partner solution enabled
- SEC 5: How do you protect your networks?
  - Controlling traffic in VPC
  - Controlling traffic at the boundary or edge
  - Control traffic using SGs, ACLs, subnets
  - AWS marketplace or APN partner solution enabled
- SEC 6: How do you stay up to date with AWS security features and industry security threats?
  - Evaluate new sec services and features
  - Using sec services and features
- SEC 7: How do you protect your compute resources?
  - Hardening default config
  - Check file integrity
  - Intrusion detection enables
  - AWS marketplace or APN partner solution enabled
  - Config mgmt tool
  - Patch and scan for vulnerabilities
- SEC 8: How do you classify your data?
  - Use a data classification schema
  - Apply the classification
- SEC 9: How do you manage data protection mechanisms?
  - Use a secure key mgmt service
  - Use service level controls
  - Use client side key mgmt
  - AWS marketplace or APN partner solution
- SEC 10: How do you protect your data at rest?
  - Encrypting
- SEC 11: How do you protect your data in transit?
  - Encrypting (TLS communications)
- SEC 12: How do you prepare to respond to an incident?
  - Pre-provisioned access
  - Pre-deployed tools
  - Run game days

### Key AWS Services
1. Identity and Access Management 
  - AWS IAM
2. Detective Control
  - AWS CloudTrail - records AWS API calls
  - AWS Config - inventory of AWS resources and config
  - AWS CloudWatch - monitoring and can trigger AWS CloudWatch Events
3. Infrastructure Protection
  - Amazon VPC enables launching into virtual network
  - AWS Cloudfront  is a global CDN
  - securely delivers data, videos, applications, and APIs
  - integrates with AWS Shield for DDos
  - AWS WAF deploys onto CloudFront or App Load Balancer
4. Data Protection
  - As an AWS customer you maintain full control over your data.
  - Encrypt your data and manage keys, including regular key rotation.
  - AWS ELB (Elastic Load Balancer)
  - AWS EBS (Elastic Block Store)
  - AWS S3 (Simple Storage Service)
  - AWS RDS (Relational Database Service)
  - Amazon Macie - automatically discovers, classifies and protects sensitive data,
  - AWS KMS (Key Management Service) - makes it easy for you to create and control keys
5. Incident Response
  - AWS CloudFormation - create a trusted env or clean room for investigations
  - AWS CloudWatch - can trigger responses (including AWS Lambda)

## 3) REL: Reliability

### Best Practices - Foundations, Change management, Failure management
- REL 1: How are you managing AWS service limits for your accounts?
  - Active monitoring and managing limits
  - Implemen automated monitoring and mgmt or limits
  - Be aware of fixed service limits
  - Ensure sufficient gap between limit and max use to accommodate for failover
  - Services limits managed across all relevant accts and regions
- REL 2: How do you plan your network topology on AWS?
  - Connectivity back to data center is not needed?
  - Highly avail connectivity between AWS and on-prem env implemented?
  - Highly avail network connectivity for users of workload implemented?
  - Non-overlapping private IP address ranges in VPCs?
  - IP subnet alloc accounts for expansion and avail?
- REL 3: How does your system adapt to changes in demand?
  - Workload scales automatically
  - Workload is load tested
- REL 4: How do you monitor AWS resources?
  - Monitor the workload in all tiers
  - Notifications are sent based on the monitoring
  - Automated responses are performed for events
  - Reviews are conducted regularly
- REL 5: How do you implement change?
  - Changes are deployed with automation
- REL 6: How do you back up data?
  - Data is backed up manually
  - Data is backed up using automated processes
  - Periodic recovery of the data is done to verify backup integrity and proc
  - Backups are secured and encrypted
- REL 7: How does your system withstand component failures?
  - Monitoring is done at all layers of the workload to detect failures
  - Deployed to multiple AZs and Regions if required
  - Loosely coupled dependencies
  - Implement graceful degradation
  - Auto healing implemented on all layers
  - Notifications sent upon events impacting availability
- REL 8: How do you test resilience?
  - Use a playbook
  - Inject failures to test
  - Schedule game days
  - Conduct RCAs
- REL 9: How do you plan for disaster recovery?

## 4) PERF: Performance Efficiency

### Design Principles for Performance Efficiency
- Democratize advanced technologies
- Go global in minutes
- Use serverless architectures
- Experiment more often
- Mechanical sympathy

### Best Practices & Key AWS Services for Performance Efficiency
- PERF 1: How do you select the best performing architecture?
  - Benchmarking
  - Load test
- PERF 2: How do you select your compute solution?
  - Consider options
  - Consider instance config options (family, instance size and feature)
  - Consider container config options (memory, CPU, tenancy config)
  - Consider function config options (memory, runtime, state)
  - Use elasticity to meet demand changes:
    - [AWS Auto Scaling](https://aws.amazon.com/autoscaling/) 
    - AWS ECS
    - AWS Lambda 
- PERF 3: How do you select your storage solution?
  - Consider characteristics: share, size, cache, access, latency, throughput, persistence
  - Consider config options (PIOPS, SSD, S3 Transfer Accel)
  - Consider access patterns (striping, key distro, partitioning)
  - AWS storage options: 
    - AWS EBS, 
    - AWS S3
- PERF 4: How do you select your database solution?
  - Consider characteristics: avail, consistency, tolerance, latency, durability, scalability, query capacility
  rational, NoSQL, warehouse, in-memory
  - Consider config options (memory, cache)
  - Consider access patterns (index, key distro, partition, scaling)
  - Consider other approaches (queryable data, search indexes, data warehouses, Big Data)
  - AWS Database solutions:
    - AWS RDS
    - AWS DynamoDB
- PERF 5: How do you configure your networking solution?
  - Consider location (Region, AZ, placement group, edge loc) = REDUCE LATENCY
  - Consider service features:
    - AWS EC2 instance network capability, 
    - Amazon EBS-optimized, 
    - AWS CloudFront
  - Consider networking features:
    - AWS Route53 latency-based routing 
    - AWS VPC endpoints 
    - AWS Direct Connect
- PERF 6: How do you evolve your workload to take advantage of new releases?
  - Use process for evaluation
  - AWS news and updated:
    - [AWS Blog](https://aws.amazon.com/blogs/aws/)
- PERF 7: How do you monitor your resources to ensure they are performing as expected?
  - Monitor, Alarm-based notifications, Trigger based actions
  - AWS monitoring solutions
    - AWS CloudWatch
- PERF 8: How do you use tradeoffs to improve performance?
  - Use services
    - ElastiCache 
    - CloudFront 
    - Snowball
  - Use patterns - caching, read replicas, sharding, compression, buffering
  - Recovery objectives are defined (RTO and RPO)
  - Recovery strategy is defined
  - Configuration drift is managed (AMIs and the system config up-to-date)
  - Test and validate DR implementation
  - Recovery is automated

## 5) Cost Optimization

### Pillars for cost optimization & Key Services
1. Cost-Effective Resources
2. Matching supply and demand
3. Expenditure Awareness
4. Optimizing Over Time

### Best Practices for Cost Optimization
- COST 1: How do you evaluate cost when you select AWS services?
  - Select service for cost reduction
  - Optimize for license costs
  - Optimize using serverless and container-base approach
  - Optimize using appropriate storage solutions
  - EBS cold storage, S3 Std-Infrequent, Glacier
  - Optimize using appropriate databases
  - Amazon RDS (Aurora, PostgreSQL, MySQL, SQL Server, Oracle Database) 
  - Amazon DynamoDB (or other key-value stores, NoSQL alternatives)
  - Optimize using other app-level services
    - AWS SQS - (Simple Queue Service) 
    - AWS SNS - (Simple Notification Service)
    - AWS SES - (Simple Email Service)
- COST 2: How do you meet cost targets with resource type and size choices?
  - Metrics-driven resource sizing
- COST 3: How do you use pricing models to reduce cost?
  - Reserved capacity and commit deals
  - Spot instances
  - Region cost
- COST 4: How do you plan for data transfer charges?
  - Optimize, WAN acceleration, Multi-AW, Regions selection
  - Use a Content Delivery Network (CDN) 
    - AWS Cloudfront
  - AWS Direct Connect
- COST 5: How do you match supply of resources with customer demand?
  - Demand-based approach
  - Buffer-based approach
  - Time-base approach
- COST 6: How do you monitor usage and cost?
  - Tag all resources!
  - Use billing and cost management tools
  - Notifications
  - Business outcome alloc
- COST 7: How do you govern AWS usage?
  - Establish groups and roles (who can spin up instances)
  - Track project lifecycle
- COST 8: How do you decommission resources?
  - Automate decommission
  - Defined process
- COST 9: How do you evaluate new services?
  - Schedule review (Sol Arch, acct team, cost benefit)
  - Establish a cost optimization function / team
  - Review and analyze workload

# [Disaster Recovery Whitepaper](https://aws.amazon.com/whitepapers/using-aws-for-disaster-recovery/) (2014)
- Recovery Time Objective (RTO) - the time it takes after a disruption to restore a business process to its service level and 
- Recovery Point Objective (RPO) - acceptable amount of data loss measured in time before the disaster occurs

## Techniques
- Backup & Restore – Data is backed up and restored, within nothing running
- Pilot light – Only minimal critical service like RDS is running and rest of the services can be recreated and scaled during recovery
- Warm Standby – Fully functional site with minimal configuration is available and can be scaled during recovery
- Multi-Site – Fully functional site with identical configuration is available and processes the load

## AWS Services for recovery
- Region and AZ to launch services across multiple facilities
- EC2 instances with the ability to scale and launch across AZs
- EBS with Snapshot to recreate volumes in different AZ or region
- AMI to quickly launch preconfigured EC2 instances
- ELB and Auto Scaling to scale and launch instances across AZs
- VPC to create private, isolated section
- Elastic IP address as static IP address
- ENI with pre allocated Mac Address
- Route 53 is highly available and scalable DNS service to distribute traffic across EC2 instances and ELB in different AZs and regions
- Direct Connect for speed data transfer (takes time to setup and expensive then VPN)
- S3 and Glacier (with RTO of 3-5 hours) provides durable storage
- RDS snapshots and Multi AZ support and Read Replicas across regions
- DynamoDB with cross region replication
- Redshift snapshots to recreate the cluster
- Storage Gateway to backup the data in AWS
- Import/Export to move large amount of data to AWS (if internet speed is the bottleneck)
- CloudFormation, Elastic Beanstalk and Opsworks as orchestration tools for automation and recreate the infrastructure



# AWS Services Summary Cheat Sheet

Original Source: [http://jayendrapatil.com/aws-certification-exam-cheat-sheet/](http://jayendrapatil.com/aws-certification-exam-cheat-sheet/)

## [AWS Organizations](https://aws.amazon.com/organizations/)

- offers **policy-based management for multiple AWS accounts**
- allows creation of groups of accounts and then apply policies to those groups
- enables you to centrally manage policies across multiple accounts, without requiring custom scripts and manual processes.
- helps simplify the billing for multiple accounts by enabling the setup of a single payment method for all the accounts in the organization through consolidated billing

## [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/) (AWS Region, AZs, Edge locations)

- Each region is a separate geographic area, completely independent, isolated from the other regions & helps achieve the greatest possible fault tolerance and stability
  - Communication between regions is across the public Internet
  - Each region has multiple Availability Zones (UPDATE: Osaka-Local has one region has 1 AZ)
- Each AZ is physically isolated, geographically separated from each other and designed as an independent failure zone
AZs are connected with low-latency private links (not public internet)
- Edge locations are locations maintained by AWS through a worldwide network of data centers for the distribution of content to reduce latency. (Not necessarily in the AZ's)
- AWS has announced plans to expand with 12 new AZs in four new geographic Regions: Bahrain, Cape Town, Hong Kong SAR, and Milan. (As of Jan 2019)

## AWS Services Region, AZ, Subnet VPC limitations
- Services like IAM (user, role, group, SSL certificate), Route 53, STS are Global and available across regions
- All other AWS services are limited to Region or within Region and do not exclusively copy data across regions unless configured
- AMIs are limited to regions and need to be copied over to other region
- EBS volumes are limited to the AZ, and can be migrated by creating snapshots and copying them to another region
- Reserved instances can be migrated to other AZ 
- RDS instances are limited to the region and can be recreated in a different region by either using snapshots or promoting a Read Replica
- Placement groups are limited to the AZ
- Cluster Placement groups are limited to single  AZs
- Spread Placement groups can span across multiple Availability Zones
- S3 data is replicated within the region to AZs and can be move to another region using cross region replication
  - [Cross region replication (CRR)](https://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) use and requirements
- DynamoDB maintains data within the region and can be replicated to another region using DynamoDB cross region replication (using DynamoDB streams) or Data Pipeline using EMR (old method)
- Redshift Cluster span within an AZ only, and can be created in other AZ using snapshots

## [AWS Consolidated Billing](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/consolidated-billing.html)

- One bill for multiple AWS accouns
- Paying account with multiple linked accounts
- Payer account is independent and should be only used for billing purpose
- Paying account cannot access resources of other accounts unless given exclusively access through Cross Account roles
- All linked accounts are independent and soft limit of 20
- Allows unused Reserved Instances to be applied across the group
- Free tier is not applicable across the accounts

## [AWS Multiple Account Billing Strategy](https://aws.amazon.com/answers/account-management/aws-multi-account-billing-strategy/)
- Use a group alias rather than an individual email address as the account email address to ensure continuity of communication
- Implement AWS tagging standards across your accounts


## Tags & [Resource Groups](https://docs.aws.amazon.com/ARG/latest/userguide/welcome.html)
- Resource Group is a collection of resources that share one or more tags
  - [AWS Resource Groups API](https://docs.aws.amazon.com/ARG/latest/APIReference/Welcome.html)
- Tags are key and value pairs that act as metadata for organizing your AWS resources
- Tags can be inherited when created resources created from Auto Scaling, Cloud Formation, Elastic Beanstalk etc
- Tags and Resource Groups can be used for:
  - Cost allocation to categorize and track the AWS costs
  - Conditional Access Control policy to define resource permission based on tags
  - Applying updates or security patches. 
  - Upgrading applications.
  - Opening or closing ports to network traffic.
  - Collecting specific log and monitoring data from your fleet of instances.

## IDS/IPS
- Promiscuous mode is not allowed. AWS and Hypervisor will not deliver any traffic to instances this is not specifically addressed to the instance

### IDS/IPS: Strategies
- Host Based Firewall 
  - Forward Deployed IDS where the IDS itself is installed on the instances
  – Traffic Replication where IDS agents installed on instances which send/duplicate the data to a centralized IDS system
- In-Line Firewall 
  – Inbound IDS/IPS Tier (like a WAF configuration) which identifies and drops suspect packets

### IDS/IPS: DDOS Mitigation
- Minimize the Attack surface
  - Use AWS ELB, AWS CloudFront, and AWS Route 53 to distribute load
  - maintain resources in private subnets and use Bastion servers
- Scale to absorb the attack
  - Scaling helps buy time to analyze and respond to an attack
  - ELB auto scaling help handle increased load to absorb attacks
  - CloudFront and Route 53 inherently scales as per the demand
- Safeguard exposed resources
  -  use Route 53 for aliases to hide source IPs and Private DNS
  -  use CloudFront geo restriction and Origin Access Identity
  - use WAF as part of the infrastructure
- Learn normal behavior (IDS/WAF)
  - analyze and benchmark to define rules on normal behavior
  - use CloudWatch
- Create an IR plan for attacks

## Security & Identity Services - IAM
- securely control access to AWS services and resources
- helps create and manage user identities and grant permissions for those users to access AWS resources
- helps create groups for multiple users with similar permissions
- not appropriate for application authentication
- is Global and does not need to be migrated to a different region
- helps define Policies,
  - in JSON format
  - all permissions are implicitly denied by default
  - most restrictive policy wins
  
## IAM Role
- helps grants and delegate access to users and services without the need of creating permanent credentials
- IAM users or AWS services can assume a role to obtain temporary security credentials that can be used to make AWS API calls
- needs Trust policy to define who and Permission policy to define what the user or service can access
- used with AWS STS (Security Token Service), a lightweight web service that provides temporary, limited privilege credentials for IAM users or for authenticated federated users

### IAM role scenarios
- Service access for e.g. EC2 to access S3 or DynamoDB
- Cross Account access for users
  - with user within the same account
  - with user within an AWS account owned the same owner
  - with user from a Third Party AWS account with External ID for enhanced security
- Identity Providers & Federation
  - Web Identity Federation, where the user can be authenticated using external authentication Identity providers like Amazon, Google or any OpenId IdP using AssumeRoleWithWebIdentity
  - Identity Provider using SAML 2.0, where the user can be authenticated using on premises Active Directory, Open Ldap or any SAML 2.0 compliant IdP using AssumeRoleWithSAML
  - For other Identity Providers, use Identity Broker to authenticate and provide temporary Credentials using AssumeRole (recommended) or GetFederationToken

## IAM Best Practices
- Do not use Root account for anything other than billing
- Create Individual IAM users
- Use groups to assign permissions to IAM users
- Grant least privilege
- **Use IAM roles for applications on EC2**
- Delegate using roles instead of sharing credentials
- Rotate credentials regularly
- Use Policy conditions for increased granularity
- Use CloudTrail to keep a history of activity
- Enforce a strong IAM password policy for IAM users
- Remove all unused users and credentials

## Security & Identity Services - [CloudHSM](https://aws.amazon.com/cloudhsm/)
- provides secure cryptographic key storage to customers by making hardware security modules (HSMs)
- single tenant, dedicated physical device to securely generate, store, and manage cryptographic keys used for data encryption
- inside the VPC (not EC2-classic) & isolated from the rest of the network
- can use VPC peering to connect to CloudHSM from multiple VPCs
- integrated with Amazon Redshift and Amazon RDS for Oracle
- EBS volume encryption, S3 object encryption and key management can be done with CloudHSM w/ custom application scripting
- **NOT fault tolerant** and would need to build a cluster - if one fails all the keys are lost
- expensive, prefer AWS Key Management Service (KMS) if cost is a criteria

## [AWS Directory Services](https://aws.amazon.com/directoryservice/)
- **Managed Microsoft Active Directory in the AWS Cloud**
- gives applications in AWS access to Active Directory services
- different from SAML + AD - where the access is granted to AWS services through Temporary Credentials

![](https://d1.awsstatic.com/Products/product-name/diagrams/directory_service_howitworks.80bfccbf2f5d1d63558ec3c086aff247147258f1.png)

## AWS Directory Services: Benefits
- EASILY MIGRATE DIRECTORY-AWARE, ON-PREMISES WORKLOADS
- USE ACTUAL MICROSOFT ACTIVE DIRECTORY
- SHARE A SINGLE DIRECTORY FOR CLOUD WORKLOADS
- EASILY EXTEND EXISTING DOMAINS
- CENTRALLY MANAGE APPLICATION ACCESS AND DEVICES IN THE AWS CLOUD
- SIMPLIFY ADMINISTRATION WITH A MANAGED SERVICE

## AWS Directory Services: [Simple AD](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/directory_simple_ad.html)
- least expensive but does not support Microsoft AD advance features
- provides a Samba 4 Microsoft Active Directory compatible standalone directory service on AWS
- No single point of Authentication or Authorization, as a separate copy is maintained
- trust relationships cannot be setup between Simple AD and other Active Directory domains
- Don’t use it, if the requirement is to leverage access and control through centralized authentication service

## AWS Directory Services: [AD Connector](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/directory_ad_connector.html)
- acts as a hosted proxy service for cloud instances to connect to on-premises Active Directory
- enables consistent enforcement (between cloud and on-prem) of existing security policies, such as:
  - password expiration
  - password history
  - account lockouts 
- needs VPN connectivity (or Direct Connect)
- enable MFA by integrating with existing RADIUS-based MFA solutions 
- does not cache data - **might lead to latency**

## AWS Directory Services: Read-only Domain Controllers (RODCs)
- works out as a Read-only Active Directory
- holds a copy of the Active Directory Domain Service (AD DS) database and respond to authentication requests
- cannot be written to and are typically deployed in locations where physical security cannot be guaranteed
- helps maintain a single point to authentication & authorization controls, however needs to be synced

## AWS Directory Services: Writable Domain Controllers
- are expensive to setup
- operate in a multi-master model
- changes can be made on any writable server in the forest, and those changes are replicated to servers throughout the entire forest

## AWS WAF (Web Application Firewall)
- helps monitor the HTTP/HTTPS requests forwarded to CloudFront and allows controlling access to the content.
- helps define Web ACLs, which is a combination of Rules, which is a combinations of Conditions and Action to block or allow

## Third Party WAF
- act as filters that apply a set of rules to web traffic to cover exploits like XSS and SQL injection and also help build resiliency against DDoS by mitigating HTTP GET or POST floods
- provides a lot of features like OWASP Top 10, HTTP rate limiting, Whitelist or blacklist, inspect and identify requests with abnormal patterns, CAPTCHA etc
- a WAF sandwich pattern can be implemented where an autoscaled WAF sits between the Internet and Internal Load Balancer

## [VPC](https://aws.amazon.com/vpc/) (Virtual Private Cloud)
- helps define a logically isolated dedicated virtual network within the AWS
- provides control of IP addressing using CIDR block from a minimum of /28 to maximum of /16 block size

## VPC Components
- Internet gateway (IGW) provides access to the Internet
- Virtual gateway (VGW) provides access to on-premises data center through VPN and Direct Connect connections
- VPC can have only one IGW and VGW
- Route tables determine where network traffic from subnet is directed
- Ability to create subnet with VPC CIDR block
- Network Address Translation (NAT) server provides outbound Internet access for EC2 instances in private subnets
- Elastic IP addresses are static, persistent public IP addresses
- Instances launched in the VPC always have a Private IP and can have a Public or a Elastic IP address associated 
- Security Groups and NACLs help define security
- Flow logs capture information about IP traffic going to and from network interfaces in your VPC

## VPC NAT (Network Address Translation)
- allows internet access to instances in private subnet
- performs the function of both address translation and port address translation (PAT)
- needs source/destination check flag to be disabled as it is not actual destination of  the traffic
- NAT gateway is a AWS managed NAT service that provides better availability, higher bandwidth, and requires less administrative effort

## VPC Route Tables
- defines rules, termed as routes, which determine where network traffic from the subnet would be routed
- Each VPC has a Main Route table, and can have multiple custom route tables created
- Every route table contains a local route that enables communication within a VPC which cannot be modified or deleted
- **Route priority is decided by matching the most specific route in the route table that matches the traffic**

## VPC Subnets
- map to AZs and do not span across AZs
- have a CIDR range that is a portion of the whole VPC.
- CIDR ranges cannot overlap between subnets within the VPC.
- AWS reserves 5 IP addresses in each subnet – first 4 and last one
- Each subnet is associated with a route table which define its behavior
- **Public subnets** – inbound/outbound Internet connectivity via IGW
- **Private subnets** – outbound Internet connectivity via an NAT or VGW
- **Protected subnets** – no outbound connectivity and used for regulated workloads

## VPC ENI (Elastic Network Interface)
- default ENI, eth0, is attached to an instance (which cannot be detached) with one or more secondary detachable ENIs (eth1-ethn)
- has primary private, one or more secondary private, public, Elastic IP address, security groups, MAC address and source/destination check flag attributes associated
- An ENI in one subnet can be attached to an instance in the same or another subnet, in the same AZ and the same VPC
- Security group membership of an ENI can be changed
- with pre allocated Mac Address can be used for applications with special licensing requirements

## VPC Security Groups vs Network Access Control Lists
|--------------------------|-----------------------------|
| Stateful | Statless |
| Instance level | Subnet level |
| Only allows ALLOW rules | Both Allot and Deny rules |
| Evaluates as a whole | Evaluated in defined order |

## VPC EIP (Elastic IPs)


## Tenancy option for instances
- shared, by default, allows instances to be launched on shared tenancy
- dedicated allows instances to be launched on a dedicated hardware


[[EDIT](https://github.com/nealalan/aws-notes/edit/master/README.md)]
