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
1) OPS: Operational Excellence
2) SEC: Security
3) REL: Reliability
4) PERF: Performance Efficiency
5) COST: Cost Optimization

## 1) OPS: Operational Excellence

### Design Principles for Operational Excellence
- Perform operations as code - limit human error and enable consistent responses to events
- Annotate documentation
- Make frequent, small, reversible changes
- Refine operations procedures frequently
- Anticipate failure
- Learn from all operational failures

### Best Practices - Prepare, Operate, Evolve
- OPS 1: What factors drive your operational priorities?
  - Evaluate Business neets
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

#### Key Services
- AWS CloudFormation = essential to Ops Excellence

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
- Hybrid Account Structures Example
  ![](https://d1.awsstatic.com/aws-answers/answers-images/hybrid-structure-1.01c5f8711781b85d4c1a429704d934d8c28a2a51.png)

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

### Strategies
- Host Based Firewall 
  - Forward Deployed IDS where the IDS itself is installed on the instances
  – Traffic Replication where IDS agents installed on instances which send/duplicate the data to a centralized IDS system
- In-Line Firewall 
  – Inbound IDS/IPS Tier (like a WAF configuration) which identifies and drops suspect packets

### DDOS Mitigation
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

### IAM Best Practices
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

### Security & Identity Services - [CloudHSM](https://aws.amazon.com/cloudhsm/)
- provides secure cryptographic key storage to customers by making hardware security modules (HSMs)
- single tenant, dedicated physical device to securely generate, store, and manage cryptographic keys used for data encryption
- inside the VPC (not EC2-classic) & isolated from the rest of the network
- can use VPC peering to connect to CloudHSM from multiple VPCs
- integrated with Amazon Redshift and Amazon RDS for Oracle
- EBS volume encryption, S3 object encryption and key management can be done with CloudHSM w/ custom application scripting
- **NOT fault tolerant** and would need to build a cluster - if one fails all the keys are lost
- expensive, prefer AWS Key Management Service (KMS) if cost is a criteria






[[EDIT](https://github.com/nealalan/aws-notes/edit/master/README.md)]
