## Amazon Terminology
### 1. Amazon Elastic Compute Cloud (EC2)
A web service that provides secure, resizable compute capacity in the cloud. Think of it as renting a computer in the cloud.
### 2. Amazon Simple Storage Servive (S3)

### 3. Amazon Elastic Block Store (EBS)
Storage for specific Amazon Elastic Compute Cloud (Amazon EC2) instances. Think of it as the storage drive for your EC2 instance.

### 4. Amazon Relational Database Service (RDS)

### 5. Amazon Dynamo DB

### 6. Amazon CloudFront
A fast content delivery network (CDN) service that securely delivers data, videos, applications, and application programming interfaces (APIs) to customers globally with low latency and high transfer speeds, all within a developer-friendly environment.

### 7. AWS Direct Connect
Direct Connect is a cloud service solution that provides the ability to establish a dedicated network connection from your on-premises environment to AWS. Using Direct Connect, you can establish private connectivity between AWS and your data center, office, or colocation environment, which in many cases can reduce your network costs, increase bandwidth throughput, and provide a more consistent network experience than internet-based connections.

### 8. Caching
Storing frequently requested data in edge locations so that it can be accessed more quickly.

### 9. Content Delivery Network (CDN)
A system of distributed servers (network) that delivers pages and other web content to a user, based on the geographic locations of the user, the origin of the webpage, and the content delivery server.

### 10. Distribution
Instructs CloudFront where to get the information that it is caching in the edge locations and how to track and manage the content delivery.

### 11. Edge Locations
A site where data can be stored for lower latency. Often, edge locations will be close to high-population areas that will generate high traffic volumes.

### 12. Origin
A complex type that describes the Amazon S3 bucket, Hypertext Transfer Protocol (HTTP) server (for example, a web server), or other server from which CloudFront gets your files.
### 13. HDD
Slower storage that uses a spinning disk to store data.

### 14. Input/Output operations per second (IOPS)
A common performance measurement used to benchmark computer storage devices like hard disk drives (HDDs) and solid state drives (SSDs).

### 15. Solid State Drive (SSD)
Very fast storage that uses flash memory instead of a spinning disk.

### 16. AWS Identity and Access Management (IAM)
Involves the application of controls to users who need access to computing resources.

### 17. Role
An IAM identity that you can create in your account that has specific permissions.

### 18. User
An entity that you create in Amazon Web Services (AWS) to represent the person or application that uses it to interact with AWS. A user in AWS consists of a name and credentials.

### 19. Security Group
A security group acts as a virtual firewall for your instance to control inbound and outbound traffic.

### 20. Policy
An object in AWS that, when associated with an identity or a resource, defines its permissions. AWS evaluates these policies when a principal entity (user or role) makes a request.

### 21. Amazon Inspector
Helps customers identify security vulnerabilities and deviations from security best practices in applications, before they are deployed and while they are running in a production environment;; An automated security assessment service. It helps you test the network accessibility of your Amazon Elastic Compute Cloud (Amazon EC2) instances and the security state of your applications running on the instances.

### 22. Group
An IAM group is a collection of IAM users. Groups let you specify permissions for multiple users, which can make it easier to manage the permissions for those users.

### 23. Root User
When you first create an AWS account, you begin with a single sign-in identity that has complete access to all AWS services and resources in the account.

### 24. Credential
AWS security credentials verify who you are and whether you have permission to access the resources that you are requesting.

### 25. Enable multi-factor authentication (MFA)
This approach to authentication requires two or more independent pieces of information to be authenticated.

### 26. AWS Shield
A managed DDoS protection service that safeguards applications running on Amazon Web Services (AWS).

### 27. AWS WAF
A service that gives you control over which traffic to allow or block to your web applications by defining customizable web security rules.

### 26. JavaScript Object Notation (JSON)
A syntax for storing and exchanging data.

### 27. Multifactor Authentication (MFA)
A security system that requires more than one method of authentication from independent categories of credentials to verify the user's identity for a login or other transaction.

### 28. Distributed denial of service (DDoS)
A malicious attempt to make a targeted system, such as a website or application, unavailable to end users. To achieve this, attackers use a variety of techniques that consume network or other resources, interrupting access for legitimate end users.

### 29. Amazon CloudWatch
A monitoring service to monitor your AWS resources and the applications that you run on AWS

### 30. Amazon CloudTrail
A service to monitor and log every action that is performed on your AWS account for security purposes

### 31. AWS Config
A service that lets you assess, audit, and evaluate the configurations of your AWS resources

### 32. Amazon Simple Notification Service (Amazon SNS)
An AWS tool that lets you send texts, emails, and messages to other cloud services and send notifications in various forms from the cloud to the client

### 33. AWS artifact
A central resource for compliance-related information. It provides on-demand access to AWS security and compliance reports and select online agreements.

### 34. Relational database
A collection of datasets organized as records and columns in tables. In a relational database system, relationships are defined between the database tables. Think of a relational database as a set of data with 1-to-1 and 1-to-many relationships. For example, a database of customers would match each customer with an identifier that uniquely identifies the customer. Developers use structured query language (SQL) to interact with the database.

### 35. Amazon Relational Database Service (Amazon RDS)
Amazon RDS lets developers create and manage relational databases in the cloud. Amazon RDS lets developers track large amounts of data and organize and search through it efficiently.

### 36. Amazon DynamoDB
The AWS nonrelational database service. Data is stored in key-value pairs.

### 37. Nonrelational database
Also called a "NoSQL" or "Not only SQL" database. Each entry is stored in a key-value pair in which each key is attached to values. Each entry can have a different number of values attached to a key.

### 38. Amazon Redshift
The AWS data-warehousing service that can store massive amounts of data in a way that makes it fast to query for business intelligence (BI) purposes.

### 39. Online transaction processing (OLTP)
A category of data processing that is focused on transaction-oriented tasks. OLTP typically involves inserting, updating, or deleting small amounts of data in a database.

### 40. Online analytic processing (OLAP)
A computing method that lets users efficiently and selectively extract and query data to analyze it from different points of view.

### 41. Amazon Aurora
A relational database engine compatible with MySQL and PostgreSQL, built for the cloud, combining the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open-source databases.

### 42. MySQL
An open-source relational database management system.

### 43. Amazon ElastiCache
A web service that makes it easy to deploy, operate, and scale an in-memory cache in the cloud. The service improves the performance of web applications by letting you retrieve information from fast, managed, in-memory caches, instead of relying on slower disk-based databases.

### 44. Cache
In computing, a cache is a high-speed data storage layer that stores a subset of data, typically transient in nature, so that future requests for that data are served up faster than is possible by accessing the data’s primary storage location.

### 45. Data caching
Storing data in a cache lets you efficiently reuse previously retrieved or computed data. The data in a cache is generally stored in fast-access hardware such as random access memory (RAM) and can also be used with a software component.

### 46. Elastic Load Balancing
Elastic Load Balancing automatically distributes incoming application traffic across multiple targets, such as Amazon Elastic Compute Cloud (Amazon EC2) instances, containers, IP addresses, and AWS Lambda functions. If traffic to a website suddenly spikes, that traffic can be routed to other EC2 instances (or other types of instances such as Lambda instances) that have been established in advance for this purpose. This load balancing avoids a single server being overloaded because of increased traffic routed to it.

### 47. Random access memory (RAM)
Volatile, temporary memory storage. This is the data that is held temporarily while a machine is in use; however, once the machine is powered off or the task is completed, this data goes away. Virtual memory is stored in the read-only memory (ROM) as a supplement to RAM when there is not enough temporary memory available.
