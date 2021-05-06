## 1. CloudFront Architecture Basics

#

### summary

- cloudfront is AWS's content delivery network(CDN) product
- lesson introduces key product concepts and terms, visually steps through the architecture and talks in detail about managing caching performance

### concepts

- cloudfront is a global object cache(CDN)
- content is cached in locations close to customers
- lower latency and higher throughput
- can handle static and dynamic content
- ![cfn basics](img/cfnconcepts.png)

### terms

- origin - source location of your content
- distribution - the configuration unit of cloudfront
- edge location - local infrastructure whic hosts a cache of your data
- regional edge cache - larger version of edge location. provides another layer of caching
- ![cfn terms](img/cfnterms.png)

### architecture

- bob uploads data to bucket, sets config in a distribution that points to bucket as origin.
- edge locations cache content, are globally distributed.
- each distribution as a domain name
- you config each distribution and deploy it to the edge locations
- in middle, are the regional edge locations. support multiple edges in same location area
- if data isnt in edge location, it checks the regional edge. see slide
- integrates w/ACM to add HTTPS availability
- caching is only for GETS. PUTS go directly to origin, no right caching. know for exam
- ![cfn arch basics w/regional edges](img/cfnarch.png)

### caching optimization

- when caching object, you also cache any query string parameters
- to get cached copy, you need to also cache the query string
- be careful when using query string parameters. i.e. order_id
- option Forward to Origin - YES or NO
- ![cfn optimization and query strings](img/cfnoptimization.png)

## 2. ACM

#

### summary

- AWS certificate manager is a service which allows the creation, management, and renewal of certs
- allows deployment of certs onto supported AWS services such as Cloudfront and ALB

### concepts

- for exam, only need to know the public cert part
- handles encryption and handle identity
- HTTP Simple and Insecure
- HTTPS - SSL/TLS layer of encryption added to HTTP
  - creates a secure tunnel where HTTP travels in
  - secure in transit
- data is encrypted in transit
- certificate prove identity
- signed by a trusted authority
- supported AWS services only eg CloudFront and ALBs NOT EC2
- ![cert mgr concepts](img/cfncertmgr.png)

### architecture

- use ACM to create cert
- created a cloudfront distribution using ALB
- customers communicate w/edge location use https and edge communicates w/origins using https(not self signed)
- ![cert mgr arch](img/cfncertmgrarch.png)

## Demos

#

2 demos:

1. first demo is 2 parts:

- 1. adding a CDN to a static website using S3 and Cloudfront part 1

  - create S3 bucket, add content, make avail globally using CFN

- 2.  Adding a CDN to a static website using S3 and Cloudfront part 2

  - continuation of first video. finishing up setting up distribution

2. second demo:

- adding a custom domain and HTTPS to a cloudfront distribution using ACM

## 3. Securing CF and S3 using OAI

#

### summary

- OAI - origin access identities is a feature where virtual identities can be created, associated with a cloudfront distribution and deployed to edge locations
- access to an S3 bucket can be controlled by using OAIs - allowing access from an OAI, and using an implicitly DENY for everything else
- OAIs are generally used to ensure no direct access to S3 objects is allowed when using private CF distributions

### concepts

- create OAI associate it w/distribution
- policy on S3 bucket - allow for OAI, everything else implicitly deny. remove all allows
- only things associated w/OAI can access bucket. the edges. no individuals directly. see slide
- distributions can be set to private, but you still need to restrict access to S3 buckets. a user can still access an S3 bucket if permissions are not setup correctly

### architecture

- ![arch of OAI distribution](img/cfnOAI.png)

## Demo

#

- this demo you implement bucket protection in S3 using OAI to restrict access to an S3 bucket to only a cloudfront distribution

## 4. Lambda@Edge

#

### summary

- Lambda@edge allows cloudfront to run lambda functions at cloudfront edge locations to modify traffic between the viewer and edge location and edge location and origins
- starting to feature in exams
- dont need experience implementing, but need to know arch

### concepts

- run lightweight lambda functions at edge locations
- adjust data between viewer and origin
- limitations - currently support NodeJS and Python
- run in the AWS public space - not VPC
- layers are not supported(?)
- different limits vs normal lambda functions
- ![lambda edge concepts](img/cfnlambdaedgeconcepts.png)

### architecture

- cloundfront architecture is same
- 4 components of architecture
  - view request -> origin request -> origin response -> viewer response
- you can run a lambda function at each component. see slide
- there are memory limits, see slide
- ![lambda edge arch](img/cfnlambdaedgearch.png)

### use cases

- A/B testing - viewer request testing
- migration between S3 origins - origin request
- different objects based on device - origin request- diff sizes, diff quality levels
- content by country - origin request
- link in lesson gives examples - aws docs. outside of course scope. only need to know architecture for exam
- ![lambda edge use cases](img/cfnlambdaedgeusecases.png)

## 5. Global Accelerator

#

### summary

- designed to improve global network performance by offering entry point onto the global AWS transit network as close to customers as possible using ANycast IP addresses

### concepts

- optimize flow of data from user to AWS infrastructure
- arch is similar to cloudfront
- both improve performance in diff ways and diff reasons
- anycast ip addresses can be used my multiple devices
- user connects to a global edge using an anycast address, the global accelerator then xfers data to the endpoint using AWS backbone. see slide
- very much like cloudfront
- connects enter at edge using anycast IPs
- traffic transits over AWS backbones to 1+ locations
- global accelerator is a network products. can be used for non HTTP/S. diff from cloudfront
- ![GA concepts](img/cfnGAconcepts.png)

- ### architecture
- for exam, just understand arch and how it works
- ![arch for GA](img/cfnGAarch.png)
