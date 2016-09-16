#AWS Certified Solutions Architect
###Associate Exam Blueprint

This guide is based, in large part, on the exam blueprint located here:

[AWS certified solutions architect associate blueprint](https://d0.awsstatic.com/training-and-certification/docs-sa-assoc/AWS_certified_solutions_architect_associate_blueprint.pdf "https://d0.awsstatic.com/training-and-certification/docs-sa-assoc/AWS_certified_solutions_architect_associate_blueprint.pdf")(pdf)

---
This exam requires a comfortable grasp of, or experience with, the following:

- AWS Knowledge
	- Hands-on experience using compute, networking, storage, and database AWS services
	- Professional experience architecting large-scale distributed systems
	- Understanding of elasticity and scalability concepts
	- Understanding of the AWS global infrastructure
	- Understanding of network technologies as they relate to AWS
	- A good understanding of all security features and tools that AWS provides and how they relate to traditional services
	- A strong understanding of client interfaces to the AWS platform
	- Hands-on experience with AWS deployment and management services
- General IT Knowledge
	- Excellent understanding of typical multi-tier architectures: web servers, caching, application servers, load balancers, and storage
	- Understanding of Relational Database Management System (RDBMS) and NoSQL
	- Knowledge of message queuing and Enterprise Service Bus (ESB)
	- Familiarity with loose coupling and stateless systems
	- Understanding of different consistency models in distributed systems
	- Knowledge of Content Delivery Networks (CDN)
	- Hands-on experience with core LAN/WAN network technologies
	- Experience with route tables, access control lists, firewalls, NAT, HTTP, DNS, IP and OSI Network
	- Knowledge of RESTful Web Services, XML, JSON
	- Familiarity with the software development lifecycle
	- Work experience with information and application security concepts, mechanisms, and tools
	- Awareness of end-user computing and collaborative technologies

---


Domain | % of Examination
------------ | -------------
1.0 Designing highly available, cost-efficient, fault-tolerant, scalable systems | 60%
2.0 Implementation/Deployment | 10%
3.0 Data Security | 20%
4.0 Troubleshooting | 10%
TOTAL | 100%

Anything else listed additionally is based on my own observations. Links listed here may be subject to copyright protection and access to such is up to the discretion of the authors\owners to which they pertain.

####Additional Resources
- [AWS Video library](https://aws.amazon.com/training/intro_series/ "https://aws.amazon.com/training/intro_series/") 
- [AWS Cloud Computing Services Whitepapers](http://aws.amazon.com/whitepapers/ "http://aws.amazon.com/whitepapers/")
- [AWS Architecture Center](http://aws.amazon.com/architecture/ "http://aws.amazon.com/architecture/")


###Domain 1.0: Designing highly available, cost-efficient, fault-tolerant, scalable systems

1.1	Identify and recognize cloud architecture considerations, such as
fundamental components and effective designs.

Content may include the following:

- How to design cloud services
- Planning and design
- Monitoring and logging
- Familiarity with:
	- Best practices for AWS architecture
	- Developing to client specifications, including pricing/cost (e.g., on Demand vs. Reserved vs. Spot; RTO and RPO DR Design)
	- Architectural trade-off decisions (e.g., high availability vs. cost, Amazon Relational Database Service (RDS) vs. installing your own database on Amazon Elastic Compute Cloud (EC2))
	- Hybrid IT architectures (e.g., Direct Connect, Storage Gateway, VPC, Directory Services)
	- Elasticity and scalability (e.g., Auto Scaling, SQS, ELB, CloudFront)

###Domain 2.0: Implementation/Deployment

2.1 Identify the appropriate techniques and methods using Amazon EC2, Amazon S3, AWS Elastic Beanstalk, AWS CloudFormation, AWS OpsWorks, Amazon Virtual Private Cloud (VPC), and AWS Identity and Access Management (IAM) to code and implement a cloud solution.

Content may include the following:

- Configure an Amazon Machine Image (AMI)
- Operate and extend service management in a hybrid IT architecture
- Configure services to support compliance requirements in the cloud
- Launch instances across the AWS global infrastructure
- Configure IAM policies and best practices