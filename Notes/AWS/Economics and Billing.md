# Fundamentals of Pricing
## AWS Pricing Model
Three fundamental drivers of cost with AWS:
- Compute
	1. Charged by hour/second
	2. Varies by instance type
- Storage
	1. Charged typically per GB
- Data Transfer
	1. Outbound is aggregated and charged
	2. Inbound has no charge (with some exceptions)
	3. Charged typically per GB
## How do you pay for AWS?
- At the end of each month you pay for what you use.
- You can start or stop using products at any time

### The utility-style pricing model includes:
**Pay for what you use**
Pay only for the services that you consume with no large upfront expenses.

**Pay less when you reserve**
For certain services such as Amazon EC2 and Amazon RDS  you can invest in reserved capacity. With reserved instances you can save up to 75% over equivalent on-demand capacity.

**Pay less by using more**
With AWS you can get volume-based discounts and realize important savings as your usage increases.
- Savings as usage increases
- Tiered pricing for services like Amazon Simple Storage Service (Amazon S3).
- Multiple storage services deliver lower storage costs based on needs.

**Pay even less as AWS grows**
- AWS focuses on lowering costs of doing business
- AWS passing savings from economies of scale to you
- Feature higher-performance resources replace current resources for no extra charge

**Custom pricing**
- Meet varying needs through custom pricing
- Available for high-volume projects with unique requirements

**AWS Free tier**
Enabled you to gain free hands-on experience with the AWS platform, products and services. Free for 1 year for new customers

**Services with no charge**
AWS provides a variety of services for no additional charge.
- Amazon Virtual Private Cloud (Amazon VPC)
- AWS Identity and Access Management (IAM)
- Consolidated Billing

# Total Cost of Ownership
![](/Images/aws_on_premises_vs_cloud.png)
An on-premises infrastructure is installed locally on a companies own computers and servers. Capital expenses that are associated with the traditional infrastructure are included.

A cloud infrastructure is purchased from a service provider who builds and maintains the facilities, hardware and maintenance staff. Customers pay for what they use. Scaling is simple and costs are easy to estimate.

**Total Cost of Ownership (TCO)** is the financial estimate to help identify direct and indirect costs of a system.
It is used to compare the costs of running an entire infrastructure environment or specific workload on-premises vs on AWS. As well as to budget and build the business case for moving to the cloud.
![](/Images/aws_tco_considerations.png)
## AWS Pricing Calculator
- Estimates monthly costs
- Identify opportunities to reduce monthly costs
- Model your solutions before building them
- Explore price points band calculations behind your estimate
- Find the available instance types and contract terms that meet your needs
- Name your estimate and create and name groups of services

# AWS Organizations
A free account management service that enables you to consolidate multiple AWS accounts into an organization that you create and centrally manage.

**Benefits:**
1. Centrally managed access to policies across multiple AWS accounts
2. Controlled access to AWS services
3. Automated AWS account creation and management
4. Consolidated billing across multiple AWS accounts

![](/Images/aws_organization_terminology.png)
- Root - The organization
- OU (Organizational Unit) - Container for accounts within root
## Security
- Control access with AWS Identity and Access Management (IAM)
- IAM policies enable you to allow or deny access to AWS services for users, groups and roles
- Service Control Policies (SCPs) enable you to allow or deny access to AWS services for individuals or group accounts in an organizations unit (OU)
## Limits
![](/Images/aws_organizational_limits.png)
# Billing and Cost Management
AWS Billing and Cost Management is the service you use to pay your AWS bill, monitor your usage, and budget your costs. 
