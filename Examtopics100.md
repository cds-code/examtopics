
# 1/529 

<div style="color:blue">single</div>
Question #1<br>A company needs to architect a hybrid DNS solution. This solution will use an Amazon Route 53 private hosted zone for the domain cloud.example.com for the resources stored within VPCs.<br>The company has the following DNS resolution requirements:<br>On-premises systems should be able to resolve and connect to cloud.example.com.<br>All VPCs should be able to resolve cloud.example.com.<br>There is already an AWS Direct Connect connection between the on-premises corporate network and AWS Transit Gateway.<br>Which architecture should the company use to meet these requirements with the HIGHEST performance?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Associate the private hosted zone to all the VPCs. Create a Route 53 inbound resolver in the shared services VPC. Attach all VPCs to the transit gateway and create forwarding rules in the on-premises DNS server for cloud.example.com that point to the inbound resolver.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Associate the private hosted zone to all the VPCs. Deploy an Amazon EC2 conditional forwarder in the shared services VPC. Attach all VPCs to the transit gateway and create forwarding rules in the on-premises DNS server for cloud.example.com that point to the conditional forwarder.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Associate the private hosted zone to the shared services VPC. Create a Route 53 outbound resolver in the shared services VPC. Attach all VPCs to the transit gateway and create forwarding rules in the on-premises DNS server for cloud.example.com that point to the outbound resolver.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. &nbsp;Associate the private hosted zone to the shared services VPC. Create a Route 53 inbound resolver in the shared services VPC. Attach the shared services VPC to the transit gateway and create forwarding rules in the on-premises DNS server for cloud.example.com that point to the inbound resolver.&nbsp;
</div>
        
<details>

<summary>English</summary>

<div translate="no">
Question #1<br>A company needs to architect a hybrid DNS solution. This solution will use an Amazon Route 53 private hosted zone for the domain cloud.example.com for the resources stored within VPCs.<br>The company has the following DNS resolution requirements:<br>On-premises systems should be able to resolve and connect to cloud.example.com.<br>All VPCs should be able to resolve cloud.example.com.<br>There is already an AWS Direct Connect connection between the on-premises corporate network and AWS Transit Gateway.<br>Which architecture should the company use to meet these requirements with the HIGHEST performance?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>The correct answer is A. Here's the detailed explanation:<br>Why Option A is the Best Solution?<br>The requirements are:<br>1.On-premises systems must resolve `cloud.example.com`.<br>2.All VPCs must resolve `cloud.example.com`.<br>3.High performance is required (minimal latency and complexity).<br>Option A meets these requirements by:<br>1.Associating the private hosted zone with all VPCs → Ensures VPC resources can resolve `cloud.example.com` natively via Route 53.<br>2.Creating a Route 53 inbound resolver in the shared services VPC → Provides a centralized DNS resolution endpoint for on-premises queries.<br>3.Using AWS Transit Gateway for connectivity → Ensures low-latency communication between VPCs and on-premises.<br>4.Forwarding on-premises DNS queries to the inbound resolver → Allows on-premises systems to resolve `cloud.example.com` efficiently.<br>Why Other Options Are Incorrect?<br>-Option B: Uses anEC2-based conditional forwarder, which introduces unnecessary management overhead (scaling, patching) compared to Route 53 Resolver (fully managed).<br>-Option C: Associates the private hosted zoneonly with the shared services VPC, meaning other VPCs cannot resolve `cloud.example.com` natively (requires outbound resolver, which adds complexity).<br>-Option D: Similar to Option C, but uses aninbound resolver while still restricting the hosted zone to one VPC, breaking resolution for other VPCs.<br>Key Considerations for Performance<br>-Route 53 private hosted zones provide the fastest DNS resolution within VPCs when associated directly.<br>-Route 53 Resolver (inbound) is fully managed and optimized for hybrid DNS, unlike manual EC2 solutions.<br>-Transit Gateway ensures high-speed connectivity between VPCs and on-premises.<br>Conclusion<br>Option A is the most efficient, scalable, and performant solution, leveraging native AWS services (Route 53 private hosted zones + inbound resolver) without introducing unnecessary complexity.<br>ref:: https://aws.amazon.com/blogs/networking-and-content-delivery/centralized-dns-management-of-hybrid-cloud-withamazon-route-53-and-aws-transit-gateway/ <br><br><br><br><br>
</div>

</details>

    
# 2/529 

<div style="color:blue">single</div>
<br>Question #2<br>A company is providing weather data over a REST-based API to several customers. The API is hosted by Amazon API Gateway and is integrated with different AWS Lambda functions for each API operation. The company uses Amazon Route 53 for DNS and has created a resource record of weather.example.com. The company stores data for the API in Amazon DynamoDB tables. The company needs a solution that will give the API the ability to fail over to a different AWS Region.<br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Deploy a new set of Lambda functions in a new Region. Update the API Gateway API to use an edge-optimized API endpoint with Lambda functions from both Regions as targets. Convert the DynamoDB tables to global tables.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Deploy a new API Gateway API and Lambda functions in another Region. Change the Route 53 DNS record to a multivalue answer. Add both API Gateway APIs to the answer. Enable target health monitoring. Convert the DynamoDB tables to global tables.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Deploy a new API Gateway API and Lambda functions in another Region. Change the Route 53 DNS record to a failover record. Enable target health monitoring. Convert the DynamoDB tables to global tables.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Deploy a new API Gateway API in a new Region. Change the Lambda functions to global functions. Change the Route 53 DNS record to a multivalue answer. Add both API Gateway APIs to the answer. Enable target health monitoring. Convert the DynamoDB tables to global tables.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #2<br>A company is providing weather data over a REST-based API to several customers. The API is hosted by Amazon API Gateway and is integrated with different AWS Lambda functions for each API operation. The company uses Amazon Route 53 for DNS and has created a resource record of weather.example.com. The company stores data for the API in Amazon DynamoDB tables. The company needs a solution that will give the API the ability to fail over to a different AWS Region.<br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>Based on the information provided, the best solution for implementing a multi-region failover capability for the company's REST API would be:<br>C. Deploy a new API Gateway API and Lambda functions in another Region. Change the Route 53 DNS record to a failover record. Enable target health monitoring. Convert the DynamoDB tables to global tables.<br>This approach provides a complete disaster recovery solution by:<br>Deploying the entire API infrastructure (API Gateway and Lambda functions) in a second region<br>Using Route 53 failover records with health monitoring to automatically redirect traffic when needed<br>Converting DynamoDB tables to global tables to ensure data consistency across regions<br>Option A is incomplete because it only deploys new Lambda functions in the new region and updates the existing API Gateway to use an edge-optimized endpoint. This doesn't provide true regional failover since the API Gateway itself would still be a single point of failure in one region.<br>The correct solution (C) creates a fully redundant setup across regions with automatic failover capabilities through Route 53 health checks and global tables for data replication.<br>Sources<br>Implementing multi-Region failover for Amazon API Gateway | AWS Compute Blog (https://aws.amazon.com/cn/blogs/compute/implementing-multi-region-failover-for-amazon-api-gateway/）<br>Deploy a reference architecture that models a serverless active/passive workload with asynchronous replication of application data and failover from a primary to a secondary AWS Region - Multi-Region Application Architecture Solution （ https://docs.aws.amazon.com/solutions/latest/multi-region-application-architecture/welcome.html）<br>AWS Backup vs global table/database for cost-effective RTO,RPO requirements | AWS re:Post （https://repost.aws/questions/QUWf0GuonKSvW8U2N4o8huHw/aws-backup-vs-global-table-database-for-cost-effective-rto-rpo-requirements）<br>Configure custom health checks for DNS failover for an API Gateway API - Amazon API Gateway （https://docs.aws.amazon.com/apigateway/latest/developerguide/dns-failover.html）<br>Community | Scale across borders: build a multi-region architecture while maintaining data residency （https://community.aws/content/2dhVhtsciD5gVBlCKUlHoszrDzU/scale-beyond-borders）<br>
</div>

</details>

    
# 3/529 

<div style="color:blue">single</div>
Question #3<br>A company uses AWS Organizations with a single OU named Production to manage multiple accounts. All accounts are members of the Production OU. Administrators use deny list SCPs in the root of the organization to manage access to restricted services.<br>The company recently acquired a new business unit and invited the new unit’s existing AWS account to the organization. Once onboarded, the administrators of the new business unit discovered that they are not able to update existing AWS Config rules to meet the company’s policies.<br>Which option will allow administrators to make changes and continue to enforce the current policies without introducing additional long-term maintenance?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Remove the organization&rsquo;s root SCPs that limit access to AWS Config. Create AWS Service Catalog products for the company&rsquo;s standard AWS Config rules and deploy them throughout the organization, including the new account.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create a temporary OU named Onboarding for the new account. Apply an SCP to the Onboarding OU to allow AWS Config actions. Move the new account to the Production OU when adjustments to AWS Config are complete.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Convert the organization&rsquo;s root SCPs from deny list SCPs to allow list SCPs to allow the required services only. Temporarily apply an SCP to the organization&rsquo;s root that allows AWS Config actions for principals only in the new account.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create a temporary OU named Onboarding for the new account. Apply an SCP to the Onboarding OU to allow AWS Config actions. Move the organization&rsquo;s root SCP to the Production OU. Move the new account to the Production OU when adjustments to AWS Config are complete.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
Question #3<br>A company uses AWS Organizations with a single OU named Production to manage multiple accounts. All accounts are members of the Production OU. Administrators use deny list SCPs in the root of the organization to manage access to restricted services.<br>The company recently acquired a new business unit and invited the new unit’s existing AWS account to the organization. Once onboarded, the administrators of the new business unit discovered that they are not able to update existing AWS Config rules to meet the company’s policies.<br>Which option will allow administrators to make changes and continue to enforce the current policies without introducing additional long-term maintenance?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">D</span>
To allow the new business unit's administrators to make changes to AWS Config rules while maintaining the existing policies, the solution is to create a temporary OU named Onboarding for the new account, as described in option D. By applying an SCP to this OU that allows AWS Config actions, the new account can adjust its AWS Config rules as needed. Once the adjustments are complete, moving the root SCP to the Production OU ensures that the current policies continue to be enforced across all accounts, and moving the new account to the Production OU integrates it with the rest of the organization while applying the same policies.<br>ref:https://docs.aws.amazon.com/whitepapers/latest/organizing-your-aws-environment/transitional-ou.html<br><br><br>
</div>

</details>

    
# 4/529 

<div style="color:blue">single</div>
<br>Question #4<br>A company is running a two-tier web-based application in an on-premises data center. The application layer consists of a single server running a stateful application. The application connects to a PostgreSQL database running on a separate server. The application’s user base is expected to grow significantly, so the company is migrating the application and database to AWS. The solution will use Amazon Aurora PostgreSQL, Amazon EC2 Auto Scaling, and Elastic Load Balancing.<br>Which solution will provide a consistent user experience that will allow the application and database tiers to scale?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Enable Aurora Auto Scaling for Aurora Replicas. Use a Network Load Balancer with the least outstanding requests routing algorithm and sticky sessions enabled.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Enable Aurora Auto Scaling for Aurora writers. Use an Application Load Balancer with the round robin routing algorithm and sticky sessions enabled.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Enable Aurora Auto Scaling for Aurora Replicas. Use an Application Load Balancer with the round robin routing and sticky sessions enabled.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Enable Aurora Scaling for Aurora writers. Use a Network Load Balancer with the least outstanding requests routing algorithm and sticky sessions enabled.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #4<br>A company is running a two-tier web-based application in an on-premises data center. The application layer consists of a single server running a stateful application. The application connects to a PostgreSQL database running on a separate server. The application’s user base is expected to grow significantly, so the company is migrating the application and database to AWS. The solution will use Amazon Aurora PostgreSQL, Amazon EC2 Auto Scaling, and Elastic Load Balancing.<br>Which solution will provide a consistent user experience that will allow the application and database tiers to scale?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>Based on the information provided, the best solution for migrating the stateful application to AWS while ensuring scalability and a consistent user experience would be:<br>C. Enable Aurora Auto Scaling for Aurora Replicas. Use an Application Load Balancer with the round robin routing and sticky sessions enabled.<br>This solution is optimal because:<br>Aurora Auto Scaling for Aurora Replicas will allow the database tier to automatically scale read capacity based on demand, which is essential as the user base grows significantly.<br>The Application Load Balancer (ALB) is the appropriate choice for HTTP/HTTPS traffic of a web-based application, offering more advanced routing capabilities than a Network Load Balancer.<br>Sticky sessions are crucial for maintaining a consistent user experience with a stateful application, as they ensure that a user's session remains connected to the same EC2 instance throughout their session.<br>Round robin routing with the ALB will distribute incoming traffic evenly across the healthy EC2 instances in the Auto Scaling group, providing efficient load distribution.<br>Option A is less suitable because Network Load Balancers operate at the transport layer (TCP/UDP) and are typically used for extreme performance requirements rather than standard web applications. Additionally, NLBs don't natively support sticky sessions in the same way ALBs do, which is critical for this stateful application.<br>Sources<br>REL07-BP01 Use automation when obtaining or scaling resources - AWS Well-Architected Framework（https://docs.aws.amazon.com/wellarchitected/2023-10-03/framework/rel_adapt_to_changes_autoscale_adapt.html）<br>HA and automatic scaling for ASP.NET Web Forms applications on AWS - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/migration-asp-net-web-forms/ha-scaling.html）<br>Hyperscaling Aurora MySQL-Compatible to handle sudden traffic growth - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/hyperscale-aurora-mysql/introduction.html）<br>Replatforming backend databases - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/migration-replatforming-cots-applications/replatforming-backend-databases.html）<br>Navigating the Cloud: Joby Aviation’s PLM migration to AWS | AWS for Industries （https://aws.amazon.com/cn/blogs/industries/navigating-the-cloud-joby-aviations-plm-migration-to-aws/）<br>
</div>

</details>

    
# 5/529 

<div style="color:blue">single</div>
Question #5<br>A company uses a service to collect metadata from applications that the company hosts on premises. Consumer devices such as TVs and internet radios access the applications. Many older devices do not support certain HTTP headers and exhibit errors when these headers are present in responses. The company has configured an on-premises load balancer to remove the unsupported headers from responses sent to older devices, which the company identified by the User-Agent headers.<br>The company wants to migrate the service to AWS, adopt serverless technologies, and retain the ability to support older devices. The company has already migrated the applications into a set of AWS Lambda functions.<br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an Amazon CloudFront distribution for the metadata service. Create an Application Load Balancer (ALB). Configure the CloudFront distribution to forward requests to the ALB. Configure the ALB to invoke the correct Lambda function for each type of request. Create a CloudFront function to remove the problematic headers based on the value of the User-Agent header.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an Amazon API Gateway REST API for the metadata service. Configure API Gateway to invoke the correct Lambda function for each type of request. Modify the default gateway responses to remove the problematic headers based on the value of the User-Agent header.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an Amazon API Gateway HTTP API for the metadata service. Configure API Gateway to invoke the correct Lambda function for each type of request. Create a response mapping template to remove the problematic headers based on the value of the User-Agent. Associate the response data mapping with the HTTP API.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an Amazon CloudFront distribution for the metadata service. Create an Application Load Balancer (ALB). Configure the CloudFront distribution to forward requests to the ALB. Configure the ALB to invoke the correctLambda function for each type of request. Create a Lambda@Edge function that will remove the problematic headers in response to viewer requests based on the value of the User-Agent header.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
Question #5<br>A company uses a service to collect metadata from applications that the company hosts on premises. Consumer devices such as TVs and internet radios access the applications. Many older devices do not support certain HTTP headers and exhibit errors when these headers are present in responses. The company has configured an on-premises load balancer to remove the unsupported headers from responses sent to older devices, which the company identified by the User-Agent headers.<br>The company wants to migrate the service to AWS, adopt serverless technologies, and retain the ability to support older devices. The company has already migrated the applications into a set of AWS Lambda functions.<br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
The company needs to migrate its metadata service to AWS with the following requirements:<ol><li>Serverless Architecture: The company wants to adopt serverless technologies.</li><li>Backward Compatibility: Older consumer devices, which do not support certain HTTP headers, must still be supported.</li><li>Header Removal Logic: Specific HTTP headers, identified by the User-Agent, must be removed for compatibility with older devices.</li></ol><br>Options Analysis:<br><ul><li><br>A: Creating an Amazon CloudFront distribution and an Application Load Balancer (ALB) allows requests to be routed efficiently. CloudFront can remove the problematic HTTP headers using a CloudFront function based on the User-Agent value. The ALB can invoke the appropriate Lambda function for request processing. This solution aligns well with the requirements and involves minimal effort.<br></li><li><br>B: Using an API Gateway REST API and configuring the gateway to handle header removal introduces unnecessary complexity. While functional, it requires creating additional mapping templates or modifying responses, which adds operational overhead compared to the simplicity of CloudFront and ALB.<br></li><li><br>C: Using an API Gateway HTTP API to remove headers requires managing response mapping templates and associating them with the HTTP API. Similar to option B, this adds complexity and operational effort.<br></li><li><br>D: Using a Lambda@Edge function with a CloudFront distribution is a viable alternative but adds latency since Lambda@Edge executes at the edge locations. This may impact performance compared to CloudFront functions, which are natively integrated and faster for lightweight tasks like header removal.<br></li></ul><br>Key Benefits of Option A:<br><ul><li>Seamless Header Removal: CloudFront functions provide a lightweight mechanism to remove headers based on the User-Agent value.</li><li>Efficient Routing: The ALB efficiently routes requests to the correct Lambda function for processing.</li><li>Serverless Design: Fully aligns with the serverless architecture requirement while ensuring backward compatibility.</li></ul><br>Thus, Option A is the correct answer.<br>
</div>

</details>

    
# 6/529 

<div style="color:blue">multiple</div>
Question #6<br>A retail company needs to provide a series of data files to another company, which is its business partner. These files are saved in an Amazon S3 bucket under Account A, which belongs to the retail company. The business partner company wants one of its IAM users, User_DataProcessor, to access the files from its own AWS account (Account B).<br>Which combination of steps must the companies take so that User_DataProcessor can access the S3 bucket successfully? (Choose two.)<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Turn on the cross-origin resource sharing (CORS) feature for the S3 bucket in Account A.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. In Account A, set the S3 bucket policy to the following:<img src="https://up.zaixiankaoshi.com/5240831/question/a50bde88faf8026d7abc938bbabf8a97.png" >
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. In Account A, set the S3 bucket policy to the following:<img src="https://up.zaixiankaoshi.com/5240831/question/8a5ede91bffcb9c102d86f43b5227388.png" >
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. In Account B, set the permissions of User_DataProcessor to the following:<img src="https://up.zaixiankaoshi.com/5240831/question/8a55bd151d9ade02c4061dbad2c228e2.png" >
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. &nbsp;In Account B, set the permissions of User_DataProcessor to the following:<img src="https://up.zaixiankaoshi.com/5240831/question/497534486bef4b408b0c29a37896d52e.png" >
</div>
        
<details>

<summary>English</summary>

<div translate="no">
Question #6<br>A retail company needs to provide a series of data files to another company, which is its business partner. These files are saved in an Amazon S3 bucket under Account A, which belongs to the retail company. The business partner company wants one of its IAM users, User_DataProcessor, to access the files from its own AWS account (Account B).<br>Which combination of steps must the companies take so that User_DataProcessor can access the S3 bucket successfully? (Choose two.)<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">CD</span>
To allow User_DataProcessor to access the S3 bucket from Account B, the following steps need to be taken: <br>In Account A, set the S3 bucket policy to allow access to the bucket from the IAM user in Account B. This is done by adding a statement to the <br>bucket policy that allows the IAM user in Account B to perform the necessary actions (GetObject and ListBucket) on the bucket and its contents. <br>In Account B, create an IAM policy that allows the IAM user (User_DataProcessor) to perform the necessary actions (GetObject and ListBucket) on <br>the S3 bucket and its contents. The policy should reference the ARN of the S3 bucket and the actions that the user is allowed to perform. <br>Note: turning on the cross-origin resource sharing (CORS) feature for the S3 bucket in Account A is not necessary for this scenario as it is typically <br>used for allowing web browsers to access resources from different domains. <br><br><br>此题具有一定的争议，可自行确认。建议C&amp;D<br>
</div>

</details>

    
# 7/529 

<div style="color:blue">single</div>
<br>Question #7<br>A company is running a traditional web application on Amazon EC2 instances. The company needs to refactor the application as microservices that run on containers. Separate versions of the application exist in two distinct environments: production and testing. Load for the application is variable, but the minimum load and the maximum load are known. A solutions architect needs to design the updated application with a serverless architecture that minimizes operational complexity.<br>Which solution will meet these requirements MOST cost-effectively?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Upload the container images to AWS Lambda as functions. Configure a concurrency limit for the associated Lambda functions to handle the expected peak load. Configure two separate Lambda integrations within Amazon API Gateway: one for production and one for testing.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Upload the container images to Amazon Elastic Container Registry (Amazon ECR). Configure two auto scaled Amazon Elastic Container Service (Amazon ECS) clusters with the Fargate launch type to handle the expected load. Deploy tasks from the ECR images. Configure two separate Application Load Balancers to direct traffic to the ECS clusters.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Upload the container images to Amazon Elastic Container Registry (Amazon ECR). Configure two auto scaled Amazon Elastic Kubernetes Service (Amazon EKS) clusters with the Fargate launch type to handle the expected load. Deploy tasks from the ECR images. Configure two separate Application Load Balancers to direct traffic to the EKS clusters.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Upload the container images to AWS Elastic Beanstalk. In Elastic Beanstalk, create separate environments and deployments for production and testing. Configure two separate Application Load Balancers to direct traffic to the Elastic Beanstalk deployments.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #7<br>A company is running a traditional web application on Amazon EC2 instances. The company needs to refactor the application as microservices that run on containers. Separate versions of the application exist in two distinct environments: production and testing. Load for the application is variable, but the minimum load and the maximum load are known. A solutions architect needs to design the updated application with a serverless architecture that minimizes operational complexity.<br>Which solution will meet these requirements MOST cost-effectively?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Themost cost-effective solution that meets the requirements (minimizing operational complexity while supporting variable load with microservices in containers) is: &nbsp;<br>Option B &nbsp;<br>Upload the container images to Amazon Elastic Container Registry (Amazon ECR). Configure two auto-scaled Amazon Elastic Container Service (Amazon ECS) clusters with the Fargate launch type to handle the expected load. Deploy tasks from the ECR images. Configure two separate Application Load Balancers to direct traffic to the ECS clusters. &nbsp;<br>#Why Option B? &nbsp;<br>1.Serverless & Low Operational Overhead: &nbsp;<br> &nbsp; -ECS with Fargate is serverless, eliminating the need to manage EC2 instances. &nbsp;<br> &nbsp; - Auto-scaling ensures cost efficiency by adjusting to variable load. &nbsp;<br>2.Container Support: &nbsp;<br> &nbsp; - ECR stores container images, and ECS deploys them seamlessly. &nbsp;<br>3.Separate Environments: &nbsp;<br> &nbsp; - Two distinct ECS clusters (production & testing) ensure isolation. &nbsp;<br> &nbsp; - Application Load Balancers (ALBs) route traffic appropriately. &nbsp;<br>4.Cost-Effectiveness: &nbsp;<br> &nbsp; - Fargate scales automatically, avoiding over-provisioning. &nbsp;<br> &nbsp; - No Kubernetes overhead (unlike EKS in Option C). &nbsp;<br>#Why Not Other Options? &nbsp;<br>-Option A (Lambda with containers): Lambda is not ideal for long-running microservices (cold starts, concurrency limits). &nbsp;<br>-Option C (EKS with Fargate): EKS introduces unnecessary Kubernetes complexity for this use case. &nbsp;<br>-Option D (Elastic Beanstalk): Not fully serverless, and less suited for microservices compared to ECS Fargate. &nbsp;<br>Conclusion:Option B provides the best balance of cost efficiency, scalability, and operational simplicity. ✅<br><br><br>ref:https://www.densify.com/eks-best-practices/aws-ecs-vs-eks/<br>
</div>

</details>

    
# 8/529 

<div style="color:blue">single</div>
<br>Question #8<br>A company has a multi-tier web application that runs on a fleet of Amazon EC2 instances behind an Application Load Balancer (ALB). The instances are in an Auto Scaling group. The ALB and the Auto Scaling group are replicated in a backup AWS Region. The minimum value and the maximum value for the Auto Scaling group are set to zero. An Amazon RDS Multi-AZ DB instance stores the application’s data. The DB instance has a read replica in the backup Region. The application presents an endpoint to end users by using an Amazon Route 53 record.<br>The company needs to reduce its RTO to less than 15 minutes by giving the application the ability to automatically fail over to the backup Region.The company does not have a large enough budget for an active-active strategy. <br>What should a solutions architect recommend to meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Reconfigure the application&rsquo;s Route 53 record with a latency-based routing policy that load balances traffic between the two ALBs. Create an AWS Lambda function in the backup Region to promote the read replica and modify the Auto Scaling group values. Create an Amazon CloudWatch alarm that is based on the HTTPCode_Target_5XX_Count metric for the ALB in the primary Region. Configure the CloudWatch alarm to invoke the Lambda function.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. &nbsp;Create an AWS Lambda function in the backup Region to promote the read replica and modify the Auto Scaling group values. Configure Route 53 with a health check that monitors the web application and sends an Amazon Simple Notification Service (Amazon SNS) notification to the Lambda function when the health check status is unhealthy. Update the application&rsquo;s Route 53 record with a failover policy that routes traffic to the ALB in the backup Region when a health check failure occurs.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Configure the Auto Scaling group in the backup Region to have the same values as the Auto Scaling group in the primary Region. Reconfigure the application&rsquo;s Route 53 record with a latency-based routing policy that load balances traffic between the two ALBs. Remove the read replica. Replace the read replica with a standalone RDS DB instance. Configure Cross-Region Replication between the RDS DB instances by using snapshots and Amazon S3.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Configure an endpoint in AWS Global Accelerator with the two ALBs as equal weighted targets. Create an AWS Lambda function in the backup Region to promote the read replica and modify the Auto Scaling group values. Create an Amazon CloudWatch alarm that is based on the HTTPCode_Target_5XX_Count metric for the ALB in the primary Region. Configure the CloudWatch alarm to invoke the Lambda function.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #8<br>A company has a multi-tier web application that runs on a fleet of Amazon EC2 instances behind an Application Load Balancer (ALB). The instances are in an Auto Scaling group. The ALB and the Auto Scaling group are replicated in a backup AWS Region. The minimum value and the maximum value for the Auto Scaling group are set to zero. An Amazon RDS Multi-AZ DB instance stores the application’s data. The DB instance has a read replica in the backup Region. The application presents an endpoint to end users by using an Amazon Route 53 record.<br>The company needs to reduce its RTO to less than 15 minutes by giving the application the ability to automatically fail over to the backup Region.The company does not have a large enough budget for an active-active strategy. <br>What should a solutions architect recommend to meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>To reduce the RTO to less than 15 minutes and enable automatic failover to the backup Region, the solution recommended in option B should be implemented. By creating an AWS Lambda function in the backup Region to promote the read replica and modify the Auto Scaling group values, the company can ensure that the backup Region is ready to take over in case of a failure. Configuring Route 53 with a health check that monitors the web application and triggers the Lambda function when the health check status is unhealthy allows for immediate action in the event of a failure. Updating the Route 53 record with a failover policy ensures that traffic is automatically routed to the ALB in the backup Region when the health check fails, facilitating a quick recovery.<br>The correct answer isB. Here's why:<br>Requirements:<br>1.Reduce RTO to &lt;15 minutes with automatic failover to the backup Region.<br>2.No active-active strategy (due to budget constraints).<br>3. Current setup:<br> &nbsp; - Multi-tier web app on EC2 (Auto Scaling + ALB) in primary Region.<br> &nbsp; - Backup Region has ALB + Auto Scaling (min/max = 0).<br> &nbsp; - RDS Multi-AZ in primary Region + read replica in backup Region.<br> &nbsp; - Route 53 manages the application endpoint.<br>Why Option B?<br>-Route 53 Failover Routing Policy: This is the most cost-effective way to automate failover. Route 53 can monitor the health of the primary Region and switch traffic to the backup Region when unhealthy.<br>-Lambda Function: Promotes the RDS read replica to a standalone instance and modifies the Auto Scaling group in the backup Region (scaling from 0 to desired capacity).<br>-Health Check + SNS: Route 53 health checks can trigger the Lambda function via SNS when the primary Region fails.<br>-Meets RTO Requirement: The combination of Route 53 failover and Lambda automation ensures fast recovery (&lt;15 minutes).<br>Why Not Other Options?<br>-A: Latency-based routing doesn’t provide failover; CloudWatch alarms alone don’t ensure Route 53 traffic redirection.<br>-C: Active-active setup (latency routing + equal Auto Scaling) is expensive and against budget constraints. Cross-Region replication via snapshots is slow.<br>-D: Global Accelerator improves performance but doesn’t inherently handle database failover or Auto Scaling adjustments.<br>Conclusion:<br>B is the most cost-effective and automated solution for achieving&lt;15-minute RTO withpassive standby in the backup Region. &nbsp;<br>Answer: B<br>ref:https://docs.amazonaws.cn/en_us/Route53/latest/DeveloperGuide/welcome-health-checks.html &nbsp;and https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-types.html<br>
</div>

</details>

    
# 9/529 

<div style="color:blue">multiple</div>
<br>Question #9<br>A company is hosting a critical application on a single Amazon EC2 instance. The application uses an Amazon ElastiCache for Redis single-node cluster for an in-memory data store. The application uses an Amazon RDS for MariaDB DB instance for a relational database. For the application to function, each piece of the infrastructure must be healthy and must be in an active state.<br>A solutions architect needs to improve the application's architecture so that the infrastructure can automatically recover from failure with the least possible downtime.<br><br><br>Which combination of steps will meet these requirements? (Choose three.)<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Use an Elastic Load Balancer to distribute traffic across multiple EC2 instances. Ensure that the EC2 instances are part of an Auto Scaling group that has a minimum capacity of two instances.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use an Elastic Load Balancer to distribute traffic across multiple EC2 instances. Ensure that the EC2 instances are configured in unlimited mode.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Modify the DB instance to create a read replica in the same Availability Zone. Promote the read replica to be the primary DB instance in failure scenarios.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Modify the DB instance to create a Multi-AZ deployment that extends across two Availability Zones.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Create a replication group for the ElastiCache for Redis cluster. Configure the cluster to use an Auto Scaling group that has a minimum capacity of two instances.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
F. Create a replication group for the ElastiCache for Redis cluster. Enable Multi-AZ on the cluster.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #9<br>A company is hosting a critical application on a single Amazon EC2 instance. The application uses an Amazon ElastiCache for Redis single-node cluster for an in-memory data store. The application uses an Amazon RDS for MariaDB DB instance for a relational database. For the application to function, each piece of the infrastructure must be healthy and must be in an active state.<br>A solutions architect needs to improve the application's architecture so that the infrastructure can automatically recover from failure with the least possible downtime.<br><br><br>Which combination of steps will meet these requirements? (Choose three.)<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">ADF</span>
<br>The correct combination of steps to improve the application's architecture for automatic recovery from failure with minimal downtime is:<br>A,D, andF. &nbsp;<br> Explanation: &nbsp;<br>1.A – Using anElastic Load Balancer (ELB) with anAuto Scaling group (minimum of two instances) ensures high availability for the EC2 instances. If one instance fails, the other can continue serving traffic, and Auto Scaling will replace the failed instance. &nbsp;<br>2.D – Modifying theRDS for MariaDB to a Multi-AZ deployment ensures automatic failover to a standby replica in another Availability Zone if the primary DB instance fails, minimizing downtime. &nbsp;<br>3.F – Creating areplication group for ElastiCache for Redis with Multi-AZ enabled ensures high availability by maintaining a standby replica in a different Availability Zone, allowing automatic failover if the primary node fails. &nbsp;<br> Why not the others? &nbsp;<br>-B – "Unlimited mode" for EC2 instances is not relevant to high availability. &nbsp;<br>-C – A read replica in thesame AZ does not provide automatic failover (Multi-AZ does). &nbsp;<br>-E – ElastiCache does not use Auto Scaling groups; instead, it usesreplication groups with Multi-AZ. &nbsp;<br>Thus, the best combination isA, D, and F. ✅<br><br><br>
</div>

</details>

    
# 10/529 

<div style="color:blue">multiple</div>
<br>Question #10<br>A retail company is operating its ecommerce application on AWS. The application runs on Amazon EC2 instances behind an Application Load Balancer (ALB). The company uses an Amazon RDS DB instance as the database backend. Amazon CloudFront is configured with one origin that points to the ALB. Static content is cached. Amazon Route 53 is used to host all public zones.<br>After an update of the application, the ALB occasionally returns a 502 status code (Bad Gateway) error. The root cause is malformed HTTP headers that are returned to the ALB. The webpage returns successfully when a solutions architect reloads the webpage immediately after the error occurs.<br>While the company is working on the problem, the solutions architect needs to provide a custom error page instead of the standard ALB error page to visitors.<br>Which combination of steps will meet this requirement with the LEAST amount of operational overhead? (Choose two.)<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an Amazon S3 bucket. Configure the S3 bucket to host a static webpage. Upload the custom error pages to Amazon S3.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an Amazon CloudWatch alarm to invoke an AWS Lambda function if the ALB health check response Target.FailedHealthChecks is greater than 0. Configure the Lambda function to modify the forwarding rule at the ALB to point to a publicly accessible web server.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Modify the existing Amazon Route 53 records by adding health checks. Configure a fallback target if the health check fails. Modify DNS records to point to a publicly accessible webpage.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an Amazon CloudWatch alarm to invoke an AWS Lambda function if the ALB health check response Elb.InternalError is greater than 0. Configure the Lambda function to modify the forwarding rule at the ALB to point to a public accessible web server.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. &nbsp;Add a custom error response by confi guring a CloudFront custom error page. Modify DNS records to point to a publicly accessible web page.&nbsp;
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #10<br>A retail company is operating its ecommerce application on AWS. The application runs on Amazon EC2 instances behind an Application Load Balancer (ALB). The company uses an Amazon RDS DB instance as the database backend. Amazon CloudFront is configured with one origin that points to the ALB. Static content is cached. Amazon Route 53 is used to host all public zones.<br>After an update of the application, the ALB occasionally returns a 502 status code (Bad Gateway) error. The root cause is malformed HTTP headers that are returned to the ALB. The webpage returns successfully when a solutions architect reloads the webpage immediately after the error occurs.<br>While the company is working on the problem, the solutions architect needs to provide a custom error page instead of the standard ALB error page to visitors.<br>Which combination of steps will meet this requirement with the LEAST amount of operational overhead? (Choose two.)<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">AE</span>
<br>To provide a custom error page with the least amount of operational overhead, the solutions architect should create an Amazon S3 bucket to host a static webpage with the custom error pages (option A) and configure Amazon CloudFront to use those custom error pages (option E). This approach allows for a quick and straightforward implementation without the need to modify the underlying infrastructure or manage additional services like AWS Lambda or Route 53 health checks. The custom error pages can be easily updated and maintained in the S3 bucket, and CloudFront can be quickly reconfigured to point to the new error pages, minimizing the impact on the ongoing operations.<br>The correct answers areA andE. &nbsp;<br>Explanation: &nbsp;<br>The requirement is todisplay a custom error page when the ALB returns a502 error (Bad Gateway) due to malformed HTTP headers, with theleast operational overhead. &nbsp;<br>#Option A: &nbsp;<br>-Create an S3 bucket to host a static custom error page. &nbsp;<br>- This is a simple and cost-effective way to serve a static error page without additional infrastructure. &nbsp;<br>#Option E: &nbsp;<br>-Configure CloudFront to return a custom error page when a 502 error occurs. &nbsp;<br>- Since CloudFront is already in front of the ALB, this is the most straightforward solution. CloudFront allows you to definecustom error pages for specific HTTP status codes (like 502) and point them to an S3 bucket or another origin. &nbsp;<br>Why not the other options? &nbsp;<br>-B & D: Using Lambda to modify ALB rules introduces unnecessary complexity and operational overhead. &nbsp;<br>-C: Modifying Route 53 health checks and DNS records is not ideal because it would require switching traffic away from the application entirely, which is overkill for handling transient 502 errors. &nbsp;<br>Best Solution: &nbsp;<br>1.Upload a custom error page to S3 (A). &nbsp;<br>2.Configure CloudFront to serve this custom error page when a 502 occurs (E). &nbsp;<br>This approach isserverless, low-maintenance, and leverages existing AWS services (CloudFront + S3) without requiring additional infrastructure changes. &nbsp;<br>Final Answer:A & E<br>
</div>

</details>

    
# 11/529 

<div style="color:blue">multiple</div>
<br>Question #11<br>A company has many AWS accounts and uses AWS Organizations to manage them. A solutions architect must implement a solution that the company can use to share a common network across multiple accounts.<br><br><br>The company’s infrastructure team has a dedicated infrastructure account that has a VPC. The infrastructure team must use this account to manage the network. Individual accounts cannot have the ability to manage their own networks. However, individual accounts must be able to create AWS resources within subnets.<br><br>Which combination of actions should the solutions architect perform to meet these requirements? (Choose two.) <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create a transit gateway in the infrastructure account.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Enable resource sharing from the AWS Organizations management account.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create VPCs in each AWS account within the organization in AWS Organizations. Configure the VPCs to share the same CIDR range and subnets as the VPC in the infrastructure account. Peer the VPCs in each individual account with the VPC in the infrastructure account.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create a resource share in AWS Resource Access Manager in the infrastructure account. Select the specific AWS Organizations OU that will use the shared network. Select each subnet to associate with the resource share.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Create a resource share in AWS Resource Access Manager in the infrastructure account. Select the specific AWS Organizations OU that will use the shared network. Select each prefix list to associate with the resource share.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #11<br>A company has many AWS accounts and uses AWS Organizations to manage them. A solutions architect must implement a solution that the company can use to share a common network across multiple accounts.<br><br><br>The company’s infrastructure team has a dedicated infrastructure account that has a VPC. The infrastructure team must use this account to manage the network. Individual accounts cannot have the ability to manage their own networks. However, individual accounts must be able to create AWS resources within subnets.<br><br>Which combination of actions should the solutions architect perform to meet these requirements? (Choose two.) <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">BD</span>
<br>Based on the information provided, to implement a solution for sharing a common network across multiple AWS accounts while ensuring the infrastructure team maintains control of the network management, the following two actions should be taken:<br>B. Enable resource sharing from the AWS Organizations management account.<br>D. Create a resource share in AWS Resource Access Manager in the infrastructure account. Select the specific AWS Organizations OU that will use the shared network. Select each subnet to associate with the resource share.<br>This combination works because:<br>First, you need to enable resource sharing at the AWS Organizations level (option B). This is a prerequisite step that must be performed in the management account of the organization before any resources can be shared between accounts.<br>Then, in the infrastructure account that owns the VPC, you need to create a resource share using AWS Resource Access Manager (RAM) and specify which organizational units (OUs) should have access to the shared network resources (option D). By selecting specific subnets to associate with the resource share, you're allowing the individual accounts to create resources within those subnets while maintaining network management control in the infrastructure account.<br>This approach satisfies all requirements:<br>The infrastructure team maintains control of network management through their dedicated account<br>Individual accounts cannot manage the network themselves<br>Individual accounts can create AWS resources within the shared subnets<br>The common network is shared across multiple accounts in the organization<br>The other options would either not fulfill all requirements or implement the sharing incorrectly.<br>Sources<br>Shareable AWS resources - AWS Resource Access Manager （https://docs.aws.amazon.com/ram/latest/userguide/shareable.html）<br>SEC03-BP08 Share resources securely - AWS Well-Architected Framework (2022-03-31) （https://docs.aws.amazon.com/wellarchitected/2022-03-31/framework/sec_permissions_share_securely.html）<br>Share your VPC subnets with other accounts - Amazon Virtual Private Cloud （https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html）<br>SEC03-BP08 Share resources securely within your organization - AWS Well-Architected Framework （https://docs.aws.amazon.com/wellarchitected/latest/framework/sec_permissions_share_securely.html）<br>VPC sharing - Building a Scalable and Secure Multi-VPC AWS Network Infrastructure （https://docs.aws.amazon.com/whitepapers/latest/building-scalable-secure-multi-vpc-network-infrastructure/amazon-vpc-sharing.html）<br>
</div>

</details>

    
# 12/529 

<div style="color:blue">single</div>
<br>Question #12<br>A company wants to use a third-party software-as-a-service (SaaS) application. The third-party SaaS application is consumed through several API calls. The third-party SaaS application also runs on AWS inside a VPC.<br>The company will consume the third-party SaaS application from inside a VPC. The company has internal security policies that mandate the use of private connectivity that does not traverse the internet. No resources that run in the company VPC are allowed to be accessed from outside the company’s VPC. All permissions must conform to the principles of least privilege.<br>Which solution meets these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an AWS PrivateLink interface VPC endpoint. Connect this endpoint to the endpoint service that the third-party SaaS application provides. Create a security group to limit the access to the endpoint. Associate the security group with the endpoint.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an AWS Site-to-Site VPN connection between the third-party SaaS application and the company VPC. Configure network ACLs to limit access across the VPN tunnels.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create a VPC peering connection between the third-party SaaS application and the company VPUpdate route tables by adding the needed routes for the peering connection.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an AWS PrivateLink endpoint service. Ask the third-party SaaS provider to create an interface VPC endpoint for this endpoint service. Grant permissions for the endpoint service to the specific account of the third-party SaaS provider.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #12<br>A company wants to use a third-party software-as-a-service (SaaS) application. The third-party SaaS application is consumed through several API calls. The third-party SaaS application also runs on AWS inside a VPC.<br>The company will consume the third-party SaaS application from inside a VPC. The company has internal security policies that mandate the use of private connectivity that does not traverse the internet. No resources that run in the company VPC are allowed to be accessed from outside the company’s VPC. All permissions must conform to the principles of least privilege.<br>Which solution meets these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>The correct answer isA. Here's why:<br>Requirements Summary:<br>1.Private connectivity (no internet traversal).<br>2.No inbound access from outside the company’s VPC.<br>3.Least privilege permissions must be enforced.<br>Why Option A is Correct:<br>-AWS PrivateLink (Interface VPC Endpoint) allows private connectivity between the company’s VPC and the third-party SaaS applicationwithout traversing the internet.<br>- The company creates aninterface VPC endpoint in its own VPC and connects it to the SaaS provider’sendpoint service.<br>-Security groups can restrict access to only the necessary resources, enforcing least privilege.<br>-No inbound access is allowed from outside the company’s VPC (meets security policy).<br>Why Other Options Are Incorrect:<br>-B. Site-to-Site VPN: &nbsp;<br> &nbsp;- Traffic still traverses an encrypted VPN over the internet (does not fully meet "no internet traversal" requirement). &nbsp;<br> &nbsp;- Network ACLs are less granular than security groups for least privilege.<br>-C. VPC Peering: &nbsp;<br> &nbsp;- Requires routing configuration that could inadvertently allow unwanted access. &nbsp;<br> &nbsp;- Peering does not inherently enforce least privilege as strictly as PrivateLink. &nbsp;<br> &nbsp;- SaaS provider’s VPC and company VPC must be in the same region (not always feasible).<br>-D. PrivateLink Endpoint Service (Incorrect Direction): &nbsp;<br> &nbsp;- This would allow the SaaS provider to initiate connections into the company’s VPC (violates "no inbound access" policy). &nbsp;<br> &nbsp;- The company should be the consumer, not the provider, of the endpoint service.<br>Conclusion: &nbsp;<br>Option A is the only solution that fully meets the requirements of private connectivity, no internet traversal, no inbound access, and least privilege. &nbsp;<br>Answer: A<br>ref: https://docs.aws.amazon.com/vpc/latest/privatelink/privatelink-access-saas.html <br><br><br>- The interface VPC Endpoint will provide local access to the SaaS service from within the company's VPC. Moreover, traffic to and acces from the SaaS VPC will traverse the AWS network rather than the internet. This is considered private traffic . ref:<br>https://docs.aws.amazon.com/vpc/latest/privatelink/privatelink-access-saas.html https://aws.amazon.com/blogs/apn/enabling-new-saas-strategies-with-aws-privatelink/ &nbsp;<br>
</div>

</details>

    
# 13/529 

<div style="color:blue">single</div>
<br>Question #13<br>A company needs to implement a patching process for its servers. The on-premises servers and Amazon EC2 instances use a variety of tools to perform patching. Management requires a single report showing the patch status of all the servers and instances.<br><br>Which set of actions should a solutions architect take to meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Use AWS Systems Manager to manage patches on the on-premises servers and EC2 instances. Use Systems Manager to generate patch compliance reports.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use AWS OpsWorks to manage patches on the on-premises servers and EC2 instances. Use Amazon QuickSight integration with OpsWorks to generate patch compliance reports.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Use an Amazon EventBridge rule to apply patches by scheduling an AWS Systems Manager patch remediation job. Use Amazon Inspector to generate patch compliance reports.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use AWS OpsWorks to manage patches on the on-premises servers and EC2 instances. Use AWS X-Ray to post the patch status to AWS Systems Manager OpsCenter to generate patch compliance reports.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #13<br>A company needs to implement a patching process for its servers. The on-premises servers and Amazon EC2 instances use a variety of tools to perform patching. Management requires a single report showing the patch status of all the servers and instances.<br><br>Which set of actions should a solutions architect take to meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>Based on the information provided, the best answer for implementing a patching process with unified reporting across on-premises servers and EC2 instances is:<br>A. Use AWS Systems Manager to manage patches on the on-premises servers and EC2 instances. Use Systems Manager to generate patch compliance reports.<br>This is the correct approach because:<br>AWS Systems Manager is specifically designed to manage both on-premises servers and EC2 instances through the Systems Manager Agent (SSM Agent), which can be installed on both types of environments.<br>Systems Manager Patch Manager provides a unified patching solution that works across different operating systems and environments, addressing the company's need to consolidate their variety of patching tools.<br>Systems Manager includes built-in patch compliance reporting capabilities that can generate a single comprehensive report showing the patch status of all servers and instances, which directly fulfills the management requirement.<br>Option B is incorrect because AWS OpsWorks is primarily a configuration management service that uses Chef or Puppet, and while it can help with some aspects of server management, it's not specifically designed for cross-platform patching with unified reporting.<br>Option C is incomplete because while Amazon EventBridge can schedule Systems Manager patch jobs, Amazon Inspector is focused on vulnerability assessment rather than providing comprehensive patch compliance reporting across both on-premises and EC2 environments.<br>AWS Systems Manager (Option A) provides the most comprehensive and purpose-built solution for this specific requirement.<br>Sources<br>Increase visibility and governance on cloud with AWS Cloud Operations services – Part 2 | AWS Cloud Operations & Migrations Blog （https://aws.amazon.com/cn/blogs/mt/increase-visibility-and-governance-aws-cloud-operations-part-2/）<br>AWS Systems Manager Patch Manager - AWS Systems Manager （https://docs.aws.amazon.com/systems-manager/latest/userguide/patch-manager.html）<br>Getting Started with Patch Manager and Amazon EC2 Systems Manager | AWS Cloud Operations & Migrations Blog （https://aws.amazon.com/cn/blogs/mt/getting-started-with-patch-manager-and-amazon-ec2-systems-manager/）<br>Automate Systems Manager patching reports via email and Slack notifications in an AWS Organization | AWS Cloud Operations Blog （https://aws.amazon.com/cn/blogs/mt/automate-systems-manager-patching-reports-via-email-and-slack-notifications-in-an-aws-organization/）<br>Patching solution design for mutable EC2 instances - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/patch-management-hybrid-cloud/design-standard.html）<br>
</div>

</details>

    
# 14/529 

<div style="color:blue">single</div>
<br>Question #14<br>A company is running an application on several Amazon EC2 instances in an Auto Scaling group behind an Application Load Balancer. The load on the application varies throughout the day, and EC2 instances are scaled in and out on a regular basis. Log files from the EC2 instances are copied to a central Amazon S3 bucket every 15 minutes. The security team discovers that log files are missing from some of the terminated EC2 instances.<br><br>Which set of actions will ensure that log files are copied to the central S3 bucket from the terminated EC2 instances?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create a script to copy log files to Amazon S3, and store the script in a file on the EC2 instance. Create an Auto Scaling lifecycle hook and an Amazon EventBridge rule to detect lifecycle events from the Auto Scaling group. Invoke an AWS Lambda function on the autoscaling:EC2_INSTANCE_TERMINATING transition to send ABANDON to the Auto Scaling group to prevent termination, run the script to copy the log files, and terminate the instance using the AWS SDK.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an AWS Systems Manager document with a script to copy log files to Amazon S3. Create an Auto Scaling lifecycle hook and an Amazon EventBridge rule to detect lifecycle events from the Auto Scaling group. Invoke an AWS Lambda function on the autoscaling:EC2_INSTANCE_TERMINATING transition to call the AWS Systems Manager API SendCommand operation to run the document to copy the log files and send CONTINUE to the Auto Scaling group to terminate the instance.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Change the log delivery rate to every 5 minutes. Create a script to copy log files to Amazon S3, and add the script to EC2 instance user data. Create an Amazon EventBridge rule to detect EC2 instance termination. Invoke an AWS Lambda function from the EventBridge rule that uses the AWS CLI to run the user-data script to copy the log files and terminate the instance.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an AWS Systems Manager document with a script to copy log files to Amazon S3. Create an Auto Scaling lifecycle hook that publishes a message to an Amazon Simple Notification Service (Amazon SNS) topic. From the SNS notification, call the AWS Systems Manager API SendCommand operation to run the document to copy the log files and send ABANDON to the Auto Scaling group to terminate the instance.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #14<br>A company is running an application on several Amazon EC2 instances in an Auto Scaling group behind an Application Load Balancer. The load on the application varies throughout the day, and EC2 instances are scaled in and out on a regular basis. Log files from the EC2 instances are copied to a central Amazon S3 bucket every 15 minutes. The security team discovers that log files are missing from some of the terminated EC2 instances.<br><br>Which set of actions will ensure that log files are copied to the central S3 bucket from the terminated EC2 instances?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Option B is the correct solution as it uses an Auto Scaling lifecycle hook and an Amazon EventBridge rule to detect lifecycle events from the Auto Scaling group. An AWS Lambda function is then invoked on the autoscaling:EC2_INSTANCE_TERMINATING transition to call the AWS Systems Manager API SendCommand operation to run the document to copy the log files and send CONTINUE to the Auto Scaling group to terminate the instance. This ensures that log files are copied to S3 before the instance is terminated.<br>Problem Analysis:<br>- EC2 instances in an Auto Scaling group are terminated before log files are fully copied to S3.<br>- Logs are copied every 15 minutes, but some instances are terminated before the next sync.<br>- Need a mechanism to ensure logs are copiedbefore termination.<br>Why Option B is Correct:<br>1.Auto Scaling Lifecycle Hook: &nbsp;<br> &nbsp; - A lifecycle hook (`autoscaling:EC2_INSTANCE_TERMINATING`) pauses instance termination, allowing time to perform actions.<br>2.AWS Systems Manager (SSM) Document: &nbsp;<br> &nbsp; - Uses `SendCommand` to execute a predefined script (stored in SSM) to copy logs to S3.<br> &nbsp; - SSM ensures the script runs even if the instance is in the process of termination.<br>3.EventBridge + Lambda Integration: &nbsp;<br> &nbsp; - EventBridge detects the termination event.<br> &nbsp; - Lambda triggers the SSM `SendCommand` to copy logs.<br> &nbsp; - After completion, Lambda sends `CONTINUE` to Auto Scaling to proceed with termination.<br>Why Other Options Are Incorrect:<br>-A: Uses `ABANDON` instead of `CONTINUE`, which prevents Auto Scaling from terminating the instance, requiring manual termination (inefficient and error-prone).<br>-C: Changing the log delivery rate to 5 minutes doesn’t guarantee logs are copied before termination. Also, user-data scripts run at launch, not termination.<br>-D: Uses `ABANDON` (incorrect for this use case) and relies on SNS, which adds unnecessary complexity compared to EventBridge + Lambda.<br>Key AWS Services Used:<br>-Auto Scaling Lifecycle Hooks (to delay termination).<br>-AWS Systems Manager (SSM) (to reliably run commands on instances).<br>-Amazon EventBridge (to detect lifecycle events).<br>-AWS Lambda (to trigger SSM and resume termination).<br>Thus,B is the most reliable and automated solution. &nbsp;<br>Answer: B<br>https://aws.amazon.com/blogs/infrastructure-and-automation/run-code-before-terminating-an-ec2-auto-scaling-instance/ <br>https://www.examtopics.com/discussions/amazon/view/69532-exam-aws-certified-solutions-architect-professional-topic-1/ &nbsp;<br>
</div>

</details>

    
# 15/529 

<div style="color:blue">multiple</div>
<br>Question #15 <br>A company is using multiple AWS accounts. The DNS records are stored in a private hosted zone for Amazon Route 53 in Account A. The company’s applications and databases are running in Account B.<br><br><br>A solutions architect will deploy a two-tier application in a new VPC. To simplify the confi guration, the db.example.com CNAME record set for the Amazon RDS endpoint was created in a private hosted zone for Amazon Route 53. <br><br><br>During deployment, the application failed to start. Troubleshooting revealed that db.example.com is not resolvable on the Amazon EC2 instance. <br><br><br>The solutions architect confi rmed that the record set was created correctly in Route 53. <br><br><br>Which combination of steps should the solutions architect take to resolve this issue? (Choose two.) <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Deploy the database on a separate EC2 instance in the new VPC. Create a record set for the instance&rsquo;s private IP in the private hosted zone.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use SSH to connect to the application tier EC2 instance. Add an RDS endpoint IP address to the /etc/resolv.conf file.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an authorization to associate the private hosted zone in Account A with the new VPC in Account B.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create a private hosted zone for the example com domain in Account B. Configure Route 53 replication between AWS accounts.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Associate a new VPC in Account B with a hosted zone in Account A. Delete the association authorization in Account A.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #15 <br>A company is using multiple AWS accounts. The DNS records are stored in a private hosted zone for Amazon Route 53 in Account A. The company’s applications and databases are running in Account B.<br><br><br>A solutions architect will deploy a two-tier application in a new VPC. To simplify the confi guration, the db.example.com CNAME record set for the Amazon RDS endpoint was created in a private hosted zone for Amazon Route 53. <br><br><br>During deployment, the application failed to start. Troubleshooting revealed that db.example.com is not resolvable on the Amazon EC2 instance. <br><br><br>The solutions architect confi rmed that the record set was created correctly in Route 53. <br><br><br>Which combination of steps should the solutions architect take to resolve this issue? (Choose two.) <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">CE</span>
<br>The correct answers are:<br>C. Create an authorization to associate the private hosted zone in Account A with the new VPC in Account B. &nbsp;<br>E. Associate a new VPC in Account B with a hosted zone in Account A. Delete the association authorization in Account A.<br> Explanation:<br>1.Private Hosted Zone Sharing Across Accounts: &nbsp;<br> &nbsp; - The private hosted zone (`db.example.com`) is inAccount A, but the application and database inAccount B need to resolve this DNS record. &nbsp;<br> &nbsp; - To allowAccount B to resolve records fromAccount A's private hosted zone, you must: &nbsp;<br> &nbsp; &nbsp; -Authorize the association inAccount A (the hosted zone owner). &nbsp;<br> &nbsp; &nbsp; -Associate the VPC inAccount B with the hosted zone inAccount A. &nbsp;<br> &nbsp; - After the association is complete, the authorization can be deleted (optional but recommended for security). &nbsp;<br>2.Why Other Options Are Incorrect: &nbsp;<br> &nbsp; -A: Deploying the database on a separate EC2 instance is unnecessary—the issue is DNS resolution, not the database itself. &nbsp;<br> &nbsp; -B: Manually modifying `/etc/resolv.conf` is not a scalable or recommended solution. &nbsp;<br> &nbsp; -D: Creating a duplicate private hosted zone inAccount B and setting up replication is overly complex—cross-account VPC association is the correct approach. &nbsp;<br> Steps to Resolve:<br>1. InAccount A, authorizeAccount B's VPC to associate with the private hosted zone. &nbsp;<br>2. InAccount B, associate the VPC with the hosted zone. &nbsp;<br>3. (Optional) Delete the authorization inAccount A after association. &nbsp;<br>This ensures the EC2 instances inAccount B can resolve `db.example.com` via the shared private hosted zone. &nbsp;<br>Final Answer: C & E<br>
</div>

</details>

    
# 16/529 

<div style="color:blue">single</div>
<br>Question #16<br>A company used Amazon EC2 instances to deploy a web fleet to host a blog site. The EC2 instances are behind an Application Load Balancer (ALB) and are configured in an Auto Scaling group. The web application stores all blog content on an Amazon EFS volume.<br><br><br>The company recently added a feature for bloggers to add video to their posts, attracting 10 times the previous user traffic. At peak times of day, users report buffering and timeout issues while attempting to reach the site or watch videos.<br><br>Which is the MOST cost-effi cient and scalable deployment that will resolve the issues for users?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Reconfigure Amazon EFS to enable maximum I/O.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Update the blog site to use instance store volumes for storage. Copy the site contents to the volumes at launch and to Amazon S3 at shutdown.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Configure an Amazon CloudFront distribution. Point the distribution to an S3 bucket, and migrate the videos from EFS to Amazon S3.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Set up an Amazon CloudFront distribution for all site contents, and point the distribution at the ALB.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #16<br>A company used Amazon EC2 instances to deploy a web fleet to host a blog site. The EC2 instances are behind an Application Load Balancer (ALB) and are configured in an Auto Scaling group. The web application stores all blog content on an Amazon EFS volume.<br><br><br>The company recently added a feature for bloggers to add video to their posts, attracting 10 times the previous user traffic. At peak times of day, users report buffering and timeout issues while attempting to reach the site or watch videos.<br><br>Which is the MOST cost-effi cient and scalable deployment that will resolve the issues for users?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>Based on the information provided, the most cost-efficient and scalable deployment that will resolve the buffering and timeout issues for users is:<br>C. Configure an Amazon CloudFront distribution. Point the distribution to an S3 bucket, and migrate the videos from EFS to Amazon S3.<br>This solution is optimal because:<br>Video content delivery is the primary cause of the performance issues. CloudFront is a content delivery network (CDN) that caches content at edge locations worldwide, significantly reducing latency for video streaming.<br>Amazon S3 is designed for high-throughput storage and retrieval of objects like video files, making it much more suitable than EFS for this use case.<br>This approach offloads the video content delivery from the EC2 instances and EFS, allowing the web servers to focus on serving the blog's dynamic content.<br>CloudFront with S3 provides automatic scaling to handle the 10x increase in traffic without requiring manual intervention or complex configurations.<br>The pay-as-you-go pricing model of CloudFront and S3 is more cost-effective for serving video content compared to scaling up EC2 instances or upgrading EFS performance modes.<br>Option A (reconfiguring EFS for maximum I/O) would increase costs significantly without addressing the fundamental issue that EFS isn't optimized for serving video content to many simultaneous users.<br>Option B (using instance store volumes) would be complex to manage, wouldn't persist through instance terminations without additional work, and wouldn't solve the fundamental issue of efficiently delivering video content to users across different geographical locations.<br>Sources<br>Videos are lagging and too slow to load | AWS re:Post （https://repost.aws/questions/QUwi8VdIPqSCGjqnpuy0xf5w/videos-are-lagging-and-too-slow-to-load）<br>Video on demand and live streaming video with CloudFront - Amazon CloudFront （https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/on-demand-streaming-video.html）<br>Evolving the architecture with Amazon CloudFront - Hosting Static Websites on AWS （https://docs.aws.amazon.com/whitepapers/latest/build-static-websites-aws/evolving-the-architecture-with-amazon-cloudfront.html）<br>Seeking Cost Saving options For ALB with Autoscaling | AWS re:Post （https://repost.aws/questions/QUSbPCZMSxTaKYWC07NXryuQ/seeking-cost-saving-options-for-alb-with-autoscaling）<br><br><br>
</div>

</details>

    
# 17/529 

<div style="color:blue">single</div>
<br>Question #17<br>A company with global offices has a single 1 Gbps AWS Direct Connect connection to a single AWS Region. The company’s on-premises network uses the connection to communicate with the company’s resources in the AWS Cloud. The connection has a single private virtual interface that connects to a single VPC.<br><br><br>A solutions architect must implement a solution that adds a redundant Direct Connect connection in the same Region. The solution also must provide connectivity to other Regions through the same pair of Direct Connect connections as the company expands into other Regions. <br><br><br>Which solution meets these requirements? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Provision a Direct Connect gateway. Delete the existing private virtual interface from the existing connection. Create the second Direct Connect connection. Create a new private virtual interface on each connection, and connect both private virtual interfaces to the Direct Connect gateway. Connect the Direct Connect gateway to the single VPC.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Keep the existing private virtual interface. Create the second Direct Connect connection. Create a new private virtual interface on the new connection, and connect the new private virtual interface to the single VPC.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Keep the existing private virtual interface. Create the second Direct Connect connection. Create a new public virtual interface on the new connection, and connect the new public virtual interface to the single VPC.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Provision a transit gateway. Delete the existing private virtual interface from the existing connection. Create the second Direct Connect connection. Create a new private virtual interface on each connection, and connect both private virtual interfaces to the transit gateway. Associate the transit gateway with the single VPC.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #17<br>A company with global offices has a single 1 Gbps AWS Direct Connect connection to a single AWS Region. The company’s on-premises network uses the connection to communicate with the company’s resources in the AWS Cloud. The connection has a single private virtual interface that connects to a single VPC.<br><br><br>A solutions architect must implement a solution that adds a redundant Direct Connect connection in the same Region. The solution also must provide connectivity to other Regions through the same pair of Direct Connect connections as the company expands into other Regions. <br><br><br>Which solution meets these requirements? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>The correct answer isA. Here's why:<br> Requirements:<br>1.Add a redundant Direct Connect (DX) connection in the same Region – Ensures high availability.<br>2.Provide connectivity to other Regions through the same pair of DX connections – Requires a solution that allows cross-Region connectivity.<br>3.Use the same pair of DX connections as the company expands – Avoids needing additional DX connections for future Regions.<br> Why Option A is Correct:<br>-Direct Connect Gateway (DX Gateway) allows you to connect multiple VPCs (including those in other Regions) to an on-premises network over a single or redundant DX connection.<br>- Steps in Option A:<br> &nbsp;1.Provision a DX Gateway – This enables multi-Region connectivity.<br> &nbsp;2.Delete the existing private VIF – Prepares for a new configuration.<br> &nbsp;3.Create a second DX connection – Provides redundancy.<br> &nbsp;4.Create a new private VIF on each connection and attach them to the DX Gateway – Ensures both connections are used.<br> &nbsp;5.Connect the DX Gateway to the single VPC – Maintains current connectivity while enabling future expansion.<br>-Benefits:<br> &nbsp;-Redundancy: Two DX connections in the same Region.<br> &nbsp;-Multi-Region Support: The DX Gateway allows future expansion to other Regions without additional DX connections.<br> Why Other Options Are Incorrect:<br>-Option B: Only connects the second DX to the same VPC. Doesnot support multi-Region connectivity.<br>-Option C: Uses apublic VIF, which is not suitable for private VPC connectivity (and does not address multi-Region needs).<br>-Option D: Uses aTransit Gateway, which can connect multiple VPCs but doesnot natively support cross-Region DX connectivity (unlike a DX Gateway).<br> Key Takeaway:<br>ADirect Connect Gateway is the correct solution because it enables bothredundancy andmulti-Region connectivity through the same pair of DX connections.<br>
</div>

</details>

    
# 18/529 

<div style="color:blue">single</div>
<br>Question #18<br>A company has a web application that allows users to upload short videos. The videos are stored on Amazon EBS volumes and analyzed by custom recognition software for categorization. The website contains static content that has variable traffic with peaks in certain months. The architecture consists of Amazon EC2 instances running in an Auto Scaling group for the web application and EC2 instances running in an Auto Scaling group to process an Amazon SQS queue.<br><br><br>The company wants to re-architect the application to reduce operational overhead using AWS managed services where possible and remove dependencies on third-party software. <br><br><br>Which solution meets these requirements? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Use Amazon ECS containers for the web application and Spot instances for the Auto Scaling group that processes the SQS queue. Replace the custom software with Amazon Rekognition to categorize the videos.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Store the uploaded videos in Amazon EFS and mount the file system to the EC2 instances for the web application. Process the SQS queue with an AWS Lambda function that calls the Amazon Rekognition API to categorize the videos.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Host the web application in Amazon S3. Store the uploaded videos in Amazon S3. Use S3 event notification to publish events to the SQS queue. Process the SQS queue with an AWS Lambda function that calls the Amazon Rekognition API to categorize the videos.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use AWS Elastic Beanstalk to launch EC2 instances in an Auto Scaling group for the web application and launch a worker environment to process the SQS queue. Replace the custom software with Amazon Rekognition to categorize the videos.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #18<br>A company has a web application that allows users to upload short videos. The videos are stored on Amazon EBS volumes and analyzed by custom recognition software for categorization. The website contains static content that has variable traffic with peaks in certain months. The architecture consists of Amazon EC2 instances running in an Auto Scaling group for the web application and EC2 instances running in an Auto Scaling group to process an Amazon SQS queue.<br><br><br>The company wants to re-architect the application to reduce operational overhead using AWS managed services where possible and remove dependencies on third-party software. <br><br><br>Which solution meets these requirements? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>The correct answer isC. Here's why it meets the requirements best:<br>Key Requirements:<br>1.Reduce operational overhead – Use managed services where possible.<br>2.Remove third-party software dependencies – Replace custom recognition software with AWS services.<br>3.Handle variable traffic efficiently – The solution should scale seamlessly.<br>4.Store and process videos effectively – Should leverage AWS services for storage and analysis.<br>Why Option C is Best:<br>-Host static web content in Amazon S3 – S3 is a fully managed, highly scalable service for static websites, reducing the need for EC2 instances.<br>-Store uploaded videos in Amazon S3 – More scalable and cost-effective than EBS or EFS for object storage.<br>-S3 Event Notifications + SQS Queue – When a video is uploaded, S3 can trigger an SQS message automatically.<br>-Lambda + Amazon Rekognition – Lambda is serverless (no EC2 management) and integrates seamlessly with Rekognition for video analysis.<br>-Fully managed services – Eliminates the need for maintaining EC2 instances for processing.<br>Why Other Options Are Less Optimal:<br>-A – Still uses EC2 (operational overhead) and Spot Instances (not fully managed).<br>-B – EFS is overkill for video storage (better for shared file systems) and still uses EC2 for the web app.<br>-D – Elastic Beanstalk still involves managing EC2 instances (not fully serverless).<br>Conclusion:<br>Option C is the most serverless, scalable, and operationally efficient solution, fully leveraging AWS managed services (S3, Lambda, Rekognition, SQS). &nbsp;<br>
</div>

</details>

    
# 19/529 

<div style="color:blue">single</div>
<br>Question #19<br>A company has a serverless application comprised of Amazon CloudFront, Amazon API Gateway, and AWS Lambda functions. The current deployment process of the application code is to create a new version number of the Lambda function and run an AWS CLI script to update. If the new function version has errors, another CLI script reverts by deploying the previous working version of the function. The company would like to decrease the time to deploy new versions of the application logic provided by the Lambda functions, and also reduce the time to detect and revert when errors are identified.<br><br>How can this be accomplished?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create and deploy nested AWS CloudFormation stacks with the parent stack consisting of the AWS CloudFront distribution and API Gateway, and the child stack containing the Lambda function. For changes to Lambda, create an AWS CloudFormation change set and deploy; if errors are triggered, revert the AWS CloudFormation change set to the previous version.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use AWS SAM and built-in AWS CodeDeploy to deploy the new Lambda version, gradually shift traffic to the new version, and use pre-traffic and post-traffic test functions to verify code. Rollback if Amazon CloudWatch alarms are triggered.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Refactor the AWS CLI scripts into a single script that deploys the new Lambda version. When deployment is completed, the script tests execute. If errors are detected, revert to the previous Lambda version.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create and deploy an AWS CloudFormation stack that consists of a new API Gateway endpoint that references the new Lambda version. Change the CloudFront origin to the new API Gateway endpoint, monitor errors and if detected, change the AWS CloudFront origin to the previous API Gateway endpoint.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #19<br>A company has a serverless application comprised of Amazon CloudFront, Amazon API Gateway, and AWS Lambda functions. The current deployment process of the application code is to create a new version number of the Lambda function and run an AWS CLI script to update. If the new function version has errors, another CLI script reverts by deploying the previous working version of the function. The company would like to decrease the time to deploy new versions of the application logic provided by the Lambda functions, and also reduce the time to detect and revert when errors are identified.<br><br>How can this be accomplished?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>The best answer to decrease the time to deploy new versions of the Lambda functions and reduce the time to detect and revert errors is:<br>B. Use AWS SAM and built-in AWS CodeDeploy to deploy the new Lambda version, gradually shift traffic to the new version, and use pre-traffic and post-traffic test functions to verify code. Rollback if Amazon CloudWatch alarms are triggered.<br> Explanation:<br>-AWS Serverless Application Model (SAM) simplifies the deployment of serverless applications (including Lambda, API Gateway, etc.).<br>-AWS CodeDeploy integration with SAM enablescanary or linear traffic shifting, allowing gradual rollout of new Lambda versions while monitoring for errors.<br>-Pre-traffic and post-traffic test functions can validate the new version before and after shifting traffic.<br>-Automated rollback occurs if CloudWatch alarms (e.g., error rates) are triggered, reducing downtime and manual intervention.<br>- This approach improves deployment speed (compared to CLI scripts) and provides better error detection and rollback mechanisms.<br> Why not the other options?<br>-A: While CloudFormation helps with infrastructure management, change sets are slower and less automated for Lambda deployments compared to SAM/CodeDeploy.<br>-C: Refactoring CLI scripts still requires manual testing and rollback, which is less efficient than automated traffic shifting and monitoring.<br>-D: Changing CloudFront origins and API Gateway endpoints is overly complex for Lambda version updates and introduces unnecessary overhead.<br>Thus,B is the most efficient and automated solution.<br>
</div>

</details>

    
# 20/529 

<div style="color:blue">single</div>
Question #20 <br>A company is planning to store a large number of archived documents and make the documents available to employees through the corporate intranet. Employees will access the system by connecting through a client VPN service that is attached to a VPC. The data must not be accessible to the public.<br><br>The documents that the company is storing are copies of data that is held on physical media elsewhere. The number of requests will be low. Availability and speed of retrieval are not concerns of the company.<br><br>Which solution will meet these requirements at the LOWEST cost?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an Amazon S3 bucket. Configure the S3 bucket to use the S3 One Zone-Infrequent Access (S3 One Zone-IA) storage class as default. Configure the S3 bucket for website hosting. Create an S3 interface endpoint. Configure the S3 bucket to allow access only through that endpoint.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. &nbsp;Launch an Amazon EC2 instance that runs a web server. Attach an Amazon Elastic File System (Amazon EFS) file system to store the archived data in the EFS One Zone-Infrequent Access (EFS One Zone-IA) storage class. Configure the instance security groups to allow access only from private networks.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Launch an Amazon EC2 instance that runs a web server. Attach an Amazon Elastic Block Store (Amazon EBS) volume to store the archived data. Use the Cold HDD (sc1) volume type. Configure the instance security groups to allow access only from private networks.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an Amazon S3 bucket. Configure the S3 bucket to use the S3 Glacier Deep Archive storage class as default. Configure the S3 bucket for website hosting. Create an S3 interface endpoint. Configure the S3 bucket to allow access only through that endpoint.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
Question #20 <br>A company is planning to store a large number of archived documents and make the documents available to employees through the corporate intranet. Employees will access the system by connecting through a client VPN service that is attached to a VPC. The data must not be accessible to the public.<br><br>The documents that the company is storing are copies of data that is held on physical media elsewhere. The number of requests will be low. Availability and speed of retrieval are not concerns of the company.<br><br>Which solution will meet these requirements at the LOWEST cost?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">D</span>
<br>- Option A: S3 One Zone - IA is designed for less frequently accessed data, but it is more expensive than S3 Glacier Deep Archive for long - term storage. Since the requests are low and availability/speed of retrieval are not concerns, using S3 One Zone - IA will cost more than necessary. So, this option is not the lowest - cost solution.<br> - Option B: Launching an EC2 instance with an EFS file system in the EFS One Zone - IA storage class incurs costs for the EC2 instance (including compute, storage, and networking) and the EFS file system. Managing an EC2 instance also has operational overhead. This is a more complex and costly solution compared to using S3 Glacier Deep Archive in an S3 bucket. So, this option is not the best choice.<br> - Option C: Using an EC2 instance with an EBS Cold HDD (sc1) volume also has costs associated with the EC2 instance and the EBS volume. Additionally, managing the EC2 instance requires more effort. Similar to Option B, this is more expensive and operationally complex than using S3 Glacier Deep Archive. So, this option is not optimal.<br> - Option D: S3 Glacier Deep Archive is the lowest - cost storage class in S3, suitable for long - term archived data with infrequent access. Creating an S3 bucket with S3 Glacier Deep Archive as the default storage class, configuring it for website hosting, and restricting access through an S3 interface endpoint meets the requirements. It is a cost - effective solution as it leverages S3's low - cost storage for archived data and provides a secure way to access the data through the corporate intranet. So, this option is the best choice to meet the requirements at the lowest cost. <br>
</div>

</details>

    
# 21/529 

<div style="color:blue">single</div>
<br>Question #21<br>A company is using an on-premises Active Directory service for user authentication. The company wants to use the same authentication service to sign in to the company’s AWS accounts, which are using AWS Organizations. AWS Site-to-Site VPN connectivity already exists between the on-premises environment and all the company’s AWS accounts. <br><br><br>The company’s security policy requires conditional access to the accounts based on user groups and roles. User identities must be managed in a single location.<br><br>Which solution will meet these requirements? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Configure AWS IAM Identity Center (AWS Single Sign-On) to connect to Active Directory by using SAML 2.0. Enable automatic provisioning by using the System for Cross-domain Identity Management (SCIM) v2.0 protocol. Grant access to the AWS accounts by using attribute-based access controls (ABACs).
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Configure AWS IAM Identity Center (AWS Single Sign-On) by using IAM Identity Center as an identity source. Enable automatic provisioning by using the System for Cross-domain Identity Management (SCIM) v2.0 protocol. Grant access to the AWS accounts by using IAM Identity Center permission sets.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. &nbsp;In one of the company&rsquo;s AWS accounts, configure AWS Identity and Access Management (IAM) to use a SAML 2.0 identity provider. Provision IAM users that are mapped to the federated users. Grant access that corresponds to appropriate groups in Active Directory. Grant access to the required AWS accounts by using cross-account IAM users.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. In one of the company&rsquo;s AWS accounts, configure AWS Identity and Access Management (IAM) to use an OpenID Connect (OIDC) identity provider. Provision IAM roles that grant access to the AWS account for the federated users that correspond to appropriate groups in Active Directory. Grant access to the required AWS accounts by using cross-account IAM roles.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #21<br>A company is using an on-premises Active Directory service for user authentication. The company wants to use the same authentication service to sign in to the company’s AWS accounts, which are using AWS Organizations. AWS Site-to-Site VPN connectivity already exists between the on-premises environment and all the company’s AWS accounts. <br><br><br>The company’s security policy requires conditional access to the accounts based on user groups and roles. User identities must be managed in a single location.<br><br>Which solution will meet these requirements? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>The correct answer isA. &nbsp;<br> Explanation: &nbsp;<br>The requirements are: &nbsp;<br>1.Use on-premises Active Directory for authentication across AWS accounts (under AWS Organizations). &nbsp;<br>2.Conditional access based on user groups and roles. &nbsp;<br>3.Centralized identity management (user identities must be managed in a single location). &nbsp;<br>4.Existing Site-to-Site VPN ensures connectivity between on-premises AD and AWS. &nbsp;<br>Why Option A is correct: &nbsp;<br>-AWS IAM Identity Center (AWS Single Sign-On) + SAML 2.0 allows integration with on-premises Active Directory. &nbsp;<br>-SCIM v2.0 enables automatic provisioning of users and groups from AD to AWS IAM Identity Center. &nbsp;<br>-Attribute-Based Access Control (ABAC) allows conditional access based on user attributes (e.g., group membership). &nbsp;<br>- This setup meets the requirement of managing identities in a single location (Active Directory) while enabling federated access to AWS accounts. &nbsp;<br>Why other options are incorrect: &nbsp;<br>-B: Uses IAM Identity Center as the identity source (not on-premises AD). &nbsp;<br>-C & D: Require manual IAM user/role provisioning (not centralized) and do not leverage AWS IAM Identity Center for seamless multi-account access. &nbsp;<br>Thus,A is the best solution. &nbsp;<br>AWS IAM Identity Center (AWS SSO) allows for the integration of on-premises Active Directory with AWS accounts, enabling users to sign in with their existing credentials. By using SAML 2.0, the company can establish a trust relationship between AWS SSO and Active Directory. The SCIM v2.0 protocol can be used for automatic provisioning and de-provisioning of user identities across AWS accounts. ABACs can be implemented to grant access to AWS resources based on user attributes, aligning with the company's security policy for conditional access. This centralized approach ensures that user identities are managed in a single location, meeting the company's requirements.<br>
</div>

</details>

    
# 22/529 

<div style="color:blue">single</div>
<br>Question #22 <br>A software company has deployed an application that consumes a REST API by using Amazon API Gateway, AWS Lambda functions, and an Amazon DynamoDB table. The application is showing an increase in the number of errors during PUT requests. Most of thePUT calls come from a small number of clients that are authenticated with specific API keys. <br><br><br>A large number of the PUT requests originate from one client. The API is noncritical, and clients can tolerate retries of unsuccessful calls. However, the errors are displayed to customers and are causing damage to the API’s reputation.<br><br><br>What should the solutions architect recommend to improve the customer experience?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Implement retry logic with exponential backoff and irregular variation in the client application. Ensure that the errors are caught and handled with descriptive error messages.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Implement API throttling through a usage plan at the API Gateway level. Ensure that the client application handles code 429 replies without error.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Turn on API caching to enhance responsiveness for the production stage. Run 10-minute load tests. Verify that the cache capacity is appropriate for the workload.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Implement reserved concurrency at the Lambda function level to provide the resources that are needed during sudden increases in traffic.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #22 <br>A software company has deployed an application that consumes a REST API by using Amazon API Gateway, AWS Lambda functions, and an Amazon DynamoDB table. The application is showing an increase in the number of errors during PUT requests. Most of thePUT calls come from a small number of clients that are authenticated with specific API keys. <br><br><br>A large number of the PUT requests originate from one client. The API is noncritical, and clients can tolerate retries of unsuccessful calls. However, the errors are displayed to customers and are causing damage to the API’s reputation.<br><br><br>What should the solutions architect recommend to improve the customer experience?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>The correct answer isB. Implement API throttling through a usage plan at the API Gateway level. Ensure that the client application handles code 429 replies without error.<br> Explanation:<br>-Problem Identification: A small number of clients (especially one client) are generating a large number of PUT requests, leading to errors that affect the API’s reputation. The API is non-critical, and clients can tolerate retries.<br>-Solution Approach: <br> &nbsp;-API Throttling with Usage Plans: API Gateway allows you to set throttling limits (rate and burst limits) via usage plans. This ensures that no single client can overwhelm the system with excessive requests.<br> &nbsp;-Handling 429 (Too Many Requests): When throttling is applied, API Gateway returns a `429` status code. The client application should gracefully handle this response (e.g., by implementing retries) instead of showing errors to users.<br>-Why Not Other Options?:<br> &nbsp;-A: While retry logic with exponential backoff is good practice, it doesn’t address the root cause (excessive requests from a single client).<br> &nbsp;-C: API caching improves responsiveness but does not solve throttling issues for PUT requests (caching is typically used for idempotent GET requests).<br> &nbsp;-D: Reserved concurrency in Lambda ensures resource availability but doesn’t prevent API overload from excessive client requests.<br>Thus,B is the best solution to improve customer experience by enforcing fair usage and ensuring clients handle throttling gracefully.<br>
</div>

</details>

    
# 23/529 

<div style="color:blue">single</div>
<br>Question #23<br>A company is running a data-intensive application on AWS. The application runs on a cluster of hundreds of Amazon EC2 instances. A shared file system also runs on several EC2 instances that store 200 TB of data. The application reads and modifies the data on the shared file system and generates a report. The job runs once monthly, reads a subset of the files from the shared file system, and takes about 72 hours to complete. The compute instances scale in an Auto Scaling group, but the instances that host the shared file system run continuously. The compute and storage instances are all in the same AWS Region. <br><br><br>A solutions architect needs to reduce costs by replacing the shared file system instances. The file system must provide high performance access to the needed data for the duration of the 72-hour run.<br><br>Which solution will provide the LARGEST overall cost reduction while meeting these requirements? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Migrate the data from the existing shared file system to an Amazon S3 bucket that uses the S3 Intelligent-Tiering storage class. Before the job runs each month, use Amazon FSx for Lustre to create a new file system with the data from Amazon S3 by using lazy loading. Use the new file system as the shared storage for the duration of the job. Delete the file system when the job is complete.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Migrate the data from the existing shared file system to a large Amazon Elastic Block Store (Amazon EBS) volume with Multi-Attach enabled. Attach the EBS volume to each of the instances by using a user data script in the Auto Scaling group launch template. Use the EBS volume as the shared storage for the duration of the job. Detach the EBS volume when the job is complete.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Migrate the data from the existing shared file system to an Amazon S3 bucket that uses the S3 Standard storage class. Before the job runs each month, use Amazon FSx for Lustre to create a new file system with the data from Amazon S3 by using batch loading. Use the new file system as the shared storage for the duration of the job. Delete the file system when the job is complete.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Migrate the data from the existing shared file system to an Amazon S3 bucket. Before the job runs each month, use AWS Storage Gateway to create a file gateway with the data from Amazon S3. Use the file gateway as the shared storage for the job. Delete the file gateway when the job is complete.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #23<br>A company is running a data-intensive application on AWS. The application runs on a cluster of hundreds of Amazon EC2 instances. A shared file system also runs on several EC2 instances that store 200 TB of data. The application reads and modifies the data on the shared file system and generates a report. The job runs once monthly, reads a subset of the files from the shared file system, and takes about 72 hours to complete. The compute instances scale in an Auto Scaling group, but the instances that host the shared file system run continuously. The compute and storage instances are all in the same AWS Region. <br><br><br>A solutions architect needs to reduce costs by replacing the shared file system instances. The file system must provide high performance access to the needed data for the duration of the 72-hour run.<br><br>Which solution will provide the LARGEST overall cost reduction while meeting these requirements? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>The correct answer isA. Migrate the data from the existing shared file system to an Amazon S3 bucket that uses the S3 Intelligent-Tiering storage class. Before the job runs each month, use Amazon FSx for Lustre to create a new file system with the data from Amazon S3 by using lazy loading. Use the new file system as the shared storage for the duration of the job. Delete the file system when the job is complete.<br> Explanation:<br>1.Cost Efficiency:<br> &nbsp; -S3 Intelligent-Tiering automatically optimizes storage costs by moving data between tiers based on access patterns, which is ideal for infrequently accessed data (monthly job).<br> &nbsp; -FSx for Lustre (lazy loading) only loads data when it is accessed, reducing initial setup costs and time compared to batch loading (which pre-loads all data upfront).<br> &nbsp; - Since the job runs only once a month,deleting the FSx for Lustre file system after the job avoids ongoing costs.<br>2.Performance:<br> &nbsp; - FSx for Lustre provideshigh-performance, low-latency access needed for data-intensive applications, especially when dealing with large datasets (200 TB).<br>3.Alternatives Analysis:<br> &nbsp; -Option B (EBS Multi-Attach): While EBS Multi-Attach allows shared storage, it is not cost-effective for large-scale (200 TB) storage and does not scale as well as FSx for Lustre for high-performance workloads.<br> &nbsp; -Option C (FSx for Lustre with batch loading): Batch loading pre-loads all data upfront, which is slower and more expensive than lazy loading (since not all data may be needed).<br> &nbsp; -Option D (Storage Gateway): File Gateway is not designed for high-performance compute workloads and would introduce latency compared to FSx for Lustre.<br> Conclusion:<br>Option A provides thelargest cost reduction while meeting performance requirements by leveraging S3 Intelligent-Tiering for long-term storage and FSx for Lustre (lazy loading) for temporary high-performance access.<br>
</div>

</details>

    
# 24/529 

<div style="color:blue">single</div>
<br>Question #24 <br>A company is developing a new service that will be accessed using TCP on a static port. A solutions architect must ensure that the service is highly available, has redundancy across Availability Zones, and is accessible using the DNS name my.service.com, which is publicly accessible. The service must use fixed address assignments so other companies can add the addresses to their allow lists.<br><br><br>Assuming that resources are deployed in multiple Availability Zones in a single Region, which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. &nbsp;Create Amazon EC2 instances with an Elastic IP address for each instance. Create a Network Load Balancer (NLB) and expose the static TCP port. Register EC2 instances with the NLB. Create a new name server record set named my.service.com, and assign the Elastic IP addresses of the EC2 instances to the record set. Provide the Elastic IP addresses of the EC2 instances to the other companies to add to their allow lists.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an Amazon ECS cluster and a service definition for the application. Create and assign public IP addresses for the ECS cluster. Create a Network Load Balancer (NLB) and expose the TCP port. Create a target group and assign the ECS cluster name to the NLB. Create a new A record set named my.service.com, and assign the public IP addresses of the ECS cluster to the record set. Provide the public IP addresses of the ECS cluster to the other companies to add to their allow lists.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create Amazon EC2 instances for the service. Create one Elastic IP address for each Availability Zone. Create a Network Load Balancer (NLB) and expose the assigned TCP port. Assign the Elastic IP addresses to the NLB for each Availability Zone. Create a target group and register the EC2 instances with the NLB. Create a new A (alias) record set named my.service.com, and assign the NLB DNS name to the record set.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an Amazon ECS cluster and a service definition for the application. Create and assign public IP address for each host in the cluster. Create an Application Load Balancer (ALB) and expose the static TCP port. Create a target group and assign the ECS service definition name to the ALB. Create a new CNAME record set and associate the public IP addresses to the record set. Provide the Elastic IP addresses of the Amazon EC2 instances to the other companies to add to their allow lists.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #24 <br>A company is developing a new service that will be accessed using TCP on a static port. A solutions architect must ensure that the service is highly available, has redundancy across Availability Zones, and is accessible using the DNS name my.service.com, which is publicly accessible. The service must use fixed address assignments so other companies can add the addresses to their allow lists.<br><br><br>Assuming that resources are deployed in multiple Availability Zones in a single Region, which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>The correct answer isC. &nbsp;<br> Explanation: &nbsp;<br>The requirements are: &nbsp;<br>1.High availability & redundancy across Availability Zones (AZs) – This is achieved by deploying resources in multiple AZs and using a Network Load Balancer (NLB). &nbsp;<br>2.Accessible via DNS name (`my.service.com`) – AnA (alias) record pointing to the NLB's DNS name satisfies this. &nbsp;<br>3.Static TCP port & fixed IP addresses for allow lists – The NLB can be assignedElastic IPs (EIPs) per AZ, providing stable IPs that other companies can whitelist. &nbsp;<br>4.Public accessibility – The NLB is internet-facing and uses public IPs. &nbsp;<br> Why Option C is Correct: &nbsp;<br>- UsesNLB (supports static TCP ports and retains source IP). &nbsp;<br>- AssignsEIPs per AZ to the NLB (fixed IPs for allow lists). &nbsp;<br>-A (alias) record points to the NLB's DNS name (best practice for load balancers). &nbsp;<br>- EC2 instances are registered with the NLB (ensures traffic distribution). &nbsp;<br> Why Other Options Are Wrong: &nbsp;<br>-A: Uses EC2 instance EIPs directly (not scalable; no load balancing if an instance fails). &nbsp;<br>-B: Uses ECS cluster public IPs (not fixed; NLB should have EIPs, not the cluster). &nbsp;<br>-D: UsesALB (does not support static TCP ports) and incorrect DNS setup (CNAME with IPs). &nbsp;<br>To meet the requirements of high availability, redundancy, and fixed address assignments, the best solution is to use Amazon EC2 instances with Elastic IP addresses and a Network Load Balancer (NLB). By assigning an Elastic IP address to each Availability Zone and attaching them to the NLB, the service can maintain a fixed address that can be added to allow lists by other companies. The NLB ensures that traffic is distributed across healthy instances and provides redundancy across Availability Zones. Using an A (alias) record set for the DNS name my.service.com and pointing it to the NLB DNS name ensures that the service is accessible using the specified DNS name.<br>
</div>

</details>

    
# 25/529 

<div style="color:blue">single</div>
Question #25<br>A company uses an on-premises data analytics platform. The system is highly available in a fully redundant configuration across 12 servers in the company’s data center. <br><br><br>The system runs scheduled jobs, both hourly and daily, in addition to one-time requests from users. Scheduled jobs can take between 20 minutes and 2 hours to finish running and have tight SLAs. The scheduled jobs account for 65% of the system usage. User jobs typically finish running in less than 5 minutes and have no SLA. The user jobs account for 35% of system usage. During system failures, scheduled jobs must continue to meet SLAs. However, user jobs can be delayed. <br><br><br>A solutions architect needs to move the system to Amazon EC2 instances and adopt a consumption-based model to reduce costs with no long-term commitments. The solution must maintain high availability and must not affect the SLAs.<br><br><br>Which solution will meet these requirements MOST cost-effectively?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Split the 12 instances across two Availability Zones in the chosen AWS Region. Run two instances in each Availability Zone as On-Demand Instances with Capacity Reservations. Run four instances in each Availability Zone as Spot Instances.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Split the 12 instances across three Availability Zones in the chosen AWS Region. In one of the Availability Zones, run all four instances as On-Demand Instances with Capacity Reservations. Run the remaining instances as Spot Instances.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Split the 12 instances across three Availability Zones in the chosen AWS Region. Run two instances in each Availability Zone as On-Demand Instances with a Savings Plan. Run two instances in each Availability Zone as Spot Instances.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Split the 12 instances across three Availability Zones in the chosen AWS Region. Run three instances in each Availability Zone as On-Demand Instances with Capacity Reservations. Run one instance in each Availability Zone as a Spot Instance.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
Question #25<br>A company uses an on-premises data analytics platform. The system is highly available in a fully redundant configuration across 12 servers in the company’s data center. <br><br><br>The system runs scheduled jobs, both hourly and daily, in addition to one-time requests from users. Scheduled jobs can take between 20 minutes and 2 hours to finish running and have tight SLAs. The scheduled jobs account for 65% of the system usage. User jobs typically finish running in less than 5 minutes and have no SLA. The user jobs account for 35% of system usage. During system failures, scheduled jobs must continue to meet SLAs. However, user jobs can be delayed. <br><br><br>A solutions architect needs to move the system to Amazon EC2 instances and adopt a consumption-based model to reduce costs with no long-term commitments. The solution must maintain high availability and must not affect the SLAs.<br><br><br>Which solution will meet these requirements MOST cost-effectively?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>To determine the most cost-effective solution, we analyze the requirements and options as follows:<br><br><br> Key Requirements:<br>1. High Availability: The system must remain highly available, with scheduled jobs meeting SLAs even during failures. This requires distribution across multiple Availability Zones (AZs) to avoid single points of failure.<br>2. Consumption-Based Model with No Long-Term Commitments: Solutions must avoid long-term contracts (e.g., reserved instances) and prioritize cost efficiency through flexible pricing.<br>3. Workload Prioritization: Scheduled jobs (65% of usage) have strict SLAs and require guaranteed capacity; user jobs (35% of usage) are non-critical and can use cheaper, interruptible capacity.<br><br><br> Analysis of Options:<br>- Option A: Using only 2 AZs increases risk of downtime if one AZ fails, as remaining capacity may be insufficient to meet scheduled job SLAs. This violates high availability requirements.<br> &nbsp;<br>- Option B: Concentrating all 4 On-Demand Instances in one AZ creates a single point of failure. If that AZ fails, only Spot Instances (interruptible) remain, which cannot guarantee SLA compliance for scheduled jobs.<br><br><br>- Option C: <br> &nbsp;- Distributes 12 instances across 3 AZs (4 per AZ), ensuring redundancy and meeting high availability standards. <br> &nbsp;- 2 On-Demand Instances per AZ with a Savings Plan: Savings Plans offer flexible, consumption-based discounts without locking into specific instances or AZs, aligning with the "no long-term commitments" requirement. They provide guaranteed capacity for critical scheduled jobs.<br> &nbsp;- 2 Spot Instances per AZ: Spot Instances are cost-effective for non-critical user jobs, which can tolerate delays. This split (50% On-Demand, 50% Spot) aligns with the 65% vs. 35% usage distribution, ensuring scheduled jobs have sufficient guaranteed capacity.<br><br><br>- Option D: Running 3 On-Demand Instances per AZ (9 total) is excessive for the 65% scheduled job usage, increasing costs unnecessarily. The minimal use of Spot Instances (3 total) fails to leverage cost savings for non-critical user jobs.<br><br><br>Conclusion: Option C optimally balances high availability (3 AZs), cost efficiency (Savings Plans for guaranteed capacity + Spot Instances for non-critical jobs), and compliance with a consumption-based model.<br>
</div>

</details>

    
# 26/529 

<div style="color:blue">single</div>
<br>Question #26<br>A security engineer determined that an existing application retrieves credentials to an Amazon RDS for MySQL database from an encrypted file in Amazon S3. For the next version of the application, the security engineer wants to implement the following application design changes to improve security: <br>The database must use strong, randomly generated passwords stored in a secure AWS managed service. <br>The application resources must be deployed through AWS CloudFormation. <br>The application must rotate credentials for the database every 90 days. <br>A solutions architect will generate a CloudFormation template to deploy the application. <br><br><br>Which resources specified in the CloudFormation template will meet the security engineer’s requirements with the LEAST amount of operational overhead?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Generate the database password as a secret resource using AWS Secrets Manager. Create an AWS Lambda function resource to rotate the database password. Specify a Secrets Manager RotationSchedule resource to rotate the database password every 90 days.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Generate the database password as a SecureString parameter type using AWS Systems Manager Parameter Store. Create an AWS Lambda function resource to rotate the database password. Specify a Parameter Store RotationSchedule resource to rotate the database password every 90 days.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Generate the database password as a secret resource using AWS Secrets Manager. Create an AWS Lambda function resource to rotate the database password. Create an Amazon EventBridge scheduled rule resource to trigger the Lambda function password rotation every 90 days.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Generate the database password as a SecureString parameter type using AWS Systems Manager Parameter Store. Specify an AWS AppSync DataSource resource to automatically rotate the database password every 90 days.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #26<br>A security engineer determined that an existing application retrieves credentials to an Amazon RDS for MySQL database from an encrypted file in Amazon S3. For the next version of the application, the security engineer wants to implement the following application design changes to improve security: <br>The database must use strong, randomly generated passwords stored in a secure AWS managed service. <br>The application resources must be deployed through AWS CloudFormation. <br>The application must rotate credentials for the database every 90 days. <br>A solutions architect will generate a CloudFormation template to deploy the application. <br><br><br>Which resources specified in the CloudFormation template will meet the security engineer’s requirements with the LEAST amount of operational overhead?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>The correct answer isA. &nbsp;<br> Explanation: &nbsp;<br>The security engineer's requirements are: &nbsp;<br>1.Store credentials securely in an AWS-managed service – AWS Secrets Manager is designed for this purpose (better than Parameter Store for secrets management). &nbsp;<br>2.Deploy via AWS CloudFormation – All options use CloudFormation, so this is satisfied. &nbsp;<br>3.Rotate credentials every 90 days – Secrets Manager has built-in rotation capabilities with `RotationSchedule`, reducing operational overhead. &nbsp;<br> Why Option A is Best: &nbsp;<br>-AWS Secrets Manager securely stores and manages the database password. &nbsp;<br>-RotationSchedule resource automates rotation every 90 days (no need for manual EventBridge rules). &nbsp;<br>-Lambda function handles the rotation logic (Secrets Manager provides a rotation template). &nbsp;<br> Why Other Options Are Incorrect: &nbsp;<br>-B: Parameter Store (SecureString) is not ideal for automatic rotation (Secrets Manager is better suited). &nbsp;<br>-C: While possible, using EventBridge for scheduling adds unnecessary complexity compared to Secrets Manager’s built-in rotation. &nbsp;<br>-D: AppSync is not used for credential rotation, and Parameter Store lacks native rotation support like Secrets Manager. &nbsp;<br>Thus,A meets all requirements with theleast operational overhead. <br>
</div>

</details>

    
# 27/529 

<div style="color:blue">multiple</div>
<br>Question #27<br>A company is storing data in several Amazon DynamoDB tables. A solutions architect must use a serverless architecture to make the data accessible publicly through a simple API over HTTPS. The solution must scale automatically in response to demand.<br><br>Which solutions meet these requirements? (Choose two.)<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an Amazon API Gateway REST API. Configure this API with direct integrations to DynamoDB by using API Gateway&rsquo;s AWS integration type.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an Amazon API Gateway HTTP API. Configure this API with direct integrations to DynamoDB by using API Gateway&rsquo;s AWS integration type.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an Amazon API Gateway HTTP API. Configure this API with integrations to AWS Lambda functions that return data from the DynamoDB tables.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an accelerator in AWS Global Accelerator. Configure this accelerator with AWS Lambda@Edge function integrations that return data from the DynamoDB tables.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Create a Network Load Balancer. Configure listener rules to forward requests to the appropriate AWS Lambda functions.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #27<br>A company is storing data in several Amazon DynamoDB tables. A solutions architect must use a serverless architecture to make the data accessible publicly through a simple API over HTTPS. The solution must scale automatically in response to demand.<br><br>Which solutions meet these requirements? (Choose two.)<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">AC</span>
<br>Based on the information provided, the two solutions that meet the requirements for making DynamoDB data accessible through a serverless API over HTTPS that scales automatically are:<br>A. Create an Amazon API Gateway REST API. Configure this API with direct integrations to DynamoDB by using API Gateway's AWS integration type.<br>C. Create an Amazon API Gateway HTTP API. Configure this API with integrations to AWS Lambda functions that return data from the DynamoDB tables.<br>Here's why these two options are correct:<br>Option A: API Gateway REST API with direct DynamoDB integration is a valid approach that allows you to connect API Gateway directly to DynamoDB using the AWS service integration type. This eliminates the need for Lambda functions as intermediaries and can be configured using mapping templates. This is a fully serverless solution that scales automatically with demand.<br>Option C: API Gateway HTTP API with Lambda integration is another valid approach where Lambda functions act as intermediaries between the API Gateway and DynamoDB. The Lambda functions can contain business logic to process the data before returning it to the client. This solution is also fully serverless and scales automatically.<br>Option B is incorrect because API Gateway HTTP APIs do not support direct AWS service integrations with DynamoDB. HTTP APIs can only integrate with Lambda functions, HTTP endpoints, or private resources in a VPC, but not directly with AWS services like DynamoDB.<br>Both options A and C provide serverless architectures that make DynamoDB data accessible through HTTPS and scale automatically in response to demand, meeting all the requirements specified in the question.<br>Sources<br>Tutorial: Create a CRUD HTTP API with Lambda and DynamoDB - Amazon API Gateway （https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-dynamo-db.html）<br>Is Direct Integration API Gateway to DDB Still Supported? | AWS re:Post （https://repost.aws/questions/QUMtrOZH6XR0WhWaBf2qRtTg/is-direct-integration-api-gateway-to-ddb-still-supported）<br>API Gateway use cases - Amazon API Gateway （https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-overview-developer-experience.html）<br>Get started with API Gateway - Serverless （https://docs.aws.amazon.com/serverless/latest/devguide/starter-apigw.html）<br>Building a Serverless Architecture on AWS | AWS re:Post （https://repost.aws/articles/ARTqFF9AQmSgqrx2BNH-wkbw/building-a-serverless-architecture-on-aws）<br>Use PutIntegration with an AWS SDK or CLI - AWS SDK Code Examples （https://docs.aws.amazon.com/code-library/latest/ug/api-gateway_example_api-gateway_PutIntegration_section.html）<br>Community | Using API Gateway mapping templates for direct DynamoDB integrations （https://community.aws/content/2f0C1U6QRHgVMRaN4L8dhMur3EB/using-api-gateway-mapping-templates-for-direct-dynamodb-integrations）<br>
</div>

</details>

    
# 28/529 

<div style="color:blue">multiple</div>
<br>Question #28<br>A company has registered 10 new domain names. The company uses the domains for online marketing. The company needs a solution that will redirect online visitors to a specific URL for each domain. <br><br><br>All domains and target URLs are defined in a JSON document. All DNS records are managed by Amazon Route 53. A solutions architect must implement a redirect service that accepts HTTP and HTTPS requests.<br><br><br>Which combination of steps should the solutions architect take to meet these requirements with the LEAST amount of operational effort? (Choose three.) <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. &nbsp;Create a dynamic webpage that runs on an Amazon EC2 instance. Configure the webpage to use the JSON document in combination with the event message to look up and respond with a redirect URL.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an Application Load Balancer that includes HTTP and HTTPS listeners.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an AWS Lambda function that uses the JSON document in combination with the event message to look up and respond with a redirect URL.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use an Amazon API Gateway API with a custom domain to publish an AWS Lambda function.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Create an Amazon CloudFront distribution. Deploy a Lambda@Edge function.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
F. Create an SSL certificate by using AWS Certificate Manager (ACM). Include the domains as Subject Alternative Names.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #28<br>A company has registered 10 new domain names. The company uses the domains for online marketing. The company needs a solution that will redirect online visitors to a specific URL for each domain. <br><br><br>All domains and target URLs are defined in a JSON document. All DNS records are managed by Amazon Route 53. A solutions architect must implement a redirect service that accepts HTTP and HTTPS requests.<br><br><br>Which combination of steps should the solutions architect take to meet these requirements with the LEAST amount of operational effort? (Choose three.) <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">CEF</span>
<br>Based on the information provided, to implement a redirect service for multiple domains with the least operational effort, the following three steps should be taken:<br>C. Create an AWS Lambda function that uses the JSON document in combination with the event message to look up and respond with a redirect URL.<br>E. Create an Amazon CloudFront distribution. Deploy a Lambda@Edge function.<br>F. Create an SSL certificate by using AWS Certificate Manager (ACM). Include the domains as Subject Alternative Names.<br>This combination provides the most efficient solution because:<br>Lambda@Edge (options C and E together) allows you to run code at AWS edge locations in response to CloudFront events. The Lambda function can use the JSON document to look up the appropriate redirect URL based on the incoming domain name in the request. This is a serverless approach that requires minimal operational effort.<br>CloudFront (option E) provides a global content delivery network that can handle both HTTP and HTTPS requests, which is a requirement. It also integrates seamlessly with Lambda@Edge for the redirect logic.<br>AWS Certificate Manager (option F) allows you to create and manage SSL certificates for all the domains with minimal effort. By including all domains as Subject Alternative Names (SANs) in a single certificate, you can secure all 10 domains without having to manage individual certificates. This certificate can then be attached to the CloudFront distribution to enable HTTPS.<br>This solution meets all the requirements:<br>Handles both HTTP and HTTPS requests<br>Uses the JSON document to map domains to target URLs<br>Works with Route 53 for DNS management<br>Requires minimal operational effort through serverless components<br>Scales automatically to handle visitor traffic<br>The other options would either require more operational effort or wouldn't fully meet the requirements specified in the question.<br>Sources<br>DNS forwarder externally | AWS re:Post （https://repost.aws/questions/QULgvWEouMTuGFdPl53nCB0A/dns-forwarder-externally）<br>Point a domain to your Lightsail instance using Amazon Route 53 - Amazon Lightsail （https://docs.aws.amazon.com/lightsail/latest/userguide/amazon-lightsail-using-route-53-to-point-a-domain-to-an-instance.html）<br>
</div>

</details>

    
# 29/529 

<div style="color:blue">single</div>
<br>Question #29 <br>A company that has multiple AWS accounts is using AWS Organizations. The company’s AWS accounts host VPCs, Amazon EC2 instances, and containers. The company’s compliance team has deployed a security tool in each VPC where the company has deployments. The security tools run on EC2 instances and send information to the AWS account that is dedicated for the compliance team. The company has tagged all the compliance related resources with a key of “costCenter” and a value of “compliance”.<br><br><br>The company wants to identify the cost of the security tools that are running on the EC2 instances so that the company can charge the compliance team’s AWS account. The cost calculation must be as accurate as possible.<br><br>What should a solutions architect do to meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. In the management account of the organization, activate the costCenter user-defined tag. Configure monthly AWS Cost and Usage Reports to save to an Amazon S3 bucket in the management account. Use the tag breakdown in the report to obtain the total cost for the costCenter tagged resources.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. In the member accounts of the organization, activate the costCenter user-defined tag. Configure monthly AWS Cost and Usage Reports to save to an Amazon S3 bucket in the management account. Schedule a monthly AWS Lambda function to retrieve the reports and calculate the total cost for the costCenter tagged resources.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. In the member accounts of the organization activate the costCenter user-defined tag. From the management account, schedule a monthly AWS Cost and Usage Report. Use the tag breakdown in the report to calculate the total cost for the costCenter tagged resources.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create a custom report in the organization view in AWS Trusted Advisor. Configure the report to generate a monthly billing summary for the costCenter tagged resources in the compliance team&rsquo;s AWS account.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #29 <br>A company that has multiple AWS accounts is using AWS Organizations. The company’s AWS accounts host VPCs, Amazon EC2 instances, and containers. The company’s compliance team has deployed a security tool in each VPC where the company has deployments. The security tools run on EC2 instances and send information to the AWS account that is dedicated for the compliance team. The company has tagged all the compliance related resources with a key of “costCenter” and a value of “compliance”.<br><br><br>The company wants to identify the cost of the security tools that are running on the EC2 instances so that the company can charge the compliance team’s AWS account. The cost calculation must be as accurate as possible.<br><br>What should a solutions architect do to meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>The correct answer isA. Here's the detailed explanation:<br>Why Option A is Correct:<br>1.Activate the `costCenter` tag in the management account: &nbsp;<br> &nbsp; - AWS Organizations allows you to activateuser-defined cost allocation tags (like `costCenter`) in themanagement account. Once activated, these tags become available for cost allocation tracking across all member accounts in the organization.<br>2.Configure AWS Cost and Usage Reports (CUR): &nbsp;<br> &nbsp; - TheAWS Cost and Usage Report (CUR) provides the most detailed breakdown of AWS costs, including resource-level tagging information.<br> &nbsp; - By saving the CUR to anAmazon S3 bucket in the management account, you can analyze costs across all member accounts.<br> &nbsp; - The report includes atag breakdown, allowing you to filter costs by the `costCenter:compliance` tag.<br>3.Accurate Cost Calculation: &nbsp;<br> &nbsp; - The CUR provides granular data, ensuring the cost calculation for the security tools isas accurate as possible.<br> &nbsp; - Since the compliance team’s resources are tagged consistently, the report can accurately attribute costs to them.<br>Why Other Options Are Incorrect:<br>-Option B: &nbsp;<br> &nbsp;- While activating the tag in member accounts is possible, it’snot necessary—the management account can activate the tag for the whole organization. &nbsp;<br> &nbsp;- Using a Lambda function to manually calculate costs isless efficient than using CUR’s built-in tag breakdown.<br>-Option C: &nbsp;<br> &nbsp;- TheAWS Cost and Usage Report must be configured in the payer (management) account, not member accounts. &nbsp;<br> &nbsp;- The phrasing "schedule a monthly report" is misleading—CUR is continuous, not scheduled.<br>-Option D: &nbsp;<br> &nbsp;-Trusted Advisor does not provide cost allocation tagging reports. It focuses on performance, security, and fault tolerance, not detailed billing breakdowns.<br>Conclusion: &nbsp;<br>Option A is the best solution because it leverages AWS Organizations' tag activation and the detailed cost breakdown provided by AWS Cost and Usage Reports (CUR) to accurately track and allocate costs for the compliance team’s resources. &nbsp;<br>
</div>

</details>

    
# 30/529 

<div style="color:blue">multiple</div>
<br>Question #30 <br>A company has 50 AWS accounts that are members of an organization in AWS Organizations. Each account contains multiple VPCs. The company wants to use AWS Transit Gateway to establish connectivity between the VPCs in each member account. Each time a new member account is created, the company wants to automate the process of creating a new VPC and a transit gateway attachment.<br><br>Which combination of steps will meet these requirements? (Choose two.)<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. From the management account, share the transit gateway with member accounts by using AWS Resource Access Manager.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. From the management account, share the transit gateway with member accounts by using an AWS Organizations SCP.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Launch an AWS CloudFormation stack set from the management account that automatically creates a new VPC and a VPC transit gateway attachment in a member account. Associate the attachment with the transit gateway in the management account by using the transit gateway ID.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Launch an AWS CloudFormation stack set from the management account that automatically creates a new VPC and a peering transit gateway attachment in a member account. Share the attachment with the transit gateway in the management account by using a transit gateway service-linked role.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. From the management account, share the transit gateway with member accounts by using AWS Service Catalog.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #30 <br>A company has 50 AWS accounts that are members of an organization in AWS Organizations. Each account contains multiple VPCs. The company wants to use AWS Transit Gateway to establish connectivity between the VPCs in each member account. Each time a new member account is created, the company wants to automate the process of creating a new VPC and a transit gateway attachment.<br><br>Which combination of steps will meet these requirements? (Choose two.)<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">AC</span>
<br>Based on the information provided, to automate the process of creating a new VPC and transit gateway attachment each time a new member account is created in an AWS Organization, the following two steps should be taken:<br>A. From the management account, share the transit gateway with member accounts by using AWS Resource Access Manager.<br>C. Launch an AWS CloudFormation stack set from the management account that automatically creates a new VPC and a VPC transit gateway attachment in a member account. Associate the attachment with the transit gateway in the management account by using the transit gateway ID.<br>This combination works because:<br>AWS Resource Access Manager (RAM) is the correct service to share resources like transit gateways across accounts within an AWS Organization. By sharing the transit gateway from the management account using RAM, all member accounts can access and attach to it. This is a prerequisite for establishing connectivity between VPCs across different accounts.<br>AWS CloudFormation stack sets provide the automation capability needed to deploy the same resources (in this case, a VPC and transit gateway attachment) across multiple accounts. By launching a stack set from the management account, you can automatically create these resources in each member account and associate the attachment with the shared transit gateway using its ID.<br>Option B is incorrect because Service Control Policies (SCPs) are used to manage permissions and restrict actions within an organization, not to share resources between accounts.<br>This solution meets all the requirements by:<br>Enabling connectivity between VPCs across all 50 member accounts<br>Automating the process of creating a new VPC and transit gateway attachment when new member accounts are created<br>Using the management account to orchestrate and share the necessary resources<br>Sources<br>Automate setting up and managing your transit networks with AWS Transit Gateway - Network Orchestration for AWS Transit Gateway （https://docs.aws.amazon.com/solutions/latest/network-orchestration-aws-transit-gateway/solution-overview.html）<br>Automate Networking foundation in multi-account environments | Networking & Content Delivery （https://aws.amazon.com/cn/blogs/networking-and-content-delivery/automate-networking-foundation-in-multi-account-environments/）<br>Securely scale multi-account architecture with AWS Network Firewall and AWS Control Tower | AWS Cloud Operations & Migrations Blog （https://aws.amazon.com/cn/blogs/mt/scale-multi-account-architecture-aws-network-firewall-and-aws-control-tower/）<br>Transit gateway attachment configuration | AWS re:Post （https://repost.aws/questions/QUvX0QyO3pRQWkBQspwcgVKg/transit-gateway-attachment-configuration）<br>Automating AWS Transit Gateway attachments to a transit gateway in a central account | Networking & Content Delivery （https://aws.amazon.com/cn/blogs/networking-and-content-delivery/automating-aws-transit-gateway-attachments-to-a-transit-gateway-in-a-central-account/）<br>Automate your network setup in AWS Control Tower using Aviatrix | AWS Marketplace （https://aws.amazon.com/cn/blogs/awsmarketplace/automate-your-network-setup-in-aws-control-tower-using-aviatrix/）<br>
</div>

</details>

    
# 31/529 

<div style="color:blue">single</div>
<br>Question #31<br>An enterprise company wants to allow its developers to purchase third-party software through AWS Marketplace. The company uses an AWS Organizations account structure with full features enabled, and has a shared services account in each organizational unit (OU) that will be used by procurement managers. The procurement team’s policy indicates that developers should be able to obtain third-party software from an approved list only and use Private Marketplace in AWS Marketplace to achieve this requirement. The procurement team wants administration of Private Marketplace to be restricted to a role named procurement-manager-role, which could be assumed by procurement managers. Other IAM users, groups, roles, and account administrators in the company should be denied Private Marketplace administrative access.<br><br>What is the MOST effi cient way to design an architecture to meet these requirements? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an IAM role named procurement-manager-role in all AWS accounts in the organization. Add the PowerUserAccess managed policy to the role. Apply an inline policy to all IAM users and roles in every AWS account to deny permissions on the AWSPrivateMarketplaceAdminFullAccess managed policy.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an IAM role named procurement-manager-role in all AWS accounts in the organization. Add the AdministratorAccess managed policy to the role. Define a permissions boundary with the AWSPrivateMarketplaceAdminFullAccess managed policy and attach it to all the developer roles.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an IAM role named procurement-manager-role in all the shared services accounts in the organization. Add the AWSPrivateMarketplaceAdminFullAccess managed policy to the role. Create an organization root-level SCP to deny permissions to administer Private Marketplace to everyone except the role named procurement-manager-role. Create another organization root-level SCP to deny permissions to create an IAM role named procurement-manager-role to everyone in the organization.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an IAM role named procurement-manager-role in all AWS accounts that will be used by developers. Add the AWSPrivateMarketplaceAdminFullAccess managed policy to the role. Create an SCP in Organizations to deny permissions to administer Private Marketplace to everyone except the role named procurement-manager-role. Apply the SCP to all the shared services accounts in the organization.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #31<br>An enterprise company wants to allow its developers to purchase third-party software through AWS Marketplace. The company uses an AWS Organizations account structure with full features enabled, and has a shared services account in each organizational unit (OU) that will be used by procurement managers. The procurement team’s policy indicates that developers should be able to obtain third-party software from an approved list only and use Private Marketplace in AWS Marketplace to achieve this requirement. The procurement team wants administration of Private Marketplace to be restricted to a role named procurement-manager-role, which could be assumed by procurement managers. Other IAM users, groups, roles, and account administrators in the company should be denied Private Marketplace administrative access.<br><br>What is the MOST effi cient way to design an architecture to meet these requirements? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>TheMOST efficient way to design the architecture to meet the given requirements is:<br>Option C &nbsp;<br>Explanation: &nbsp;<br>1.IAM Role in Shared Services Accounts: &nbsp;<br> &nbsp; - The procurement-manager-role is created only in theshared services accounts (not all accounts), which aligns with the requirement that procurement managers use these accounts. &nbsp;<br> &nbsp; - The role is granted the`AWSPrivateMarketplaceAdminFullAccess` managed policy, allowing it to administer Private Marketplace.<br>2.SCP at Root Level to Restrict Private Marketplace Admin Access: &nbsp;<br> &nbsp; - AService Control Policy (SCP) at theroot level denies permissions to administer Private Marketplacefor everyone except `procurement-manager-role`. &nbsp;<br> &nbsp; - This ensures no other IAM user, role, or administrator can modify Private Marketplace settings.<br>3.SCP to Prevent Creation of Unauthorized Roles: &nbsp;<br> &nbsp; - A secondSCP denies permissions tocreate an IAM role named `procurement-manager-role` to prevent unauthorized users from bypassing restrictions.<br>Why Not Other Options? &nbsp;<br>-A: Incorrect because: &nbsp;<br> &nbsp;- `PowerUserAccess` does not grant Private Marketplace admin permissions. &nbsp;<br> &nbsp;- Applying inline deny policies to every IAM user/role is inefficient and hard to manage. &nbsp;<br>-B: Incorrect because: &nbsp;<br> &nbsp;- `AdministratorAccess` is overly permissive. &nbsp;<br> &nbsp;- Permissions boundaries on developer roles do not restrict other admins from accessing Private Marketplace. &nbsp;<br>-D: Incorrect because: &nbsp;<br> &nbsp;- The role should be inshared services accounts, not all developer accounts. &nbsp;<br> &nbsp;- The SCP should be applied at theroot level, not just shared services accounts, to cover the entire organization. &nbsp;<br>
</div>

</details>

    
# 32/529 

<div style="color:blue">single</div>
<br>Question #32<br>A company is in the process of implementing AWS Organizations to constrain its developers to use only Amazon EC2, Amazon S3, and Amazon DynamoDB. The developers account resides in a dedicated organizational unit (OU). The solutions architect has implemented the following SCP on the developers account: <img src="https://up.zaixiankaoshi.com/5240831/question/61faadc126fb4fc55ec1eba8ee369d53.png" alt="61faadc126fb4fc55ec1eba8ee369d53.png" data-href="" style=""/><br>When this policy is deployed, IAM users in the developers account are still able to use AWS services that are not listed in the policy. <br>What should the solutions architect do to eliminate the developers’ ability to use services outside the scope of this policy? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an explicit deny statement for each AWS service that should be constrained.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Remove the FullAWSAccess SCP from the developers account&rsquo;s OU.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Modify the FullAWSAccess SCP to explicitly deny all services.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Add an explicit deny statement using a wildcard to the end of the SCP.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #32<br>A company is in the process of implementing AWS Organizations to constrain its developers to use only Amazon EC2, Amazon S3, and Amazon DynamoDB. The developers account resides in a dedicated organizational unit (OU). The solutions architect has implemented the following SCP on the developers account: <img src="https://up.zaixiankaoshi.com/5240831/question/61faadc126fb4fc55ec1eba8ee369d53.png" alt="61faadc126fb4fc55ec1eba8ee369d53.png" data-href="" style=""/><br>When this policy is deployed, IAM users in the developers account are still able to use AWS services that are not listed in the policy. <br>What should the solutions architect do to eliminate the developers’ ability to use services outside the scope of this policy? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Based on the information provided, the correct answer is:<br>B. Remove the FullAWSAccess SCP from the developers account's OU.<br>This is the correct solution because:<br>AWS Organizations applies a default SCP called "FullAWSAccess" to all accounts and OUs when SCPs are first enabled. This default policy allows all actions on all AWS services.<br>SCPs work on a "deny by default" principle, where permissions must be explicitly allowed. However, the default FullAWSAccess SCP is overriding this by allowing all services.<br>When multiple SCPs apply to an account, they work using a logical AND operation. This means that even though the custom SCP is trying to restrict services to only EC2, S3, and DynamoDB, the FullAWSAccess SCP is still allowing all other services.<br>By removing the FullAWSAccess SCP from the developers account's OU, only the custom SCP will apply, which explicitly allows only EC2, S3, and DynamoDB. All other services will be implicitly denied because they're not explicitly allowed in any applicable SCP.<br>Option A (creating explicit deny statements for each service) would be impractical and difficult to maintain as AWS regularly adds new services.<br>Option C (modifying the FullAWSAccess SCP) is incorrect because the FullAWSAccess SCP is a managed policy that cannot be modified.<br>Option D (adding an explicit deny with a wildcard) is unnecessary and could potentially cause unintended consequences. The proper approach is to leverage the implicit deny behavior of SCPs by removing the FullAWSAccess SCP.<br>Sources<br>Restrict outbound network for accounts in my AWS organizations using SCP | AWS re:Post （https://repost.aws/questions/QUvA8rKb94QV2ag83SiQ1o2A/restrict-outbound-network-for-accounts-in-my-aws-organizations-using-scp）<br>Enforcing enterprise-wide preventive controls with AWS Organizations | AWS Cloud Operations Blog （）https://aws.amazon.com/cn/blogs/mt/enforcing-enterprise-wide-preventive-controls-with-aws-organizations/<br>Service control policy examples - AWS Organizations （https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_examples.html）<br>Using AWS Organizations for security - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/security-reference-architecture/organizations-security.html）<br>SCP not matching implicit Deny | AWS re:Post （https://repost.aws/questions/QU9g5-9ZIHSjWa9_xe5006Vw/scp-not-matching-implicit-deny）<br>Service control policies (SCPs) - AWS Organizations （https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html）<br>
</div>

</details>

    
# 33/529 

<div style="color:blue">single</div>
<br>Question #33<br>A company is hosting a monolithic REST-based API for a mobile app on five Amazon EC2 instances in public subnets of a VPC. Mobile clients connect to the API by using a domain name that is hosted on Amazon Route 53. The company has created a Route 53 multivalue answer routing policy with the IP addresses of all the EC2 instances. Recently, the app has been overwhelmed by large and sudden increases to traffic.<br>A solutions architect needs to implement a solution so that the app can handle the new and varying load.<br><br>Which solution will meet these requirements with the LEAST operational overhead?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Separate the API into individual AWS Lambda functions. Configure an Amazon API Gateway REST API with Lambda integration for the backend. Update the Route 53 record to point to the API Gateway API.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Containerize the API logic. Create an Amazon Elastic Kubernetes Service (Amazon EKS) cluster. Run the containers in the cluster by using Amazon EC2. Create a Kubernetes ingress. Update the Route 53 record to point to the Kubernetes ingress.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an Auto Scaling group. Place all the EC2 instances in the Auto Scaling group. Configure the Auto Scaling group to perform scaling actions that are based on CPU utilization. Create an AWS Lambda function that reacts to Auto Scaling group changes and updates the Route 53 record.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an Application Load Balancer (ALB) in front of the API. Move the EC2 instances to private subnets in the VPC. Add the EC2 instances as targets for the ALB. Update the Route 53 record to point to the ALB.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #33<br>A company is hosting a monolithic REST-based API for a mobile app on five Amazon EC2 instances in public subnets of a VPC. Mobile clients connect to the API by using a domain name that is hosted on Amazon Route 53. The company has created a Route 53 multivalue answer routing policy with the IP addresses of all the EC2 instances. Recently, the app has been overwhelmed by large and sudden increases to traffic.<br>A solutions architect needs to implement a solution so that the app can handle the new and varying load.<br><br>Which solution will meet these requirements with the LEAST operational overhead?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">D</span>
<br>The best solution to handle the large and sudden increases in traffic with theleast operational overhead is:<br>D. Create an Application Load Balancer (ALB) in front of the API. Move the EC2 instances to private subnets in the VPC. Add the EC2 instances as targets for the ALB. Update the Route 53 record to point to the ALB.<br> Why?<br>1.Scalability: The ALB automatically distributes incoming traffic across multiple EC2 instances and can integrate withAuto Scaling (though not explicitly mentioned here, it's easily added later if needed).<br>2.High Availability: The ALB improves fault tolerance by routing traffic only to healthy instances.<br>3.Security: Moving EC2 instances to private subnets enhances security by shielding them from direct internet exposure.<br>4.Least Operational Overhead: This solution requires minimal changes to the existing architecture—no need to refactor into Lambda (Option A), containerize (Option B), or manually manage Route 53 updates (Option C).<br>5.Route 53 Simplification: Instead of managing multiple IPs with a multivalue policy, Route 53 simply points to the ALB’s DNS name.<br> Why Not the Other Options?<br>-A (Lambda + API Gateway): Requires significant refactoring of the monolithic API into serverless functions, increasing complexity.<br>-B (EKS): Kubernetes introduces high operational overhead for management and scaling.<br>-C (Auto Scaling + Lambda for Route 53 updates): Managing Route 53 dynamically via Lambda is complex and unnecessary when ALB provides a simpler solution.<br>Thus,Option D is the most efficient and scalable approach with minimal operational effort.<br>
</div>

</details>

    
# 34/529 

<div style="color:blue">single</div>
<br>Question #34<br>A company has created an OU in AWS Organizations for each of its engineering teams. Each OU owns multiple AWS accounts. The organization has hundreds of AWS accounts.<br>A solutions architect must design a solution so that each OU can view a breakdown of usage costs across its AWS accounts.<br>Which solution meets these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an AWS Cost and Usage Report (CUR) for each OU by using AWS Resource Access Manager. Allow each team to visualize the CUR through an Amazon QuickSight dashboard.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an AWS Cost and Usage Report (CUR) from the AWS Organizations management account. Allow each team to visualize the CUR through an Amazon QuickSight dashboard.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an AWS Cost and Usage Report (CUR) in each AWS Organizations member account. Allow each team to visualize the CUR through an Amazon QuickSight dashboard.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an AWS Cost and Usage Report (CUR) by using AWS Systems Manager. Allow each team to visualize the CUR through SystemsManager OpsCenter dashboards.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #34<br>A company has created an OU in AWS Organizations for each of its engineering teams. Each OU owns multiple AWS accounts. The organization has hundreds of AWS accounts.<br>A solutions architect must design a solution so that each OU can view a breakdown of usage costs across its AWS accounts.<br>Which solution meets these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Based on the information provided, the correct answer is:<br>B. Create an AWS Cost and Usage Report (CUR) from the AWS Organizations management account. Allow each team to visualize the CUR through an Amazon QuickSight dashboard.<br>This is the most efficient and recommended approach for the following reasons:<br>Centralized Cost Management: Creating the AWS Cost and Usage Report (CUR) from the management account provides a comprehensive view of costs across the entire organization, including all OUs and their member accounts.<br>Consolidated Data: The management account in AWS Organizations has visibility into the billing and usage data for all member accounts through consolidated billing, making it the ideal place to generate organization-wide cost reports.<br>Scalability: With hundreds of AWS accounts, creating and managing individual CURs in each member account (option C) would be extremely inefficient and difficult to maintain.<br>Data Visualization: Amazon QuickSight can connect to the CUR data and create dashboards that filter the data by OU, allowing each engineering team to see only their relevant cost information.<br>Access Control: Through proper IAM permissions and QuickSight dashboard sharing, each team can be granted access to view only the cost data relevant to their OU.<br>Option A is incorrect because AWS Resource Access Manager (RAM) cannot be used to share Cost and Usage Reports between accounts. RAM is designed for sharing AWS resources like subnets, transit gateways, and License Manager configurations, not billing data.<br>Option C is incorrect because it would create unnecessary complexity and management overhead by requiring the creation and maintenance of separate CURs in each of the hundreds of member accounts, rather than leveraging the consolidated view available from the management account.<br>Sources<br>CUR report for Organisation | AWS re:Post （https://repost.aws/questions/QURjr672h1QPGj4ja2fGGnRA/cur-report-for-organisation）<br>Is it possible to view the actual spending and budget values for all accounts through CUDOS? | AWS re:Post （https://repost.aws/questions/QUGtzcr2LcTbObILBiM63Fgw/is-it-possible-to-view-the-actual-spending-and-budget-values-for-all-accounts-through-cudos）<br>Introducing custom billing views: tailored cost and usage view for your stakeholders | AWS Cloud Financial Management （https://aws.amazon.com/cn/blogs/aws-cloud-financial-management/introducing-custom-billing-views-tailored-cost-and-usage-view-relevant-for-your-stakeholders/）<br>Access to CUR and Billing Info | AWS re:Post （https://repost.aws/questions/QUAjlooP76TaGBvVSZlyRHyQ/access-to-cur-and-billing-info）<br>
</div>

</details>

    
# 35/529 

<div style="color:blue">single</div>
<br>Question #35<br>A company is storing data on premises on a Windows file server. The company produces 5 GB of new data daily. The company migrated part of its Windows-based workload to AWS and needs the data to be available on a file system in the cloud. The company already has established an AWS Direct Connect connection between the on-premises network and AWS.<br>Which data migration strategy should the company use?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Use the file gateway option in AWS Storage Gateway to replace the existing Windows file server, and point the existing file share to the new file gateway.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use AWS DataSync to schedule a daily task to replicate data between the on-premises Windows file server and Amazon FSx.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Use AWS Data Pipeline to schedule a daily task to replicate data between the on-premises Windows file server and Amazon Elastic File System (Amazon EFS).
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use AWS DataSync to schedule a daily task to replicate data between the on-premises Windows file server and Amazon Elastic File System (Amazon EFS).
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #35<br>A company is storing data on premises on a Windows file server. The company produces 5 GB of new data daily. The company migrated part of its Windows-based workload to AWS and needs the data to be available on a file system in the cloud. The company already has established an AWS Direct Connect connection between the on-premises network and AWS.<br>Which data migration strategy should the company use?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Based on the information provided, the best data migration strategy for the company is:<br>B. Use AWS DataSync to schedule a daily task to replicate data between the on-premises Windows file server and Amazon FSx.<br>This is the optimal solution because:<br>AWS DataSync is specifically designed for efficient data transfer and synchronization between on-premises storage and AWS cloud storage services. It's ideal for the company's scenario of needing to transfer 5 GB of new data daily.<br>Amazon FSx provides a fully managed native Windows file system in the cloud, which is the perfect target for migrating data from a Windows file server. This ensures compatibility with Windows-based workloads that have been migrated to AWS.<br>DataSync can leverage the existing AWS Direct Connect connection to provide secure, fast, and reliable data transfer between the on-premises environment and AWS.<br>The solution allows for scheduled, automated daily transfers to keep the cloud file system up to date with the new data being produced on-premises.<br>Option A (using Storage Gateway's file gateway) is less suitable because it's designed more as a hybrid storage solution rather than a migration tool. While it could work, it would replace the existing file server rather than replicate data from it.<br>Option C (using AWS Data Pipeline with Amazon EFS) is incorrect because Data Pipeline is not optimized for file server migration scenarios, and Amazon EFS is a Linux-based file system that wouldn't be compatible with Windows-based workloads without additional configuration.<br>AWS DataSync with Amazon FSx provides the most straightforward, efficient, and compatible solution for this Windows file server migration scenario.<br>Sources<br>Migrating existing file storage to FSx for Windows File Server - Amazon FSx for Windows File Server（https://docs.aws.amazon.com/fsx/latest/WindowsGuide/migrate-files-fsx.html） <br>Which aws service i can use to continuesly sync data from onpremises to aws | AWS re:Post （https://repost.aws/questions/QUL4bbFAh0QUy51quD4Foa0w/which-aws-service-i-can-use-to-continuesly-sync-data-from-onpremises-to-aws）<br>Field Notes: Migrating File Servers to Amazon FSx and Integrating with AWS Managed Microsoft AD | AWS Architecture Blog （https://aws.amazon.com/cn/blogs/architecture/field-notes-migrating-file-servers-to-amazon-fsx-and-integrating-with-aws-managed-microsoft-ad/）<br>AWS Storage sessions at AWS re:Invent 2020-2021: Week 2 | AWS Storage Blog （https://aws.amazon.com/cn/blogs/storage/aws-storage-sessions-at-aws-reinvent-2020-week-2/）<br>Migrating existing files to FSx for Windows File Server using AWS DataSync - Amazon FSx for Windows File Server （https://docs.aws.amazon.com/fsx/latest/WindowsGuide/migrate-files-to-fsx-datasync.html）<br>
</div>

</details>

    
# 36/529 

<div style="color:blue">single</div>
<br>Question #36<br>A company’s solutions architect is reviewing a web application that runs on AWS. The application references static assets in an Amazon S3 bucket in the us-east-1 Region. The company needs resiliency across multiple AWS Regions. The company already has created an S3 bucket in a second Region.<br>Which solution will meet these requirements with the LEAST operational overhead?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Configure the application to write each object to both S3 buckets. Set up an Amazon Route 53 public hosted zone with a record set using a weighted routing policy for each S3 bucket. Configure the application to reference the objects by using the Route 53 DNS name.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an AWS Lambda function to copy objects from the S3 bucket in us-east-1 to the S3 bucket in the second Region. Invoke the Lambda function each time an object is written to the S3 bucket in us-east-1. Set up an Amazon CloudFront distribution with an origin group that contains the two S3 buckets as origins.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Configure replication on the S3 bucket in us-east-1 to replicate objects to the S3 bucket in the second Region. Set up an Amazon CloudFront distribution with an origin group that contains the two S3 buckets as origins.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Configure replication on the S3 bucket in us-east-1 to replicate objects to the S3 bucket in the second Region. If failover is required, update the application code to load S3 objects from the S3 bucket in the second Region.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #36<br>A company’s solutions architect is reviewing a web application that runs on AWS. The application references static assets in an Amazon S3 bucket in the us-east-1 Region. The company needs resiliency across multiple AWS Regions. The company already has created an S3 bucket in a second Region.<br>Which solution will meet these requirements with the LEAST operational overhead?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>Based on the information provided, the best solution with the least operational overhead is:<br>C. Configure replication on the S3 bucket in us-east-1 to replicate objects to the S3 bucket in the second Region. Set up an Amazon CloudFront distribution with an origin group that contains the two S3 buckets as origins.<br>This solution is optimal because:<br>S3 Cross-Region Replication (CRR) automatically copies objects from the source bucket in us-east-1 to the destination bucket in the second region, ensuring data consistency across regions with minimal manual intervention.<br>CloudFront with origin groups provides built-in failover capability. If the primary S3 bucket becomes unavailable, CloudFront will automatically route requests to the secondary bucket in the other region.<br>This approach requires minimal ongoing operational overhead as the replication is handled automatically by AWS, and the failover mechanism is managed by CloudFront.<br>CloudFront also provides additional benefits like edge caching, which improves performance for end users by serving content from locations closer to them.<br>Option A (writing objects to both buckets and using Route 53 weighted routing) would require more operational overhead because:<br>The application would need to be modified to write each object twice (to both regions)<br>It would require managing DNS records and routing policies in Route 53<br>It doesn't provide automatic synchronization between buckets if one write operation fails<br>The CloudFront with S3 Cross-Region Replication approach provides a more streamlined, automated solution that meets the multi-region resilience requirements while minimizing the operational burden on the company.<br>Sources<br>Replicating objects within and across Regions - Amazon Simple Storage Service （https://docs.aws.amazon.com/AmazonS3/latest/userguide/replication.html）<br>Data protection in Amazon S3 - Amazon Simple Storage Service （https://docs.aws.amazon.com/AmazonS3/latest/userguide/data-protection.html）<br>Cross region S3 backup and restore v/s cross region S3 replication | AWS re:Post （https://repost.aws/questions/QUd92uKIKbSqqEO1hStW-AzA/cross-region-s3-backup-and-restore-v-s-cross-region-s3-replication）<br>Configuring replication for use with Multi-Region Access Points - Amazon Simple Storage Service （https://docs.aws.amazon.com/AmazonS3/latest/userguide/MultiRegionAccessPointBucketReplication.html）<br>
</div>

</details>

    
# 37/529 

<div style="color:blue">single</div>
<br>Question #37<br>A company is hosting a three-tier web application in an on-premises environment. Due to a recent surge in traffic that resulted in downtime and a significant financial impact, company management has ordered that the application be moved to AWS. The application is written in .NET and has a dependency on a MySQL database. A solutions architect must design a scalable and highly available solution to meet the demand of 200,000 daily users.<br>Which steps should the solutions architect take to design an appropriate solution?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Use AWS Elastic Beanstalk to create a new application with a web server environment and an Amazon RDS MySQL Multi-AZ DB instance. The environment should launch a Network Load Balancer (NLB) in front of an Amazon EC2 Auto Scaling group in multiple Availability Zones. Use an Amazon Route 53 alias record to route traffic from the company&rsquo;s domain to the NLB.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use AWS CloudFormation to launch a stack containing an Application Load Balancer (ALB) in front of an Amazon EC2 Auto Scaling group spanning three Availability Zones. The stack should launch a Multi-AZ deployment of an Amazon Aurora MySQL DB cluster with a Retain deletion policy. Use an Amazon Route 53 alias record to route traffic from the company&rsquo;s domain to the ALB.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Use AWS Elastic Beanstalk to create an automatically scaling web server environment that spans two separate Regions with an Application Load Balancer (ALB) in each Region. Create a Multi-AZ deployment of an Amazon Aurora MySQL DB cluster with a cross-Region read replica. Use Amazon Route 53 with a geoproximity routing policy to route traffic between the two Regions.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use AWS CloudFormation to launch a stack containing an Application Load Balancer (ALB) in front of an Amazon ECS cluster of Spot instances spanning three Availability Zones. The stack should launch an Amazon RDS MySQL DB instance with a Snapshot deletion policy. Use an Amazon Route 53 alias record to route traffic from the company&rsquo;s domain to the ALB.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #37<br>A company is hosting a three-tier web application in an on-premises environment. Due to a recent surge in traffic that resulted in downtime and a significant financial impact, company management has ordered that the application be moved to AWS. The application is written in .NET and has a dependency on a MySQL database. A solutions architect must design a scalable and highly available solution to meet the demand of 200,000 daily users.<br>Which steps should the solutions architect take to design an appropriate solution?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>The correct answer isB. Here's why:<br> Key Requirements:<br>1.Scalable & Highly Available: The solution must handle 200,000 daily users with no downtime.<br>2.Three-Tier .NET Application: Requires a web tier, application tier, and database tier.<br>3.MySQL Dependency: The database must be highly available and scalable.<br>4.On-Premises to AWS Migration: The solution should leverage AWS best practices for resilience and performance.<br> Why Option B is Correct:<br>-Application Load Balancer (ALB): Distributes traffic across multiple Availability Zones (AZs) and is ideal for web applications (supports HTTP/HTTPS).<br>-EC2 Auto Scaling Group (Multi-AZ): Ensures the application scales horizontally and remains available even if one AZ fails.<br>-Amazon Aurora MySQL (Multi-AZ): Provides high availability with automatic failover and better performance than standard RDS MySQL.<br>-Retain Deletion Policy: Ensures the database is not accidentally deleted during stack updates/deletions.<br>-Route 53 Alias Record: Efficiently routes traffic to the ALB.<br> Why Other Options Are Incorrect:<br>-Option A: Uses aNetwork Load Balancer (NLB), which is better suited for low-latency/TCP traffic rather than web applications. Elastic Beanstalk is acceptable, but CloudFormation (Option B) offers more control for enterprise architectures.<br>-Option C: Overcomplicates the solution by introducingmulti-Region deployment, which is unnecessary for handling 200,000 daily users (a single Region with Multi-AZ is sufficient). Geoproximity routing is not required here.<br>-Option D: UsesSpot Instances for ECS, which is risky for production workloads due to potential interruptions. Also, aSnapshot deletion policy is less robust than aRetain policy for critical databases.<br> Conclusion:<br>Option B provides the most scalable, highly available, and cost-effective solution using ALB, Multi-AZ Aurora MySQL, and CloudFormation for infrastructure-as-code reliability. &nbsp;<br>
</div>

</details>

    
# 38/529 

<div style="color:blue">single</div>
<br>Question #38<br>A company is using AWS Organizations to manage multiple AWS accounts. For security purposes, the company requires the creation of an Amazon Simple Notification Service (Amazon SNS) topic that enables integration with a third-party alerting system in all the Organizations member accounts.<br>A solutions architect used an AWS CloudFormation template to create the SNS topic and stack sets to automate the deployment of CloudFormation stacks. Trusted access has been enabled in Organizations.<br>What should the solutions architect do to deploy the CloudFormation StackSets in all AWS accounts?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create a stack set in the Organizations member accounts. Use service-managed permissions. Set deployment options to deploy to an organization. Use CloudFormation StackSets drift detection.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create stacks in the Organizations member accounts. Use self-service permissions. Set deployment options to deploy to an organization.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create a stack set in the Organizations management account. Use service-managed permissions. Set deployment options to deploy to the organization. Enable CloudFormation StackSets automatic deployment.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create stacks in the Organizations management account. Use service-managed permissions. Set deployment options to deploy to the organization. Enable CloudFormation StackSets drift detection.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #38<br>A company is using AWS Organizations to manage multiple AWS accounts. For security purposes, the company requires the creation of an Amazon Simple Notification Service (Amazon SNS) topic that enables integration with a third-party alerting system in all the Organizations member accounts.<br>A solutions architect used an AWS CloudFormation template to create the SNS topic and stack sets to automate the deployment of CloudFormation stacks. Trusted access has been enabled in Organizations.<br>What should the solutions architect do to deploy the CloudFormation StackSets in all AWS accounts?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>The correct answer is: &nbsp;<br>C. Create a stack set in the Organizations management account. Use service-managed permissions. Set deployment options to deploy to the organization. Enable CloudFormation StackSets automatic deployment. &nbsp;<br> Explanation: &nbsp;<br>1.Stack Sets must be created in the management account – Since the company is using AWS Organizations, the management account is responsible for deploying StackSets across member accounts. &nbsp;<br>2.Use service-managed permissions – This allows AWS Organizations to handle permissions automatically, ensuring the StackSet can deploy to all specified accounts. &nbsp;<br>3.Deploy to the organization – This ensures the StackSet is deployed to all (or selected) member accounts within the organization. &nbsp;<br>4.Enable automatic deployment – This ensures that new accounts added to the organization in the future will automatically receive the StackSet deployment. &nbsp;<br> Why not the other options? &nbsp;<br>-A: Incorrect because StackSets must be created in themanagement account, not member accounts. &nbsp;<br>-B: Incorrect becauseself-service permissions require manual intervention, whereasservice-managed permissions are needed for automated deployment across an organization. &nbsp;<br>-D: Incorrect becausestacks (not StackSets) are created in individual accounts, but the requirement is to deploy acrossall member accounts using StackSets. &nbsp;<br>
</div>

</details>

    
# 39/529 

<div style="color:blue">multiple</div>
<br>Question #39<br>A company wants to migrate its workloads from on premises to AWS. The workloads run on Linux and Windows. The company has a large on-premises infrastructure that consists of physical machines and VMs that host numerous applications.<br>The company must capture details about the system configuration, system performance, running processes, and network connections of its on-premises workloads. The company also must divide the on-premises applications into groups for AWS migrations. The company needs recommendations for Amazon EC2 instance types so that the company can run its workloads on AWS in the most cost-effective manner.<br>Which combination of steps should a solutions architect take to meet these requirements? (Choose three.)<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Assess the existing applications by installing AWS Application Discovery Agent on the physical machines and VMs.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Assess the existing applications by installing AWS Systems Manager Agent on the physical machines and VMs.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Group servers into applications for migration by using AWS Systems Manager Application Manager.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Group servers into applications for migration by using AWS Migration Hub.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Generate recommended instance types and associated costs by using AWS Migration Hub.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
F. Import data about server sizes into AWS Trusted Advisor. Follow the recommendations for cost optimization.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #39<br>A company wants to migrate its workloads from on premises to AWS. The workloads run on Linux and Windows. The company has a large on-premises infrastructure that consists of physical machines and VMs that host numerous applications.<br>The company must capture details about the system configuration, system performance, running processes, and network connections of its on-premises workloads. The company also must divide the on-premises applications into groups for AWS migrations. The company needs recommendations for Amazon EC2 instance types so that the company can run its workloads on AWS in the most cost-effective manner.<br>Which combination of steps should a solutions architect take to meet these requirements? (Choose three.)<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">ADE</span>
<br>The correct combination of steps to meet the company's requirements is:<br>A. Assess the existing applications by installing AWS Application Discovery Agent on the physical machines and VMs. &nbsp;<br>D. Group servers into applications for migration by using AWS Migration Hub. &nbsp;<br>E. Generate recommended instance types and associated costs by using AWS Migration Hub. &nbsp;<br> Explanation: &nbsp;<br>1.AWS Application Discovery Agent (Option A) is designed to collect system configuration, performance, processes, and network connection details from on-premises servers (both physical and VMs). This data is crucial for assessing and planning migrations. &nbsp;<br>2.AWS Migration Hub (Option D) allows you to group discovered servers into applications for migration tracking. &nbsp;<br>3.AWS Migration Hub (Option E) provides recommendations for EC2 instance types and cost estimates based on the collected discovery data. &nbsp;<br> Why not the other options? &nbsp;<br>-B. AWS Systems Manager Agent (SSM Agent) is used for managing instances post-migration, not for discovery and migration planning. &nbsp;<br>-C. AWS Systems Manager Application Manager is for operational management, not migration grouping. &nbsp;<br>-F. Trusted Advisor provides general AWS cost optimization tips but does not generate migration-specific instance recommendations. &nbsp;<br>Thus, the best choices areA, D, and E.<br>
</div>

</details>

    
# 40/529 

<div style="color:blue">single</div>
<br>Question #40<br>A company is hosting an image-processing service on AWS in a VPC. The VPC extends across two Availability Zones. Each Availability Zone contains one public subnet and one private subnet.<br><br><br>The service runs on Amazon EC2 instances in the private subnets. An Application Load Balancer in the public subnets is in front of the service.The service needs to communicate with the internet and does so through two NAT gateways. The service uses Amazon S3 for image storage. The EC2 instances retrieve approximately 1 TB of data from an S3 bucket each day.<br><br><br>The company has promoted the service as highly secure. A solutions architect must reduce cloud expenditures as much as possible without compromising the service’s security posture or increasing the time spent on ongoing operations.<br><br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Replace the NAT gateways with NAT instances.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Move the EC2 instances to the public subnets. Remove the NAT gateways.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Set up an S3 gateway VPC endpoint in the VPC. Attach an endpoint policy to the endpoint to allow the required actions on the S3 bucket.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Attach an Amazon Elastic File System (Amazon EFS) volume to the EC2 instances. Host the images on the EFS volume.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #40<br>A company is hosting an image-processing service on AWS in a VPC. The VPC extends across two Availability Zones. Each Availability Zone contains one public subnet and one private subnet.<br><br><br>The service runs on Amazon EC2 instances in the private subnets. An Application Load Balancer in the public subnets is in front of the service.The service needs to communicate with the internet and does so through two NAT gateways. The service uses Amazon S3 for image storage. The EC2 instances retrieve approximately 1 TB of data from an S3 bucket each day.<br><br><br>The company has promoted the service as highly secure. A solutions architect must reduce cloud expenditures as much as possible without compromising the service’s security posture or increasing the time spent on ongoing operations.<br><br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>The correct answer isC. Set up an S3 gateway VPC endpoint in the VPC. Attach an endpoint policy to the endpoint to allow the required actions on the S3 bucket.<br> Explanation:<br>1.Current Cost Issue: The service uses NAT gateways for internet access, which incur costs based on data processed and hourly usage. Additionally, the EC2 instances retrieve1 TB of data daily from S3, which traverses the NAT gateways, increasing costs unnecessarily.<br>2.Security Requirement: The service is promoted as highly secure, so changes must not weaken security or increase operational overhead.<br>3.Optimization:<br> &nbsp; -S3 Gateway VPC Endpoint: <br> &nbsp; &nbsp; - Allows private EC2 instances to communicate directly with S3without going through NAT gateways or the public internet, reducing NAT gateway costs.<br> &nbsp; &nbsp; - Data transfer via the endpoint isfree (no additional charges for S3 traffic within the same region).<br> &nbsp; &nbsp; - Maintains security since traffic stays within the AWS network.<br> &nbsp; &nbsp; - An endpoint policy can restrict access to only the required S3 bucket and actions.<br> &nbsp; -No Operational Overhead: VPC endpoints are fully managed by AWS, requiring no maintenance.<br> Why Not the Other Options?<br>-A. Replace NAT gateways with NAT instances:<br> &nbsp;- NAT instances areless reliable (not highly available like NAT gateways) and requiremanual management (scaling, patching), increasing operational overhead.<br> &nbsp;- Cost savings are minimal compared to eliminating NAT gateway usage for S3 traffic.<br>-B. Move EC2 instances to public subnets and remove NAT gateways:<br> &nbsp;- Exposing EC2 instances to the public internetcompromises security, violating the requirement.<br>-D. Use Amazon EFS instead of S3:<br> &nbsp;- EFS ismore expensive for storage and throughput compared to S3, and it doesn’t address the NAT gateway cost issue.<br> &nbsp;- Adds complexity without solving the core problem.<br> Conclusion:<br>Option C is the most cost-effective and secure solution, eliminating NAT gateway costs for S3 traffic while maintaining security and operational simplicity. <br>
</div>

</details>

    
# 41/529 

<div style="color:blue">single</div>
<br>Question #41<br>A company recently deployed an application on AWS. The application uses Amazon DynamoDB. The company measured the application load and configured the RCUs and WCUs on the DynamoDB table to match the expected peak load. The peak load occurs once a week for a 4-hour period and is double the average load. The application load is close to the average load for the rest of the week. The access pattern includes many more writes to the table than reads of the table.<br><br><br>A solutions architect needs to implement a solution to minimize the cost of the table.<br><br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Use AWS Application Auto Scaling to increase capacity during the peak period. Purchase reserved RCUs and WCUs to match the average load.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Configure on-demand capacity mode for the table.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Configure DynamoDB Accelerator (DAX) in front of the table. Reduce the provisioned read capacity to match the new peak load on the table.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Configure DynamoDB Accelerator (DAX) in front of the table. Configure on-demand capacity mode for the table.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #41<br>A company recently deployed an application on AWS. The application uses Amazon DynamoDB. The company measured the application load and configured the RCUs and WCUs on the DynamoDB table to match the expected peak load. The peak load occurs once a week for a 4-hour period and is double the average load. The application load is close to the average load for the rest of the week. The access pattern includes many more writes to the table than reads of the table.<br><br><br>A solutions architect needs to implement a solution to minimize the cost of the table.<br><br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>Based on the information provided, the most cost-effective solution for minimizing the cost of the DynamoDB table is:<br>A. Use AWS Application Auto Scaling to increase capacity during the peak period. Purchase reserved RCUs and WCUs to match the average load.<br>This solution is optimal because:<br>Reserved capacity provides significant cost savings (up to 70%) compared to on-demand pricing for the predictable portion of the workload, which in this case is the average load that occurs most of the time.<br>AWS Application Auto Scaling can automatically adjust the provisioned capacity to handle the peak load that occurs once a week for 4 hours, ensuring the application performs well during these periods without having to pay for that extra capacity all the time.<br>Since the peak load is predictable (once a week for 4 hours) and the rest of the time the load is consistent (close to average), this combination of reserved capacity for the baseline and auto-scaling for the peaks provides the most cost-effective approach.<br>Option B (on-demand capacity mode) would be simpler to manage but more expensive for this workload pattern. On-demand mode is typically more cost-effective for unpredictable workloads, but in this case, the workload has a predictable pattern with a consistent baseline.<br>Option C (using DAX) would not be cost-effective because:<br>DAX is designed to improve read performance, but the scenario states the access pattern includes "many more writes to the table than reads"<br>DAX would add additional costs without addressing the core issue of optimizing the write capacity costs, which is the primary concern given the write-heavy workload<br>The combination of reserved capacity for the predictable baseline load and auto-scaling for the weekly peak provides the most cost-effective solution for this specific workload pattern.<br>Sources<br>Choose the right throughput strategy for Amazon DynamoDB applications | AWS Database Blog （https://aws.amazon.com/cn/blogs/database/choose-the-right-throughput-strategy-for-amazon-dynamodb-applications/）<br>Evaluate your DynamoDB table's capacity mode - Amazon DynamoDB （https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/CostOptimization_TableCapacityMode.html）<br>Real time Database Dynamodb - Scaling Error | AWS re:Post （https://repost.aws/questions/QUpwt70SzaT1qhk6lEhnW9nw/real-time-database-dynamodb-scaling-error）<br>Demystifying Amazon DynamoDB on-demand capacity mode | AWS Database Blog （https://aws.amazon.com/cn/blogs/database/demystifying-amazon-dynamodb-on-demand-capacity-mode/）<br>
</div>

</details>

    
# 42/529 

<div style="color:blue">single</div>
<br>Question #42<br>A solutions architect needs to advise a company on how to migrate its on-premises data processing application to the AWS Cloud. Currently, users upload input files through a web portal. The web server then stores the uploaded files on NAS and messages the processing server over a message queue. Each media file can take up to 1 hour to process. The company has determined that the number of media files awaiting processing is significantly higher during business hours, with the number of files rapidly declining after business hours.<br>What is the MOST cost-effective migration recommendation?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create a queue using Amazon SQS. Configure the existing web server to publish to the new queue. When there are messages in the queue, invoke an AWS Lambda function to pull requests from the queue and process the files. Store the processed files in an Amazon S3 bucket.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create a queue using Amazon MQ. Configure the existing web server to publish to the new queue. When there are messages in the queue, create a new Amazon EC2 instance to pull requests from the queue and process the files. Store the processed files in Amazon EFS. Shut down the EC2 instance after the task is complete.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create a queue using Amazon MQ. Configure the existing web server to publish to the new queue. When there are messages in the queue, invoke an AWS Lambda function to pull requests from the queue and process the files. Store the processed files in Amazon EFS.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create a queue using Amazon SQS. Configure the existing web server to publish to the new queue. Use Amazon EC2 instances in an EC2 Auto Scaling group to pull requests from the queue and process the files. Scale the EC2 instances based on the SQS queue length. Store the processed files in an Amazon S3 bucket.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #42<br>A solutions architect needs to advise a company on how to migrate its on-premises data processing application to the AWS Cloud. Currently, users upload input files through a web portal. The web server then stores the uploaded files on NAS and messages the processing server over a message queue. Each media file can take up to 1 hour to process. The company has determined that the number of media files awaiting processing is significantly higher during business hours, with the number of files rapidly declining after business hours.<br>What is the MOST cost-effective migration recommendation?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">D</span>
<br>Themost cost-effective migration recommendation for this scenario is: &nbsp;<br>Answer: D &nbsp;<br>Explanation: &nbsp;<br>1.Amazon SQS is a fully managed, cost-effective queue service that eliminates the need to manage your own message broker (like Amazon MQ). It is the better choice for this migration. &nbsp;<br>2.EC2 Auto Scaling is ideal for processing tasks that take up to1 hour per file, as Lambda has a maximum execution time of15 minutes (which rules out options A and C). Auto Scaling allows the system to: &nbsp;<br> &nbsp; - Scaleup during business hours when the queue is long. &nbsp;<br> &nbsp; - Scaledown after business hours when the queue is short, reducing costs. &nbsp;<br>3.Amazon S3 is the most cost-effective and scalable storage solution for processed files (compared to Amazon EFS, which is more expensive for this use case). &nbsp;<br>Why Not the Other Options? &nbsp;<br>-A & C: Lambda has a15-minute execution limit, making it unsuitable for 1-hour processing tasks. &nbsp;<br>-B: Amazon MQ is more expensive than SQS (since it requires managing a broker). Also, manually launching EC2 instances is less efficient than Auto Scaling. &nbsp;<br>-C: UsingEFS for storage is more expensive and unnecessary compared to S3 for processed files. &nbsp;<br>Thus,Option D provides thebest balance of cost efficiency, scalability, and AWS-native services for this workload.<br>
</div>

</details>

    
# 43/529 

<div style="color:blue">single</div>
<br>Question #43<br>A company is using Amazon OpenSearch Service to analyze data. The company loads data into an OpenSearch Service cluster with 10 data nodes from an Amazon S3 bucket that uses S3 Standard storage. The data resides in the cluster for 1 month for read-only analysis. After 1 month, the company deletes the index that contains the data from the cluster. For compliance purposes, the company must retain a copy of all input data.<br><br><br>The company is concerned about ongoing costs and asks a solutions architect to recommend a new solution.<br><br><br>Which solution will meet these requirements MOST cost-effectively?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Replace all the data nodes with UltraWarm nodes to handle the expected capacity. Transition the input data from S3 Standard to S3 Glacier Deep Archive when the company loads the data into the cluster.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Reduce the number of data nodes in the cluster to 2. Add UltraWarm nodes to handle the expected capacity. Configure the indexes to transition to UltraWarm when OpenSearch Service ingests the data. Transition the input data to S3 Glacier Deep Archive after 1 month by using an S3 Lifecycle policy.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Reduce the number of data nodes in the cluster to 2. Add UltraWarm nodes to handle the expected capacity. Configure the indexes to transition to UltraWarm when OpenSearch Service ingests the data. Add cold storage nodes to the cluster. Transition the indexes from UltraWarm to cold storage. Delete the input data from the S3 bucket after 1 month by using an S3 Lifecycle policy.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Reduce the number of data nodes in the cluster to 2. Add instance-backed data nodes to handle the expected capacity. Transition the input data from S3 Standard to S3 Glacier Deep Archive when the company loads the data into the cluster.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #43<br>A company is using Amazon OpenSearch Service to analyze data. The company loads data into an OpenSearch Service cluster with 10 data nodes from an Amazon S3 bucket that uses S3 Standard storage. The data resides in the cluster for 1 month for read-only analysis. After 1 month, the company deletes the index that contains the data from the cluster. For compliance purposes, the company must retain a copy of all input data.<br><br><br>The company is concerned about ongoing costs and asks a solutions architect to recommend a new solution.<br><br><br>Which solution will meet these requirements MOST cost-effectively?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Themost cost-effective solution that meets the requirements is: &nbsp;<br>Option B &nbsp;<br>Reduce the number of data nodes in the cluster to 2. Add UltraWarm nodes to handle the expected capacity. Configure the indexes to transition to UltraWarm when OpenSearch Service ingests the data. Transition the input data to S3 Glacier Deep Archive after 1 month by using an S3 Lifecycle policy. &nbsp;<br>Why Option B? &nbsp;<br>1.Cost Optimization with UltraWarm Nodes &nbsp;<br> &nbsp; - UltraWarm nodes arecheaper than standard data nodes for read-only workloads (like analytics). &nbsp;<br> &nbsp; - By reducing the number of standard data nodes to2 (minimum for high availability) and using UltraWarm for storage, the company saves costs. &nbsp;<br>2.Compliance Requirement (Data Retention in S3) &nbsp;<br> &nbsp; - The input data must be retained, butS3 Standard is expensive for long-term storage. &nbsp;<br> &nbsp; - Moving data toS3 Glacier Deep Archive after 1 month (via S3 Lifecycle policy) is thecheapest storage option for compliance. &nbsp;<br>3.No Need for Cold Storage Nodes (Option C is Overkill) &nbsp;<br> &nbsp; - Cold storage nodes in OpenSearch arenot necessary since UltraWarm already provides cost-efficient storage for read-only data. &nbsp;<br>4.Option A is Incorrect &nbsp;<br> &nbsp; - Replacingall data nodes with UltraWarm isnot feasible because UltraWarm cannot handleingestion—onlyquerying. &nbsp;<br>5.Option D is Incorrect &nbsp;<br> &nbsp; - Instance-backed data nodes arenot cost-effective compared to UltraWarm for read-only workloads. &nbsp;<br>Conclusion: &nbsp;<br>Option B provides thebest balance of cost savings and compliance by leveraging UltraWarm for OpenSearch and S3 Glacier Deep Archive for long-term retention. &nbsp;<br>Answer: B<br>
</div>

</details>

    
# 44/529 

<div style="color:blue">single</div>
<br>Question #44<br>A company has 10 accounts that are part of an organization in AWS Organizations. AWS Config is configured in each account. All accounts belong to either the Prod OU or the NonProd OU.<br><br><br>The company has set up an Amazon EventBridge rule in each AWS account to notify an Amazon Simple Notification Service (Amazon SNS) topic when an Amazon EC2 security group inbound rule is created with 0.0.0.0/0 as the source. The company’s security team is subscribed to the SNS topic.<br><br><br>For all accounts in the NonProd OU, the security team needs to remove the ability to create a security group inbound rule that includes 0.0.0.0/0 as the source.<br><br><br>Which solution will meet this requirement with the LEAST operational overhead?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Modify the EventBridge rule to invoke an AWS Lambda function to remove the security group inbound rule and to publish to the SNS topic.Deploy the updated rule to the NonProd OU.&nbsp;
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Add the vpc-sg-open-only-to-authorized-ports AWS Config managed rule to the NonProd OU.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Configure an SCP to allow the ec2:AuthorizeSecurityGroupIngress action when the value of the aws:SourceIp condition key is not 0.0.0.0/0.Apply the SCP to the NonProd OU.&nbsp;
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Configure an SCP to deny the ec2:AuthorizeSecurityGroupIngress action when the value of the aws:SourceIp condition key is 0.0.0.0/0.Apply the SCP to the NonProd OU.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #44<br>A company has 10 accounts that are part of an organization in AWS Organizations. AWS Config is configured in each account. All accounts belong to either the Prod OU or the NonProd OU.<br><br><br>The company has set up an Amazon EventBridge rule in each AWS account to notify an Amazon Simple Notification Service (Amazon SNS) topic when an Amazon EC2 security group inbound rule is created with 0.0.0.0/0 as the source. The company’s security team is subscribed to the SNS topic.<br><br><br>For all accounts in the NonProd OU, the security team needs to remove the ability to create a security group inbound rule that includes 0.0.0.0/0 as the source.<br><br><br>Which solution will meet this requirement with the LEAST operational overhead?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">D</span>
<br>Based on the information provided, the correct answer is:<br>D. Configure an SCP to deny the ec2:AuthorizeSecurityGroupIngress action when the value of the aws:SourceIp condition key is 0.0.0.0/0. Apply the SCP to the NonProd OU.<br>This solution is the most effective with the least operational overhead because:<br>Service Control Policies (SCPs) are preventive controls that can be applied at the OU level to deny specific actions. In this case, denying the ec2:AuthorizeSecurityGroupIngress action with a condition that checks for 0.0.0.0/0 as the source IP will prevent users from creating open security group rules.<br>SCPs are enforced at the AWS Organizations level and apply to all accounts within the NonProd OU, providing centralized management with minimal configuration.<br>Once configured, the SCP will immediately prevent the creation of non-compliant security group rules without requiring any additional monitoring or remediation steps.<br>This approach has minimal operational overhead as it's a one-time setup that doesn't require enabling or configuring additional services beyond AWS Organizations, which is already in use.<br>Option B (adding the vpc-sg-open-only-to-authorized-ports AWS Config managed rule) would have higher operational overhead because:<br>AWS Config rules are detective controls, not preventive. They would detect non-compliant security groups after they've been created but wouldn't prevent their creation.<br>While AWS Config is already configured in each account, implementing and managing the rule would still require more operational effort than an SCP.<br>The Config rule would require additional remediation actions to fix non-compliant resources, whereas the SCP prevents the creation of non-compliant resources in the first place.<br>The SCP approach (Option D) provides a more direct and efficient solution with less operational overhead for preventing the creation of security group rules with 0.0.0.0/0 as the source in the NonProd OU.<br>Sources<br>Enforcing enterprise-wide preventive controls with AWS Organizations | AWS Cloud Operations Blog （https://aws.amazon.com/cn/blogs/mt/enforcing-enterprise-wide-preventive-controls-with-aws-organizations/）<br>Protect your AWS resources from unauthorized access using AWS Organizations integrations | AWS Cloud Operations Blog （https://aws.amazon.com/cn/blogs/mt/protect-your-aws-resources-from-unauthorized-access-using-aws-organizations-integrations/）<br>Example SCPs for Amazon Elastic Compute Cloud (Amazon EC2) - AWS Organizations （https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_examples_ec2.html）<br>Application team example: Creating an AWS Config rule - AWS Prescriptive Guidance（https://docs.aws.amazon.com/prescriptive-guidance/latest/vulnerability-management/application-team-example.html） <br>SCP evaluation - AWS Organizations （https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_evaluation.html）<br>Amazon Elastic Compute Cloud (Amazon EC2) controls - AWS Control Tower （https://docs.aws.amazon.com/controltower/latest/controlreference/ec2-rules.html）<br>
</div>

</details>

    
# 45/529 

<div style="color:blue">single</div>
<br>Question #45<br>A company hosts a Git repository in an on-premises data center. The company uses webhooks to invoke functionality that runs in the AWS Cloud.<br><br><br>The company hosts the webhook logic on a set of Amazon EC2 instances in an Auto Scaling group that the company set as a target for an Application Load Balancer (ALB). The Git server calls the ALB for the configured webhooks. The company wants to move the solution to a serverless architecture.<br><br><br>Which solution will meet these requirements with the LEAST operational overhead?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. For each webhook, create and configure an AWS Lambda function URL. Update the Git servers to call the individual Lambda function URLs.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an Amazon API Gateway HTTP API. Implement each webhook logic in a separate AWS Lambda function. Update the Git servers to call the API Gateway endpoint.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Deploy the webhook logic to AWS App Runner. Create an ALB, and set App Runner as the target. Update the Git servers to call the ALB endpoint.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Containerize the webhook logic. Create an Amazon Elastic Container Service (Amazon ECS) cluster, and run the webhook logic in AWS Fargate. Create an Amazon API Gateway REST API, and set Fargate as the target. Update the Git servers to call the API Gateway endpoint.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #45<br>A company hosts a Git repository in an on-premises data center. The company uses webhooks to invoke functionality that runs in the AWS Cloud.<br><br><br>The company hosts the webhook logic on a set of Amazon EC2 instances in an Auto Scaling group that the company set as a target for an Application Load Balancer (ALB). The Git server calls the ALB for the configured webhooks. The company wants to move the solution to a serverless architecture.<br><br><br>Which solution will meet these requirements with the LEAST operational overhead?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Based on the information provided, the best solution with the least operational overhead is:<br>B. Create an Amazon API Gateway HTTP API. Implement each webhook logic in a separate AWS Lambda function. Update the Git servers to call the API Gateway endpoint.<br>This solution is optimal for the following reasons:<br>Serverless Architecture: Both API Gateway and Lambda are fully managed serverless services, eliminating the need to manage any infrastructure like EC2 instances, Auto Scaling groups, or load balancers.<br>Centralized Management: Using a single API Gateway endpoint provides a centralized entry point for all webhooks, which simplifies the configuration on the Git server side. You only need to update the Git server to point to one endpoint instead of multiple function URLs.<br>Separation of Concerns: Implementing each webhook logic in a separate Lambda function allows for independent development, deployment, and scaling of each webhook handler.<br>Minimal Operational Overhead: API Gateway HTTP APIs are specifically designed for low-latency, cost-effective API proxying to Lambda functions. They require minimal configuration and maintenance compared to REST APIs.<br>Built-in Features: API Gateway provides built-in features like request validation, throttling, and monitoring that would otherwise need to be implemented separately.<br>Option A (Lambda function URLs) would require updating the Git server configuration for each webhook separately, increasing operational overhead and complexity in management.<br>Option C (AWS App Runner with ALB) introduces unnecessary components like an ALB, which adds complexity and operational overhead compared to the API Gateway approach. App Runner is more suitable for containerized applications rather than simple webhook handlers.<br>The API Gateway with Lambda functions approach provides the best balance of simplicity, scalability, and low operational overhead for this serverless migration.<br>Sources<br>AWS Lambda function URLs - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/choosing-the-right-aws-service-for-your-microservice-endpoints/function-urls.html）<br>Community | EC2 cost optimization:15 ways to save on Amazon EC2 （https://community.aws/content/2hQNGTh6vpwOHTgKELzL8mkqmKb/ec2-cost-optimization-15-ways-to-save-on-amazon-ec2）<br>Lambda Function URL Invoke with ALB | AWS re:Post （https://repost.aws/questions/QUYKEaKLPIQ2ui-DkJjHT-kQ/lambda-function-url-invoke-with-alb）<br>Least operational overhead to handle monolithic app | AWS re:Post （https://repost.aws/questions/QUuoRkJsZURTe6xML-FfpFNQ/least-operational-overhead-to-handle-monolithic-app）<br>
</div>

</details>

    
# 46/529 

<div style="color:blue">single</div>
<br>Question #46<br>A company is planning to migrate 1,000 on-premises servers to AWS. The servers run on several VMware clusters in the company’s data center. As part of the migration plan, the company wants to gather server metrics such as CPU details, RAM usage, operating system information, and running processes. The company then wants to query and analyze the data.<br><br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Deploy and configure the AWS Agentless Discovery Connector virtual appliance on the on-premises hosts. Configure Data Exploration in AWS Migration Hub. Use AWS Glue to perform an ETL job against the data. Query the data by using Amazon S3 Select.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Export only the VM performance information from the on-premises hosts. Directly import the required data into AWS Migration Hub. Update any missing information in Migration Hub. Query the data by using Amazon QuickSight.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create a script to automatically gather the server information from the on-premises hosts. Use the AWS CLI to run the put-resource-attributes command to store the detailed server data in AWS Migration Hub. Query the data directly in the Migration Hub console.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Deploy the AWS Application Discovery Agent to each on-premises server. Configure Data Exploration in AWS Migration Hub. Use Amazon Athena to run predefined queries against the data in Amazon S3.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #46<br>A company is planning to migrate 1,000 on-premises servers to AWS. The servers run on several VMware clusters in the company’s data center. As part of the migration plan, the company wants to gather server metrics such as CPU details, RAM usage, operating system information, and running processes. The company then wants to query and analyze the data.<br><br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">D</span>
<br>Based on the information provided, the correct answer is:<br>D. Deploy the AWS Application Discovery Agent to each on-premises server. Configure Data Exploration in AWS Migration Hub. Use Amazon Athena to run predefined queries against the data in Amazon S3.<br>This solution is the most appropriate for gathering detailed server metrics and analyzing the data for a large-scale migration because:<br>The AWS Application Discovery Agent provides comprehensive data collection capabilities, gathering detailed metrics about CPU, RAM usage, operating system information, and running processes directly from each server. This level of detail is essential for proper migration planning for 1,000 servers.<br>The agent continuously collects data over time, allowing the company to understand usage patterns and performance characteristics, which is crucial for right-sizing resources in AWS.<br>AWS Migration Hub's Data Exploration feature stores the collected data in Amazon S3, creating a centralized repository of all server information.<br>Amazon Athena provides powerful SQL-based querying capabilities against the data stored in S3, allowing the company to run complex analyses, filter data, and generate reports without having to set up additional infrastructure.<br>Option B is incorrect because:<br>Exporting only VM performance information would miss critical details like operating system information and running processes<br>Directly importing data into Migration Hub without using the Discovery Agent would require manual updates for missing information, which is impractical for 1,000 servers<br>This approach would not provide the comprehensive data collection and analysis capabilities needed for a migration of this scale<br>The AWS Application Discovery Agent with Data Exploration in Migration Hub and Amazon Athena provides the most complete solution for gathering, storing, and analyzing server metrics for a large-scale migration to AWS.<br>Sources<br>Discover on-premises resources using AWS Migration Hub discovery tools - AWS Migration Hub （https://docs.aws.amazon.com/migrationhub/latest/ug/gs-new-user-discovery.html）<br>What is AWS Application Discovery Service? - AWS Application Discovery Service （https://docs.aws.amazon.com/application-discovery/latest/userguide/what-is-appdiscovery.html）<br>Assess - Migration Lens （https://docs.aws.amazon.com/wellarchitected/latest/migration-lens/assess-cost.html）<br>Welcome - AWS Application Discovery Service （https://docs.aws.amazon.com/application-discovery/latest/APIReference/Welcome.html）<br>
</div>

</details>

    
# 47/529 

<div style="color:blue">single</div>
<br>Question #47<br>A company is building a serverless application that runs on an AWS Lambda function that is attached to a VPC. The company needs to integrate the application with a new service from an external provider. The external provider supports only requests that come from public IPv4 addresses that are in an allow list.<br><br><br>The company must provide a single public IP address to the external provider before the application can start using the new service.<br><br><br>Which solution will give the application the ability to access the new service?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Deploy a NAT gateway. Associate an Elastic IP address with the NAT gateway. Configure the VPC to use the NAT gateway.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Deploy an egress-only internet gateway. Associate an Elastic IP address with the egress-only internet gateway. Configure the elastic network interface on the Lambda function to use the egress-only internet gateway.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Deploy an internet gateway. Associate an Elastic IP address with the internet gateway. Configure the Lambda function to use the internet gateway.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Deploy an internet gateway. Associate an Elastic IP address with the internet gateway. Configure the default route in the public VPC route table to use the internet gateway.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #47<br>A company is building a serverless application that runs on an AWS Lambda function that is attached to a VPC. The company needs to integrate the application with a new service from an external provider. The external provider supports only requests that come from public IPv4 addresses that are in an allow list.<br><br><br>The company must provide a single public IP address to the external provider before the application can start using the new service.<br><br><br>Which solution will give the application the ability to access the new service?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>Based on the information provided, the correct answer is:<br>A. Deploy a NAT gateway. Associate an Elastic IP address with the NAT gateway. Configure the VPC to use the NAT gateway.<br>This solution is the most appropriate for enabling a Lambda function attached to a VPC to access an external service that requires a whitelisted public IP address because:<br>NAT Gateway with an Elastic IP: This setup allows Lambda functions in private subnets to initiate outbound connections to the internet through a consistent, static public IP address (the Elastic IP associated with the NAT gateway). This public IP can be provided to the external provider for their allow list.<br>Security Best Practices: This approach follows AWS security best practices by keeping the Lambda function in a private subnet while still allowing it to make outbound connections. The Lambda function itself remains protected from inbound internet traffic.<br>Proper VPC Architecture: The NAT gateway is designed specifically for this use case - allowing resources in private subnets to access the internet while maintaining a consistent source IP address for outbound traffic.<br>Option C (using an internet gateway with an Elastic IP) is incorrect because:<br>Internet gateways don't have Elastic IP addresses directly associated with them<br>Internet gateways provide bidirectional internet connectivity, which could expose the Lambda function to inbound traffic<br>Lambda functions cannot directly use internet gateways - they would need to be placed in public subnets with public IP addresses, which is not a recommended security practice<br>The NAT gateway solution provides the single, consistent public IP address required by the external provider while maintaining proper security architecture for the serverless application.<br>Sources<br>NAT Gateway for outbound request | AWS re:Post （https://repost.aws/questions/QU9RYFVH0ARXWaNvUt9LB2-w/nat-gateway-for-outbound-request）<br>Troubleshoot networking issues in Lambda - AWS Lambda （https://docs.aws.amazon.com/lambda/latest/dg/troubleshooting-networking.html）<br>Lambda in RDS VPC needs bi-directional inet access | AWS re:Post （https://repost.aws/questions/QUcNlaEOLcTkqL2lD2RW_WbA/lambda-in-rds-vpc-needs-bi-directional-inet-access）<br>Leverage VPC endpoints - Serverless Applications Lens （https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/leverage-vpc-endpoints.html）<br>InternalError when associating EIP with Lambda ENI | AWS re:Post （https://repost.aws/questions/QUiBy0C0gUQYSjrq4HbFrNQQ/internalerror-when-associating-eip-with-lambda-eni）<br>how to provide static ip address for external system to whitelist my ec2 in private subnet ip address in aws? | AWS re:Post （https://repost.aws/questions/QUwBqnAslLTU-TSzztE8_O5A/how-to-provide-static-ip-address-for-external-system-to-whitelist-my-ec2-in-private-subnet-ip-address-in-aws）<br>
</div>

</details>

    
# 48/529 

<div style="color:blue">multiple</div>
<br>Question #48<br>A solutions architect has developed a web application that uses an Amazon API Gateway Regional endpoint and an AWS Lambda function. The consumers of the web application are all close to the AWS Region where the application will be deployed. The Lambda function only queries an Amazon Aurora MySQL database. The solutions architect has configured the database to have three read replicas.<br>During testing, the application does not meet performance requirements. Under high load, the application opens a large number of database connections. The solutions architect must improve the application’s performance.<br>Which actions should the solutions architect take to meet these requirements? (Choose two.)<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Use the cluster endpoint of the Aurora database.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use RDS Proxy to set up a connection pool to the reader endpoint of the Aurora database.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Use the Lambda Provisioned Concurrency feature.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Move the code for opening the database connection in the Lambda function outside of the event handler.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Change the API Gateway endpoint to an edge-optimized endpoint.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #48<br>A solutions architect has developed a web application that uses an Amazon API Gateway Regional endpoint and an AWS Lambda function. The consumers of the web application are all close to the AWS Region where the application will be deployed. The Lambda function only queries an Amazon Aurora MySQL database. The solutions architect has configured the database to have three read replicas.<br>During testing, the application does not meet performance requirements. Under high load, the application opens a large number of database connections. The solutions architect must improve the application’s performance.<br>Which actions should the solutions architect take to meet these requirements? (Choose two.)<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">BD</span>
<br>Based on the information provided, the two actions that the solutions architect should take to improve the application's performance are:<br>B. Use RDS Proxy to set up a connection pool to the reader endpoint of the Aurora database. <br>D. Move the code for opening the database connection in the Lambda function outside of the event handler.<br>These solutions directly address the performance issues caused by the large number of database connections under high load:<br>RDS Proxy (Option B):<br>RDS Proxy provides connection pooling for Aurora databases, which efficiently manages and reuses database connections.<br>By setting up RDS Proxy to the reader endpoint, read queries can be distributed across the three read replicas while maintaining a controlled number of actual database connections.<br>This significantly reduces connection overhead and prevents connection exhaustion, which is critical when the application is under high load.<br>RDS Proxy also handles connection multiplexing, allowing multiple Lambda invocations to share a smaller pool of database connections.<br>Moving connection code outside the event handler (Option D):<br>In Lambda functions, code outside the event handler executes only when a new execution environment is initialized, not on every invocation.<br>By moving the database connection code outside the handler, the connection can be reused across multiple invocations of the same Lambda instance.<br>This reduces the overhead of repeatedly establishing new database connections for each request, improving response times and reducing the total number of connections.<br>Option C (Lambda Provisioned Concurrency) would help reduce cold starts and improve initial response times, but it doesn't directly address the database connection issue. While it might be beneficial for overall application performance, it's not one of the most effective solutions for the specific problem of managing a large number of database connections.<br>The combination of RDS Proxy for connection pooling and moving the database connection code outside the Lambda event handler provides the most effective solution for improving the application's performance under high load by efficiently managing database connections.<br>Sources<br>Community | We Improved Our Lambda Warm Start Speed by 95%! Here’s How （https://community.aws/content/2e2OlZen47W4OziSbu1on004vFI/improved-lambda-warm-start-speed-95）<br>RDS Proxy causing a consistent increase in DB Connections from Lambda | AWS re:Post （https://repost.aws/questions/QU2hiJKCLUQcq5ApSro0ixMQ/rds-proxy-causing-a-consistent-increase-in-db-connections-from-lambda）<br>Which is preferred, Lambda-&gt;RDS Proxy-&gt;RDS or Lambda-&gt;RDS? | AWS re:Post （https://repost.aws/questions/QU1U72jyYWTcisPaIF3CSSqg/which-is-preferred-lambda-rds-proxy-rds-or-lambda-rds）<br>Aurora Read Replica Scale In Connection Issue with RDS Proxy and Lambda | AWS re:Post （https://repost.aws/questions/QUKpsQ6HemSxWm0AjL3BSaDQ/aurora-read-replica-scale-in-connection-issue-with-rds-proxy-and-lambda）<br><br><br>
</div>

</details>

    
# 49/529 

<div style="color:blue">single</div>
<br>Question #49<br>A company is planning to host a web application on AWS and wants to load balance the traffic across a group of Amazon EC2 instances. One of the security requirements is to enable end-to-end encryption in transit between the client and the web server.<br><br><br>Which solution will meet this requirement?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Place the EC2 instances behind an Application Load Balancer (ALB). Provision an SSL certificate using AWS Certificate Manager (ACM), and associate the SSL certificate with the ALB. Export the SSL certificate and install it on each EC2 instance. Configure the ALB to listen on port 443 and to forward traffic to port 443 on the instances.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Associate the EC2 instances with a target group. Provision an SSL certificate using AWS Certificate Manager (ACM). Create an Amazon CloudFront distribution and configure it to use the SSL certificate. Set CloudFront to use the target group as the origin server.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Place the EC2 instances behind an Application Load Balancer (ALB). Provision an SSL certificate using AWS Certificate Manager (ACM), and associate the SSL certificate with the ALB. Provision a third-party SSL certificate and install it on each EC2 instance. Configure the ALB to listen on port 443 and to forward traffic to port 443 on the instances.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Place the EC2 instances behind a Network Load Balancer (NLB). Provision a third-party SSL certificate and install it on the NLB and on each EC2 instance. Configure the NLB to listen on port 443 and to forward traffic to port 443 on the instances.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #49<br>A company is planning to host a web application on AWS and wants to load balance the traffic across a group of Amazon EC2 instances. One of the security requirements is to enable end-to-end encryption in transit between the client and the web server.<br><br><br>Which solution will meet this requirement?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>Based on the information provided, the correct answer for implementing end-to-end encryption in transit between the client and the web server is:<br>C. Place the EC2 instances behind an Application Load Balancer (ALB). Provision an SSL certificate using AWS Certificate Manager (ACM), and associate the SSL certificate with the ALB. Provision a third-party SSL certificate and install it on each EC2 instance. Configure the ALB to listen on port 443 and to forward traffic to port 443 on the instances.<br>This solution provides true end-to-end encryption because:<br>The connection between the client and the ALB is encrypted using the ACM certificate associated with the ALB, securing the first part of the communication path.<br>The connection between the ALB and the EC2 instances is also encrypted using the third-party SSL certificates installed on each EC2 instance, securing the second part of the communication path.<br>By configuring the ALB to listen on port 443 (HTTPS) and forward traffic to port 443 on the instances, the entire communication path remains encrypted without any point where the traffic is unencrypted.<br>Option B does not provide end-to-end encryption because:<br>While CloudFront would use an SSL certificate to encrypt traffic between the client and CloudFront, the question mentions using a target group as the origin.<br>Target groups don't support SSL termination directly - they would typically be used with an ALB.<br>The solution doesn't specify how the traffic would be encrypted between CloudFront and the EC2 instances.<br>True end-to-end encryption requires that the data remains encrypted throughout its entire journey from the client to the web server. Only option C ensures that both segments of the connection (client to ALB and ALB to EC2) are encrypted, meeting the security requirement for end-to-end encryption in transit.<br>Sources<br>Encryption-in-transit for public sector workloads with AWS Nitro Enclaves and AWS Certificate Manager | AWS Public Sector Blog （https://aws.amazon.com/cn/blogs/publicsector/encryption-in-transit-public-sector-workloads-aws-nitro-enclaves-aws-certificate-manager/）<br>SEC09-BP02 Enforce encryption in transit - Security Pillar （https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/sec_protect_data_transit_encrypt.html）<br>SEC09-BP02 Enforce encryption in transit - AWS Well-Architected Framework (2023-04-10) （https://docs.aws.amazon.com/wellarchitected/2023-04-10/framework/sec_protect_data_transit_encrypt.html）<br>Activate end-to-end HTTPS connectivity with AWS PrivateLink | AWS re:Post （https://repost.aws/knowledge-center/privatelink-https-connectivity）<br>Configuring HTTPS for your Elastic Beanstalk environment - AWS Elastic Beanstalk （https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/configuring-https.html）<br>
</div>

</details>

    
# 50/529 

<div style="color:blue">single</div>
<br>Question #50<br>A company wants to migrate its data analytics environment from on premises to AWS. The environment consists of two simple Node.js applications. One of the applications collects sensor data and loads it into a MySQL database. The other application aggregates the data into reports. When the aggregation jobs run, some of the load jobs fail to run correctly. <br><br><br>The company must resolve the data loading issue. The company also needs the migration to occur without interruptions or changes for the company’s customers. <br><br><br>What should a solutions architect do to meet these requirements? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Set up an Amazon Aurora MySQL database as a replication target for the on-premises database. Create an Aurora Replica for the Aurora MySQL database, and move the aggregation jobs to run against the Aurora Replica. Set up collection endpoints as AWS Lambda functions behind a Network Load Balancer (NLB), and use Amazon RDS Proxy to write to the Aurora MySQL database. When the databases are synced, disable the replication job and restart the Aurora Replica as the primary instance. Point the collector DNS record to the NLB.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Set up an Amazon Aurora MySQL database. Use AWS Database Migration Service (AWS DMS) to perform continuous data replication from the on-premises database to Aurora. Move the aggregation jobs to run against the Aurora MySQL database. Set up collection endpoints behind an Application Load Balancer (ALB) as Amazon EC2 instances in an Auto Scaling group. When the databases are synced, point the collector DNS record to the ALDisable the AWS DMS sync task after the cutover from on premises to AWS.&nbsp;
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Set up an Amazon Aurora MySQL database. Use AWS Database Migration Service (AWS DMS) to perform continuous data replication from the on-premises database to Aurora. Create an Aurora Replica for the Aurora MySQL database, and move the aggregation jobs to run against the Aurora Replica. Set up collection endpoints as AWS Lambda functions behind an Application Load Balancer (ALB), and use Amazon RDS Proxy to write to the Aurora MySQL database. When the databases are synced, point the collector DNS record to the ALB. Disable the AWS DMS sync task after the cutover from on premises to AWS.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Set up an Amazon Aurora MySQL database. Create an Aurora Replica for the Aurora MySQL database, and move the aggregation jobs to run against the Aurora Replica. Set up collection endpoints as an Amazon Kinesis data stream. Use Amazon Kinesis Data Firehose to replicate the data to the Aurora MySQL database. When the databases are synced, disable the replication job and restart the Aurora Replica as the primary instance. Point the collector DNS record to the Kinesis data stream.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #50<br>A company wants to migrate its data analytics environment from on premises to AWS. The environment consists of two simple Node.js applications. One of the applications collects sensor data and loads it into a MySQL database. The other application aggregates the data into reports. When the aggregation jobs run, some of the load jobs fail to run correctly. <br><br><br>The company must resolve the data loading issue. The company also needs the migration to occur without interruptions or changes for the company’s customers. <br><br><br>What should a solutions architect do to meet these requirements? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>The correct answer isC. Here's why:<br> Key Requirements:<br>1.Migrate without interruptions or changes for customers: This requires a seamless cutover with minimal downtime.<br>2.Resolve data loading issues: The aggregation jobs are causing load jobs to fail, so separating the workloads (aggregation vs. data collection) is critical.<br>3.Use AWS services effectively: The solution should leverage AWS managed services for scalability, reliability, and cost-efficiency.<br> Why Option C is Correct:<br>-AWS DMS for continuous replication: Ensures the on-premises MySQL database is synced with Aurora MySQL before cutover.<br>-Aurora Replica for aggregation jobs: Offloads the aggregation workload to a read replica, preventing interference with the primary database's write performance (resolving the load job failures).<br>-Lambda + ALB for collection endpoints: <br> &nbsp;- Lambda is serverless and scales automatically for the data collection application.<br> &nbsp;- ALB routes traffic to Lambda, providing a single endpoint for customers.<br>-RDS Proxy: Manages database connections efficiently, preventing connection pool issues for Lambda functions.<br>-Cutover process: <br> &nbsp;- After syncing, the DNS record is updated to point to the ALB (minimal downtime).<br> &nbsp;- AWS DMS is disabled post-cutover.<br> Why Other Options Are Incorrect:<br>-A: Uses a Network Load Balancer (NLB) instead of ALB, which is less optimal for HTTP-based Node.js apps. Also, restarting the replica as primary is unnecessary with Aurora's failover capabilities.<br>-B: Uses EC2 instances instead of Lambda, which adds unnecessary management overhead and doesn’t fully leverage serverless scalability.<br>-D: Uses Kinesis for data collection, which is overkill for this use case (simple sensor data loading) and doesn’t address the aggregation job issue as cleanly as an Aurora Replica.<br> Summary:<br>OptionC provides the most seamless migration, resolves the performance issue by separating read/write workloads, and uses the most appropriate AWS services (Lambda, ALB, RDS Proxy, and Aurora Replica). <br>
</div>

</details>

    
# 51/529 

<div style="color:blue">single</div>
Question #51<br>A health insurance company stores personally identifiable information (PII) in an Amazon S3 bucket. The company uses server-side encryption with S3 managed encryption keys (SSE-S3) to encrypt the objects. According to a new requirement, all current and future objects in the S3 bucket must be encrypted by keys that the company’s security team manages. The S3 bucket does not have versioning enabled.<br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. In the S3 bucket properties, change the default encryption to SSE-S3 with a customer managed key. Use the AWS CLI to re-upload all objects in the S3 bucket. Set an S3 bucket policy to deny unencrypted PutObject requests.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. In the S3 bucket properties, change the default encryption to server-side encryption with AWS KMS managed encryption keys (SSE-KMS). Set an S3 bucket policy to deny unencrypted PutObject requests. Use the AWS CLI to re-upload all objects in the S3 bucket.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. In the S3 bucket properties, change the default encryption to server-side encryption with AWS KMS managed encryption keys (SSE-KMS). Set an S3 bucket policy to automatically encrypt objects on GetObject and PutObject requests.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. In the S3 bucket properties, change the default encryption to AES-256 with a customer managed key. Attach a policy to deny unencrypted PutObject requests to any entities that access the S3 bucket. Use the AWS CLI to re-upload all objects in the S3 bucket.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
Question #51<br>A health insurance company stores personally identifiable information (PII) in an Amazon S3 bucket. The company uses server-side encryption with S3 managed encryption keys (SSE-S3) to encrypt the objects. According to a new requirement, all current and future objects in the S3 bucket must be encrypted by keys that the company’s security team manages. The S3 bucket does not have versioning enabled.<br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Based on the given question and requirements, the correct solution is:<br>B. In the S3 bucket properties, change the default encryption to server-side encryption with AWS KMS managed encryption keys (SSE-KMS). Set an S3 bucket policy to deny unencrypted PutObject requests. Use the AWS CLI to re-upload all objects in the S3 bucket. [[1]](https://repost.aws/questions/QUa2uGgWvVTeCAkp6vKHBmdw/how-to-encrypt-your-object-in-s3)<br>This solution meets the requirements for the following reasons:<br>1. It changes the encryption method from SSE-S3 to SSE-KMS, allowing the company's security team to manage the encryption keys.<br>2. It ensures that all future objects will be encrypted using the new SSE-KMS method by changing the default encryption settings.<br>3. The S3 bucket policy that denies unencrypted PutObject requests adds an extra layer of security, preventing any unencrypted objects from being uploaded. [[2]](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingDSSEncryption.html)<br>4. Re-uploading all existing objects using the AWS CLI ensures that all current objects in the bucket are also encrypted with the new SSE-KMS method. [[3]](https://docs.aws.amazon.com/AmazonS3/latest/userguide/serv-side-encryption.html)<br>Implementation steps:<br>1. Change the default encryption in the S3 bucket properties to SSE-KMS.<br>2. Create a customer-managed KMS key for the security team to manage.<br>3. Set up an S3 bucket policy to deny unencrypted PutObject requests.<br>4. Use the AWS CLI to download and then re-upload all existing objects in the bucket, which will apply the new encryption method.<br>It's important to note that this process may take some time depending on the number and size of objects in the bucket. Also, ensure that proper access controls are in place for the KMS key to maintain the principle of least privilege.<br>Option C is incorrect because it suggests using GetObject and PutObject requests to automatically encrypt objects, which is not a valid method for changing the encryption of existing objects in S3.<br>For the most up-to-date information on S3 encryption and best practices, please refer to the official AWS documentation.<br>Sources<br>[1] [[1] How to encrypt your object in S3 | AWS re:Post] (https://repost.aws/questions/QUa2uGgWvVTeCAkp6vKHBmdw/how-to-encrypt-your-object-in-s3)<br>[3] [[2] Using dual-layer server-side encryption with AWS KMS keys (DSSE-KMS) - Amazon Simple Storage Service] (https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingDSSEncryption.html)<br>[6] [[3] Protecting data with server-side encryption - Amazon Simple Storage Service] (https://docs.aws.amazon.com/AmazonS3/latest/userguide/serv-side-encryption.html)<br><br><br>
</div>

</details>

    
# 52/529 

<div style="color:blue">single</div>
<br>Question #52<br>A company is running a web application in the AWS Cloud. The application consists of dynamic content that is created on a set of Amazon EC2 instances. The EC2 instances run in an Auto Scaling group that is confi gured as a target group for an Application Load Balancer (ALB). <br><br><br>The company is using an Amazon CloudFront distribution to distribute the application globally. The CloudFront distribution uses the ALB as an origin. The company uses Amazon Route 53 for DNS and has created an A record of www.example.com for the CloudFront distribution. <br><br><br>A solutions architect must confi gure the application so that itis highly available and fault tolerant. <br><br><br>Which solution meets these requirements? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Provision a full, secondary application deployment in a different AWS Region. Update the Route 53 A record to be a failover record. Add both of the CloudFront distributions as values. Create Route 53 health checks.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Provision an ALB, an Auto Scaling group, and EC2 instances in a different AWS Region. Update the CloudFront distribution, and create a second origin for the new ALB. Configure one origin as primary and one origin as secondary.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Provision an Auto Scaling group and EC2 instances in a different AWS Region. Create a second target for the new Auto Scaling group in the ALB. Set up the failover routing algorithm on the ALB.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Provision a full, secondary application deployment in a different AWS Region. Create a second CloudFront distribution, and add the new application setup as an origin. Create an AWS Global Accelerator accelerator. Add both of the CloudFront distributions as endpoints.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #52<br>A company is running a web application in the AWS Cloud. The application consists of dynamic content that is created on a set of Amazon EC2 instances. The EC2 instances run in an Auto Scaling group that is confi gured as a target group for an Application Load Balancer (ALB). <br><br><br>The company is using an Amazon CloudFront distribution to distribute the application globally. The CloudFront distribution uses the ALB as an origin. The company uses Amazon Route 53 for DNS and has created an A record of www.example.com for the CloudFront distribution. <br><br><br>A solutions architect must confi gure the application so that itis highly available and fault tolerant. <br><br><br>Which solution meets these requirements? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>The correct answer isB. &nbsp;<br>Explanation: &nbsp;<br>The question requires ahighly available and fault-tolerant solution for a web application using CloudFront with an ALB as the origin. The best approach is toset up a secondary origin in another AWS Region and configure CloudFront to failover to it if the primary origin is unhealthy. &nbsp;<br>-Option B suggests: &nbsp;<br> &nbsp;- Deploying a secondary ALB, Auto Scaling group, and EC2 instances in a different AWS Region. &nbsp;<br> &nbsp;- Updating the CloudFront distribution to include thesecond origin. &nbsp;<br> &nbsp;- Creating anorigin group (a feature that allows CloudFront to failover to a secondary origin if the primary fails). &nbsp;<br> &nbsp;- This ensures that if the primary Region fails, CloudFront automatically routes traffic to the secondary Region. &nbsp;<br>Why not the other options? &nbsp;<br>-Option A: Uses Route 53 failover with two CloudFront distributions, but this isnot optimal because CloudFront already has built-in origin failover capabilities. Also, Route 53 failover would require DNS propagation time, whereas CloudFront origin failover is faster. &nbsp;<br>-Option C: Suggests adding a second target group to thesame ALB, but this does not providecross-Region redundancy (ALB is Region-bound). &nbsp;<br>-Option D: Uses AWS Global Accelerator, which isunnecessary since CloudFront already provides global distribution. Also, it adds complexity without significant benefits over CloudFront's native failover. &nbsp;<br>Conclusion: &nbsp;<br>Option B is the best solution because it leverages CloudFront'sorigin failover capability, ensuring high availability and fault tolerance without relying on slower DNS-based failover. &nbsp;<br>
</div>

</details>

    
# 53/529 

<div style="color:blue">single</div>
<br>Question #53<br>A company has an organization in AWS Organizations that has a large number of AWS accounts. One of the AWS accounts is designated as a transit account and has a transit gateway that is shared with all of the other AWS accounts. AWS Site-to-Site VPN connections are configured between all of the company’s global offices and the transit account. <br><br><br>The company has AWS Config enabled on all of its accounts. The company’s networking team needs to centrally manage a list of internal IP address ranges that belong to the global offices. Developers will reference this list to gain access to their applications securely.<br><br>Which solution meets these requirements with the LEAST amount of operational overhead?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create a JSON file that is hosted in Amazon S3 and that lists all of the internal IP address ranges. Configure an Amazon Simple Notification Service (Amazon SNS) topic in each of the accounts that can be invoked when the JSON file is updated. Subscribe an AWS Lambda function to the SNS topic to update all relevant security group rules with the updated IP address ranges.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create a new AWS Config managed rule that contains all of the internal IP address ranges. Use the rule to check the security groups in each of the accounts to ensure compliance with the list of IP address ranges. Configure the rule to automatically remediate any noncompliant security group that is detected.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. In the transit account, create a VPC prefix list with all of the internal IP address ranges. Use AWS Resource Access Manager to share the prefix list with all of the other accounts. Use the shared prefix list to configure security group rules in the other accounts.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. In the transit account, create a security group with all of the internal IP address ranges. Configure the security groups in the other accounts to reference the transit account&rsquo;s security group by using a nested security group reference of &ldquo;/sg-1a2b3c4d&rdquo;.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #53<br>A company has an organization in AWS Organizations that has a large number of AWS accounts. One of the AWS accounts is designated as a transit account and has a transit gateway that is shared with all of the other AWS accounts. AWS Site-to-Site VPN connections are configured between all of the company’s global offices and the transit account. <br><br><br>The company has AWS Config enabled on all of its accounts. The company’s networking team needs to centrally manage a list of internal IP address ranges that belong to the global offices. Developers will reference this list to gain access to their applications securely.<br><br>Which solution meets these requirements with the LEAST amount of operational overhead?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>The correct answer isC. &nbsp;<br>Explanation: &nbsp;<br>The requirement is tocentrally manage a list of internal IP address ranges with theleast operational overhead, allowing developers to reference this list in security group rules. &nbsp;<br>-Option A involves manual updates to an S3 file, SNS notifications, and Lambda functions to update security groups. This introduces complexity and operational overhead. &nbsp;<br>-Option B uses AWS Config rules for compliance checks and remediation, but this is reactive (detects and fixes misconfigurations rather than centrally managing the list). &nbsp;<br>-Option C usesVPC Prefix Lists (a native AWS feature) to store IP ranges and shares them across accounts usingAWS Resource Access Manager (RAM). This allows security groups in any account to reference the centrally managed prefix list, reducing overhead. &nbsp;<br>-Option D suggests referencing a security group from another account, butsecurity groups cannot be shared across accounts in this way (nested security group references only work within the same VPC). &nbsp;<br>Why C is the Best Choice: &nbsp;<br>✅Centralized management (single prefix list in the transit account). &nbsp;<br>✅Least operational overhead (shared via RAM, automatically available in all accounts). &nbsp;<br>✅Directly usable in security group rules (no need for custom automation). &nbsp;<br>Thus,C is the correct answer.<br>
</div>

</details>

    
# 54/529 

<div style="color:blue">single</div>
<br>Question #54<br>A company runs a new application as a static website in Amazon S3. The company has deployed the application toa production AWS account and uses Amazon CloudFront to deliver the website. The website calls an Amazon API Gateway REST API. An AWS Lambda function backs each API method. <br><br><br>The company wants to create a CSV report every 2 weeks to show each API Lambda function’s recommended configured memory, recommended cost, and the price difference between current configurations and the recommendations. The company will store the reports in an S3 bucket.<br><br>Which solution will meet these requirements with the LEAST development time? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create a Lambda function that extracts metrics data for each API Lambda function from Amazon CloudWatch Logs for the 2-week period. Collate the data into tabular format. Store the data as a .csv file in an S3 bucket. Create an Amazon EventBridge rule to schedule the Lambda function to run every 2 weeks.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. &nbsp;Opt in to AWS Compute Optimizer. Create a Lambda function that calls the ExportLambdaFunctionRecommendations operation. Export the .csv file to an S3 bucket. Create an Amazon EventBridge rule to schedule the Lambda function to run every 2 weeks.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Opt in to AWS Compute Optimizer. Set up enhanced infrastructure metrics. Within the Compute Optimizer console, schedule a job to export the Lambda recommendations to a .csv file. Store the file in an S3 bucket every 2 weeks.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Purchase the AWS Business Support plan for the production account. Opt in to AWS Compute Optimizer for AWS Trusted Advisor checks. In the Trusted Advisor console, schedule a job to export the cost optimization checks to a .csv file. Store the file in an S3 bucket every 2 weeks.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #54<br>A company runs a new application as a static website in Amazon S3. The company has deployed the application toa production AWS account and uses Amazon CloudFront to deliver the website. The website calls an Amazon API Gateway REST API. An AWS Lambda function backs each API method. <br><br><br>The company wants to create a CSV report every 2 weeks to show each API Lambda function’s recommended configured memory, recommended cost, and the price difference between current configurations and the recommendations. The company will store the reports in an S3 bucket.<br><br>Which solution will meet these requirements with the LEAST development time? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>The correct answer isB. &nbsp;<br> Explanation: &nbsp;<br>The requirements are to generate a CSV report every 2 weeks showing: &nbsp;<br>1. Recommended memory configurations for API Lambda functions &nbsp;<br>2. Recommended cost &nbsp;<br>3. Price difference between current and recommended configurations &nbsp;<br>AWS Compute Optimizer is the best service for this task because it provides Lambda function memory recommendations based on historical usage. &nbsp;<br># WhyB is the best option: &nbsp;<br>-Opt in to AWS Compute Optimizer (required to get recommendations). &nbsp;<br>-ExportLambdaFunctionRecommendations API call retrieves the needed data in CSV format. &nbsp;<br>-Lambda function + EventBridge rule automates the report generation every 2 weeks. &nbsp;<br>-Least development effort (just calling an API and storing the result, no manual data processing). &nbsp;<br># Why the other options are incorrect: &nbsp;<br>-A: Requires manually extracting and processing CloudWatch Logs (high development effort). &nbsp;<br>-C: Compute Optimizer does not natively support scheduled CSV exports (must use API). &nbsp;<br>-D: AWS Business Support and Trusted Advisor do not provide Lambda memory recommendations in this way. &nbsp;<br>Thus,B meets the requirements with the least development time. &nbsp;<br>
</div>

</details>

    
# 55/529 

<div style="color:blue">multiple</div>
<br>Question #55<br>A company’s factory and automation applications are running in a single VPC. More than 20 applications run on a combination of Amazon EC2, Amazon Elastic Container Service (Amazon ECS), and Amazon RDS. <br><br><br>The company has software engineers spread across three teams. One of the three teams owns each application, and each time is responsible for the cost and performance of all of its applications. Team resources have tags that represent their application and team. The teams use IAM access for daily activities. The company needs to determine which costs on the monthly AWS bill are attributable to each application or team. <br><br><br>The company also must be able to create reports to compare costs from the last 12 months and to help forecast costs for the next 12 months. A solutions architect must recommend an AWS Billing and Cost Management solution that provides these cost reports.<br><br>Which combination of actions will meet these requirements? (Choose three.) <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Activate the user-deﬁned cost allocation tags that represent the application and the team.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Activate the AWS generated cost allocation tags that represent the application and the team.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create a cost category for each application in Billing and Cost Management.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Activate IAM access to Billing and Cost Management.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Create a cost budget.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
F. Enable Cost Explorer.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #55<br>A company’s factory and automation applications are running in a single VPC. More than 20 applications run on a combination of Amazon EC2, Amazon Elastic Container Service (Amazon ECS), and Amazon RDS. <br><br><br>The company has software engineers spread across three teams. One of the three teams owns each application, and each time is responsible for the cost and performance of all of its applications. Team resources have tags that represent their application and team. The teams use IAM access for daily activities. The company needs to determine which costs on the monthly AWS bill are attributable to each application or team. <br><br><br>The company also must be able to create reports to compare costs from the last 12 months and to help forecast costs for the next 12 months. A solutions architect must recommend an AWS Billing and Cost Management solution that provides these cost reports.<br><br>Which combination of actions will meet these requirements? (Choose three.) <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">ACF</span>
<br>The correct combination of actions to meet the requirements is: &nbsp;<br>A. Activate the user-defined cost allocation tags that represent the application and the team. &nbsp;<br>*(The teams already have tags for applications and teams, so enabling these as cost allocation tags will allow cost tracking by these dimensions.)* &nbsp;<br>C. Create a cost category for each application in Billing and Cost Management. &nbsp;<br>*(Cost Categories allow grouping costs by business dimensions, such as applications or teams, even if tags are inconsistent.)* &nbsp;<br>F. Enable Cost Explorer. &nbsp;<br>*(Cost Explorer provides cost visualization, historical trends over 12 months, and forecasting capabilities.)* &nbsp;<br> Why not the others? &nbsp;<br>-B. AWS-generated tags (like `aws:createdBy`) are not relevant here—the teams already have custom tags. &nbsp;<br>-D. IAM access to billing is unrelated to cost reporting. &nbsp;<br>-E. Cost budgets are for setting spending alerts, not historical analysis or forecasting. &nbsp;<br> Final Answer: &nbsp;A, C, F <br>
</div>

</details>

    
# 56/529 

<div style="color:blue">single</div>
<br>Question #56<br>An AWS customer has a web application that runs on premises. The web application fetches data from a third-party API that is behind a firewall. The third party accepts only one public CIDR block in each client’s allow list. <br><br><br>The customer wants to migrate their web application to the AWS Cloud. The application will be hosted on a set of Amazon EC2 instances behind an Application Load Balancer (ALB) in a VPC. The ALB is located in public subnets. The EC2 instances are located in private subnets. NAT gateways provide internet access to the private subnets. <br><br><br>How should a solutions architect ensure that the web application can continue to call the third-party API after the migration?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Associate a block of customer-owned public IP addresses to the VPC. Enable public IP addressing for public subnets in the VPC.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Register a block of customer-owned public IP addresses in the AWS account. Create Elastic IP addresses from the address block and assign them to the NAT gateways in the VPC.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create Elastic IP addresses from the block of customer-owned IP addresses. Assign the static Elastic IP addresses to the ALB.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Register a block of customer-owned public IP addresses in the AWS account. Set up AWS Global Accelerator to use Elastic IP addresses from the address block. Set the ALB as the accelerator endpoint.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #56<br>An AWS customer has a web application that runs on premises. The web application fetches data from a third-party API that is behind a firewall. The third party accepts only one public CIDR block in each client’s allow list. <br><br><br>The customer wants to migrate their web application to the AWS Cloud. The application will be hosted on a set of Amazon EC2 instances behind an Application Load Balancer (ALB) in a VPC. The ALB is located in public subnets. The EC2 instances are located in private subnets. NAT gateways provide internet access to the private subnets. <br><br><br>How should a solutions architect ensure that the web application can continue to call the third-party API after the migration?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>The correct answer is B. Register a block of customer-owned public IP addresses in the AWS account. Create Elastic IP addresses from the address block and assign them to the NAT gateways in the VPC.<br> Explanation:<br>1.Problem Context: &nbsp;<br> &nbsp; - The third-party API only accepts requests from a singlepublic CIDR block (a fixed set of IP addresses).<br> &nbsp; - The web application runs on EC2 instances inprivate subnets, which access the internet viaNAT gateways.<br> &nbsp; - The NAT gateways provide outbound internet connectivity for the EC2 instances, but by default, they useAWS-owned public IPs, which are not fixed or controllable by the customer.<br>2.Why Option B is Correct: &nbsp;<br> &nbsp; - Bybringing your own public IP addresses (BYOIP) and assigning them asElastic IPs (EIPs) to the NAT gateways, all outbound traffic from the EC2 instances will use these fixed IPs.<br> &nbsp; - The third-party API can then whitelist this CIDR block, ensuring the application can still access the API after migration.<br>3.Why Other Options Are Incorrect: &nbsp;<br> &nbsp; -A: Enabling public IPs for public subnets affects instances in those subnets, not the private subnet EC2 instances calling the API. &nbsp;<br> &nbsp; -C: ALBs do not support static Elastic IP assignments (they use AWS-managed IPs). &nbsp;<br> &nbsp; -D: Global Accelerator provides fixed IPs for incoming traffic, not outbound traffic from EC2 instances.<br> Conclusion: &nbsp;<br>Assigning customer-owned Elastic IPs to NAT gateways ensures that all outbound API calls from the EC2 instances originate from a known, whitelisted IP range. &nbsp;<br>Final Answer: B<br>
</div>

</details>

    
# 57/529 

<div style="color:blue">single</div>
<br>Question #57<br>A company with several AWS accounts is using AWS Organizations and service control policies (SCPs). An administrator created the following SCP and has attached it to an organizational unit (OU) that contains AWS account 1111-1111-1111: <br><img src="https://up.zaixiankaoshi.com/5240831/question/84e247f2b716db7432e6c7e949e6e496.png" alt="84e247f2b716db7432e6c7e949e6e496.png" data-href="" style=""/><br>Developers working in account 1111-1111-1111 complain that they cannot create Amazon S3 buckets. How should the administrator address this problem?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Add s3:CreateBucket with &ldquo;Allow&rdquo; effect to the SCP.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Remove the account from the OU, and attach the SCP directly to account 1111-1111-1111.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Instruct the developers to add Amazon S3 permissions to their IAM entities.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Remove the SCP from account 1111-1111-1111.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #57<br>A company with several AWS accounts is using AWS Organizations and service control policies (SCPs). An administrator created the following SCP and has attached it to an organizational unit (OU) that contains AWS account 1111-1111-1111: <br><img src="https://up.zaixiankaoshi.com/5240831/question/84e247f2b716db7432e6c7e949e6e496.png" alt="84e247f2b716db7432e6c7e949e6e496.png" data-href="" style=""/><br>Developers working in account 1111-1111-1111 complain that they cannot create Amazon S3 buckets. How should the administrator address this problem?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>Based on the information provided, the correct answer is:<br>C. Instruct the developers to add Amazon S3 permissions to their IAM entities.<br>This is the correct solution because:<br>Service Control Policies (SCPs) in AWS Organizations act as permission boundaries or guardrails that limit the maximum permissions available in an account, but they do not grant any permissions themselves.<br>Even though the SCP content wasn't provided in the question, we can determine that the issue is not with the SCP blocking S3 bucket creation. If that were the case, adding permissions to IAM entities wouldn't help, as SCPs override IAM permissions when they explicitly deny actions.<br>The developers are likely missing the necessary IAM permissions to create S3 buckets. SCPs only define the maximum available permissions, but users still need to have those permissions granted through IAM policies attached to their roles, users, or groups.<br>Option A (adding s3:CreateBucket with "Allow" effect to the SCP) is incorrect because SCPs don't grant permissions; they only restrict them. Adding an allow statement to an SCP doesn't grant permissions to users.<br>Option B (removing the account from the OU and attaching the SCP directly) wouldn't solve the permission issue, as it would just change where the SCP is attached without addressing the underlying IAM permission problem.<br>Option D (removing the SCP from the account) is incorrect because the problem isn't that the SCP is blocking the action (if it were, the solution would be to modify the SCP, not remove it entirely).<br>The correct approach is to ensure that the developers have the necessary IAM permissions (s3:CreateBucket) attached to their IAM roles, users, or groups, which is what option C suggests.<br>Sources<br>Enforcing enterprise-wide preventive controls with AWS Organizations | AWS Cloud Operations Blog （https://aws.amazon.com/cn/blogs/mt/enforcing-enterprise-wide-preventive-controls-with-aws-organizations/）<br>Service control policies (SCPs) - AWS Organizations （https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html）<br>Policies and permissions in AWS Identity and Access Management - AWS Identity and Access Management（https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html） <br>When to use AWS Organizations - AWS Account Management （https://docs.aws.amazon.com/accounts/latest/reference/using-orgs.html）<br>I cant access all my private repositories in my ECR | AWS re:Post （https://repost.aws/questions/QUtkQFbO_1R4uiXcvDXAFvOg/i-cant-access-all-my-private-repositories-in-my-ecr）<br>Troubleshoot SCPs explicit deny errors in AWS Organizations | AWS re:Post（https://repost.aws/knowledge-center/iam-organizations-scp-deny-error） <br>
</div>

</details>

    
# 58/529 

<div style="color:blue">single</div>
<br>Question #58<br>A company has a monolithic application that is critical to the company’s business. The company hosts the application on an Amazon EC2 instance that runs Amazon Linux 2. The company’s application team receives a directive from the legal department to back up the data from the instance’s encrypted Amazon Elastic Block Store (Amazon EBS) volume to an Amazon S3 bucket. The application team does not have the administrative SSH key pair for the instance. The application must continue to serve the users.<br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Attach a role to the instance with permission to write to Amazon S3. Use the AWS Systems Manager Session Manager option to gain access to the instance and run commands to copy data into Amazon S3.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an image of the instance with the reboot option turned on. Launch a new EC2 instance from the image. Attach a role to the new instance with permission to write to Amazon S3. Run a command to copy data into Amazon S3.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Take a snapshot of the EBS volume by using Amazon Data Lifecycle Manager (Amazon DLM). Copy the data to Amazon S3.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an image of the instance. Launch a new EC2 instance from the image. Attach a role to the new instance with permission to write to Amazon S3. Run a command to copy data into Amazon S3.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #58<br>A company has a monolithic application that is critical to the company’s business. The company hosts the application on an Amazon EC2 instance that runs Amazon Linux 2. The company’s application team receives a directive from the legal department to back up the data from the instance’s encrypted Amazon Elastic Block Store (Amazon EBS) volume to an Amazon S3 bucket. The application team does not have the administrative SSH key pair for the instance. The application must continue to serve the users.<br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>The correct answer is C. Take a snapshot of the EBS volume by using Amazon Data Lifecycle Manager (Amazon DLM). Copy the data to Amazon S3.<br> Explanation:<br>1.Requirements:<br> &nbsp; - Back up data from an encrypted EBS volume to Amazon S3.<br> &nbsp; - The application must remain running (no downtime).<br> &nbsp; - The team does not have SSH access (no direct instance access).<br>2.Why Option C is Correct:<br> &nbsp; -EBS Snapshots are the standard way to back up EBS volumes without downtime.<br> &nbsp; -Amazon Data Lifecycle Manager (DLM) automates snapshot creation and retention.<br> &nbsp; - Snapshots can becopied to S3 (indirectly via AWS Backup or other methods).<br> &nbsp; - No need to access the instance directly (no SSH required).<br> &nbsp; - The application continues running without interruption.<br>3.Why Other Options Are Incorrect:<br> &nbsp; -A: While Session Manager allows access without SSH, manually copying data to S3 is inefficient and not scalable for backups.<br> &nbsp; -B & D: Creating a new instance from an AMI involves downtime (reboot/restart), which violates the requirement of continuous service.<br> Conclusion:<br>Option C is the best solution because it usesautomated EBS snapshots (via DLM) to safely back up data without downtime or requiring SSH access.<br>参考：<br>[1] [Storage options for your Amazon EC2 instances - Amazon Elastic Compute Cloud] (https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Storage.html)<br>[3] [Use Amazon S3 with Amazon EC2 instances - Amazon Elastic Compute Cloud] (https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonS3.html)<br>[6] [Migrate to a new instance type by launching a new EC2 instance - Amazon Elastic Compute Cloud] (https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/migrate-instance-configuration.html)<br>
</div>

</details>

    
# 59/529 

<div style="color:blue">multiple</div>
<br>Question #59<br>A solutions architect needs to copy data from an Amazon S3 bucket in one AWS account to a new S3 bucket in a new AWS account. The solutions architect must implement a solution that uses the AWS CLI.<br><br>Which combination of steps will successfully copy the data? (Choose three.)<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create a bucket policy to allow the source bucket to list its contents and to put objects and set object ACLs in the destination bucket. Attach the bucket policy to the destination bucket.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create a bucket policy to allow a user in the destination account to list the source bucket&rsquo;s contents and read the source bucket&rsquo;s objects. Attach the bucket policy to the source bucket.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an IAM policy in the source account. Configure the policy to allow a user in the source account to list contents and get objects in the source bucket, and to list contents, put objects, and set object ACLs in the destination bucket. Attach the policy to the user.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an IAM policy in the destination account. Configure the policy to allow a user in the destination account to list contents and get objects in the source bucket, and to list contents, put objects, and set object ACLs in the destination bucket. Attach the policy to the user.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Run the aws s3 sync command as a user in the source account. Specify the source and destination buckets to copy the data.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
F. Run the aws s3 sync command as a user in the destination account. Specify the source and destination buckets to copy the data.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #59<br>A solutions architect needs to copy data from an Amazon S3 bucket in one AWS account to a new S3 bucket in a new AWS account. The solutions architect must implement a solution that uses the AWS CLI.<br><br>Which combination of steps will successfully copy the data? (Choose three.)<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">BDF</span>
<br>To successfully copy data from an Amazon S3 bucket in one AWS account to a new S3 bucket in another AWS account using the AWS CLI, the following combination of steps is required:<br>Correct Answer: B, D, F &nbsp;<br>Explanation: &nbsp;<br>1.Step B: &nbsp;<br> &nbsp; - Abucket policy must be attached to thesource bucket to allow the destination account's user tolist objects (s3:ListBucket) andread objects (s3:GetObject). &nbsp;<br> &nbsp; - This ensures the destination account hasread access to the source bucket. &nbsp;<br>2.Step D: &nbsp;<br> &nbsp; - AnIAM policy must be created in thedestination account and attached to the user who will run the `aws s3 sync` command. &nbsp;<br> &nbsp; - This policy should grant permissions to: &nbsp;<br> &nbsp; &nbsp; -Read from the source bucket (`s3:ListBucket`, `s3:GetObject`). &nbsp;<br> &nbsp; &nbsp; -Write to the destination bucket (`s3:ListBucket`, `s3:PutObject`, `s3:PutObjectAcl`). &nbsp;<br>3.Step F: &nbsp;<br> &nbsp; - The `aws s3 sync` command must be runfrom the destination account’s user (the one with the IAM policy from Step D). &nbsp;<br> &nbsp; - This ensures the user has the necessary permissions to pull data from the source bucket and write it to the destination bucket. &nbsp;<br>Why Not Other Options? &nbsp;<br>-A: Incorrect because thebucket policy should be on the source bucket (not destination) to allow cross-account access. &nbsp;<br>-C: Incorrect because the IAM policy should be in thedestination account, not the source account. &nbsp;<br>-E: Incorrect because the `aws s3 sync` should be run from thedestination account, not the source account. &nbsp;<br>
</div>

</details>

    
# 60/529 

<div style="color:blue">single</div>
<br>Question #60<br>A company built an application based on AWS Lambda deployed in an AWS CloudFormation stack. The last production release of the web application introduced an issue that resulted in an outage lasting several minutes. A solutions architect must adjust the deployment process to support a canary release.<br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an alias for every new deployed version of the Lambda function. Use the AWS CLI update-alias command with the routing-conﬁg parameter to distribute the load.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Deploy the application into a new CloudFormation stack. Use an Amazon Route 53 weighted routing policy to distribute the load.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create a version for every new deployed Lambda function. Use the AWS CLI update-function-conﬁguration command with the routing-conﬁg parameter to distribute the load.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Configure AWS CodeDeploy and use CodeDeployDefault.OneAtATime in the Deployment conﬁguration to distribute the load.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #60<br>A company built an application based on AWS Lambda deployed in an AWS CloudFormation stack. The last production release of the web application introduced an issue that resulted in an outage lasting several minutes. A solutions architect must adjust the deployment process to support a canary release.<br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>Based on the information provided, the correct answer is:<br>A. Create an alias for every new deployed version of the Lambda function. Use the AWS CLI update-alias command with the routing-config parameter to distribute the load.<br>This solution meets the requirements for implementing a canary release deployment for the Lambda-based application because:<br>Lambda aliases with routing configuration provide a built-in way to implement canary deployments for Lambda functions. The routing-config parameter allows you to specify what percentage of traffic should go to the new version versus the old version.<br>This approach allows for gradual traffic shifting between Lambda function versions, which is the essence of a canary deployment. You can start by routing a small percentage of traffic to the new version, monitor its performance, and gradually increase the percentage if everything works well.<br>If issues are detected with the new version, you can quickly revert all traffic back to the previous stable version by updating the alias routing configuration, minimizing potential downtime.<br>This solution doesn't require taking the application offline or creating duplicate infrastructure, ensuring the application continues to serve users during the deployment process.<br>The other options are not as suitable:<br>Option B (using Route 53 weighted routing with a new CloudFormation stack) would require duplicating the entire infrastructure, which is more complex and resource-intensive than necessary.<br>Option C is incorrect because the update-function-configuration command doesn't have a routing-config parameter for traffic distribution.<br>Option D (using CodeDeploy with OneAtATime configuration) doesn't implement a true canary deployment pattern. The OneAtATime deployment configuration deploys to one instance at a time, which isn't appropriate for Lambda functions and doesn't provide the gradual traffic shifting needed for canary releases.<br>Lambda aliases with routing configuration provide the most straightforward and effective way to implement canary deployments for Lambda functions while minimizing risk and potential downtime.<br>Sources<br>Deployment approaches - Serverless Applications Lens （https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/deployment-approaches.html）<br>Blue/Green deployment | AWS re:Post （https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/deployment-approaches.html）<br>Implement Lambda canary deployments using a weighted alias - AWS Lambda （https://docs.aws.amazon.com/lambda/latest/dg/configuring-alias-routing.html）<br>AWS CodeDeploy - Overview of Deployment Options on AWS （https://docs.aws.amazon.com/whitepapers/latest/overview-deployment-options/aws-codedeploy.html）<br>Iterate rapidly, stay agile - AWS Serverless Multi-Tier Architectures with Amazon API Gateway and AWS Lambda （https://docs.aws.amazon.com/whitepapers/latest/serverless-multi-tier-architectures-api-gateway-lambda/iterate-rapidly-stay-agile.html）<br>
</div>

</details>

    
# 61/529 

<div style="color:blue">single</div>
<br>Question #61<br>A finance company hosts a data lake in Amazon S3. The company receives ﬁnancial data records over SFTP every night from several third parties. The company runs its own SFTP server on an Amazon EC2 instance in a public subnet of a VPC. After the ﬁles are uploaded, they are moved to the data lake by a cron job that runs on the same instance. The SFTP server is reachable on DNS sftp.example.com through the use of Amazon Route 53.<br><br>What should a solutions architect do to improve the reliability and scalability of the SFTP solution?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Move the EC2 instance into an Auto Scaling group. Place the EC2 instance behind an Application Load Balancer (ALB). Update the DNS record sftp.example.com in Route 53 to point to the ALB.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Migrate the SFTP server to AWS Transfer for SFTP. Update the DNS record sftp.example.com in Route 53 to point to the server endpoint hostname.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Migrate the SFTP server to a ﬁle gateway in AWS Storage Gateway. Update the DNS record sftp.example.com in Route 53 to point to the ﬁle gateway endpoint.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Place the EC2 instance behind a Network Load Balancer (NLB). Update the DNS record sftp.example.com in Route 53 to point to the NLB.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #61<br>A finance company hosts a data lake in Amazon S3. The company receives ﬁnancial data records over SFTP every night from several third parties. The company runs its own SFTP server on an Amazon EC2 instance in a public subnet of a VPC. After the ﬁles are uploaded, they are moved to the data lake by a cron job that runs on the same instance. The SFTP server is reachable on DNS sftp.example.com through the use of Amazon Route 53.<br><br>What should a solutions architect do to improve the reliability and scalability of the SFTP solution?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Based on the information provided, the correct answer is:<br>B. Migrate the SFTP server to AWS Transfer for SFTP. Update the DNS record sftp.example.com in Route 53 to point to the server endpoint hostname.<br>This solution best addresses the requirement to improve reliability and scalability of the SFTP solution because:<br>AWS Transfer for SFTP is a fully managed service that automatically handles high availability and scalability without requiring manual intervention. This eliminates the need to manage EC2 instances, patching, and maintenance of the SFTP server software.<br>The service automatically scales to accommodate varying loads of file transfers, which directly addresses the scalability requirement mentioned in the question.<br>AWS Transfer for SFTP integrates natively with Amazon S3, making it ideal for the company's use case of moving files to their data lake in S3. This eliminates the need for custom cron jobs to transfer the files.<br>The service supports custom domain names, allowing the company to continue using their existing sftp.example.com domain by simply updating the DNS record in Route 53 to point to the new Transfer for SFTP endpoint.<br>As a managed service, AWS Transfer for SFTP provides better reliability as AWS handles all the underlying infrastructure, redundancy, and availability concerns.<br>Option A (using an Auto Scaling group with an Application Load Balancer) is not ideal because:<br>SFTP protocol (which runs on TCP port 22) is not natively supported by Application Load Balancers, which are designed for HTTP/HTTPS traffic. ALBs don't support the SFTP protocol.<br>This approach would still require the company to manage the SFTP server software, security patches, and configuration across multiple EC2 instances.<br>It would require custom scripting to ensure file consistency across multiple instances in the Auto Scaling group.<br>The company would still need to maintain the cron jobs for transferring files to S3.<br>AWS Transfer for SFTP provides a more comprehensive solution that directly addresses both the reliability and scalability requirements while simplifying the overall architecture.<br>Sources<br>Transfer data from Snowflake to S3 | AWS re:Post （https://repost.aws/questions/QUAS44xqj_SdKIf0vdRZiNfQ/transfer-data-from-snowflake-to-s3）<br>AWS Transfer Family SFTP server vs SFTP connector | AWS re:Post （https://repost.aws/questions/QU_vV7XcunSvmE4TEgWFXSkA/aws-transfer-family-sftp-server-vs-sftp-connector）<br>SFTP through AWS LB | AWS re:Post （https://repost.aws/questions/QUbOaWvs92SjWPjTYDKt13dA/sftp-through-aws-lb）<br>
</div>

</details>

    
# 62/529 

<div style="color:blue">single</div>
<br>Question #62<br>A company wants to migrate an application to Amazon EC2 from VMware Infrastructure that runs in an on-premises data center. A solutions architect must preserve the software and configuration settings during the migration.<br><br>What should the solutions architect do to meet these requirements? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Configure the AWS DataSync agent to start replicating the data store to Amazon FSx for Windows File Server. Use the SMB share to host the VMware data store. Use VM Import/Export to move the VMs to Amazon EC2.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use the VMware vSphere client to export the application as an image in Open Virtualization Format (OVF) format. Create an Amazon S3 bucket to store the image in the destination AWS Region. Create and apply an IAM role for VM Import. Use the AWS CLI to run the EC2 import command.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Configure AWS Storage Gateway for ﬁles service to export a Common Internet File System (CIFS) share. Create a backup copy to the shared folder. Sign in to the AWS Management Console and create an AMI from the backup copy. Launch an EC2 instance that is based on the AMI.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create a managed-instance activation for a hybrid environment in AWS Systems Manager. Download and install Systems Manager Agent on the on-premises VM. Register the VM with Systems Manager to be a managed instance. Use AWS Backup to create a snapshot of the VM and create an AMI. Launch an EC2 instance that is based on the AMI.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #62<br>A company wants to migrate an application to Amazon EC2 from VMware Infrastructure that runs in an on-premises data center. A solutions architect must preserve the software and configuration settings during the migration.<br><br>What should the solutions architect do to meet these requirements? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Based on the information provided, the correct answer is:<br>B. Use the VMware vSphere client to export the application as an image in Open Virtualization Format (OVF) format. Create an Amazon S3 bucket to store the image in the destination AWS Region. Create and apply an IAM role for VM Import. Use the AWS CLI to run the EC2 import command.<br>This solution is the most appropriate for preserving software and configuration settings during migration from VMware to EC2 because:<br>VM Import/Export is specifically designed to migrate existing virtual machines from your on-premises environment to Amazon EC2 while preserving the software and configuration settings, which is the key requirement mentioned in the question.<br>The process described in option B follows the standard VM Import workflow:<br>Exporting the VM as an OVF file from VMware vSphere<br>Creating an S3 bucket to store the exported image<br>Setting up the necessary IAM permissions for the import process<br>Using the EC2 import command to convert the VM to an Amazon EC2 AMI<br>This approach ensures that all software installations, configurations, and settings from the original VMware VM are preserved in the resulting EC2 instance.<br>Option A is not the correct approach because:<br>AWS DataSync is primarily designed for transferring files and objects between storage systems, not for migrating complete virtual machines with their operating systems and configurations.<br>While FSx for Windows File Server could store the VMware data, this approach doesn't provide a direct path to convert the VMware VM into an EC2 instance.<br>The combination of DataSync and VM Import/Export in this manner doesn't represent the standard workflow for VM migration and would likely introduce unnecessary complexity.<br>The VM Import/Export service described in option B is specifically designed for this migration scenario and provides the most direct path to preserve all software and configuration settings when moving from VMware to EC2.<br>Sources<br>Relocate migration options - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/migration-vmware-aws/relocate-options.html）<br>Choosing a migration approach for relocating your VMware applications and workloads to the AWS Cloud - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/migration-vmware-aws/welcome.html）<br>What is VM Import/Export? - VM Import/Export （https://docs.aws.amazon.com/vm-import/latest/userguide/what-is-vmimport.html）<br>Choosing a migration approach - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/migration-vmware-aws/migration-approach.html）<br>Accelerate VMware Migrations to AWS using AWS Migration Hub Journeys | AWS Cloud Operations Blog （https://aws.amazon.com/cn/blogs/mt/accelerate-vmware-migrations-to-aws-using-aws-migration-hub-journeys/）<br>VMware ESXI to AWS migration | AWS re:Post （https://repost.aws/questions/QUyuhMhfmQTvGlvy0lI8-f9w/vmware-esxi-to-aws-migration）<br>
</div>

</details>

    
# 63/529 

<div style="color:blue">multiple</div>
<br>Question #63<br>A video processing company has an application that downloads images from an Amazon S3 bucket, processes the images, stores a transformed image in a second S3 bucket, and updates metadata about the image in an Amazon DynamoDB table. The application is written in Node.js and runs by using an AWS Lambda function. The Lambda function is invoked when a new image is uploaded to Amazon S3. <br><br><br>The application ran without incident for a while. However, the size of the images has grown significantly. The Lambda function is now failing frequently with timeout errors. The function timeout is set to its maximum value. A solutions architect needs to refactor the application’s architecture to prevent invocation failures. The company does not want to manage the underlying infrastructure.<br><br>Which combination of steps should the solutions architect take to meet these requirements? (Choose two.) <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Modify the application deployment by building a Docker image that contains the application code. Publish the image to Amazon Elastic Container Registry (Amazon ECR).
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create a new Amazon Elastic Container Service (Amazon ECS) task definition with a compatibility type of AWS Fargate. Configure the task definition to use the new image in Amazon Elastic Container Registry (Amazon ECR). Adjust the Lambda function to invoke an ECS task by using the ECS task definition when a new file arrives in Amazon S3.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an AWS Step Functions state machine with a Parallel state to invoke the Lambda function. Increase the provisioned concurrency of the Lambda function.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create a new Amazon Elastic Container Service (Amazon ECS) task definition with a compatibility type of Amazon EC2. Configure the task definition to use the new image in Amazon Elastic Container Registry (Amazon ECR). Adjust the Lambda function to invoke an ECS task by using the ECS task definition when a new file arrives in Amazon S3.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Modify the application to store images on Amazon Elastic File System (Amazon EFS) and to store metadata on an Amazon RDS DB instance. Adjust the Lambda function to mount the EFS file share.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #63<br>A video processing company has an application that downloads images from an Amazon S3 bucket, processes the images, stores a transformed image in a second S3 bucket, and updates metadata about the image in an Amazon DynamoDB table. The application is written in Node.js and runs by using an AWS Lambda function. The Lambda function is invoked when a new image is uploaded to Amazon S3. <br><br><br>The application ran without incident for a while. However, the size of the images has grown significantly. The Lambda function is now failing frequently with timeout errors. The function timeout is set to its maximum value. A solutions architect needs to refactor the application’s architecture to prevent invocation failures. The company does not want to manage the underlying infrastructure.<br><br>Which combination of steps should the solutions architect take to meet these requirements? (Choose two.) <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">AB</span>
<br>The correct answers are A and B. &nbsp;<br>Explanation: &nbsp;<br>The Lambda function is timing out because the image processing task is exceeding Lambda's maximum timeout limit (15 minutes) and possibly hitting other resource constraints (memory, CPU). Since the company does not want to manage infrastructure,AWS Fargate (serverless ECS) is the best alternative. &nbsp;<br>#Steps to Refactor the Architecture: &nbsp;<br>1.A. Modify the application deployment by building a Docker image that contains the application code. Publish the image to Amazon ECR. &nbsp;<br> &nbsp; - Containerizing the application allows it to run in a more scalable and flexible environment (ECS Fargate). &nbsp;<br> &nbsp; - Amazon ECR stores the Docker image for deployment. &nbsp;<br>2.B. Create a new Amazon ECS task definition with a compatibility type of AWS Fargate. Configure the task definition to use the new image in Amazon ECR. Adjust the Lambda function to invoke an ECS task when a new file arrives in Amazon S3. &nbsp;<br> &nbsp; -AWS Fargate removes the need to manage servers (meets the "no infrastructure management" requirement). &nbsp;<br> &nbsp; - The Lambda function can now act as a lightweightorchestrator, triggering an ECS task for heavy processing instead of doing the work itself. &nbsp;<br>Why Not the Other Options? &nbsp;<br>-C: Step Functions with Parallel state and provisioned concurrency does not solve the timeout issue (Lambda still has execution limits). &nbsp;<br>-D: UsingEC2-based ECS requires managing infrastructure (violates the requirement). &nbsp;<br>-E: Storing images on EFS and metadata on RDS does not address the core issue (Lambda timeout due to long processing). &nbsp;<br>Conclusion: &nbsp;<br>A + B is the best solution—migrating the heavy processing toECS Fargate while keeping Lambda as the lightweight trigger. &nbsp;<br>
</div>

</details>

    
# 64/529 

<div style="color:blue">single</div>
<br>Question #64<br>A company has an organization in AWS Organizations. The company is using AWS Control Tower to deploy a landing zone for the organization. The company wants to implement governance and policy enforcement. The company must implement a policy that will detect Amazon RDS DB instances that are not encrypted at rest in the company’s production OU.<br><br>Which solution will meet this requirement? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Turn on mandatory guardrails in AWS Control Tower. Apply the mandatory guardrails to the production OU.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Enable the appropriate guardrail from the list of strongly recommended guardrails in AWS Control Tower. Apply the guardrail to the production OU.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Use AWS Conﬁg to create a new mandatory guardrail. Apply the rule to all accounts in the production OU.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create a custom SCP in AWS Control Tower. Apply the SCP tothe production OU.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #64<br>A company has an organization in AWS Organizations. The company is using AWS Control Tower to deploy a landing zone for the organization. The company wants to implement governance and policy enforcement. The company must implement a policy that will detect Amazon RDS DB instances that are not encrypted at rest in the company’s production OU.<br><br>Which solution will meet this requirement? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Based on the information provided, the correct answer is:<br>B. Enable the appropriate guardrail from the list of strongly recommended guardrails in AWS Control Tower. Apply the guardrail to the production OU.<br>This is the correct solution because:<br>AWS Control Tower has different types of guardrails: mandatory guardrails and strongly recommended guardrails.<br>Mandatory guardrails are automatically enabled when you set up AWS Control Tower and cannot be disabled. They provide foundational security and operational benefits that are essential for maintaining the integrity of your landing zone.<br>Strongly recommended guardrails are optional but highly advised based on AWS best practices. They can be enabled or disabled according to your organization's needs.<br>The specific guardrail that detects unencrypted Amazon RDS DB instances is called "Detect Whether Storage Encryption is Enabled for Amazon RDS Database Instances" and it is classified as a strongly recommended detective guardrail, not a mandatory guardrail.<br>This guardrail uses AWS Config rules to monitor RDS instances and check whether storage encryption is enabled, which directly addresses the requirement to detect RDS DB instances that are not encrypted at rest in the production OU.<br>Option A is incorrect because mandatory guardrails do not include the specific control for detecting unencrypted RDS instances. Mandatory guardrails focus on foundational security controls that cannot be disabled, while the RDS encryption detection is part of the strongly recommended guardrails that can be selectively applied to specific OUs like the production OU mentioned in the question.<br>Therefore, to implement a policy that will detect Amazon RDS DB instances that are not encrypted at rest in the company's production OU, the company should enable the appropriate guardrail from the list of strongly recommended guardrails in AWS Control Tower and apply it to the production OU.<br>Sources<br>Optional controls - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/designing-control-tower-landing-zone/optional.html）<br>Controls - Management and Governance Cloud Environment Guide （https://docs.aws.amazon.com/wellarchitected/latest/management-and-governance-guide/controls.html）<br>Strongly recommended controls with detective behavior - AWS Control Tower （https://docs.aws.amazon.com/controltower/latest/controlreference/strongly-recommended-detective-controls.html）<br>Preventive vs. Proactive vs. Detective Controls in AWS Control Tower | AWS re:Post (https://repost.aws/articles/ARbi64fKJCQsCpqOskL6vb4g/preventive-vs-proactive-vs-detective-controls-in-aws-control-tower)<br>
</div>

</details>

    
# 65/529 

<div style="color:blue">single</div>
<br>Question #65<br>A startup company hosts a fleet of Amazon EC2 instances in private subnets using the latest Amazon Linux 2 AMI. The company’s engineers rely heavily on SSH access to the instances for troubleshooting. <br><br><br>The company’s existing architecture includes the following: <br><br><br>• A VPC with private and public subnets, and a NAT gateway. <br>• Site-to-Site VPN for connectivity with the on-premises environment. <br>• EC2 security groups with direct SSH access from the on-premises environment. <br><br><br>The company needs to increase security controls around SSH access and provide auditing of commands run by the engineers. <br><br><br>Which strategy should a solutions architect use? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Install and conﬁgure EC2 Instance Connect on the ﬂeet of EC2 instances. Remove all security group rules attached to EC2 instances that allow inbound TCP on port 22. Advise the engineers to remotely access the instances by using the EC2 Instance Connect CLI.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Update the EC2 security groups to only allow inbound TCP on port 22 to the IP addresses of the engineer&rsquo;s devices. Install the Amazon CloudWatch agent on all EC2 instances and send operating system audit logs to CloudWatch Logs.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Update the EC2 security groups to only allow inbound TCP on port 22 to the IP addresses of the engineer&rsquo;s devices. Enable AWS Conﬁg for EC2 security group resource changes. Enable AWS Firewall Manager and apply a security group policy that automatically remediates changes to rules.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an IAM role with the AmazonSSMManagedInstanceCore managed policy attached. Attach the IAM role to all the EC2 instances. Remove all security group rules attached to the EC2 instances that allow inbound TCP on port 22. Have the engineers install the AWS Systems Manager Session Manager plugin for their devices and remotely access the instances by using the start-session API call from Systems Manager.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #65<br>A startup company hosts a fleet of Amazon EC2 instances in private subnets using the latest Amazon Linux 2 AMI. The company’s engineers rely heavily on SSH access to the instances for troubleshooting. <br><br><br>The company’s existing architecture includes the following: <br><br><br>• A VPC with private and public subnets, and a NAT gateway. <br>• Site-to-Site VPN for connectivity with the on-premises environment. <br>• EC2 security groups with direct SSH access from the on-premises environment. <br><br><br>The company needs to increase security controls around SSH access and provide auditing of commands run by the engineers. <br><br><br>Which strategy should a solutions architect use? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">D</span>
<br>The correct answer isD. &nbsp;<br>Explanation: &nbsp;<br>The company needs toincrease security controls around SSH access andprovide auditing of commands run by engineers. The best approach is to useAWS Systems Manager Session Manager, which provides: &nbsp;<br>No open inbound ports (eliminates SSH security risks) – Session Manager does not require inbound port 22 access, improving security. &nbsp;<br>Auditability – All session activity is logged in AWS CloudTrail and can be stored in S3 or CloudWatch Logs. &nbsp;<br>IAM-based access control – Engineers can be granted permissions via IAM policies. &nbsp;<br>No need for bastion hosts or NAT gateways – Sessions are established via AWS Systems Manager, reducing complexity. &nbsp;<br>Why not the other options? &nbsp;<br>-A: EC2 Instance Connect still relies on SSH and temporary SSH keys, which doesn’t fully eliminate SSH exposure. &nbsp;<br>-B & C: Both options still allow direct SSH access (port 22), which is less secure than using Session Manager. While logging helps, it doesn’t remove the attack surface. &nbsp;<br>Correct Answer: &nbsp;<br>D. Create an IAM role with the `AmazonSSMManagedInstanceCore` managed policy, attach it to EC2 instances, remove SSH security group rules, and have engineers use Session Manager. &nbsp;<br>This approach provides thehighest security and auditing capabilities while eliminating the need for open SSH ports.<br>
</div>

</details>

    
# 66/529 

<div style="color:blue">multiple</div>
<br>Question #66<br>A company that uses AWS Organizations allows developers to experiment on AWS. As part of the landing zone that the company has deployed, developers use their company email address to request an account. The company wants to ensure that developers are not launching costly services or running services unnecessarily. The company must give developers a ﬁxed monthly budget to limit their AWS costs.<br><br>Which combination of steps will meet these requirements? (Choose three.) <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an SCP to set a ﬁxed monthly account usage limit. Apply the SCP to the developer accounts.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use AWS Budgets to create a ﬁxed monthly budget for each developer&rsquo;s account as part of the account creation process.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an SCP to deny access to costly services and components. Apply the SCP to the developer accounts.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an IAM policy to deny access to costly services and components. Apply the IAM policy to the developer accounts.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Create an AWS Budgets alert action to terminate services when the budgeted amount is reached. Configure the action to terminate all services.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
F. Create an AWS Budgets alert action to send an Amazon Simple Notiﬁcation Service (Amazon SNS) notiﬁcation when the budgeted amount is reached. Invoke an AWS Lambda function to terminate all services.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #66<br>A company that uses AWS Organizations allows developers to experiment on AWS. As part of the landing zone that the company has deployed, developers use their company email address to request an account. The company wants to ensure that developers are not launching costly services or running services unnecessarily. The company must give developers a ﬁxed monthly budget to limit their AWS costs.<br><br>Which combination of steps will meet these requirements? (Choose three.) <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">BCF</span>
<br>Based on the information provided, the correct answer is:<br>B. Use AWS Budgets to create a fixed monthly budget for each developer's account as part of the account creation process. <br>C. Create an SCP to deny access to costly services and components. Apply the SCP to the developer accounts. <br>F. Create an AWS Budgets alert action to send an Amazon Simple Notification Service (Amazon SNS) notification when the budgeted amount is reached. Invoke an AWS Lambda function to terminate all services.<br>This combination of steps will effectively implement a fixed monthly budget for developers and limit AWS costs:<br>Option B establishes the foundation by creating a fixed monthly budget for each developer's account during the account creation process. AWS Budgets allows you to set specific budget amounts and track spending against those budgets.<br>Option C provides preventive controls by using Service Control Policies (SCPs) to deny access to costly services and components. This helps prevent developers from launching expensive resources in the first place, addressing the requirement to ensure "developers are not launching costly services."<br>Option F implements reactive controls by setting up an automated response when the budget limit is reached. The AWS Budgets alert action sends an SNS notification, which then triggers a Lambda function to terminate all services. This addresses the requirement to limit costs and prevent developers from "running services unnecessarily" beyond their fixed monthly budget.<br>Together, these three options create a comprehensive cost management strategy:<br>Preventive controls (SCPs) to block access to expensive services<br>Monitoring controls (AWS Budgets) to track spending against fixed budgets<br>Reactive controls (SNS notifications and Lambda functions) to automatically terminate services when budgets are exceeded<br>This approach ensures that developers can experiment on AWS while staying within their allocated budget, preventing unexpected or excessive costs for the company.<br>Sources<br>AWS Budgets & Billing | AWS re:Post (https://repost.aws/questions/QUWxq5rqz5RAaNUQxtd7KnQQ/aws-budgets-billing)<br>Budget methods - AWS Cost Management (https://docs.aws.amazon.com/cost-management/latest/userguide/budget-methods.html)<br>COST02-BP05 Implement cost controls - AWS Well-Architected Framework (https://docs.aws.amazon.com/wellarchitected/2023-10-03/framework/cost_govern_usage_controls.html)<br>COST02-BP05 Implement cost controls - Cost Optimization Pillar (https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/cost_govern_usage_controls.html)<br>AWS Rekognition | AWS re:Post (https://repost.aws/questions/QU0B7Z5vnzROOEmcB9edL_iQ/aws-rekognition)<br>DevOps team wants to automate cost monitoring and receive alerts if AWS costs exceed a certain threshold. What AWS services and automation strategies would you use?. | AWS re:Post (https://repost.aws/questions/QUWml6NyN8TLqU-zfvrIKa2g/devops-team-wants-to-automate-cost-monitoring-and-receive-alerts-if-aws-costs-exceed-a-certain-threshold-what-aws-services-and-automation-strategies-would-you-use)<br>Serverless Automated Cost Controls, Part1 | AWS Compute Blog (https://aws.amazon.com/cn/blogs/compute/serverless-automated-cost-controls-part1/)<br>COST02-BP05 Implement cost controls - AWS Well-Architected Framework (2023-04-10) (https://docs.aws.amazon.com/wellarchitected/2023-04-10/framework/cost_govern_usage_controls.html)<br>
</div>

</details>

    
# 67/529 

<div style="color:blue">single</div>
<br>Question #67<br>A company has applications in an AWS account that is named Source. The account is in an organization in AWS Organizations. One of the applications uses AWS Lambda functions and stores inventory data in an Amazon Aurora database. The application deploys the Lambda functions by using a deployment package. The company has configured automated backups for Aurora. <br><br><br>The company wants to migrate the Lambda functions and the Aurora database to a new AWS account that is named Target. The application processes critical data, so the company must minimize downtime.<br><br>Which solution will meet these requirements? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Download the Lambda function deployment package from the Source account. Use the deployment package and create new Lambda functions in the Target account. Share the automated Aurora DB cluster snapshot with the Target account.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Download the Lambda function deployment package from the Source account. Use the deployment package and create new Lambda functions in the Target account. Share the Aurora DB cluster with the Target account by using AWS Resource Access Manager (AWS RAM). Grant the Target account permission to clone the Aurora DB cluster.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Use AWS Resource Access Manager (AWS RAM) to share the Lambda functions and the Aurora DB cluster with the Target account. Grant the Target account permission to clone the Aurora DB cluster.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use AWS Resource Access Manager (AWS RAM) to share the Lambda functions with the Target account. Share the automated Aurora DB cluster snapshot with the Target account.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #67<br>A company has applications in an AWS account that is named Source. The account is in an organization in AWS Organizations. One of the applications uses AWS Lambda functions and stores inventory data in an Amazon Aurora database. The application deploys the Lambda functions by using a deployment package. The company has configured automated backups for Aurora. <br><br><br>The company wants to migrate the Lambda functions and the Aurora database to a new AWS account that is named Target. The application processes critical data, so the company must minimize downtime.<br><br>Which solution will meet these requirements? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>The correct answer isB. Here's why:<br> Key Requirements:<br>1.Migrate Lambda functions and Aurora database to a new AWS account (Target).<br>2.Minimize downtime (critical data processing).<br>3. The Lambda functions are deployed via adeployment package, and Aurora hasautomated backups.<br> Why Option B?<br>-Lambda Migration: &nbsp;<br> &nbsp;- Since Lambda functions are deployed via a deployment package, you can download the package from theSource account and recreate the functions in theTarget account. AWS RAMcannot be used to share Lambda functions directly (they are not shareable via RAM), so options C and D are incorrect for Lambda migration.<br> &nbsp;<br>-Aurora Migration: &nbsp;<br> &nbsp;- To minimize downtime, sharing thelive Aurora DB cluster via AWS RAM (instead of restoring from a snapshot) allows theTarget account to clone the database, ensuring minimal disruption. &nbsp;<br> &nbsp;- Automated snapshots (Option A) require arestore operation, which takes longer and causes more downtime compared to cloning a live cluster. &nbsp;<br> &nbsp;- AWS RAM enables cross-account sharing of Aurora clusters, and cloning is faster than snapshot restoration.<br> Why Not Other Options?<br>-A: Uses a snapshot (slower, more downtime). &nbsp;<br>-C: AWS RAM cannot share Lambda functions. &nbsp;<br>-D: AWS RAM cannot share Lambda functions, and using a snapshot is slower than cloning.<br> Conclusion: &nbsp;<br>B is the best solution because it efficiently migrates the Lambda functions (via redeployment) and minimizes Aurora downtime by using AWS RAM to share and clone the live cluster. &nbsp;<br>Answer: B<br>
</div>

</details>

    
# 68/529 

<div style="color:blue">single</div>
<br>Question #68<br>A company runs a Python script on an Amazon EC2 instance to process data. The script runs every 10 minutes. The script ingests files from an Amazon S3 bucket and processes the files. On average, the script takes approximately 5 minutes to process each file The script will not reprocess a file that the script has already processed. <br><br><br>The company reviewed Amazon CloudWatch metrics and noticed that the EC2 instance is idle for approximately 40% of the time because of the file processing speed. The company wants to make the workload highly available and scalable. The company also wants to reduce long-term management overhead. <br><br><br>Which solution will meet these requirements MOST cost-effectively? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Migrate the data processing script to an AWS Lambda function. Use an S3 event notification to invoke the Lambda function to process the objects when the company uploads the objects.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an Amazon Simple Queue Service (Amazon SQS) queue. Configure Amazon S3 to send event notifications to the SQS queue. Create an EC2 Auto Scaling group with a minimum size of one instance. Update the data processing script to poll the SQS queue. Process the S3 objects that the SQS message identifies.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Migrate the data processing script to a container image. Run the data processing container on an EC2 instance. Configure the container to poll the S3 bucket for new objects and to process the resulting objects.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Migrate the data processing script to a container image that runs on Amazon Elastic Container Service (Amazon ECS) on AWS Fargate. Create an AWS Lambda function that calls the Fargate RunTaskAPI operation when the container processes the file. Use an S3 event notification to invoke the Lambda function.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #68<br>A company runs a Python script on an Amazon EC2 instance to process data. The script runs every 10 minutes. The script ingests files from an Amazon S3 bucket and processes the files. On average, the script takes approximately 5 minutes to process each file The script will not reprocess a file that the script has already processed. <br><br><br>The company reviewed Amazon CloudWatch metrics and noticed that the EC2 instance is idle for approximately 40% of the time because of the file processing speed. The company wants to make the workload highly available and scalable. The company also wants to reduce long-term management overhead. <br><br><br>Which solution will meet these requirements MOST cost-effectively? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>Themost cost-effective solution that meets the requirements ofhigh availability, scalability, and reduced management overhead is:<br>Option A &nbsp;<br>Migrate the data processing script to an AWS Lambda function. Use an S3 event notification to invoke the Lambda function to process the objects when the company uploads the objects.<br>Why Option A? &nbsp;<br>1.Serverless & Cost-Effective: &nbsp;<br> &nbsp; - Lambda runs only when triggered (by S3 events), eliminating idle time. &nbsp;<br> &nbsp; - No need to manage EC2 instances or pay for unused compute time. &nbsp;<br>2.Highly Available & Scalable: &nbsp;<br> &nbsp; - Lambda automatically scales with the number of file uploads. &nbsp;<br> &nbsp; - No need to manage scaling policies (unlike EC2 Auto Scaling in Option B). &nbsp;<br>3.Reduced Management Overhead: &nbsp;<br> &nbsp; - No EC2 instances, containers, or clusters to manage (unlike Options B, C, and D). &nbsp;<br> &nbsp; - S3 event notifications directly trigger Lambda, simplifying the architecture. &nbsp;<br>Why Not Other Options? &nbsp;<br>-Option B: Uses EC2 Auto Scaling, which still requires managing instances and incurs costs during idle time. &nbsp;<br>-Option C: Running a container on EC2 still involves managing infrastructure and idle costs. &nbsp;<br>-Option D: Using Fargate + Lambda adds complexity and higher costs compared to a pure Lambda solution. &nbsp;<br>Conclusion &nbsp;<br>Option A is themost cost-effective, scalable, and low-management solution for this workload. &nbsp;<br>
</div>

</details>

    
# 69/529 

<div style="color:blue">single</div>
<br>Question #69<br>A financial services company in North America plans to release a new online web application to its customers on AWS. The company will launch the application in the us-east-1 Region on Amazon EC2 instances. The application must be highly available and must dynamically scale to meet user traffic. The company also wants to implement a disaster recovery environment for the application in the us-west-1 Region by using active-passive failover.<br><br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create a VPC in us-east-1 and a VPC in us-west-1. Configure VPC peering. In the us-east-1 VPC, create an Application Load Balancer (ALB) that extends across multiple Availability Zones in both VPCs. Create an Auto Scaling group that deploys the EC2 instances across the multiple Availability Zones in both VPCs. Place the Auto Scaling group behind the ALB.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create a VPC in us-east-1 and a VPC in us-west-1. In the us-east-1 VPC, create an Application Load Balancer (ALB) that extends across multiple Availability Zones in that VPC. Create an Auto Scaling group that deploys the EC2 instances across the multiple Availability Zones in the us-east-1 VPC. Place the Auto Scaling group behind the ALB. Set up the same configuration in the us-west-1 VPC. Create an Amazon Route 53 hosted zone. Create separate records for each ALB. Enable health checks to ensure high availability between Regions.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create a VPC in us-east-1 and a VPC in us-west-1. In the us-east-1 VPC, create an Application Load Balancer (ALB) that extends across multiple Availability Zones in that VPC. Create an Auto Scaling group that deploys the EC2 instances across the multiple Availability Zones in the us-east-1 VPC. Place the Auto Scaling group behind the ALB. Set up the same configuration in the us-west-1 VPC. Create an Amazon Route 53 hosted zone. Create separate records for each ALB. Enable health checks and configure a failover routing policy for each record.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create a VPC in us-east-1 and a VPC in us-west-1. Configure VPC peering. In the us-east-1 VPC, create an Application Load Balancer (ALB) that extends across multiple Availability Zones in both VPCs. Create an Auto Scaling group that deploys the EC2 instances across the multiple Availability Zones in both VPCs. Place the Auto Scaling group behind the ALB. Create an Amazon Route 53 hosted zone. Create a record for the ALB.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #69<br>A financial services company in North America plans to release a new online web application to its customers on AWS. The company will launch the application in the us-east-1 Region on Amazon EC2 instances. The application must be highly available and must dynamically scale to meet user traffic. The company also wants to implement a disaster recovery environment for the application in the us-west-1 Region by using active-passive failover.<br><br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>The correct answer isC. &nbsp;<br> Explanation:<br>The requirements are:<br>1.High availability in the primary Region (us-east-1) with dynamic scaling.<br>2.Disaster recovery (DR) in us-west-1 using anactive-passive failover model.<br>3. The solution must useAmazon Route 53 for DNS-based failover.<br>Let’s analyze the options:<br>#Option A ❌<br>-VPC peering is not required for a multi-Region failover setup (and VPC peering does not work across Regions).<br>- The ALBcannot span multiple VPCs or Regions, so this setup is invalid.<br>- No mention ofRoute 53 failover routing, which is required for active-passive DR.<br>#Option B ❌<br>- Correctly sets upALB + Auto Scaling in both Regions.<br>- However, itlacks a failover routing policy in Route 53, which is necessary for active-passive failover.<br>- Simply enabling health checks is not enough—you need to configurefailover routing.<br>#Option C ✅<br>-Correctly sets up ALB + Auto Scaling in both Regions (us-east-1 as active, us-west-1 as passive).<br>-Route 53 failover routing policy is configured with health checks, ensuring automatic failover if the primary Region fails.<br>- This matches theactive-passive disaster recovery requirement.<br>#Option D ❌<br>- Similar to Option A,VPC peering across Regions is not possible.<br>- The ALBcannot span multiple Regions.<br>- Nofailover routing policy is mentioned, only a single record.<br>Why C is the Best Answer:<br>-High Availability in Primary Region: ALB + Auto Scaling across multiple AZs in us-east-1.<br>-Disaster Recovery in Secondary Region: Passive deployment in us-west-1.<br>-Active-Passive Failover: Route 53 health checks and failover routing ensure automatic switch to us-west-1 if us-east-1 fails.<br>Thus,Option C is the correct solution. <br>
</div>

</details>

    
# 70/529 

<div style="color:blue">single</div>
Question #70<br><br><br><br>A company has an environment that has a single AWS account. A solutions architect is reviewing the environment to recommend what the company could improve specifi cally in terms of access to the AWS Management Console. The company’s IT support workers currently access the console for administrative tasks, authenticating with named IAM users that have been mapped to their job role. <br><br><br>The IT support workers no longer want to maintain both their Active Directory and IAM user accounts. They want to be able to access the console by using their existing Active Directory credentials. The solutions architect is using AWS IAM Identity Center (AWS Single Sign-On) to implement this functionality. <br><br><br>Which solution will meet these requirements MOST cost-effectively?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an organization in AWS Organizations. Turn on the IAM Identity Center feature in Organizations. Create and confi gure a directory in AWS Directory Service for Microsoft Active Directory (AWS Managed Microsoft AD) with a two-way trust to the company&rsquo;s on-premises Active Directory. Confi gure IAM Identity Center and set the AWS Managed Microsoft AD directory as the identity source. Create permission sets and map them to the existing groups within the AWS Managed Microsoft AD directory.&nbsp;
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an organization in AWS Organizations. Turn on the IAM Identity Center feature in Organizations. Create and confi gure an AD Connector to connect to the company&rsquo;s on-premises Active Directory. Confi gure IAM Identity Center and select the AD Connector as the identity source. Create permission sets and map them to the existing groups within the company&rsquo;s Active Directory.&nbsp;
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an organization in AWS Organizations. Turn on all features for the organization. Create and confi gure a directory in AWS Directory Service for Microsoft Active Directory (AWS Managed Microsoft AD) with a two-way trust to the company&rsquo;s on-premises Active Directory. Confi gure IAM Identity Center and select the AWS Managed Microsoft AD directory as the identity source. Create permission sets and map them to the existing groups within the AWS Managed Microsoft AD directory.&nbsp;
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. &nbsp;Create an organization in AWS Organizations. Turn on all features for the organization. Create and confi gure an AD Connector to connect to the company&rsquo;s on-premises Active Directory. Confi gure IAM Identity Center and set the AD Connector as the identity source. Create permission sets and map them to the existing groups within the company&rsquo;s Active Directory.&nbsp;
</div>
        
<details>

<summary>English</summary>

<div translate="no">
Question #70<br><br><br><br>A company has an environment that has a single AWS account. A solutions architect is reviewing the environment to recommend what the company could improve specifi cally in terms of access to the AWS Management Console. The company’s IT support workers currently access the console for administrative tasks, authenticating with named IAM users that have been mapped to their job role. <br><br><br>The IT support workers no longer want to maintain both their Active Directory and IAM user accounts. They want to be able to access the console by using their existing Active Directory credentials. The solutions architect is using AWS IAM Identity Center (AWS Single Sign-On) to implement this functionality. <br><br><br>Which solution will meet these requirements MOST cost-effectively?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">D</span>
https://www.examtopics.com/discussions/amazon/view/69172-exam-aws-certified-solutions-architect-professional-topic-1/ You are correct, I apologize for the oversight. To meet the requirements of the IT support workers, option D would be the correct solution: <br>This option will first enable all features in AWS Organizations, then create and configure an AD Connector to connect to the company's one premises Active Directory. Then, it will configure IAM Identity Center (AWS SSO) and set the AD Connector as the identity source, allowing the IT support workers to access the console using their existing Active Directory credentials. Finally, it will create permission sets and map them to the existing groups within the company's Active Directory. This solution will also be cost-effective as it does not involve creating a new directory in AWS Directory Service. <br>
</div>

</details>

    
# 71/529 

<div style="color:blue">multiple</div>
<br>Question #71<br>A video streaming company recently launched a mobile app for video sharing. The app uploads various files to an Amazon S3 bucket in the us-east-1 Region. The files range in size from 1 GB to 10 GB.<br><br><br>Users who access the app from Australia have experienced uploads that take long periods of time. Sometimes the files fail to completely upload for these users. A solutions architect must improve the app’s performance for these uploads.<br><br><br>Which solutions will meet these requirements? (Choose two.)<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Enable S3 Transfer Acceleration on the S3 bucket. Configure the app to use the Transfer Acceleration endpoint for uploads.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Configure an S3 bucket in each Region to receive the uploads. Use S3 Cross-Region Replication to copy the files to the distribution S3 bucket.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Set up Amazon Route 53 with latency-based routing to route the uploads to the nearest S3 bucket Region.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Configure the app to break the video files into chunks. Use a multipart upload to transfer files to Amazon S3.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Modify the app to add random prefixes to the files before uploading.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #71<br>A video streaming company recently launched a mobile app for video sharing. The app uploads various files to an Amazon S3 bucket in the us-east-1 Region. The files range in size from 1 GB to 10 GB.<br><br><br>Users who access the app from Australia have experienced uploads that take long periods of time. Sometimes the files fail to completely upload for these users. A solutions architect must improve the app’s performance for these uploads.<br><br><br>Which solutions will meet these requirements? (Choose two.)<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">AD</span>
<br>Based on the information provided, the correct answers are:<br>A. Enable S3 Transfer Acceleration on the S3 bucket. Configure the app to use the Transfer Acceleration endpoint for uploads.<br>D. Configure the app to break the video files into chunks. Use a multipart upload to transfer files to Amazon S3.<br>These solutions will improve the performance of large file uploads from Australia to the S3 bucket in us-east-1 for the following reasons:<br>S3 Transfer Acceleration (Option A):<br>This feature is specifically designed to optimize long-distance transfers across different geographic regions.<br>It uses Amazon CloudFront's globally distributed edge locations to route data through an optimized network path.<br>For users in Australia uploading to us-east-1, Transfer Acceleration can significantly improve transfer speeds (by 50-500% for cross-continental transfers).<br>It addresses the long upload times experienced by Australian users by providing a more efficient network path to the destination bucket.<br>Multipart Uploads (Option D):<br>This approach is particularly effective for large files (1-10 GB in this case).<br>Breaking files into smaller chunks allows for parallel uploads, increasing throughput.<br>If a part fails during upload, only that specific part needs to be retried rather than the entire file.<br>This directly addresses the issue of files failing to completely upload by providing resilience against network interruptions.<br>AWS recommends multipart uploads for files larger than 100MB, which applies to all files in this scenario (1-10 GB).<br>Option E (adding random prefixes) is incorrect because:<br>While prefix strategies can help with S3 performance for high-throughput scenarios with many small files, they don't significantly improve upload speeds for individual large files.<br>Random prefixes help distribute objects across multiple partitions to avoid throttling when you have extremely high request rates, but this doesn't address the network latency and reliability issues experienced by Australian users.<br>The combination of S3 Transfer Acceleration and multipart uploads provides the most effective solution for improving upload performance and reliability for large files being transferred from distant geographic locations like Australia to us-east-1.<br>Sources<br>Troubleshoot cross-region transfer issues - AWS Transfer Family （https://docs.aws.amazon.com/transfer/latest/userguide/cross-region-transfer-issues.html）<br>Using Amazon S3 Transfer Acceleration to Accelerate Geographically Disparate Data Transfers - Best Practices Design Patterns: Optimizing Amazon S3 Performance （https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html）<br>Performance guidelines for Amazon S3 - Amazon Simple Storage Service （https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance-guidelines.html）<br>Selection - Streaming Media Lens （https://docs.aws.amazon.com/wellarchitected/latest/streaming-media-lens/selection.html）<br>
</div>

</details>

    
# 72/529 

<div style="color:blue">single</div>
<br>Question #72<br>An application is using an Amazon RDS for MySQL Multi-AZ DB instance in the us-east-1 Region. After a failover test, the application lost the connections to the database and could not re-establish the connections. After a restart of the application, the application re-established the connections.<br><br><br>A solutions architect must implement a solution so that the application can re-establish connections to the database without requiring a restart.<br><br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an Amazon Aurora MySQL Serverless v1 DB instance. Migrate the RDS DB instance to the Aurora Serverless v1 DB instance. Update the connection settings in the application to point to the Aurora reader endpoint.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an RDS proxy. Configure the existing RDS endpoint as a target. Update the connection settings in the application to point to the RDS proxy endpoint.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create a two-node Amazon Aurora MySQL DB cluster. Migrate the RDS DB instance to the Aurora DB cluster. Create an RDS proxy. Configure the existing RDS endpoint as a target. Update the connection settings in the application to point to the RDS proxy endpoint.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an Amazon S3 bucket. Export the database to Amazon S3 by using AWS Database Migration Service (AWS DMS). Configure Amazon Athena to use the S3 bucket as a data store. Install the latest Open Database Connectivity (ODBC) driver for the application. Update the connection settings in the application to point to the Athena endpoint.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #72<br>An application is using an Amazon RDS for MySQL Multi-AZ DB instance in the us-east-1 Region. After a failover test, the application lost the connections to the database and could not re-establish the connections. After a restart of the application, the application re-established the connections.<br><br><br>A solutions architect must implement a solution so that the application can re-establish connections to the database without requiring a restart.<br><br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Based on the information provided, the correct answer is:<br>B. Create an RDS proxy. Configure the existing RDS endpoint as a target. Update the connection settings in the application to point to the RDS proxy endpoint.<br>This solution will meet the requirements because:<br>The core issue described in the scenario is that the application loses connections to the database during a failover event and cannot re-establish them without a restart. This is a common problem with direct database connections during failover events.<br>Amazon RDS Proxy is specifically designed to address connection management issues during failover events. It maintains a pool of database connections and actively manages them during failovers.<br>When a failover occurs with RDS Proxy in place:<br>The proxy is aware of the failover event<br>It preserves most existing connections, only canceling those in the middle of a transaction<br>It automatically redirects connections to the new primary instance without relying on DNS propagation<br>It queues incoming requests until new connections can be established<br>By pointing the application to the RDS Proxy endpoint instead of directly to the database, the application can maintain its connection to the proxy even when the underlying database fails over to the standby instance.<br>This solution doesn't require changing the database engine (staying with RDS for MySQL) and works with the existing Multi-AZ setup.<br>Option A (migrating to Aurora Serverless v1 and using the reader endpoint) is incorrect because:<br>Aurora reader endpoints are primarily designed for load balancing read traffic across multiple read replicas<br>Reader endpoints still rely on DNS propagation during failover events, which can cause connection issues<br>Reader endpoints don't provide the connection pooling and active connection management that RDS Proxy offers<br>Changing from RDS MySQL to Aurora Serverless is a more complex solution than needed to solve this specific connection management issue<br>RDS Proxy is the most appropriate solution for this scenario as it directly addresses the connection management problem during failover events without requiring application restarts.<br>Sources<br>Improving application availability with Amazon RDS Proxy | AWS Database Blog （https://aws.amazon.com/cn/blogs/database/improving-application-availability-with-amazon-rds-proxy/）<br>Targeted business outcomes - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/amazon-rds-proxy/targeted-business-outcomes.html）<br>Working with Amazon RDS Proxy endpoints - Amazon Aurora（https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/rds-proxy-endpoints.html） <br>RDS Proxy concepts and terminology - Amazon Relational Database Service （https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/rds-proxy.howitworks.html）<br>Improve application availability on Amazon Aurora | AWS Database Blog （https://aws.amazon.com/cn/blogs/database/improve-application-availability-on-amazon-aurora/）<br>RDS Proxy concepts and terminology - Amazon Aurora （https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/rds-proxy.howitworks.html）<br>
</div>

</details>

    
# 73/529 

<div style="color:blue">single</div>
<br>Question #73<br>A company is building a solution in the AWS Cloud. Thousands of devices will connect to the solution and send data. Each device needs to be able to send and receive data in real time over the MQTT protocol. Each device must authenticate by using a unique X.509 certificate.<br><br><br>Which solution will meet these requirements with the LEAST operational overhead?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Set up AWS IoT Core. For each device, create a corresponding Amazon MQ queue and provision a certificate. Connect each device to Amazon MQ.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create a Network Load Balancer (NLB) and configure it with an AWS Lambda authorizer. Run an MQTT broker on Amazon EC2 instances in an Auto Scaling group. Set the Auto Scaling group as the target for the NLB. Connect each device to the NLB.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Set up AWS IoT Core. For each device, create a corresponding AWS IoT thing and provision a certificate. Connect each device to AWS IoT Core.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Set up an Amazon API Gateway HTTP API and a Network Load Balancer (NLB). Create integration between API Gateway and the NLB. Configure a mutual TLS certificate authorizer on the HTTP API. Run an MQTT broker on an Amazon EC2 instance that the NLB targets. Connect each device to the NLB.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #73<br>A company is building a solution in the AWS Cloud. Thousands of devices will connect to the solution and send data. Each device needs to be able to send and receive data in real time over the MQTT protocol. Each device must authenticate by using a unique X.509 certificate.<br><br><br>Which solution will meet these requirements with the LEAST operational overhead?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>Based on the information provided, the correct answer is:<br>C. Set up AWS IoT Core. For each device, create a corresponding AWS IoT thing and provision a certificate. Connect each device to AWS IoT Core.<br>This solution will meet the requirements with the least operational overhead because:<br>AWS IoT Core is specifically designed for IoT scenarios where thousands of devices need to connect using the MQTT protocol. It's a fully managed service that handles the complexity of scaling to support thousands of concurrent device connections.<br>AWS IoT Core has built-in support for X.509 certificate management, making it easy to provision, manage, and rotate unique certificates for each device. This addresses the requirement for each device to authenticate using a unique X.509 certificate.<br>The "thing" concept in AWS IoT Core is designed to represent each physical device, providing a logical representation that can be associated with certificates, policies, and device shadows. This makes it straightforward to manage device identity and permissions.<br>As a fully managed service, AWS IoT Core eliminates the operational overhead of provisioning, managing, and scaling infrastructure components like MQTT brokers, load balancers, and EC2 instances.<br>Option A (using Amazon MQ) would involve higher operational overhead because:<br>Amazon MQ is not specifically optimized for IoT scenarios with thousands of devices<br>Creating and managing individual queues for each device would be cumbersome<br>Certificate management would be more manual compared to IoT Core<br>Option B (running MQTT brokers on EC2 with an NLB) would involve significantly higher operational overhead because:<br>You would need to manage EC2 instances, Auto Scaling groups, and a Network Load Balancer<br>You would need to implement and manage your own certificate authority and authentication system<br>You would be responsible for scaling, patching, and maintaining the MQTT broker software<br>AWS IoT Core provides the most streamlined solution with the least operational overhead for the specific requirements of connecting thousands of devices using MQTT with X.509 certificate authentication.<br>Sources<br>Connecting client devices to an AWS IoT Greengrass Core device with an MQTT broker - AWS IoT Greengrass （https://docs.aws.amazon.com/greengrass/v2/developerguide/connecting-to-mqtt.html）<br>Seamless migration: Securely transitioning large IoT fleets to AWS | The Internet of Things on AWS – Official Blog （https://aws.amazon.com/cn/blogs/iot/seamless-migration-securely-transitioning-large-iot-fleets-to-aws/）<br>Custom authentication with X.509 client certificates - AWS IoT Core （https://docs.aws.amazon.com/iot/latest/developerguide/custom-auth-509cert.html）<br>Choosing an AWS IoT service - Choosing an AWS IoT service （https://docs.aws.amazon.com/decision-guides/latest/iot-on-aws-how-to-choose/iot.html）<br>
</div>

</details>

    
# 74/529 

<div style="color:blue">single</div>
<br>Question #74<br>A company is running several workloads in a single AWS account. A new company policy states that engineers can provision only approved resources and that engineers must use AWS CloudFormation to provision these resources. A solutions architect needs to create a solution to enforce the new restriction on the IAM role that the engineers use for access.<br><br><br>What should the solutions architect do to create the solution?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Upload AWS CloudFormation templates that contain approved resources to an Amazon S3 bucket. Update the IAM policy for the engineers&rsquo; IAM role to only allow access to Amazon S3 and AWS CloudFormation. Use AWS CloudFormation templates to provision resources.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Update the IAM policy for the engineers&rsquo; IAM role with permissions to only allow provisioning of approved resources and AWS CloudFormation. Use AWS CloudFormation templates to create stacks with approved resources.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Update the IAM policy for the engineers&rsquo; IAM role with permissions to only allow AWS CloudFormation actions. Create a new IAM policy with permission to provision approved resources, and assign the policy to a new IAM service role. Assign the IAM service role to AWS CloudFormation during stack creation.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Provision resources in AWS CloudFormation stacks. Update the IAM policy for the engineers&rsquo; IAM role to only allow access to their own AWS CloudFormation stack.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #74<br>A company is running several workloads in a single AWS account. A new company policy states that engineers can provision only approved resources and that engineers must use AWS CloudFormation to provision these resources. A solutions architect needs to create a solution to enforce the new restriction on the IAM role that the engineers use for access.<br><br><br>What should the solutions architect do to create the solution?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>Based on the information provided, the correct answer is:<br>C. Update the IAM policy for the engineers' IAM role with permissions to only allow AWS CloudFormation actions. Create a new IAM policy with permission to provision approved resources, and assign the policy to a new IAM service role. Assign the IAM service role to AWS CloudFormation during stack creation.<br>This solution is the most appropriate because:<br>It follows the principle of least privilege by restricting the engineers' IAM role to only perform CloudFormation actions. This ensures engineers can only provision resources through CloudFormation as required by the new company policy.<br>By creating a separate IAM service role with permissions to provision only approved resources, the solution provides a clear separation of concerns. The engineers don't have direct permissions to create resources - they can only do so through CloudFormation using the service role.<br>When CloudFormation creates resources, it assumes the service role that has been carefully configured with permissions for only approved resources. This creates an additional layer of control and security.<br>This approach makes it easier to audit and track resource creation, as all changes must go through CloudFormation using the defined service role.<br>Option B is less secure because:<br>It gives engineers direct permissions to provision approved resources outside of CloudFormation<br>This could potentially allow engineers to bypass the requirement to use CloudFormation for resource provisioning<br>It doesn't provide the same level of separation between the ability to use CloudFormation and the ability to create resources<br>The approach in Option C is more aligned with AWS security best practices for CloudFormation deployments, as it ensures that:<br>Engineers can only use CloudFormation (enforcing the "must use CloudFormation" policy)<br>Only approved resources can be provisioned (enforcing the "only approved resources" policy)<br>The service role provides a controlled and auditable mechanism for resource creation<br>This implementation provides better security controls and more clearly enforces the new company policy.<br>Sources<br>Configuring least-privilege permissions to use CloudFormation - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/least-privilege-cloudformation/permissions-use-cloudformation.html）<br>Best practices for configuring identity-based policies for least-privilege CloudFormation access - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/least-privilege-cloudformation/best-practices-identity-based-policies.html）<br>Managing permissions for individuals - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/transitioning-to-multiple-aws-accounts/managing-permissions-for-individuals.html）<br>Service roles for CloudFormation - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/least-privilege-cloudformation/service-roles-for-cloudformation.html）<br>Implementing policies for least-privilege permissions for AWS CloudFormation - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/least-privilege-cloudformation/introduction.html）<br>
</div>

</details>

    
# 75/529 

<div style="color:blue">single</div>
<br>Question #75<br>A solutions architect is designing the data storage and retrieval architecture for a new application that a company will be launching soon. The application is designed to ingest millions of small records per minute from devices all around the world. Each record is less than 4 KB in size and needs to be stored in a durable location where it can be retrieved with low latency. The data is ephemeral and the company is required to store the data for 120 days only, after which the data can be deleted.<br><br><br>The solutions architect calculates that, during the course of a year, the storage requirements would be about 10-15 TB.<br><br>Which storage strategy is the MOST cost-effective and meets the design requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Design the application to store each incoming record as a single .csv file in an Amazon S3 bucket to allow for indexed retrieval. Configure a lifecycle policy to delete data older than 120 days.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Design the application to store each incoming record in an Amazon DynamoDB table properly configured for the scale. Configure the DynamoDB Time to Live (TTL) feature to delete records older than 120 days.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Design the application to store each incoming record in a single table in an Amazon RDS MySQL database. Run a nightly cron job that runs a query to delete any records older than 120 days.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Design the application to batch incoming records before writing them to an Amazon S3 bucket. Update the metadata for the object to contain the list of records in the batch and use the Amazon S3 metadata search feature to retrieve the data. Configure a lifecycle policy to delete the data after 120 days.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #75<br>A solutions architect is designing the data storage and retrieval architecture for a new application that a company will be launching soon. The application is designed to ingest millions of small records per minute from devices all around the world. Each record is less than 4 KB in size and needs to be stored in a durable location where it can be retrieved with low latency. The data is ephemeral and the company is required to store the data for 120 days only, after which the data can be deleted.<br><br><br>The solutions architect calculates that, during the course of a year, the storage requirements would be about 10-15 TB.<br><br>Which storage strategy is the MOST cost-effective and meets the design requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Themost cost-effective and suitable storage strategy for this scenario is Option B: &nbsp;<br>Correct Answer: B &nbsp;<br>Design the application to store each incoming record in an Amazon DynamoDB table properly configured for the scale. Configure the DynamoDB Time to Live (TTL) feature to delete records older than 120 days. &nbsp;<br>Why? &nbsp;<br>1.High Write Throughput & Low Latency Retrieval: &nbsp;<br> &nbsp; - DynamoDB is optimized forhigh-velocity, small-record ingestion (millions of records per minute) withsingle-digit millisecond latency for retrieval. &nbsp;<br> &nbsp; - It automatically scales to handle the workload without manual intervention. &nbsp;<br>2.Automatic Data Expiration with TTL: &nbsp;<br> &nbsp; - DynamoDB’sTime to Live (TTL) feature automatically deletes records older than 120 days, eliminating the need for manual cleanup. &nbsp;<br>3.Cost-Effectiveness: &nbsp;<br> &nbsp; - Forephemeral data (120-day retention), DynamoDB’spay-per-request pricing (or provisioned capacity, if predictable) is more cost-efficient than S3 for frequent small writes and indexed retrievals. &nbsp;<br> &nbsp; - S3 is cheaper for large batches but inefficient for millions of small individual writes per minute. &nbsp;<br>Why Not the Other Options? &nbsp;<br>-A (S3 per-record .csv files): &nbsp;<br> &nbsp;-Inefficient for millions of small writes per minute (S3 hashigh PUT request costs at scale). &nbsp;<br> &nbsp;-No built-in indexing for retrieval (you’d need Athena/S3 Select, adding complexity). &nbsp;<br>-C (RDS MySQL): &nbsp;<br> &nbsp;-Not scalable for millions of writes per minute (RDS hashigher operational overhead and scaling limits). &nbsp;<br> &nbsp;-Nightly cron jobs are less reliable than DynamoDB TTL for expiration. &nbsp;<br>-D (S3 batched writes with metadata search): &nbsp;<br> &nbsp;-Batching helps with S3 costs, butmetadata search is limited (not designed for querying record contents). &nbsp;<br> &nbsp;-Slower retrieval compared to DynamoDB. &nbsp;<br>Conclusion: &nbsp;<br>DynamoDB is thebest fit forhigh-speed ingestion, low-latency retrieval, automatic TTL cleanup, and cost efficiency at this scale. &nbsp;<br>Final Answer: B<br>
</div>

</details>

    
# 76/529 

<div style="color:blue">single</div>
<br>Question #76<br>A retail company is hosting an ecommerce website on AWS across multiple AWS Regions. The company wants the website to be operational at all times for online purchases. The website stores data in an Amazon RDS for MySQL DB instance.<br><br><br>Which solution will provide the HIGHEST availability for the database?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Configure automated backups on Amazon RDS. In the case of disruption, promote an automated backup to be a standalone DB instance. Direct database traffic to the promoted DB instance. Create a replacement read replica that has the promoted DB instance as its source.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Configure global tables and read replicas on Amazon RDS. Activate the cross-Region scope. In the case of disruption, use AWS Lambda to copy the read replicas from one Region to another Region.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Configure global tables and automated backups on Amazon RDS. In the case of disruption, use AWS Lambda to copy the read replicas from one Region to another Region.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Configure read replicas on Amazon RDS. In the case of disruption, promote a cross-Region and read replica to be a standalone DB instance. Direct database traffic to the promoted DB instance. Create a replacement read replica that has the promoted DB instance as its source.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #76<br>A retail company is hosting an ecommerce website on AWS across multiple AWS Regions. The company wants the website to be operational at all times for online purchases. The website stores data in an Amazon RDS for MySQL DB instance.<br><br><br>Which solution will provide the HIGHEST availability for the database?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">D</span>
<br>Based on the information provided, the correct answer is:<br>D. Configure read replicas on Amazon RDS. In the case of disruption, promote a cross-Region and read replica to be a standalone DB instance. Direct database traffic to the promoted DB instance. Create a replacement read replica that has the promoted DB instance as its source.<br>This solution provides the highest availability for the database because:<br>Cross-Region read replicas in Amazon RDS for MySQL provide a disaster recovery solution that allows the database to remain operational even if an entire AWS Region experiences an outage.<br>The promotion process allows a read replica in another Region to be quickly converted to a standalone database instance that can accept write operations, minimizing downtime during a regional failure.<br>After promoting the read replica and redirecting traffic to it, creating a replacement read replica with the promoted instance as its source maintains the high availability architecture for future resilience.<br>This approach provides a practical and proven method for cross-Region failover with RDS for MySQL databases.<br>Options B and C are incorrect because:<br>Amazon RDS for MySQL does not support "global tables" - this is a feature of DynamoDB and Aurora, not standard RDS MySQL<br>Using AWS Lambda to "copy" read replicas between Regions is not a standard or efficient approach for database failover<br>These solutions describe architectures that don't align with RDS MySQL's actual capabilities<br>The solution in option D represents the standard approach for achieving cross-Region high availability with Amazon RDS for MySQL. It leverages the built-in read replica promotion capability, which is specifically designed for this type of failover scenario. This approach provides the highest availability for the retail company's ecommerce website by ensuring the database can remain operational even during a regional outage.<br>Sources<br>High availability for Amazon Aurora - Amazon Aurora （https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Concepts.AuroraHighAvailability.html）<br>Scaling and high availability in Amazon RDS - Amazon Relational Database Service （https://docs.aws.amazon.com/AmazonRDS/latest/gettingstartedguide/scaling-ha.html）<br>Resilience in Amazon RDS - Amazon Relational Database Service （https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/disaster-recovery-resiliency.html）<br>Comparing Amazon Aurora replication solutions - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/aurora-replication-options/compare-solutions.html）<br>Replication with Amazon Aurora - Amazon Aurora （https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Replication.html）<br>Replication with Amazon Aurora MySQL - Amazon Aurora （https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraMySQL.Replication.html）<br>How to choose the best disaster recovery option for your Amazon Aurora MySQL cluster | AWS Database Blog （https://aws.amazon.com/cn/blogs/database/how-to-choose-the-best-disaster-recovery-option-for-your-amazon-aurora-mysql-cluster/）<br>
</div>

</details>

    
# 77/529 

<div style="color:blue">single</div>
<br>Question #77<br>Example Corp. has an on-premises data center and a VPC named VPC A in the Example Corp. AWS account. The on-premises network connects to VPC A through an AWS Site-To-Site VPN. The on-premises servers can properly access VPC A. Example Corp. just acquired AnyCompany, which has a VPC named VPC B. There is no IP address overlap among these networks. Example Corp. has peered VPC A and VPC B.<br><br><br>Example Corp. wants to connect from its on-premise servers to VPC B. Example Corp. has properly set up the network ACL and security groups.<br><br><br>Which solution will meet this requirement with the LEAST operational effort?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create a transit gateway. Attach the Site-to-Site VPN, VPC A, and VPC B to the transit gateway. Update the transit gateway route tables for all networks to add IP range routes for all other networks.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create a transit gateway. Create a Site-to-Site VPN connection between the on-premises network and VPC B, and connect the VPN connection to the transit gateway. Add a route to direct traffic to the peered VPCs, and add an authorization rule to give clients access to the VPCs A and B.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Update the route tables for the Site-to-Site VPN and both VPCs for all three networks. Configure BGP propagation for all three networks. Wait for up to 5 minutes for BGP propagation to finish.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. <br>Modify the Site-to-Site VPN’s virtual private gateway definition to include VPC A and VPC B. Split the two routers of the virtual private gateway between the two VPCs.<br>
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #77<br>Example Corp. has an on-premises data center and a VPC named VPC A in the Example Corp. AWS account. The on-premises network connects to VPC A through an AWS Site-To-Site VPN. The on-premises servers can properly access VPC A. Example Corp. just acquired AnyCompany, which has a VPC named VPC B. There is no IP address overlap among these networks. Example Corp. has peered VPC A and VPC B.<br><br><br>Example Corp. wants to connect from its on-premise servers to VPC B. Example Corp. has properly set up the network ACL and security groups.<br><br><br>Which solution will meet this requirement with the LEAST operational effort?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>The correct answer isA. Here's why:<br>Scenario Requirements:<br>-On-premises servers need to accessVPC B (in addition to VPC A, which already works).<br>-VPC A andVPC B are already peered.<br>- No IP overlap exists.<br>- Network ACLs and security groups are properly configured.<br>Problem:<br>- The existingSite-to-Site VPN only connectson-premises toVPC A.<br>-VPC peering does NOT support transitive routing, so traffic from on-premises to VPC B won’t work by default.<br>Solution:<br>-Transit Gateway (TGW) allows transitive routing between:<br> &nbsp;- TheSite-to-Site VPN (on-premises)<br> &nbsp;-VPC A<br> &nbsp;-VPC B<br>- By attaching all three to the TGW and updating theroute tables, traffic can flow between all networks.<br>Why Option A?<br>-Least operational effort: <br> &nbsp;- Only requirescreating a TGW, attaching the VPN, VPC A, and VPC B, and updating routes.<br> &nbsp;- No need for additional VPNs (unlike Option B) or complex BGP configurations (unlike Option C).<br> &nbsp;- Option D is invalid because avirtual private gateway cannot be split between VPCs.<br>Why Not Other Options?<br>-B: Unnecessary to create asecond VPN connection (extra effort).<br>-C:BGP propagation is unnecessary and adds complexity (VPC peering doesn’t support transitive routing).<br>-D:Virtual private gateway cannot be shared/modified this way (incorrect approach).<br>Final Answer:<br>✅A. Create a transit gateway. Attach the Site-to-Site VPN, VPC A, and VPC B to the transit gateway. Update the transit gateway route tables for all networks to add IP range routes for all other networks.<br>
</div>

</details>

    
# 78/529 

<div style="color:blue">single</div>
<br>Question #78<br>A company recently completed the migration from an on-premises data center to the AWS Cloud by using a replatforming strategy. One of the migrated servers is running a legacy Simple Mail Transfer Protocol (SMTP) service that a critical application relies upon. The application sends outbound email messages to the company’s customers. The legacy SMTP server does not support TLS encryption and uses TCP port 25. The application can use SMTP only.<br><br><br>The company decides to use Amazon Simple Email Service (Amazon SES) and to decommission the legacy SMTP server. The company has created and validated the SES domain. The company has lifted the SES limits.<br><br><br>What should the company do to modify the application to send email messages from Amazon SES?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Configure the application to connect to Amazon SES by using TLS Wrapper. Create an IAM role that has ses:SendEmail and ses:SendRawEmail permissions. Attach the IAM role to an Amazon EC2 instance.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Configure the application to connect to Amazon SES by using STARTTLS. Obtain Amazon SES SMTP credentials. Use the credentials to authenticate with Amazon SES.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Configure the application to use the SES API to send email messages. Create an IAM role that has ses:SendEmail and ses:SendRawEmail permissions. Use the IAM role as a service role for Amazon SES.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Configure the application to use AWS SDKs to send email messages. Create an IAM user for Amazon SES. Generate API access keys. Use the access keys to authenticate with Amazon SES.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #78<br>A company recently completed the migration from an on-premises data center to the AWS Cloud by using a replatforming strategy. One of the migrated servers is running a legacy Simple Mail Transfer Protocol (SMTP) service that a critical application relies upon. The application sends outbound email messages to the company’s customers. The legacy SMTP server does not support TLS encryption and uses TCP port 25. The application can use SMTP only.<br><br><br>The company decides to use Amazon Simple Email Service (Amazon SES) and to decommission the legacy SMTP server. The company has created and validated the SES domain. The company has lifted the SES limits.<br><br><br>What should the company do to modify the application to send email messages from Amazon SES?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>The correct answer isB. Configure the application to connect to Amazon SES by using STARTTLS. Obtain Amazon SES SMTP credentials. Use the credentials to authenticate with Amazon SES.<br> Explanation:<br>1.Legacy SMTP Constraints: The application can only use SMTP (not APIs or SDKs), and the legacy SMTP server does not support TLS encryption, using only TCP port 25. &nbsp;<br>2.Amazon SES Requirements: &nbsp;<br> &nbsp; - SES requiresTLS encryption (either viaSTARTTLS orTLS Wrapper) for SMTP connections. &nbsp;<br> &nbsp; - Since the application cannot be modified to use APIs/SDKs, using SES SMTP credentials is the best approach. &nbsp;<br>3.STARTTLS vs. TLS Wrapper: &nbsp;<br> &nbsp; -STARTTLS (Option B) is the correct choice because it upgrades an existing plaintext SMTP connection to an encrypted one (on port 25 or 587). &nbsp;<br> &nbsp; -TLS Wrapper (Option A) is incorrect because it requires a different port (typically 465) and may not be supported by the legacy application. &nbsp;<br>4.Authentication: &nbsp;<br> &nbsp; - SES SMTP credentials (username/password) must be used for authentication (not IAM roles or API keys, as SMTP does not support IAM roles directly). &nbsp;<br>5.Why Not Other Options? &nbsp;<br> &nbsp; -A: Incorrect because TLS Wrapper is not the standard method for port 25, and IAM roles cannot be used for SMTP authentication. &nbsp;<br> &nbsp; -C & D: Incorrect because the applicationcannot use SES APIs or SDKs—it must use SMTP. &nbsp;<br> Correct Steps (Option B):<br>1.Configure the application to connect to theAmazon SES SMTP endpoint (e.g., `email-smtp.us-east-1.amazonaws.com`). &nbsp;<br>2.Enable STARTTLS to encrypt the connection (port 25 or 587). &nbsp;<br>3.Generate SES SMTP credentials (IAM user with `ses:SendRawEmail` permissions). &nbsp;<br>4.Authenticate with SES using the SMTP credentials. &nbsp;<br>This approach ensures the legacy application works with SES while meeting security requirements. &nbsp;<br>Answer: B<br>
</div>

</details>

    
# 79/529 

<div style="color:blue">single</div>
<br>Question #79<br>A company recently acquired several other companies. Each company has a separate AWS account with a different billing and reporting method. The acquiring company has consolidated all the accounts into one organization in AWS Organizations. However, the acquiring company has found it difficult to generate a cost report that contains meaningful groups for all the teams.<br><br><br>The acquiring company’s finance team needs a solution to report on costs for all the companies through a self-managed application.<br><br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an AWS Cost and Usage Report for the organization. Define tags and cost categories in the report. Create a table in Amazon Athena. Create an Amazon QuickSight dataset based on the Athena table. Share the dataset with the finance team.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an AWS Cost and Usage Report for the organization. Define tags and cost categories in the report. Create a specialized template in AWS Cost Explorer that the finance department will use to build reports.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an Amazon QuickSight dataset that receives spending information from the AWS Price List Query API. Share the dataset with the finance team.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use the AWS Price List Query API to collect account spending information. Create a specialized template in AWS Cost Explorer that the finance department will use to build reports.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #79<br>A company recently acquired several other companies. Each company has a separate AWS account with a different billing and reporting method. The acquiring company has consolidated all the accounts into one organization in AWS Organizations. However, the acquiring company has found it difficult to generate a cost report that contains meaningful groups for all the teams.<br><br><br>The acquiring company’s finance team needs a solution to report on costs for all the companies through a self-managed application.<br><br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>The correct answer is: &nbsp;<br>A. Create an AWS Cost and Usage Report for the organization. Define tags and cost categories in the report. Create a table in Amazon Athena. Create an Amazon QuickSight dataset based on the Athena table. Share the dataset with the finance team. &nbsp;<br> Explanation: &nbsp;<br>1.AWS Cost and Usage Report (CUR) provides comprehensive cost and usage data for all accounts in the organization, which is necessary for consolidated reporting. &nbsp;<br>2.Tags and Cost Categories allow meaningful grouping of costs by teams, departments, or business units. &nbsp;<br>3.Amazon Athena can query the CUR data stored in Amazon S3, enabling SQL-based analysis. &nbsp;<br>4.Amazon QuickSight can visualize the data from Athena, and the dataset can be shared with the finance team for self-service reporting. &nbsp;<br> Why not the other options? &nbsp;<br>-B: AWS Cost Explorer does not support sharing templates, and it lacks the flexibility of a self-managed application. &nbsp;<br>-C: The AWS Price List Query API provides pricing information, not actual spending data. &nbsp;<br>-D: Again, the Price List Query API does not provide actual spending data, and Cost Explorer lacks self-service capabilities for a finance application. &nbsp;<br>Thus,Option A is the best solution for generating a consolidated, customizable cost report.<br>
</div>

</details>

    
# 80/529 

<div style="color:blue">multiple</div>
<br>Question #80<br>A company runs an IoT platform on AWS. IoT sensors in various locations send data to the company’s Node.js API servers on Amazon EC2 instances running behind an Application Load Balancer. The data is stored in an Amazon RDS MySQL DB instance that uses a 4 TB General Purpose SSD volume.<br><br><br>The number of sensors the company has deployed in the field has increased over time, and is expected to grow significantly. The API servers are consistently overloaded and RDS metrics show high write latency.<br><br><br>Which of the following steps together will resolve the issues permanently and enable growth as new sensors are provisioned, while keeping this platform cost-efficient? (Choose two.)<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Resize the MySQL General Purpose SSD storage to 6 TB to improve the volume&rsquo;s IOPS.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Re-architect the database tier to use Amazon Aurora instead of an RDS MySQL DB instance and add read replicas.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Leverage Amazon Kinesis Data Streams and AWS Lambda to ingest and process the raw data.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use AWS X-Ray to analyze and debug application issues and add more API servers to match the load.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Re-architect the database tier to use Amazon DynamoDB instead of an RDS MySQL DB instance.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #80<br>A company runs an IoT platform on AWS. IoT sensors in various locations send data to the company’s Node.js API servers on Amazon EC2 instances running behind an Application Load Balancer. The data is stored in an Amazon RDS MySQL DB instance that uses a 4 TB General Purpose SSD volume.<br><br><br>The number of sensors the company has deployed in the field has increased over time, and is expected to grow significantly. The API servers are consistently overloaded and RDS metrics show high write latency.<br><br><br>Which of the following steps together will resolve the issues permanently and enable growth as new sensors are provisioned, while keeping this platform cost-efficient? (Choose two.)<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">CE</span>
<br>Based on the information provided, the correct answers are:<br>C. Leverage Amazon Kinesis Data Streams and AWS Lambda to ingest and process the raw data. <br>E. Re-architect the database tier to use Amazon DynamoDB instead of an RDS MySQL DB instance.<br>These two solutions together will resolve the issues permanently and enable growth while keeping the platform cost-efficient for the following reasons:<br>Leveraging Amazon Kinesis Data Streams with AWS Lambda (Option C):<br>This approach decouples the data ingestion process from the API servers, addressing the issue of consistently overloaded EC2 instances.<br>Kinesis Data Streams can handle millions of records per second, providing massive scalability for the growing number of IoT sensors.<br>Lambda functions can process the incoming data in parallel, eliminating bottlenecks in the current architecture.<br>This serverless approach scales automatically with the incoming data volume, making it ideal for the company's expected significant growth.<br>The pay-per-use model is cost-efficient for IoT workloads with variable traffic patterns.<br>Re-architecting to use Amazon DynamoDB (Option E):<br>DynamoDB is specifically designed for high-scale, low-latency workloads, addressing the high write latency issues currently experienced with RDS MySQL.<br>It provides single-digit millisecond response times regardless of scale, which is critical for IoT applications.<br>DynamoDB scales automatically without the need to provision or manage database infrastructure.<br>It eliminates the storage constraints and IOPS limitations of RDS volumes.<br>The on-demand capacity mode makes it cost-efficient for IoT workloads with unpredictable traffic patterns.<br>Option A (resizing the MySQL General Purpose SSD storage to 6 TB) is not a good long-term solution because:<br>It only provides a temporary fix by increasing IOPS (which are tied to volume size for GP2 volumes)<br>It doesn't address the fundamental architectural issues<br>It's not cost-efficient as the company would be paying for storage they don't need just to get more IOPS<br>There's still an upper limit to the IOPS available (16,000 for GP2), which will eventually be reached as the sensor count grows significantly<br>The combination of Kinesis Data Streams with Lambda for ingestion and processing, along with DynamoDB for storage, creates a serverless, highly scalable architecture that can handle the company's growing IoT platform needs while remaining cost-efficient through pay-per-use pricing models.<br>Sources<br>Recommendations from Amazon RDS reference - Amazon Relational Database Service （https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USERRecommendationsManage.RecommendationReference.html）<br>Key AWS services - IoT Lens （https://docs.aws.amazon.com/wellarchitected/latest/iot-lens/key-aws-services-perf.html）<br>Conclusion - Optimizing MySQL Running on Amazon EC2 Using Amazon EBS （https://docs.aws.amazon.com/whitepapers/latest/optimizing-mysql-on-ec2-using-amazon-ebs/conclusion.html）<br>Lambda vs Kinesis for uploading AWS IoT data to a database. | AWS re:Post （https://repost.aws/questions/QU20mw9eVYQd2UKKBUSRDLxw/lambda-vs-kinesis-for-uploading-aws-iot-data-to-a-database）<br>Amazon RDS DB instance storage - Amazon Relational Database Service （https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Storage.html）<br>
</div>

</details>

    
# 81/529 

<div style="color:blue">multiple</div>
<br>Question #81<br>A company is building an electronic document management system in which users upload their documents. The application stack is entirely serverless and runs on AWS in the eu-central-1 Region. The system includes a web application that uses an Amazon CloudFront distribution for delivery with Amazon S3 as the origin. The web application communicates with Amazon API Gateway Regional endpoints. The API Gateway APIs call AWS Lambda functions that store metadata in an Amazon Aurora Serverless database and put the documents into an S3 bucket.<br><br><br>The company is growing steadily and has completed a proof of concept with its largest customer. The company must improve latency outside of Europe.<br><br><br>Which combination of actions will meet these requirements? (Choose two.)<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Enable S3 Transfer Acceleration on the S3 bucket. Ensure that the web application uses the Transfer Acceleration signed URLs.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an accelerator in AWS Global Accelerator. Attach the accelerator to the CloudFront distribution.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Change the API Gateway Regional endpoints to edge-optimized endpoints.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Provision the entire stack in two other locations that are spread across the world. Use global databases on the Aurora Serverless cluster.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Add an Amazon RDS proxy between the Lambda functions and the Aurora Serverless database.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #81<br>A company is building an electronic document management system in which users upload their documents. The application stack is entirely serverless and runs on AWS in the eu-central-1 Region. The system includes a web application that uses an Amazon CloudFront distribution for delivery with Amazon S3 as the origin. The web application communicates with Amazon API Gateway Regional endpoints. The API Gateway APIs call AWS Lambda functions that store metadata in an Amazon Aurora Serverless database and put the documents into an S3 bucket.<br><br><br>The company is growing steadily and has completed a proof of concept with its largest customer. The company must improve latency outside of Europe.<br><br><br>Which combination of actions will meet these requirements? (Choose two.)<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">AC</span>
<br>Based on the information provided, the correct answers are:<br>A. Enable S3 Transfer Acceleration on the S3 bucket. Ensure that the web application uses the Transfer Acceleration signed URLs. <br>C. Change the API Gateway Regional endpoints to edge-optimized endpoints.<br>These two solutions together will effectively improve latency for users outside of Europe for the following reasons:<br>Enable S3 Transfer Acceleration (Option A):<br>S3 Transfer Acceleration is specifically designed to optimize the upload of data to S3 buckets over long distances.<br>It uses Amazon's global network of edge locations to route data through optimized network paths.<br>For users outside of Europe uploading documents to the eu-central-1 bucket, this will significantly improve upload speeds.<br>The document management system requires users to upload documents, making this feature particularly relevant.<br>Using Transfer Acceleration signed URLs ensures that the web application properly leverages this optimization.<br>Change API Gateway Regional endpoints to edge-optimized endpoints (Option C):<br>Edge-optimized endpoints are specifically designed for geographically dispersed clients accessing APIs from various locations around the world.<br>When using edge-optimized endpoints, API requests are routed through CloudFront edge locations closest to the users, reducing latency.<br>This is particularly beneficial for users outside of Europe who would otherwise need to connect directly to the eu-central-1 Region.<br>The API Gateway is a critical component of the application architecture, handling communication between the web application and Lambda functions.<br>Optimizing this component will improve overall application responsiveness for global users.<br>Together, these two changes address both the upload path (S3 Transfer Acceleration) and the API request path (edge-optimized endpoints) of the application, providing comprehensive latency improvements for users outside of Europe.<br>These solutions are also aligned with the serverless architecture of the application, maintaining its scalability and operational efficiency while enhancing global performance. They don't require significant architectural changes or the complexity of multi-region deployments, making them relatively straightforward to implement while still providing substantial latency improvements.<br>Sources<br>Multi-region API Gateway with CloudFront - Multi-region API Gateway with CloudFront （https://docs.aws.amazon.com/architecture-diagrams/latest/multi-region-api-gateway-with-cloudfront/multi-region-api-gateway-with-cloudfront.html）<br>PERF04-BP02 Evaluate available networking features - AWS Well-Architected Framework （https://docs.aws.amazon.com/wellarchitected/2024-06-27/framework/perf_networking_evaluate_networking_features.html）<br>Amazon API Gateway - Serverless Applications Lens （https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/amazon-api-gateway.html）<br>Selection - Serverless Applications Lens （https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/selection.html）<br>PERF04-BP02 Evaluate available networking features - AWS Well-Architected Framework （https://docs.aws.amazon.com/wellarchitected/2023-10-03/framework/perf_networking_evaluate_networking_features.html）<br>Using Amazon S3 Transfer Acceleration to Accelerate Geographically Disparate Data Transfers - Best Practices Design Patterns: Optimizing Amazon S3 Performance （https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html）<br>
</div>

</details>

    
# 82/529 

<div style="color:blue">single</div>
<br>Question #82<br>An adventure company has launched a new feature on its mobile app. Users can use the feature to upload their hiking and rafting photos and videos anytime. The photos and videos are stored in Amazon S3 Standard storage in an S3 bucket and are served through Amazon CloudFront.<br><br><br>The company needs to optimize the cost of the storage. A solutions architect discovers that most of the uploaded photos and videos are accessed infrequently after 30 days. However, some of the uploaded photos and videos are accessed frequently after 30 days. The solutions architect needs to implement a solution that maintains millisecond retrieval availability of the photos and videos at the lowest possible cost.<br><br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Configure S3 Intelligent-Tiering on the S3 bucket.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Configure an S3 Lifecycle policy to transition image objects and video objects from S3 Standard to S3 Glacier Deep Archive after 30 days.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Replace Amazon S3 with an Amazon Elastic File System (Amazon EFS) file system that is mounted on Amazon EC2 instances.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Add a Cache-Control: max-age header to the S3 image objects and S3 video objects. Set the header to 30 days.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #82<br>An adventure company has launched a new feature on its mobile app. Users can use the feature to upload their hiking and rafting photos and videos anytime. The photos and videos are stored in Amazon S3 Standard storage in an S3 bucket and are served through Amazon CloudFront.<br><br><br>The company needs to optimize the cost of the storage. A solutions architect discovers that most of the uploaded photos and videos are accessed infrequently after 30 days. However, some of the uploaded photos and videos are accessed frequently after 30 days. The solutions architect needs to implement a solution that maintains millisecond retrieval availability of the photos and videos at the lowest possible cost.<br><br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>Based on the information provided, the correct answer is:<br>A. Configure S3 Intelligent-Tiering on the S3 bucket.<br>This solution will meet the requirements for the following reasons:<br>Mixed Access Patterns: The scenario states that "most of the uploaded photos and videos are accessed infrequently after 30 days. However, some of the uploaded photos and videos are accessed frequently after 30 days." S3 Intelligent-Tiering is specifically designed for this type of mixed or unpredictable access pattern.<br>Automatic Optimization: S3 Intelligent-Tiering automatically moves objects between two access tiers based on changing access patterns:<br>Frequent Access tier for objects that are accessed regularly<br>Infrequent Access tier for objects that haven't been accessed for 30 consecutive days<br>Millisecond Retrieval: Both tiers in S3 Intelligent-Tiering provide millisecond retrieval times, meeting the requirement to maintain "millisecond retrieval availability."<br>Cost Optimization: S3 Intelligent-Tiering can save up to 40% on storage costs for objects that become infrequently accessed, while automatically moving objects back to the Frequent Access tier if they're accessed again, with no retrieval fees.<br>No Performance Impact: There is no performance degradation or change in latency when objects move between tiers, ensuring consistent user experience regardless of how frequently the photos and videos are accessed.<br>Option D (adding a Cache-Control: max-age header set to 30 days) would not effectively address the storage cost optimization requirement because:<br>Cache-Control headers primarily affect how content is cached by browsers and CDNs like CloudFront, not how the data is stored in S3.<br>While caching can reduce the number of requests to S3 (potentially reducing request costs), it doesn't change the underlying storage costs in S3.<br>Cache-Control headers don't move objects between storage tiers based on access patterns.<br>This approach wouldn't distinguish between frequently and infrequently accessed content after 30 days, which is a key requirement in this scenario.<br>S3 Intelligent-Tiering is the most appropriate solution as it automatically optimizes storage costs based on actual access patterns while maintaining the required millisecond retrieval availability for all objects.<br>Sources<br>Managing storage costs with Amazon S3 Intelligent-Tiering - Amazon Simple Storage Service （https://docs.aws.amazon.com/AmazonS3/latest/userguide/intelligent-tiering.html）<br>Amazon S3 Intelligent-Tiering Storage Class | AWS （https://aws.amazon.com/cn/s3/storage-classes/intelligent-tiering/）<br>Understanding and managing Amazon S3 storage classes - Amazon Simple Storage Service （https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage-class-intro.html）<br>How to Optimize AWS S3 Storage Costs? | AWS re:Post （https://repost.aws/questions/QU97-ATukcRz-XashRXJSkHA/how-to-optimize-aws-s3-storage-costs）<br>How Rivian optimized cloud storage for its ADAS and Product Engineering workloads on AWS | AWS for Industries （https://aws.amazon.com/cn/blogs/industries/how-rivian-optimized-cloud-storage-for-its-adas-and-product-engineering-workloads-on-aws/）<br>
</div>

</details>

    
# 83/529 

<div style="color:blue">single</div>
<br>Question #83<br>A company uses Amazon S3 to store files and images in a variety of storage classes. The company's S3 costs have increased substantially during the past year. <br><br><br>A solutions architect needs to review data trends for the past 12 months and identify the appropriate storage class for the objects. <br><br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Download AWS Cost and Usage Reports for the last 12 months of S3 usage. Review AWS Trusted Advisor recommendations for cost savings.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use S3 storage class analysis. Import data trends into an Amazon QuickSight dashboard to analyze storage trends.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Use Amazon S3 Storage Lens. Upgrade the default dashboard to include advanced metrics for storage trends.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use Access Analyzer for S3. Download the Access Analyzer for S3 report for the last 12 months. Import the .csv file to an Amazon QuickSight dashboard.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #83<br>A company uses Amazon S3 to store files and images in a variety of storage classes. The company's S3 costs have increased substantially during the past year. <br><br><br>A solutions architect needs to review data trends for the past 12 months and identify the appropriate storage class for the objects. <br><br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>Based on the information provided, the correct answer is:<br>C. Use Amazon S3 Storage Lens. Upgrade the default dashboard to include advanced metrics for storage trends.<br>This solution will meet the requirements for the following reasons:<br>Amazon S3 Storage Lens is specifically designed for analyzing S3 storage usage, activity trends, and providing optimization recommendations. It's purpose-built for exactly the kind of analysis the company needs to perform.<br>By upgrading to the advanced metrics in S3 Storage Lens, the company gains access to 15 months of historical data, which exceeds the required 12-month analysis period mentioned in the scenario.<br>S3 Storage Lens provides contextual recommendations for cost optimization, including suggestions for appropriate storage classes based on actual usage patterns. This directly addresses the requirement to "identify the appropriate storage class for the objects."<br>The solution includes built-in interactive dashboards in the S3 console, making it easy for the solutions architect to review and analyze the data without requiring additional setup or integration with other services.<br>S3 Storage Lens allows for detailed analysis at the bucket, prefix, and account levels, providing comprehensive visibility into storage patterns across the company's entire S3 environment.<br>Option A (AWS Cost and Usage Reports with Trusted Advisor) would provide cost data but lacks the specific storage pattern analysis needed to make informed storage class decisions. While it shows what you're spending, it doesn't provide the same level of insight into object access patterns that would inform storage class decisions.<br>Option B (S3 storage class analysis with QuickSight) would require additional setup and integration with QuickSight. While it can provide useful insights, it's not as comprehensive as S3 Storage Lens for organization-wide storage analysis and doesn't include the built-in recommendations for storage class optimization.<br>Amazon S3 Storage Lens with advanced metrics is the most direct and comprehensive solution for analyzing 12 months of S3 storage trends and identifying appropriate storage classes to optimize costs.<br>Sources<br>Analyze access patterns and use the most cost-effective Amazon S3 storage class | AWS Storage Blog（https://aws.amazon.com/cn/blogs/storage/analyze-access-patterns-and-use-the-most-cost-effective-amazon-s3-storage-class/） <br>AWS Tools for Reporting and Cost Optimization - Laying the Foundation: Setting Up Your Environment for Cost Optimization （https://aws.amazon.com/cn/aws-cost-management/cost-optimization/）<br>S3 Storage Analytics and Insights – Amazon S3 （https://aws.amazon.com/cn/s3/storage-analytics-insights/）<br>Assessing your storage activity and usage with Amazon S3 Storage Lens - Amazon Simple Storage Service （https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage_lens.html）<br>Achieve cost effective cloud operations with AWS Managed Services | AWS Cloud Operations Blog （https://aws.amazon.com/cn/blogs/mt/achieve-cost-effective-cloud-operations-with-aws-managed-services/）<br>
</div>

</details>

    
# 84/529 

<div style="color:blue">single</div>
<br>Question #84<br>A company has its cloud infrastructure on AWS. A solutions architect needs to define the infrastructure as code. The infrastructure is currently deployed in one AWS Region. The company’s business expansion plan includes deployments in multiple Regions across multiple AWS accounts. <br><br><br>What should the solutions architect do to meet these requirements？<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Use AWS CloudFormation templates. Add IAM policies to control the various accounts, Deploy the templates across the multiple Regions.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use AWS Organizations. Deploy AWS CloudFormation templates from the management account. Use AWS Control Tower to manage deployments across accounts.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Use AWS Organizations and AWS CloudFormation StackSets. Deploy a CloudFormation template from an account that has the necessary IAM permissions.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use nested stacks with AWS CloudFormation templates. Change the Region by using nested stacks.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #84<br>A company has its cloud infrastructure on AWS. A solutions architect needs to define the infrastructure as code. The infrastructure is currently deployed in one AWS Region. The company’s business expansion plan includes deployments in multiple Regions across multiple AWS accounts. <br><br><br>What should the solutions architect do to meet these requirements？<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>Based on the information provided, the correct answer is:<br>C. Use AWS Organizations and AWS CloudFormation StackSets. Deploy a CloudFormation template from an account that has the necessary IAM permissions.<br>This solution is the most appropriate for defining infrastructure as code that can be deployed across multiple regions and AWS accounts because:<br>AWS Organizations provides a way to centrally manage and govern multiple AWS accounts. It allows the company to organize accounts into organizational units (OUs) and apply policies across them, which is essential for managing a multi-account environment.<br>AWS CloudFormation StackSets extends the capability of CloudFormation by enabling you to create, update, or delete stacks across multiple accounts and regions with a single operation. This is exactly what's needed for the company's business expansion plan that includes deployments in multiple regions across multiple AWS accounts.<br>Deploying from an account with the necessary IAM permissions follows the principle of least privilege and establishes proper security controls. This approach allows for centralized management while maintaining appropriate access controls.<br>This combination provides the best scalability for multi-account, multi-region deployments with the lowest management complexity compared to the other options.<br>Option A (CloudFormation templates with IAM policies) would require managing separate deployments for each region and account, leading to higher management complexity and potential inconsistencies.<br>Option B (Organizations with Control Tower) is more focused on account governance and management rather than efficient multi-region deployments. While Control Tower is useful for establishing baseline configurations, it's not the most efficient tool for deploying the same infrastructure across multiple regions and accounts.<br>Option D (Nested stacks) is primarily designed for organizing complex CloudFormation templates within a single deployment, not for managing deployments across multiple accounts and regions. Changing regions using nested stacks is not a standard or recommended approach.<br>AWS Organizations combined with CloudFormation StackSets is the AWS-recommended solution for deploying infrastructure as code across multiple accounts and regions, making it the most suitable choice for the company's expansion plans.<br>Sources<br>Using AWS CloudFormation as an IaC tool - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/choose-iac-tool/cloudformation.html）<br>Stack vs StackSets deployment - Automated Security Response on AWS （https://docs.aws.amazon.com/solutions/latest/automated-security-response-on-aws/stack-vs-stacksets-deployment.html）<br>Managing stacks across accounts and Regions with StackSets - AWS CloudFormation （https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/what-is-cfnstacksets.html）<br>Infrastructure as Code - Developing and Deploying .NET Applications on AWS （https://docs.aws.amazon.com/whitepapers/latest/develop-deploy-dotnet-apps-on-aws/infrastructure-as-code.html）<br>AWS CloudFormation StackSets and AWS Organizations - AWS Organizations（https://docs.aws.amazon.com/organizations/latest/userguide/services-that-can-integrate-cloudformation.html） <br>How SMBs can deploy a multi-account environment quickly using AWS Organizations and AWS CloudFormation StackSets | AWS Cloud Operations Blog （https://aws.amazon.com/cn/blogs/mt/how-smbs-can-deploy-a-multi-account-environment-quickly-using-aws-organizations-and-aws-cloudformation-stacksets/）<br><br><br>
</div>

</details>

    
# 85/529 

<div style="color:blue">single</div>
<br>Question #85<br>A company has its cloud infrastructure on AWS. A solutions architect needs to define the infrastructure as code. The infrastructure is currently deployed in one AWS Region. The company’s business expansion plan includes deployments in multiple Regions across multiple AWS accounts. <br><br>What should the solutions architect do to meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Use AWS CloudFormation templates. Add IAM policies to control the various accounts, Deploy the templates across the multiple Regions.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use AWS Organizations. Deploy AWS CloudFormation templates from the management account. Use AWS Control Tower to manage deployments across accounts.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Use AWS Organizations and AWS CloudFormation StackSets. Deploy a CloudFormation template from an account that has the necessary IAM permissions.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use nested stacks with AWS CloudFormation templates. Change the Region by using nested stacks.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #85<br>A company has its cloud infrastructure on AWS. A solutions architect needs to define the infrastructure as code. The infrastructure is currently deployed in one AWS Region. The company’s business expansion plan includes deployments in multiple Regions across multiple AWS accounts. <br><br>What should the solutions architect do to meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>Based on the information available, the correct answer is:<br>C. Use AWS Organizations and AWS CloudFormation StackSets. Deploy a CloudFormation template from an account that has the necessary IAM permissions.<br>This solution is the most appropriate for defining infrastructure as code that can be deployed across multiple regions and AWS accounts because:<br>AWS Organizations provides a way to centrally manage and govern multiple AWS accounts. It allows the company to organize accounts into organizational units (OUs) and apply policies across them, which is essential for managing a multi-account environment.<br>AWS CloudFormation StackSets extends the capability of CloudFormation by enabling you to create, update, or delete stacks across multiple accounts and regions with a single operation. This is exactly what's needed for the company's business expansion plan that includes deployments in multiple regions across multiple AWS accounts.<br>Key advantages of using CloudFormation StackSets include:<br>Centralized management of resources across multiple accounts and regions<br>Ability to deploy the same infrastructure consistently across the organization<br>Simplified updates that propagate changes across all accounts and regions<br>Integration with AWS Organizations for automated deployment to member accounts<br>Deploying from an account with the necessary IAM permissions follows the principle of least privilege and establishes proper security controls.<br>Option A (CloudFormation templates with IAM policies) would require managing separate deployments for each region and account, leading to higher management complexity and potential inconsistencies.<br>Option B (Organizations with Control Tower) is more focused on account governance and management rather than efficient multi-region deployments. While Control Tower is useful for establishing baseline configurations, it's not the most efficient tool for deploying the same infrastructure across multiple regions and accounts.<br>Option D (Nested stacks) is primarily designed for organizing complex CloudFormation templates within a single deployment, not for managing deployments across multiple accounts and regions. Changing regions using nested stacks is not a standard or recommended approach.<br>AWS Organizations combined with CloudFormation StackSets is the AWS-recommended solution for deploying infrastructure as code across multiple accounts and regions, making it the most suitable choice for the company's expansion plans.<br>Sources<br>Deploy CloudFormation Hooks to an Organization with service-managed StackSets | AWS DevOps Blog （https://aws.amazon.com/cn/blogs/devops/deploy-cloudformation-hooks-to-an-organization-with-service-managed-stacksets/）<br>Managing stacks across accounts and Regions with StackSets - AWS CloudFormation （https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/what-is-cfnstacksets.html）<br>Stack vs StackSets deployment - Automated Security Response on AWS （https://docs.aws.amazon.com/solutions/latest/automated-security-response-on-aws/stack-vs-stacksets-deployment.html）<br>Using AWS CloudFormation StackSets - AWS Service Catalog （https://docs.aws.amazon.com/servicecatalog/latest/adminguide/using-stacksets.html）<br>AWS CloudFormation StackSets and AWS Organizations - AWS Organizations （https://docs.aws.amazon.com/organizations/latest/userguide/services-that-can-integrate-cloudformation.html）<br>
</div>

</details>

    
# 86/529 

<div style="color:blue">single</div>
<br>Question #86<br>A company plans to refactor a monolithic application into a modern application design deployed on AWS. The CI/CD pipeline needs to be upgraded to support the modern design for the application with the following requirements:<br><br><br>• It should allow changes to be released several times every hour.<br>• It should be able to roll back the changes as quickly as possible.<br><br><br>Which design will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Deploy a CI/CD pipeline that incorporates AMIs to contain the application and their configurations. Deploy the application by replacing Amazon EC2 instances.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Specify AWS Elastic Beanstalk to stage in a secondary environment as the deployment target for the CI/CD pipeline of the application. To deploy, swap the staging and production environment URLs.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Use AWS Systems Manager to re-provision the infrastructure for each deployment. Update the Amazon EC2 user data to pull the latest code artifact from Amazon S3 and use Amazon Route 53 weighted routing to point to the new environment.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Roll out the application updates as part of an Auto Scaling event using prebuilt AMIs. Use new versions of the AMIs to add instances and phase out all instances that use the previous AMI version with the configured termination policy during a deployment event.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #86<br>A company plans to refactor a monolithic application into a modern application design deployed on AWS. The CI/CD pipeline needs to be upgraded to support the modern design for the application with the following requirements:<br><br><br>• It should allow changes to be released several times every hour.<br>• It should be able to roll back the changes as quickly as possible.<br><br><br>Which design will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Based on the requirements for a CI/CD pipeline that supports releasing changes several times every hour and rolling back changes as quickly as possible, the answer is:<br>B. Specify AWS Elastic Beanstalk to stage in a secondary environment as the deployment target for the CI/CD pipeline of the application. To deploy, swap the staging and production environment URLs.<br>This is the correct choice because:<br>Elastic Beanstalk with environment URL swapping enables faster deployments, which is essential for releasing changes several times per hour.<br>The URL swapping approach provides an extremely quick rollback mechanism - if an issue is detected, you can simply swap the URLs back to the previous environment, which happens almost instantly.<br>This blue/green deployment approach with Elastic Beanstalk allows for zero-downtime deployments, as the new version is fully deployed and tested in the staging environment before becoming production.<br>The process is highly automated, reducing the potential for human error during frequent releases.<br>Option A (using AMIs with EC2 instance replacement) would be slower for both deployments and rollbacks because:<br>Creating and distributing AMIs is more time-consuming<br>Rolling back requires launching new EC2 instances from previous AMIs, which takes longer<br>This approach wouldn't support the requirement of releasing changes several times per hour as efficiently<br>Sources<br>Build - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/strategy-devops-aws-mainframe-modernization/build.html）<br>Deploy to Elastic Beanstalk with GitHub Actions | .NET on AWS Blog （https://aws.amazon.com/cn/blogs/dotnet/deploy-to-elastic-beanstalk-environment-with-github-actions/）<br>AWS Elastic Beanstalk - Developing and Deploying .NET Applications on AWS（https://docs.aws.amazon.com/whitepapers/latest/develop-deploy-dotnet-apps-on-aws/aws-elastic-beanstalk.html） <br>Deployment policies and settings - AWS Elastic Beanstalk （https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.rolling-version-deploy.html）<br>Stage 2: Design and implement - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/startup-resiliency-baseline/stage-2.html）<br>
</div>

</details>

    
# 87/529 

<div style="color:blue">multiple</div>
<br>Question #87<br>A company has an application that runs on Amazon EC2 instances. A solutions architect is designing VPC infrastructure in an AWS Region where the application needs to access an Amazon Aurora DB Cluster. The EC2 instances are all associated with the same security group. The DB cluster is associated with its own security group.<br>The solutions architect needs to add rules to the security groups to provide the application with least privilege access to the DB Cluster.<br>Which combination of steps will meet these requirements (Choose two.)?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Add an inbound rule to the EC2 instances&#39; security group. Specify the DB cluster&#39;s security group as the source over the default Aurora port.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Add an outbound rule to the EC2 instances&#39; security group. Specify the DB cluster&#39;s security group as the destination over the default Aurora port.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Add an inbound rule to the DB cluster&#39;s security group. Specify the EC2 instances&#39; security group as the source over the default Aurora port.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Add an outbound rule to the DB cluster&#39;s security group. Specify the EC2 instances&#39; security group as the destination over the default Aurora port.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
E. Add an outbound rule to the DB cluster&#39;s security group. Specify the EC2 instances&#39; security group as the destination over the ephemeral ports.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #87<br>A company has an application that runs on Amazon EC2 instances. A solutions architect is designing VPC infrastructure in an AWS Region where the application needs to access an Amazon Aurora DB Cluster. The EC2 instances are all associated with the same security group. The DB cluster is associated with its own security group.<br>The solutions architect needs to add rules to the security groups to provide the application with least privilege access to the DB Cluster.<br>Which combination of steps will meet these requirements (Choose two.)?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">BC</span>
<br>Based on the requirements for configuring security groups to provide least privilege access from EC2 instances to an Aurora DB cluster, the correct answers are:<br>B. Add an outbound rule to the EC2 instances' security group. Specify the DB cluster's security group as the destination over the default Aurora port.<br>C. Add an inbound rule to the DB cluster's security group. Specify the EC2 instances' security group as the source over the default Aurora port.<br>These two steps work together to create a secure connection between the EC2 instances and the Aurora DB cluster:<br>The outbound rule in the EC2 security group (option B) allows traffic to leave the EC2 instances and reach the DB cluster, but only on the specific Aurora port (typically 3306 for MySQL or 5432 for PostgreSQL).<br>The inbound rule in the DB cluster's security group (option C) allows traffic to enter the DB cluster, but only if it's coming from the EC2 instances' security group and only on the specific Aurora port.<br>This configuration follows the principle of least privilege by:<br>Restricting communication to only the necessary port<br>Using security group references instead of broad IP ranges<br>Creating a precise, bidirectional security group relationship that only permits the required traffic flow<br>Ensuring that only the EC2 instances in the specified security group can access the DB cluster<br>This approach is more secure than using CIDR blocks or allowing all traffic, as it dynamically updates when instances are added or removed from the security groups.<br>Sources<br>Automatically connecting an EC2 instance and an Aurora DB cluster - Amazon Aurora （https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/ec2-rds-connect.html）<br>Scenarios for accessing a DB cluster in a VPC - Amazon Aurora （https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/USER_VPC.Scenarios.html）<br>Controlling access with security groups - Amazon Relational Database Service （https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.RDSSecurityGroups.html）<br>Creating an Amazon Aurora DB cluster - Amazon Aurora （https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.CreateInstance.html）<br>Best Practice- Security Group architecture | AWS re:Post （https://repost.aws/questions/QUBp50iDPqSju0TINNsO8-fw/best-practice-security-group-architecture）<br>How to restrict Aurora db access to EC2 instances only | AWS re:Post （https://repost.aws/questions/QU9gGOwqiiSu-8H3zBRlpcbA/how-to-restrict-aurora-db-access-to-ec2-instances-only）<br><br><br>
</div>

</details>

    
# 88/529 

<div style="color:blue">single</div>
<br>Question #88<br>A company wants to change its internal cloud billing strategy for each of its business units. Currently, the cloud governance team shares reports for overall cloud spending with the head of each business unit. The company uses AWS Organizations to manage the separate AWS accounts for each business unit. The existing tagging standard in Organizations includes the application, environment, and owner. The cloud governance team wants a centralized solution so each business unit receives monthly reports on its cloud spending. The solution should also send notifications for any cloud spending that exceeds a set threshold.<br>Which solution is the MOST cost-effective way to meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Configure AWS Budgets in each account and configure budget alerts that are grouped by application, environment, and owner. Add each business unit to an Amazon SNS topic for each alert. Use Cost Explorer in each account to create monthly reports for each business unit.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Configure AWS Budgets in the organization&#39;s management account and configure budget alerts that are grouped by application, environment, and owner. Add each business unit to an Amazon SNS topic for each alert. Use Cost Explorer in the organization&#39;s management account to create monthly reports for each business unit.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Configure AWS Budgets in each account and configure budget alerts that are grouped by application, environment, and owner. Add each business unit to an Amazon SNS topic for each alert. Use the AWS Billing and Cost Management dashboard in each account to create monthly reports for each business unit.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Enable AWS Cost and Usage Reports in the organization&#39;s management account and configure reports grouped by application, environment, and owner. Create an AWS Lambda function that processes AWS Cost and Usage Reports, sends budget alerts, and sends monthly reports to each business unit&#39;s email list.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #88<br>A company wants to change its internal cloud billing strategy for each of its business units. Currently, the cloud governance team shares reports for overall cloud spending with the head of each business unit. The company uses AWS Organizations to manage the separate AWS accounts for each business unit. The existing tagging standard in Organizations includes the application, environment, and owner. The cloud governance team wants a centralized solution so each business unit receives monthly reports on its cloud spending. The solution should also send notifications for any cloud spending that exceeds a set threshold.<br>Which solution is the MOST cost-effective way to meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>TheMOST cost-effective solution that meets the requirements is: &nbsp;<br>Answer: B &nbsp;<br>Configure AWS Budgets in the organization's management account and configure budget alerts that are grouped by application, environment, and owner. Add each business unit to an Amazon SNS topic for each alert. Use Cost Explorer in the organization's management account to create monthly reports for each business unit. &nbsp;<br>Explanation: &nbsp;<br>1.Centralized AWS Budgets in the management account allows monitoring and alerting across all linked accounts in AWS Organizations, avoiding duplication of budgets in each account. &nbsp;<br>2.Grouping by tags (application, environment, owner) ensures spending is tracked per business unit. &nbsp;<br>3.Amazon SNS notifications can be set up for budget threshold alerts. &nbsp;<br>4.Cost Explorer in the management account provides consolidated cost reporting with filtering by tags, eliminating the need for manual report generation in each account. &nbsp;<br>Why Not Other Options? &nbsp;<br>-A & C: Require configuring AWS Budgets ineach account, leading to duplication and higher management overhead. &nbsp;<br>-D: While possible, it introduces unnecessary complexity with Lambda processing instead of using native AWS Budgets and Cost Explorer features. &nbsp;<br>Thus,Option B is the most cost-effective and efficient solution.<br>
</div>

</details>

    
# 89/529 

<div style="color:blue">single</div>
<br>Question #89<br>A company is using AWS CloudFormation to deploy its infrastructure. The company is concerned that, if a production CloudFormation stack is deleted, important data stored in Amazon RDS databases or Amazon EBS volumes might also be deleted.<br>How can the company prevent users from accidentally deleting data in this way?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Modify the CloudFormation templates to add a DeletionPolicy attribute to RDS and EBS resources.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Configure a stack policy that disallows the deletion of RDS and EBS resources.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Modify IAM policies to deny deleting RDS and EBS resources that are tagged with an &quot;aws:cloudformation:stack-name&quot; tag.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use AWS Config rules to prevent deleting RDS and EBS resources.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #89<br>A company is using AWS CloudFormation to deploy its infrastructure. The company is concerned that, if a production CloudFormation stack is deleted, important data stored in Amazon RDS databases or Amazon EBS volumes might also be deleted.<br>How can the company prevent users from accidentally deleting data in this way?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>Based on the requirements to prevent accidental deletion of important data in RDS databases or EBS volumes when a CloudFormation stack is deleted, the answer is:<br>A. Modify the CloudFormation templates to add a DeletionPolicy attribute to RDS and EBS resources.<br>This is the correct choice because:<br>The DeletionPolicy attribute is specifically designed to control what happens to resources when they are removed from a CloudFormation stack or when the stack is deleted.<br>By setting DeletionPolicy to "Retain" for critical resources like RDS databases and EBS volumes, these resources will remain intact even if the CloudFormation stack is deleted.<br>Alternatively, setting DeletionPolicy to "Snapshot" would create a final snapshot before deletion, preserving the data.<br>This approach directly addresses the company's concern about data loss during stack deletion.<br>The other options are less suitable because:<br>Option B (stack policy): Stack policies control what update actions are allowed on resources within a stack, but they don't prevent the entire stack from being deleted.<br>Option C (IAM policies): While IAM policies can restrict deletion actions, they would need to be carefully crafted and maintained, and might not provide comprehensive protection against stack deletions.<br>Option D (AWS Config rules): AWS Config rules can monitor compliance but don't directly prevent deletion actions during CloudFormation stack operations.<br>Sources<br>AWS::RDS::DBInstance - AWS CloudFormation （https://docs.aws.amazon.com/AWSCloudFormation/latest/TemplateReference/aws-resource-rds-dbinstance.html）<br>DeletionPolicy attribute - AWS CloudFormation （https://docs.aws.amazon.com/AWSCloudFormation/latest/TemplateReference/aws-attribute-deletionpolicy.html）<br>Protect CloudFormation stacks from being deleted - AWS CloudFormation （https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-protect-stacks.html）<br>UpdateReplacePolicy attribute - AWS CloudFormation （https://docs.aws.amazon.com/AWSCloudFormation/latest/TemplateReference/aws-attribute-updatereplacepolicy.html）<br>Amazon Relational Database Service (Amazon RDS) controls - AWS Control Tower （https://docs.aws.amazon.com/controltower/latest/controlreference/rds-rules.html）<br>
</div>

</details>

    
# 90/529 

<div style="color:blue">single</div>
<br>Question #90<br>A company has VPC flow logs enabled for its NAT gateway. The company is seeing Action = ACCEPT for inbound traffic that comes from a public IP address 198.51.100.2 destined for a private Amazon EC2 instance.<br>The company wants to determine whether the traffic represents unsolicited inbound connections from the internet. The first two octets of the VPC CIDR block are 203.0.<br><br><br>Which set of steps should the solutions architect take to meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Open the AWS CloudTrail console. Select the log group that contains the NAT gateway&#39;s elastic network interface and the private instance&#39;s elastic network interface. Run a query to filter with the destination address set as &quot;like 203.0&quot; and the source address set as &quot;like 198.51.100.2&quot;. Run the stats command to filter the sum of bytes transferred by the source address and the destination address.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Open the Amazon CloudWatch console. Select the log group that contains the NAT gateway&#39;s elastic network interface and the private instance&#39;s elastic network interface. Run a query to filter with the destination address set as &quot;like 203.0&quot; and the source address set as &quot;like 198.51.100.2&quot;. Run the stats command to filter the sum of bytes transferred by the source address and the destination address.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Open the AWS CloudTrail console. Select the log group that contains the NAT gateway&#39;s elastic network interface and the private instance&rsquo;s elastic network interface. Run a query to filter with the destination address set as &quot;like 198.51.100.2&quot; and the source address set as &quot;like 203.0&quot;. Run the stats command to filter the sum of bytes transferred by the source address and the destination address.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Open the Amazon CloudWatch console. Select the log group that contains the NAT gateway&#39;s elastic network interface and the private instance&#39;s elastic network interface. Run a query to filter with the destination address set as &quot;like 198.51.100.2&quot; and the source address set as &quot;like 203.0&quot;. Run the stats command to filter the sum of bytes transferred by the source address and the destination address.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #90<br>A company has VPC flow logs enabled for its NAT gateway. The company is seeing Action = ACCEPT for inbound traffic that comes from a public IP address 198.51.100.2 destined for a private Amazon EC2 instance.<br>The company wants to determine whether the traffic represents unsolicited inbound connections from the internet. The first two octets of the VPC CIDR block are 203.0.<br><br><br>Which set of steps should the solutions architect take to meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>The correct answer isB. &nbsp;<br> Explanation: &nbsp;<br>The question involves analyzingVPC Flow Logs to determine if inbound traffic from a public IP (`198.51.100.2`) to a private EC2 instance (with a CIDR starting with `203.0`) represents unsolicited connections. &nbsp;<br>1.VPC Flow Logs are stored in Amazon CloudWatch Logs, not AWS CloudTrail (which is for API activity logging). So, options A and C (which suggest using CloudTrail) are incorrect. &nbsp;<br>2. The goal is to check if the private instance (`203.0.x.x`) initiated outbound traffic to `198.51.100.2` before receiving inbound traffic (indicating a response rather than unsolicited traffic). &nbsp;<br> &nbsp; - The correct filter should look for: &nbsp;<br> &nbsp; &nbsp; -Source IP (`srcaddr`) like `203.0` (outbound traffic from the private instance). &nbsp;<br> &nbsp; &nbsp; -Destination IP (`dstaddr`) like `198.51.100.2` (the public IP). &nbsp;<br> &nbsp; - If no such traffic exists, the inbound `ACCEPT` traffic from `198.51.100.2` is likely unsolicited. &nbsp;<br>3. OptionB correctly usesCloudWatch Logs and filters for: &nbsp;<br> &nbsp; - `dstaddr` (destination) like `203.0` (private instance). &nbsp;<br> &nbsp; - `srcaddr` (source) like `198.51.100.2` (public IP). &nbsp;<br> &nbsp; - This helps identify if the private instance sent traffic to the public IP first. &nbsp;<br>Option D is incorrect because it reverses the source and destination filters, looking for traffic where `198.51.100.2` is the destination (which is not relevant here). &nbsp;<br>Correct Answer: B<br>
</div>

</details>

    
# 91/529 

<div style="color:blue">single</div>
<br>Question #91<br>A company consists of two separate business units. Each business unit has its own AWS account within a single organization in AWS Organizations. The business units regularly share sensitive documents with each other. To facilitate sharing, the company created an Amazon S3 bucket in each account and configured low-way replication between the S3 buckets. The S3 buckets have millions of objects.<br><br><br>Recently, a security audit identified that neither S3 bucket has encryption at rest enabled. Company policy requires that all documents must be stored with encryption at rest. The company wants to implement server-side encryption with Amazon S3 managed encryption keys (SSE-S3).<br><br><br>What is the MOST operationally efficient solution that meets these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Turn on SSE-S3 on both S3 buckets. Use S3 Batch Operations to copy and encrypt the objects in the same location.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create an AWS Key Management Service (AWS KMS) key in each account. Turn on server-side encryption with AWS KMS keys (SSE-KMS) on each S3 bucket by using the corresponding KMS key in that AWS account. Encrypt the existing objects by using an S3 copy command in the AWS CLI.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Turn on SSE-S3 on both S3 buckets. Encrypt the existing objects by using an S3 copy command in the AWS CLI.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an AWS Key Management Service (AWS KMS) key in each account. Turn on server-side encryption with AWS KMS keys (SSE-KMS) on each S3 bucket by using the corresponding KMS key in that AWS account. Use S3 Batch Operations to copy the objects into the same location.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #91<br>A company consists of two separate business units. Each business unit has its own AWS account within a single organization in AWS Organizations. The business units regularly share sensitive documents with each other. To facilitate sharing, the company created an Amazon S3 bucket in each account and configured low-way replication between the S3 buckets. The S3 buckets have millions of objects.<br><br><br>Recently, a security audit identified that neither S3 bucket has encryption at rest enabled. Company policy requires that all documents must be stored with encryption at rest. The company wants to implement server-side encryption with Amazon S3 managed encryption keys (SSE-S3).<br><br><br>What is the MOST operationally efficient solution that meets these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>TheMOST operationally efficient solution that meets the company's requirements is:<br>A. Turn on SSE-S3 on both S3 buckets. Use S3 Batch Operations to copy and encrypt the objects in the same location.<br>1.SSE-S3 is required by company policy, and this option directly enables it.<br>2.S3 Batch Operations is the most efficient way to encrypt millions of objects at scale, as it automates the copying process without manual scripting.<br>3.No need for AWS KMS (as in options B and D) since the requirement is SSE-S3, not SSE-KMS.<br>4.Operationally simpler than manually running CLI commands (as in option C), especially for millions of objects.<br>#Why not the other options?<br>-B & D: These suggest usingSSE-KMS, which is unnecessary since the requirement isSSE-S3.<br>-C: While correct in enabling SSE-S3, manually running anS3 copy command via CLI is inefficient for millions of objects compared toS3 Batch Operations.<br>Thus,Option A is the best choice. &nbsp;<br>Final Answer: A <br>
</div>

</details>

    
# 92/529 

<div style="color:blue">single</div>
<br>Question #92<br>A company is running an application in the AWS Cloud. The application collects and stores a large amount of unstructured data in an Amazon S3 bucket. The S3 bucket contains several terabytes of data and uses the S3 Standard storage class. The data increases in size by several gigabytes every day.<br><br><br>The company needs to query and analyze the data. The company does not access data that is more than 1 year old. However, the company must retain all the data indefinitely for compliance reasons.<br><br><br>Which solution will meet these requirements MOST cost-effectively?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Use S3 Select to query the data. Create an S3 Lifecycle policy to transition data that is more than 1 year old to S3 Glacier Deep Archive.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use Amazon Redshift Spectrum to query the data. Create an S3 Lifecycle policy to transition data that is more than 1 year old to S3 Glacier.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Use an AWS Glue Data Catalog and Amazon Athena to query the data. Create an S3 Lifecycle policy to transition data that is more than 1 year old to S3 Glacier Deep Archive.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use Amazon Redshift Spectrum to query the data. Create an S3 Lifecycle policy to transition data that is more than 1 year old to S3 Intelligent-Tiering.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #92<br>A company is running an application in the AWS Cloud. The application collects and stores a large amount of unstructured data in an Amazon S3 bucket. The S3 bucket contains several terabytes of data and uses the S3 Standard storage class. The data increases in size by several gigabytes every day.<br><br><br>The company needs to query and analyze the data. The company does not access data that is more than 1 year old. However, the company must retain all the data indefinitely for compliance reasons.<br><br><br>Which solution will meet these requirements MOST cost-effectively?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>Based on the requirements for a cost-effective solution to query and analyze several terabytes of unstructured data in an S3 bucket, where data increases by gigabytes daily, data older than 1 year is not accessed but must be retained indefinitely, the answer is:<br>C. Use an AWS Glue Data Catalog and Amazon Athena to query the data. Create an S3 Lifecycle policy to transition data that is more than 1 year old to S3 Glacier Deep Archive.<br>This is the correct choice because:<br>AWS Glue Data Catalog and Amazon Athena provide a comprehensive solution for querying and analyzing large volumes of unstructured data directly from S3. This combination is specifically designed for data lake analytics at scale.<br>Athena allows for complex SQL queries across the entire dataset, which is important for analyzing several terabytes of data that grows daily.<br>AWS Glue can automatically discover and catalog the schema of the unstructured data, making it easier to query with Athena.<br>S3 Glacier Deep Archive is the most cost-effective storage class for data that must be retained indefinitely but is rarely or never accessed (in this case, data older than 1 year).<br>The S3 Lifecycle policy automates the transition of older data to the cheaper storage tier, optimizing costs without manual intervention.<br>Option A (using S3 Select) is less suitable because:<br>S3 Select is designed for simpler queries on individual objects<br>It doesn't provide the comprehensive analytics capabilities needed for terabytes of unstructured data<br>It's not as efficient for complex queries across multiple files or large datasets<br>The combination of AWS Glue, Athena, and S3 Glacier Deep Archive provides the most cost-effective solution that meets all the stated requirements.<br>Sources<br>Query data from multiple sources in S3 on Athena? | AWS re:Post （https://repost.aws/questions/QUeZq3d77YQ8-9EPtDDBe6RQ/query-data-from-multiple-sources-in-s3-on-athena）<br>Migrate and Archive data for ADAS workloads on AWS | AWS for Industries （https://aws.amazon.com/cn/blogs/industries/migrate-and-archive-data-for-adas-workloads-on-aws/）<br>Community | Unleashing Data Analytics on S3 Data lake with AWS Glue Crawler and Amazon Athena （https://community.aws/content/2d0KCVyijMpSQoN4xtFbJmN0tob/analytics-on-s3-data-lake-using-aws-glue-crawler-and-amazon-athena）<br>Amazon EMR streamlines big data processing with simplified Amazon S3 Glacier access | AWS Big Data Blog （https://aws.amazon.com/cn/blogs/big-data/amazon-emr-streamlines-big-data-processing-with-simplified-amazon-s3-glacier-access/）<br>Understanding S3 Glacier storage classes for long-term data storage - Amazon Simple Storage Service（https://docs.aws.amazon.com/AmazonS3/latest/userguide/glacier-storage-classes.html） <br>Secure archive storage – Amazon S3 Glacier storage classes – AWS （https://aws.amazon.com/cn/s3/storage-classes/glacier/?ams%23interactive-card-vertical%23pattern-data.filter=%257B%2522filters%2522%253A%255B%255D%257D）<br>
</div>

</details>

    
# 93/529 

<div style="color:blue">single</div>
<br>Question #93<br>A video processing company wants to build a machine learning (ML) model by using 600 TB of compressed data that is stored as thousands of files in the company's on-premises network attached storage system. The company does not have the necessary compute resources on premises for ML experiments and wants to use AWS.<br><br><br>The company needs to complete the data transfer to AWS within 3 weeks. The data transfer will be a one-time transfer. The data must be encrypted in transit. The measured upload speed of the company's internet connection is 100 Mbps. and multiple departments share the connection.<br><br><br>Which solution will meet these requirements MOST cost-effectively?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Order several AWS Snowball Edge Storage Optimized devices by using the AWS Management Console. Configure the devices with a destination S3 bucket. Copy the data to the devices. Ship the devices back to AWS.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Set up a 10 Gbps AWS Direct Connect connection between the company location and the nearest AWS Region. Transfer the data over a VPN connection into the Region to store the data in Amazon S3.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. &nbsp;Create a VPN connection between the on-premises network attached storage and the nearest AWS Region. Transfer the data over the VPN connection.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Deploy an AWS Storage Gateway file gateway on premises. Configure the file gateway with a destination S3 bucket. Copy the data to the file gateway.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #93<br>A video processing company wants to build a machine learning (ML) model by using 600 TB of compressed data that is stored as thousands of files in the company's on-premises network attached storage system. The company does not have the necessary compute resources on premises for ML experiments and wants to use AWS.<br><br><br>The company needs to complete the data transfer to AWS within 3 weeks. The data transfer will be a one-time transfer. The data must be encrypted in transit. The measured upload speed of the company's internet connection is 100 Mbps. and multiple departments share the connection.<br><br><br>Which solution will meet these requirements MOST cost-effectively?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>Themost cost-effective solution that meets the requirements is: &nbsp;<br>A. Order several AWS Snowball Edge Storage Optimized devices by using the AWS Management Console. Configure the devices with a destination S3 bucket. Copy the data to the devices. Ship the devices back to AWS. &nbsp;<br>Why? &nbsp;<br>1.Data Size & Time Constraint (600 TB in 3 weeks): &nbsp;<br> &nbsp; - The company's internet upload speed is100 Mbps (12.5 MB/s). &nbsp;<br> &nbsp; - Transferring600 TB (600,000 GB) over the internet would take: &nbsp;<br> &nbsp; &nbsp; \[<br> &nbsp; &nbsp; \frac{600,000 \text{ GB} \times 1024 \text{ MB/GB}}{12.5 \text{ MB/s}} \approx 5,529,600 \text{ seconds} \approx 64 \text{ days}<br> &nbsp; &nbsp; \] &nbsp;<br> &nbsp; &nbsp; This isfar beyond the 3-week deadline. &nbsp;<br>2.Snowball Edge Storage Optimized: &nbsp;<br> &nbsp; - Each Snowball Edge Storage Optimized device can hold80 TB. &nbsp;<br> &nbsp; - For600 TB, the company would need8 devices (since 600/80 = 7.5 → round up to 8). &nbsp;<br> &nbsp; - AWS Snowball is designed forlarge-scale, one-time transfers and ismuch faster than internet transfer. &nbsp;<br> &nbsp; - Data isencrypted in transit and at rest. &nbsp;<br>3.Cost-Effectiveness: &nbsp;<br> &nbsp; -Direct Connect (Option B) is expensive (requires 10 Gbps setup, ongoing costs) andoverkill for a one-time transfer. &nbsp;<br> &nbsp; -VPN Transfer (Option C) is too slow (as calculated above). &nbsp;<br> &nbsp; -Storage Gateway (Option D) is meant forongoing hybrid storage, not a one-time bulk transfer. &nbsp;<br>Conclusion: &nbsp;<br>AWS Snowball Edge is thefastest, most secure, and cost-effective solution for transferring600 TB within3 weeks. &nbsp;<br>Answer: A<br>
</div>

</details>

    
# 94/529 

<div style="color:blue">single</div>
<br>Question #94<br>A company has migrated Its forms-processing application to AWS. When users interact with the application, they upload scanned forms as files through a web application. A database stores user metadata and references to files that are stored in Amazon S3. The web application runs on Amazon EC2 instances and an Amazon RDS for PostgreSQL database.<br><br><br>When forms are uploaded, the application sends notifications to a team through Amazon Simple Notification Service (Amazon SNS). A team member then logs in and processes each form. The team member performs data validation on the form and extracts relevant data before entering the information into another system that uses an API.<br><br><br>A solutions architect needs to automate the manual processing of the forms. The solution must provide accurate form extraction, minimize time to market, and minimize long-term operational overhead.<br><br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Develop custom libraries to perform optical character recognition (OCR) on the forms. Deploy the libraries to an Amazon Elastic Kubernetes Service (Amazon EKS) cluster as an application tier. Use this tier to process the forms when forms are uploaded. Store the output in Amazon S3. Parse this output by extracting the data into an Amazon DynamoDB table. Submit the data to the target system&#39;s APL. Host the new application tier on EC2 instances.&nbsp;
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Extend the system with an application tier that uses AWS Step Functions and AWS Lambda. Configure this tier to use artificial intelligence and machine learning (AI/ML) models that are trained and hosted on an EC2 instance to perform OCR on the forms when forms are uploaded. Store the output in Amazon S3. Parse this output by extracting the data that is required within the application tier. Submit the data to the target system&#39;s API.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Host a new application tier on EC2 instances. Use this tier to call endpoints that host artificial intelligence and machine learning (AI/ML) models that are trained and hosted in Amazon SageMaker to perform OCR on the forms. Store the output in Amazon ElastiCache. Parse this output by extracting the data that is required within the application tier. Submit the data to the target system&#39;s API.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Extend the system with an application tier that uses AWS Step Functions and AWS Lambda. Configure this tier to use Amazon Textract and Amazon Comprehend to perform OCR on the forms when forms are uploaded. Store the output in Amazon S3. Parse this output by extracting the data that is required within the application tier. Submit the data to the target system&#39;s API.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #94<br>A company has migrated Its forms-processing application to AWS. When users interact with the application, they upload scanned forms as files through a web application. A database stores user metadata and references to files that are stored in Amazon S3. The web application runs on Amazon EC2 instances and an Amazon RDS for PostgreSQL database.<br><br><br>When forms are uploaded, the application sends notifications to a team through Amazon Simple Notification Service (Amazon SNS). A team member then logs in and processes each form. The team member performs data validation on the form and extracts relevant data before entering the information into another system that uses an API.<br><br><br>A solutions architect needs to automate the manual processing of the forms. The solution must provide accurate form extraction, minimize time to market, and minimize long-term operational overhead.<br><br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">D</span>
<br>The correct answer isD. Here's why:<br> Key Requirements:<br>1.Accurate form extraction: The solution must use reliable Optical Character Recognition (OCR) and data extraction.<br>2.Minimize time to market: Avoid building custom ML models or complex infrastructure.<br>3.Minimize long-term operational overhead: Prefer serverless and managed services over self-hosted solutions.<br> Why Option D is Best:<br>-Amazon Textract: A fully managed AWS AI service for OCR and form data extraction (no need to train custom ML models).<br>-Amazon Comprehend: Can be used for additional NLP tasks if needed (e.g., understanding unstructured text).<br>-AWS Step Functions & Lambda: Serverless orchestration and compute, reducing operational overhead.<br>-Amazon S3: Stores output reliably.<br>-No custom ML models or EC2 hosting: Eliminates maintenance of SageMaker/EC2 instances (unlike B and C).<br>-Faster deployment: Uses pre-trained AWS AI services instead of developing custom libraries (unlike A).<br> Why Other Options Are Inferior:<br>-A: Custom OCR libraries and EC2 hosting increase development time and operational overhead.<br>-B: Requires training/hosting custom ML models on EC2, which adds complexity and maintenance.<br>-C: Uses SageMaker (overkill for OCR) and ElastiCache (not needed for this workflow), increasing cost and overhead.<br> Conclusion:<br>D leverages AWS managed AI services (Textract/Comprehend) and serverless components (Step Functions/Lambda) to meet all requirements efficiently. <br>Answer: D<br>
</div>

</details>

    
# 95/529 

<div style="color:blue">single</div>
<br>Question #95<br>A company is refactoring its on-premises order-processing platform in the AWS Cloud. The platform includes a web front end that is hosted on a fleet of VMs, RabbitMQ to connect the front end to the backend, and a Kubernetes cluster to run a containerized backend system to process the orders. The company does not want to make any major changes to the application.<br><br><br>Which solution will meet these requirements with the LEAST operational overhead?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create an AMI of the web server VM. Create an Amazon EC2 Auto Scaling group that uses the AMI and an Application Load Balancer. Set up Amazon MQ to replace the on-premises messaging queue. Conﬁgure Amazon Elastic Kubernetes Service (Amazon EKS) to host the order-processing backend.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create a custom AWS Lambda runtime to mimic the web server environment. Create an Amazon API Gateway API to replace the front-end web servers. Set up Amazon MQ to replace the on-premises messaging queue. Conﬁgure Amazon Elastic Kubernetes Service (Amazon EKS) to host the order-processing backend.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create an AMI of the web server VM. Create an Amazon EC2 Auto Scaling group that uses the AMI and an Application Load Balancer. Set up Amazon MQ to replace the on-premises messaging queue. Install Kubernetes on a fleet of different EC2 instances to host the order-processing backend.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an AMI of the web server VM. Create an Amazon EC2 Auto Scaling group that uses the AMI and an Application Load Balancer. Set up an Amazon Simple Queue Service (Amazon SQS) queue to replace the on-premises messaging queue. Conﬁgure Amazon Elastic Kubernetes Service (Amazon EKS) to host the order-processing backend.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #95<br>A company is refactoring its on-premises order-processing platform in the AWS Cloud. The platform includes a web front end that is hosted on a fleet of VMs, RabbitMQ to connect the front end to the backend, and a Kubernetes cluster to run a containerized backend system to process the orders. The company does not want to make any major changes to the application.<br><br><br>Which solution will meet these requirements with the LEAST operational overhead?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>The correct answer isA. &nbsp;<br> Explanation: &nbsp;<br>The question asks for a solution that refactors the on-premises order-processing platform in AWSwith the least operational overhead andwithout major changes to the application. &nbsp;<br>-Option A is correct because: &nbsp;<br> &nbsp;- It uses anAMI of the existing web server VM, allowing the front end to run onEC2 Auto Scaling with minimal changes. &nbsp;<br> &nbsp;- It replaces RabbitMQ withAmazon MQ (a managed RabbitMQ or ActiveMQ service), which is a direct replacement with minimal configuration. &nbsp;<br> &nbsp;- It usesAmazon EKS (managed Kubernetes) for the backend, reducing operational overhead compared to self-managed Kubernetes. &nbsp;<br> &nbsp;- This approach requires the least modification to the existing application. &nbsp;<br>-Option B is incorrect because: &nbsp;<br> &nbsp;- Replacing the web front end withLambda and API Gateway would require significant code changes (serverless vs. VM-based). &nbsp;<br> &nbsp;- A custom Lambda runtime adds unnecessary complexity. &nbsp;<br>-Option C is incorrect because: &nbsp;<br> &nbsp;- It suggests installingself-managed Kubernetes on EC2, which introduces high operational overhead compared toAmazon EKS. &nbsp;<br>-Option D is incorrect because: &nbsp;<br> &nbsp;-Amazon SQS is not a direct replacement forRabbitMQ (which is a message broker supporting advanced protocols like AMQP).Amazon MQ is the correct managed alternative. &nbsp;<br> Conclusion: &nbsp;<br>Option A provides the most seamless migration with the least operational overhead while keeping the application mostly unchanged. &nbsp;<br>Answer: A<br>
</div>

</details>

    
# 96/529 

<div style="color:blue">single</div>
<br>Question #96<br>A solutions architect needs to implement a client-side encryption mechanism for objects that will be stored in a new Amazon S3 bucket. The solutions architect created a CMK that is stored in AWS Key Management Service (AWS KMS) for this purpose.<br>The solutions architect created the following IAM policy and attached it to an IAM role:<br><img src="https://up.zaixiankaoshi.com/5240831/question/b3df9271dd7e405314012b4226b7562d.png" alt="b3df9271dd7e405314012b4226b7562d.png" data-href="" style=""/><br>During tests, the solutions architect was able to successfully get existing test objects in the S3 bucket. However, attempts to upload a new object resulted in an error message. The error message stated that the action was forbidden.<br><br><br>Which action must the solutions architect add to the IAM policy to meet all the requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. kms:GenerateDataKey
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. kms:GetKeyPolicy
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. kms:GetPublicKey
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. kms:Sign
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #96<br>A solutions architect needs to implement a client-side encryption mechanism for objects that will be stored in a new Amazon S3 bucket. The solutions architect created a CMK that is stored in AWS Key Management Service (AWS KMS) for this purpose.<br>The solutions architect created the following IAM policy and attached it to an IAM role:<br><img src="https://up.zaixiankaoshi.com/5240831/question/b3df9271dd7e405314012b4226b7562d.png" alt="b3df9271dd7e405314012b4226b7562d.png" data-href="" style=""/><br>During tests, the solutions architect was able to successfully get existing test objects in the S3 bucket. However, attempts to upload a new object resulted in an error message. The error message stated that the action was forbidden.<br><br><br>Which action must the solutions architect add to the IAM policy to meet all the requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>Based on the scenario where a solutions architect needs to implement client-side encryption for S3 objects using a CMK stored in AWS KMS, and is able to get existing objects but receives a "forbidden" error when trying to upload new objects, the answer is:<br>A. kms:GenerateDataKey<br>This is the correct choice because:<br>For client-side encryption of S3 objects using AWS KMS, the client application needs to generate a data key from the CMK.<br>The kms:GenerateDataKey permission is specifically required to request a unique data key from KMS, which is then used to encrypt the object locally before uploading to S3.<br>Without this permission, the client cannot obtain the necessary data key to perform the encryption, resulting in the "forbidden" error message when attempting to upload new objects.<br>Since the solutions architect can already get existing objects, the IAM policy likely already includes permissions for operations like kms:Decrypt, but is missing the crucial permission needed for the encryption of new objects.<br>The other options are not correct for this specific scenario:<br>kms:GetKeyPolicy (option B) is used to view a key policy, not for encryption operations<br>kms:GetPublicKey (option C) is used for asymmetric keys to retrieve the public key, not for generating data keys<br>kms:Sign (option D) is used for digital signatures, not for encryption of S3 objects<br>Sources<br>Specifying dual-layer server-side encryption with AWS KMS keys (DSSE-KMS) - Amazon Simple Storage Service （https://docs.aws.amazon.com/AmazonS3/latest/userguide/specifying-dsse-encryption.html）<br>Using server-side encryption with AWS KMS keys (SSE-KMS) in directory buckets - Amazon Simple Storage Service （https://docs.aws.amazon.com/AmazonS3/latest/userguide/s3-express-UsingKMSEncryption.html）<br>Setting default server-side encryption behavior for Amazon S3 buckets - Amazon Simple Storage Service（https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucket-encryption.html） <br>Amazon S3 Express One Zone now supports AWS KMS with customer managed keys | AWS News Blog（https://aws.amazon.com/cn/blogs/aws/amazon-s3-express-one-zone-now-supports-aws-kms-with-customer-managed-keys/） <br>Understanding Amazon S3 client-side encryption options | AWS Storage Blog （https://aws.amazon.com/cn/blogs/storage/understanding-amazon-s3-client-side-encryption-options/）<br>How to encrypt your object in S3 | AWS re:Post （https://repost.aws/questions/QUa2uGgWvVTeCAkp6vKHBmdw/how-to-encrypt-your-object-in-s3）<br>
</div>

</details>

    
# 97/529 

<div style="color:blue">single</div>
<br>Question #97<br>A company has developed a web application. The company is hosting the application on a group of Amazon EC2 instances behind an Application Load Balancer. The company wants to improve the security posture of the application and plans to use AWS WAF web ACLs. The solution must not adversely affect legitimate traffic to the application.<br><br><br>How should a solutions architect configure the web ACLs to meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Set the action of the web ACL rules to Count. Enable AWS WAF logging. Analyze the requests for false positives. Modify the rules to avoid any false positive. Over time, change the action of the web ACL rules from Count to Block.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use only rate-based rules in the web ACLs, and set the throttle limit as high as possible. Temporarily block all requests that exceed the limit. Define nested rules to narrow the scope of the rate tracking.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Set the action of the web ACL rules to Block. Use only AWS managed rule groups in the web ACLs. Evaluate the rule groups by using Amazon CloudWatch metrics with AWS WAF sampled requests or AWS WAF logs.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use only custom rule groups in the web ACLs, and set the action to Allow. Enable AWS WAF logging. Analyze the requests for false positives. Modify the rules to avoid any false positive. Over time, change the action of the web ACL rules from Allow to Block.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #97<br>A company has developed a web application. The company is hosting the application on a group of Amazon EC2 instances behind an Application Load Balancer. The company wants to improve the security posture of the application and plans to use AWS WAF web ACLs. The solution must not adversely affect legitimate traffic to the application.<br><br><br>How should a solutions architect configure the web ACLs to meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>Based on the requirements to improve the security posture of a web application using AWS WAF web ACLs without adversely affecting legitimate traffic, the answer is:<br>A. Set the action of the web ACL rules to Count. Enable AWS WAF logging. Analyze the requests for false positives. Modify the rules to avoid any false positive. Over time, change the action of the web ACL rules from Count to Block.<br>This is the correct choice because:<br>Starting with rules in "Count" mode allows you to monitor traffic patterns without blocking any legitimate requests. This is a non-disruptive approach that meets the requirement of not adversely affecting legitimate traffic.<br>Enabling AWS WAF logging provides visibility into which requests would be blocked by your rules, allowing you to identify potential false positives before they impact users.<br>Analyzing the logs and modifying rules to avoid false positives ensures that when you do switch to "Block" mode, you'll only be blocking malicious traffic.<br>The gradual approach of changing from "Count" to "Block" over time allows for careful testing and validation, minimizing the risk to the application.<br>Option B (using only rate-based rules with high throttle limits) is less suitable because:<br>It focuses solely on rate limiting, which only addresses volumetric attacks<br>It doesn't provide the comprehensive protection that a full set of WAF rules would offer<br>Even with nested rules, this approach could still block legitimate traffic during usage spikes<br>It doesn't include the critical testing phase to identify and address false positives<br>The approach in option A represents a best practice for implementing AWS WAF in a way that balances improved security with minimal disruption to legitimate users.<br>Sources<br>Restrict access based on IP address or geolocation by using AWS WAF - AWS Prescriptive Guidance （https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/aws-waf-restrict-access-geolocation.html）<br>Testing and tuning - Guidelines for Implementing AWS WAF （https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html）<br>Is it possible to "dry run" WAF rate limiting rules? | AWS re:Post （https://repost.aws/questions/QUibVWsVgbSaqRoOf2_7dR9g/is-it-possible-to-dry-run-waf-rate-limiting-rules）<br>Preparing for testing your AWS WAF protections - AWS WAF, AWS Firewall Manager, AWS Shield Advanced, and AWS Shield network security director (https://docs.aws.amazon.com/waf/latest/developerguide/web-acl-testing-prep.html)<br>
</div>

</details>

    
# 98/529 

<div style="color:blue">single</div>
<br>Question #98<br>A company has an organization that has many AWS accounts in AWS Organizations. A solutions architect must improve how the company manages common security group rules for the AWS accounts in the organization.<br><br><br>The company has a common set of IP CIDR ranges in an allow list in each AWS account to allow access to and from the company’s on-premises network. Developers within each account are responsible for adding new IP CIDR ranges to their security groups. The security team has its own AWS account. Currently, the security team notifies the owners of the other AWS accounts when changes are made to the allow list.<br><br><br>The solutions architect must design a solution that distributes the common set of CIDR ranges across all accounts.<br><br><br>Which solution meets these requirements with the LEAST amount of operational overhead?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Set up an Amazon Simple Notification Service (Amazon SNS) topic in the security team&rsquo;s AWS account. Deploy an AWS Lambda function in each AWS account. Configure the Lambda function to run every time an SNS topic receives a message. Configure the Lambda function to take an IP address as input and add it to a list of security groups in the account. Instruct the security team to distribute changes by publishing messages to its SNS topic.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create new customer-managed prefix lists in each AWS account within the organization. Populate the prefix lists in each account with all internal CIDR ranges. Notify the owner of each AWS account to allow the new customer-managed prefix list IDs in their security groups.Instruct the security team to share updates with each AWS account owner.&nbsp;
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create a new customer-managed prefix list in the security team&rsquo;s AWS account. Populate the customer-managed prefix list with all internal CIDR ranges. Share the customer-managed prefix list with the organization by using AWS Resource Access Manager. Notify the owner of each AWS account to allow the new customer-managed prefix list ID in their security groups.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create an IAM role in each account in the organization. Grant permissions to update security groups. Deploy an AWS Lambda function in the security team&rsquo;s AWS account. Configure the Lambda function to take a list of internal IP addresses as input, assume a role in each organization account, and add the list of IP addresses to the security groups in each account.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #98<br>A company has an organization that has many AWS accounts in AWS Organizations. A solutions architect must improve how the company manages common security group rules for the AWS accounts in the organization.<br><br><br>The company has a common set of IP CIDR ranges in an allow list in each AWS account to allow access to and from the company’s on-premises network. Developers within each account are responsible for adding new IP CIDR ranges to their security groups. The security team has its own AWS account. Currently, the security team notifies the owners of the other AWS accounts when changes are made to the allow list.<br><br><br>The solutions architect must design a solution that distributes the common set of CIDR ranges across all accounts.<br><br><br>Which solution meets these requirements with the LEAST amount of operational overhead?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">C</span>
<br>The correct answer isC. &nbsp;<br>Explanation: &nbsp;<br>The requirement is to distribute common CIDR ranges across all AWS accounts with theleast operational overhead. Here’s whyOption C is the best solution: &nbsp;<br>1.Centralized Management: &nbsp;<br> &nbsp; - Acustomer-managed prefix list is created in thesecurity team’s AWS account, which acts as a single source of truth for CIDR ranges. &nbsp;<br> &nbsp; - Instead of manually updating each account, the security team only needs to update thisone prefix list. &nbsp;<br>2.Shared Across the Organization: &nbsp;<br> &nbsp; - UsingAWS Resource Access Manager (RAM), the prefix list isshared with all accounts in the organization. &nbsp;<br> &nbsp; - This avoids duplication and ensures consistency. &nbsp;<br>3.Reduced Operational Overhead: &nbsp;<br> &nbsp; - Developers in each account only need toreference the shared prefix list in their security groups (instead of manually updating IPs). &nbsp;<br> &nbsp; - The security teamdoes not need to notify each account owner for every change—they just update the prefix list, and all accounts automatically get the latest CIDRs. &nbsp;<br>Why Other Options Are Less Optimal: &nbsp;<br>-Option A: Requires deploying Lambda functions in every account and manual SNS notifications. This increases operational overhead. &nbsp;<br>-Option B: Requires creating and maintaining separate prefix lists ineach account, which is redundant and harder to manage. &nbsp;<br>-Option D: Requires Lambda to assume roles in every account and update security groups directly, which is complex and increases operational risk. &nbsp;<br>Conclusion: &nbsp;<br>Option C is themost scalable and least operationally intensive solution, as it centralizes CIDR management and leverages AWS RAM for easy sharing. &nbsp;<br>Answer: C<br>
</div>

</details>

    
# 99/529 

<div style="color:blue">single</div>
<br>Question #99<br>A company has introduced a new policy that allows employees to work remotely from their homes if they connect by using a VPN. The company is hosting internal applications with VPCs in multiple AWS accounts. Currently, the applications are accessible from the company's on-premises office network through an AWS Site-to-Site VPN connection. The VPC in the company's main AWS account has peering connections established with VPCs in other AWS accounts.<br><br><br>A solutions architect must design a scalable AWS Client VPN solution for employees to use while they work from home. <br><br><br>What is the MOST cost-effective solution that meets these requirements? <br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Create a Client VPN endpoint in each AWS account. Configure required routing that allows access to internal applications.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Create a Client VPN endpoint in the main AWS account. Configure required routing that allows access to internal applications.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Create a Client VPN endpoint in the main AWS account. Provision a transit gateway that is connected to each AWS account. Configure required routing that allows access to internal applications.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Create a Client VPN endpoint in the main AWS account. Establish connectivity between the Client VPN endpoint and the AWS Site-to-Site VPN.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #99<br>A company has introduced a new policy that allows employees to work remotely from their homes if they connect by using a VPN. The company is hosting internal applications with VPCs in multiple AWS accounts. Currently, the applications are accessible from the company's on-premises office network through an AWS Site-to-Site VPN connection. The VPC in the company's main AWS account has peering connections established with VPCs in other AWS accounts.<br><br><br>A solutions architect must design a scalable AWS Client VPN solution for employees to use while they work from home. <br><br><br>What is the MOST cost-effective solution that meets these requirements? <br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">B</span>
<br>Based on the requirements for a cost-effective AWS Client VPN solution that allows remote employees to access internal applications hosted in VPCs across multiple AWS accounts, the answer is:<br>B. Create a Client VPN endpoint in the main AWS account. Configure required routing that allows access to internal applications.<br>This is the correct choice because:<br>Creating a single Client VPN endpoint in the main AWS account is more cost-effective than deploying multiple endpoints across different accounts. AWS Client VPN pricing is based on the number of endpoints and connections, so consolidating to one endpoint reduces costs.<br>Since the VPC in the main AWS account already has peering connections established with VPCs in other AWS accounts, you can leverage this existing network architecture. The Client VPN endpoint can route traffic through these peering connections to reach resources in all connected VPCs.<br>This approach simplifies management and configuration by centralizing the VPN solution in one account rather than managing multiple endpoints across different accounts.<br>The required routing can be configured to allow access to all internal applications across the peered VPCs, meeting the requirement for employees to access applications in multiple AWS accounts.<br>Option A (creating a Client VPN endpoint in each AWS account) would be more complex to manage and significantly more expensive due to the additional endpoints, making it less cost-effective than the centralized approach in option B.<br>Sources<br>Client VPN with VPC peering vs Client VPN withTransit gateway | AWS re:Post (https://repost.aws/questions/QUUotXjy2mTV6noMA-J86AXQ/client-vpn-with-vpc-peering-vs-client-vpn-withtransit-gateway)<br>VPN &nbsp;- Building a Scalable and Secure Multi-VPC AWS Network Infrastructure (https://docs.aws.amazon.com/whitepapers/latest/building-scalable-secure-multi-vpc-network-infrastructure/vpn.html)<br>Software remote access-to-Amazon VPC connectivity options - Amazon Virtual Private Cloud Connectivity Options (https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/software-remote-access-to-amazon-vpc-connectivity-options.html)<br>How AWS Client VPN works - AWS Client VPN (https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/how-it-works.html)<br>
</div>

</details>

    
# 100/529 

<div style="color:blue">single</div>
<br>Question #100<br>A company is running an application in the AWS Cloud. Recent application metrics show inconsistent response times and a significant increase in error rates. Calls to third-party services are causing the delays. Currently, the application calls third-party services synchronously by directly invoking an AWS Lambda function.<br><br><br>A solutions architect needs to decouple the third-party service calls and ensure that all the calls are eventually completed. <br><br><br>Which solution will meet these requirements?<br>
    
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
A. Use an Amazon Simple Queue Service (Amazon SQS) queue to store events and invoke the Lambda function.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
B. Use an AWS Step Functions state machine to pass events to the Lambda function.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
C. Use an Amazon EventBridge rule to pass events to the Lambda function.
</div>
        
<div style="border-radius: 5px;border:1px solid gray;background-color:whitesmoke">
D. Use an Amazon Simple Notification Service (Amazon SNS) topic to store events and invoke the Lambda function.
</div>
        
<details>

<summary>English</summary>

<div translate="no">
<br>Question #100<br>A company is running an application in the AWS Cloud. Recent application metrics show inconsistent response times and a significant increase in error rates. Calls to third-party services are causing the delays. Currently, the application calls third-party services synchronously by directly invoking an AWS Lambda function.<br><br><br>A solutions architect needs to decouple the third-party service calls and ensure that all the calls are eventually completed. <br><br><br>Which solution will meet these requirements?<br>

option_str
<div>

</details>

<details>

<summary>Answer</summary>

<div translate="no">
<span style="color:green; font-weight: bold;">A</span>
<br>Based on the requirements to decouple third-party service calls and ensure all calls are eventually completed, the answer is:<br>A. Use an Amazon Simple Queue Service (Amazon SQS) queue to store events and invoke the Lambda function.<br>This is the correct choice because:<br>Amazon SQS provides a reliable message queuing service that effectively decouples components of a distributed application, which directly addresses the requirement to decouple the third-party service calls.<br>SQS ensures that all messages (service calls) are eventually processed, even if there are temporary failures or throttling from the third-party services, meeting the requirement that "all calls are eventually completed."<br>SQS acts as a buffer that can absorb traffic spikes and allows the Lambda function to process messages at a consistent rate, which helps address the inconsistent response times issue.<br>SQS offers features like visibility timeout and dead-letter queues that provide robust error handling and retry mechanisms for failed processing attempts.<br>The other options are less suitable for this specific scenario:<br>Option B (AWS Step Functions): While good for orchestrating complex workflows, it's more suited for coordinating multiple steps rather than simple decoupling of service calls.<br>Option C (Amazon EventBridge): Better for event routing based on patterns rather than ensuring eventual completion of all calls.<br>Option D (Amazon SNS): Primarily designed for pub/sub messaging and fanout patterns, SNS doesn't store messages for later processing if the consumer is unavailable, making it less suitable for ensuring all calls are eventually completed.<br>Sources<br>Capturing records of Lambda asynchronous invocations - AWS Lambda （https://docs.aws.amazon.com/lambda/latest/dg/invocation-async-retain-records.html）<br>Transforming Order Fulfillment with Event-Driven Architecture: A Rapid7 Success Story | AWS Partner Network (APN) Blog （https://aws.amazon.com/cn/blogs/apn/transforming-order-fulfillment-with-event-driven-architecture-a-rapid7-success-story/）<br>Creating event-driven architectures with Lambda - AWS Lambda （https://docs.aws.amazon.com/lambda/latest/dg/concepts-event-driven-architectures.html）<br>Application integration services - Amazon Simple Notification Service （https://docs.aws.amazon.com/sns/latest/dg/sns-event-sources-application-integration.html）<br>Field Notes: Orchestrating and Monitoring Complex, Long-running Workflows Using AWS Step Functions | AWS Architecture Blog （https://aws.amazon.com/cn/blogs/architecture/field-notes-orchestrating-and-monitoring-complex-long-running-workflows-using-aws-step-functions/）<br>
</div>

</details>

    