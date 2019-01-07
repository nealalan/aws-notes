# [nealalan.github.io](https://nealalan.github.io)/[aws-notes](https://nealalan.github.io/aws-notes)

## [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/) (June 2018 version)

#### Good Design Principles
- Stop guessing your capacity needs
- Test systems at production scale
- Automate to make architectural experimentation easier
- Allow for evolutionary architectures
- Drive architectures using data
- Improve through game days

### The Five Pillars of the Well-Architected Framework
1) OPS: Operational Excellence
2) SEC: Security
3) REL: Reliability
4) PERF: Performance Efficiency
5) COST: Cost Optimization

#### 1) OPS: Operational Excellence

##### Design Principles for Operational Excellence
- Perform operations as code - limit human error and enable consistent responses to events
- Annotate documentation
- Make frequent, small, reversible changes
- Refine operations procedures frequently
- Anticipate failure
- Learn from all operational failures

##### Best Practices - Prepare, Operate, Evolve
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

###### Key Services
- AWS CloudFormation = essential to Ops Excellence

#### 2) SEC: Security

##### Design principles for Security

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

##### Best Practices
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

##### Key AWS Services
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

#### 3) REL: Reliability

##### Best Practices - Foundations, Change management, Failure management
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

#### 4) PERF: Performance Efficiency

##### Design Principles for Performance Efficiency
- Democratize advanced technologies
- Go global in minutes
- Use serverless architectures
- Experiment more often
- Mechanical sympathy

##### Best Practices & Key AWS Services for Performance Efficiency
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

#### 5) Cost Optimization

##### Pillars for cost optimization & Key Services
1. Cost-Effective Resources
2. Matching supply and demand
3. Expenditure Awareness
4. Optimizing Over Time

##### Best Practices for Cost Optimization
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




[[EDIT](https://github.com/nealalan/aws-notes/edit/master/README.md)]
