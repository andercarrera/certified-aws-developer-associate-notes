* **Amazon Simple Queue Service (SQS) has a set of APIs for various actions supported by the service.
  As a developer associate, which of the following would you identify as correct regarding the CreateQueue API? (Select
  two)**
    * You can't change the queue type after you create it - _You can't change the queue type after you create it and you
      can't convert an existing standard queue into a FIFO queue. You must either create a new FIFO queue for your
      application or delete your existing standard queue and recreate it as a FIFO queue._
    * The visibility timeout value for the queue is in seconds, which defaults to 30 seconds - _The visibility timeout
      for the queue is in seconds. Valid values are: An integer from 0 to 43,200 (12 hours), the Default value is 30._
* **A retail company is migrating its on-premises database to Amazon RDS for PostgreSQL. The company has read-heavy
  workloads. The development team at the company is looking at refactoring the code to achieve optimum read performance
  for SQL queries.
  Which solution will address this requirement with the least current as well as future development effort?**
    * Set up Amazon RDS with one or more read replicas. Refactor the application code so that the queries use the
      endpoint for the read replicas - _Amazon RDS uses the PostgreSQL DB engine's built-in replication functionality to
      create a special type of DB instance
      called a read replica from a source DB instance. The source DB instance becomes the primary DB instance. Updates
      made to
      the primary DB instance are asynchronously copied to the read replica. You can reduce the load on your primary DB
      instance by routing read queries from your applications to the read replica. Using read replicas, you can
      elastically
      scale out beyond the capacity constraints of a single DB instance for read-heavy database workloads. For the given
      use
      case, you can achieve optimum read performance for SQL queries by using the read-replica endpoint for the
      read-heavy
      workload._
* **You are a developer for a web application written in .NET which uses the AWS SDK. You need to implement an
  authentication mechanism that returns a JWT (JSON Web Token).x
  Which AWS service will help you with token handling and management?**
    * Cognito User Pools - _After successful authentication, Amazon Cognito returns user pool tokens to your app. You
      can use the tokens to grant your users access to your own server-side resources, or to the Amazon API Gateway.
      Amazon Cognito user pools implement ID, access, and refresh tokens as defined by the OpenID Connect (OIDC) open
      standard._
    * ~~Cognito Identity
      Pools - _You can use Identity pools to grant your users access to other AWS services. With an identity pool, your
      users can obtain temporary AWS credentials to access AWS services, such as Amazon S3 and DynamoDB. Identity pools
      support anonymous guest users, as well as the specific identity providers that you can use to authenticate users
      for identity pools._~~
* **Your company has stored all application secrets in SSM Parameter Store. The audit team has requested to get a report
  to better understand when and who has issued API calls against SSM Parameter Store.
  Which of the following options can be used to produce your report?**
    * Use AWS CloudTrail to get a record of actions taken by a user - _AWS Systems Manager Parameter Store provides
      secure, hierarchical storage for configuration data management and secrets management. You can store data such as
      passwords, database strings, Amazon Machine Image (AMI) IDs, and license codes as parameter values. You can store
      values as plain text or encrypted data.
      AWS CloudTrail provides a record of actions taken by a user, role, or an AWS service in Systems Manager. Using the
      information collected by AWS CloudTrail, you can determine the request that was made to Systems Manager, the IP
      address from which the request was made, who made the request, when it was made, and additional details._
      ~~* Use SSM Parameter Store Access Logs in CloudWatch Logs to get a record of actions taken by a
      user - _CloudWatch Logs can be integrated but that will not help determine who issued API calls._~~
* **An e-commerce company has developed an API that is hosted on Amazon ECS. Variable traffic spikes on the application
  are causing order processing to take too long. The application processes orders using Amazon SQS queues. The
  ApproximateNumberOfMessagesVisible metric spikes at very high values throughout the day which triggers the CloudWatch
  alarm. Other ECS metrics for the API containers are well within limits.
  As a Developer Associate, which of the following will you recommend for improving performance while keeping costs low?**
    * Use backlog per instance metric with target tracking scaling policy - _If you use a target tracking scaling policy
      based on a custom Amazon SQS queue metric, dynamic scaling can adjust to the demand curve of your application more
      effectively.
      The issue with using a CloudWatch Amazon SQS metric like ApproximateNumberOfMessagesVisible for target tracking is
      that the number of messages in the queue might not change proportionally to the size of the Auto Scaling group
      that processes messages from the queue. That's because the number of messages in your SQS queue does not solely
      define the number of instances needed. The number of instances in your Auto Scaling group can be driven by
      multiple factors, including how long it takes to process a message and the acceptable amount of latency (queue
      delay).
      The solution is to use a backlog per instance metric with the target value being the acceptable backlog per
      instance to maintain. You can calculate these numbers as follows:
      Backlog per instance: To calculate your backlog per instance, start with the ApproximateNumberOfMessages queue
      attribute to determine the length of the SQS queue (number of messages available for retrieval from the queue).
      Divide that number by the fleet's running capacity, which for an Auto Scaling group is the number of instances in
      the InService state, to get the backlog per instance.
      Acceptable backlog per instance: To calculate your target value, first determine what your application can accept
      in terms of latency. Then, take the acceptable latency value and divide it by the average time that an EC2
      instance takes to process a message.
      To illustrate with an example, let's say that the current ApproximateNumberOfMessages is 1500 and the fleet's
      running capacity is 10. If the average processing time is 0.1 seconds for each message and the longest acceptable
      latency is 10 seconds, then the acceptable backlog per instance is 10 / 0.1, which equals 100. This means that 100
      is the target value for your target tracking policy. If the backlog per instance is currently at 150 (1500 / 10),
      your fleet scales out, and it scales out by five instances to maintain proportion to the target value._
    * ~~Use ECS service scheduler - _ Amazon ECS provides a service scheduler (for long-running tasks and applications),
      the ability to run tasks manually (for batch jobs or single run tasks), with Amazon ECS placing tasks on your
      cluster for you. You can specify task placement strategies and constraints that allow you to run tasks in the
      configuration you choose, such as spread out across Availability Zones. It is also possible to integrate with
      custom or third-party schedulers._~~
