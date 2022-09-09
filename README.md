# AWS re/Start Capstone Project
A couple of months ago we started our journey to the cloud through AWS re/Restart program where we have been introduced to multiple AWS services that run on the cloud to ease the work of building and maintaining the data centers by yourself which is costly and leave it to Amazon where you only pay for what you use. This will lead you to the most common benefits of AWS cloud including trade fixed expense for variable expense, benefit from massive economiees of scale, stop guessing capacity, and going global in minutes where you can deploy your application in less time.

Throughout our training on AWS services, we were given a case study to architect a solution for a user who wants to host their website on the cloud and the case study was formulated this way; An e-commerce company wants to host its website on Amazon EC2 instances. There is a requirement that the website should ONLY be accessible in the Africa and Asia continents (Demonstrate using VPN). The website should also have a domain associated with it. As a cloud practitioner, come up with a solution to host their website on AWS.

Before we jump into the solution, let see first what is AWS and why you should choose it among other cloud service providers.

## What are AWS?
AWS is a cloud computing platform that a mixture of infrastructure as a service (IaaS), platform as a service (PaaS) and packaged software as a service (SaaS) offerings.

## Why choosing AWS for cloud solutions?
People choose to use Amazon Cloud services to take advantage of the economies of scale, build a secure, reliable, scalable and cost-effective environment for their IT infrastructures. AWS provide a wide variety of services from the whole IT domain. AWS services can offer an organization tool such as compute power, database storage and content delivery services.

## Our suggested solution and services involved:
- AWS services needed:
- Amazon CloudFront
- Amazon Elastic Compute Cloud (Amazon EC2)
- Amazon Simple Storage Service (Amazon S3)
- Amazon Route 53
- AWS Shield

From the case study above, website applications need to be protected against traffic outside Africa and Asia in AWS. There are various ways and options you can use to achieve this objective, and to find the best optimized solution we will need to use the AWS well architected framework to come up with the best solution to this problem. Some of the approaches that can be used are blocking access with Network Access Control List (ACLs), we can also use Route 53 to block traffic from a particular geographical area, or use AWS Web Application Firewall to block access to our application. There are a lot of ways this can be done, each with its own application or use case depending on what specifically you want to achieve.

To solve our particular problem, we choose to use [AWS Web Application Firewall (AWS WAF)](https://aws.amazon.com/waf), which is a service provided by AWS under the security and compliance area. AWS WAF is a web application firewall that lets you monitor the HTTP and HTTPS requests that are forwarded to your protected web application resources, in our case it is our website. AWS WAF lets you control access to your content based on conditions that you specify, such as the IP addresses that requests originate from or the values of query strings.

Using AWS WAF we can block all requests outside Asia and Africa, so that our application serves contents to users who are identifiable and valid through the IP addresses that they use to browse to the website.

Here is a hypothetical diagram of how this application cloud looks in the cloud and how AWS WAF could be applied to block access from unauthorized users.

In the below diagram, you will see that AWS WAF is placed above the Elastic Load Balancer, so that it blocks traffic before the elastic load balancer distributes the traffic to our website.

## Prototype/Archictecture

![ Architecture for how an ecommerce site can be hosted on EC2](Images/case%20study%20architecture.png "Architecture")

Because we need the website to have a domain associated with it there is an AWS service to handle that called [Amazon Route 53](https://aws.amazon.com/route53), a highly available and scalable Domain Name System (DNS) web service. This will improve our application’s availability through registering the website’s domain and maintaining compliance. As an ecommerce website which will be receiving several requests from two continents it will need a service for protecting users’ requests made to Amazon Route 53 and [Amazon CloudFront](https://aws.amazon.com/cloudfront) from being delayed through the denial of service. That’s where AWS Shield comes into play, [AWS Shield](https://aws.amazon.com/shield) is a managed Distributed Denial of Service (DDoS) protection service that safeguards applications running on AWS. AWS Shield provides always-on detection and automatic inline mitigations that minimize application downtime and latency, so there is no need to engage AWS Support to benefit from DDoS protection.


With the help of these services and the other services we didn’t mention like [Amazon Macie](https://aws.amazon.com/macie), [Amazon Cloud Search](https://aws.amazon.com/cloudsearch), [Amazon Lex](https://aws.amazon.com/lex), and other many services we can’t cover in this article. All could help you create a well functioning reliable ecommerce website.


