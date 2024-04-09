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
  As a Developer Associate, which of the following will you recommend for improving performance while keeping costs low?
  **
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