* **As an AWS Certified Developer Associate, you are writing a CloudFormation template in YAML. The template consists of an EC2 instance creation and one RDS resource. Once your resources are created you would like to output the connection endpoint for the RDS database.
Which intrinsic function returns the value needed?**:
  * `GetAtt` - _The intrinsic function GetAtt returns the value of an attribute from a resource in the template. For example, to get the endpoint of an RDS database, you can use the GetAtt function to return the endpoint attribute of the RDS resource._
  * ~~`Ref` - _The intrinsic function Ref returns the value of the specified parameter or resource._~~
  * ~~`Fn::Sub` - _The intrinsic function Fn::Sub substitutes variables in an input string with values that you specify._~~
* **As a developer associate, can you identify the key characteristics of the strongly consistent data model followed by S3? (Select two)**:
  * A process deletes an existing object and immediately tries to read it. Amazon S3 will not return any data as the object has been deleted
    * _Amazon S3 provides strong read-after-write consistency for PUTs and DELETEs of objects in your Amazon S3 bucket in all AWS Regions. This applies to both writes to new objects as well as PUTs that overwrite existing objects and DELETEs._
  * If you delete a bucket and immediately list all buckets, the deleted bucket might still appear in the list
    * _Bucket configurations have an eventual consistency model. If you delete a bucket and immediately list all buckets, the deleted bucket might still appear in the list._
* **A company uses microservices-based infrastructure to process the API calls from clients, perform request filtering and cache requests using the AWS API Gateway. Users report receiving 501 error code and you have been contacted to find out what is failing. Which service will you choose to help you troubleshoot?**:
  * Use X-Ray service: _Troubleshoot always X RAY_
* **The development team at an IT company uses CloudFormation to manage its AWS infrastructure. The team has created a network stack containing a VPC with subnets and a web application stack with EC2 instances and an RDS instance. The team wants to reference the VPC created in the network stack into its web application stack. As a Developer Associate, which of the following solutions would you recommend for the given use-case?**:
  * Create a cross-stack reference and use the Export output field to flag the value of VPC from the network stack. Then use `Fn::ImportValue` intrinsic function to import the value of VPC into the web application stack
* **A company stores confidential data on an Amazon Simple Storage Service (S3) bucket. New regulatory guidelines require that files be stored with server-side encryption. The encryption used must be Advanced Encryption Standard (AES-256) and the company does not want to manage S3 encryption keys. Which of the following options should you use?**
  * Use SSE-S3: _SSE-S3 encrypts your objects with AES-256 encryption keys that are managed by Amazon S3. There is no additional charge for using SSE-S3._ 
* **An organization with high data volume workloads have successfully moved to DynamoDB after having many issues with traditional database systems. However, a few months into production, DynamoDB tables are consistently recording high latency. As a Developer Associate, which of the following would you suggest to reduce the latency? (Select two)**
  * Use eventually consistent reads in place of strongly consistent reads whenever possible - _Eventually consistent reads are less expensive than strongly consistent reads. If your application can tolerate reading data that might not be consistent, you can use eventually consistent reads to reduce latency._
  * Consider using Global tables if your application is accessed by globally distributed users - _Global tables replicate your Amazon DynamoDB tables automatically across your choice of AWS regions. Global tables provide a fully managed solution for deploying a multi-region, multi-master database, without having to build and maintain your own replication solution._
* **You are a developer working at a cloud company that embraces serverless. You have performed your initial deployment and would like to work towards adding API Gateway stages and associate them with existing deployments. Your stages will include prod, test, and dev and will need to match a Lambda function variant that can be updated over time. Which of the following features must you add to achieve this? (select two)**
  * Lambda Aliases: _Lambda aliases are a feature that allows you to point to a specific version of a Lambda function. This is useful when you want to work with different versions of your Lambda function in different environments, such as dev, test, and prod._
  * Stage Variables: 