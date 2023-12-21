## Introduction to Serverless Architectures on AWS by David Tucker

- WHAT WE'LL BE BUILDING:
    - Defining serverless:
        - A serverless architecture provides a new model for building applications in the cloud that provides multiple advantages.
            1. Speed of innvoation over depth of customization. We build out exactly what we need for today. Tomorrow's tomorrow.
            2. Deferred risk over extensive ownership. Leverage what was already built. And integrate. We do not control everything.
            3. Costs for actual use over costs for predicted use.
            4. Scalability by default over scalability by design.
            5. Managed services over custom infrastructure.
    - Navigating this learning path:
        - Five core concepts:
            1. Hosting. SPA. And deploy on a CDN.
            2. Serverless compute and APIs.
            3. Event-based architectures.
            4. Authentication and authorization. Best prwctices.
            5. Deployment and production support. Continuous delivery.
        - Learning.
        - Implementing.
    - AWS Serverless Services:
        - Compute services:
            - AWS Lambda. Run compute workloads.
            - AWS Fargate. Containers as a service.
        - App orchestration services:
            - Step functions. Workflow.
            - EventBridge. Managed messaging bus.
            - SQS. Simple queue service.
            - SNS. Simple notification service.
        - API services:
            - API Gateway
            - AppSync. Managed GraphQL endpoint.
        - Data services:
            - S3.
            - DynamoDB. Managed No-SQL database.
            - Aurora serverless. (Relational database.)
            - RDS proxy. (Relational database.)
        - Observability services:
            - CloudWatch. Metrics. Alarms. And application logging.
            - X-Ray: Tracing.
    - AWS Serverless Tools:
        - Third-party serverless tools. 
            - Serverless Framework.
            - Terraform. Infrastructure as code sol;ution.
            - Pulumi. Claudia.js, Zappa, Architect.
        - Serverless deployment:
            - CloudFormation: AWS managed service for infrasture as code. Reading a descriptive template. And deleting and destroying.
            - Serverless Application Model (SAM:)
            - Cloud Development Kit (CDK:) 
                - Enables you to write programmatic code for your infrastructure.
                - And generates CloudFormation templates based upon your code.
                - Provides support for packaging of Node.js Lambda functions. (ES Build.)
                - Works well in a monorepo structure.
                - Provides pipeline capabilities for continiuous delivery. (Pre-built assets.)
    - Demo Application Overview:
        - Document management system. 
            - Web-baseed interface. Upload and process DPF documents. 
            - Secure role-based access. Scale to the entire company. Implemented with continuous delivery.
        - Core application components:
            - Frontend: React application built in JavaScript.
            - Backend: Serverless microservices built in JavaScript.
            - Infrastructure: AWS CDK levberaging TypeScript.
            - CloudFront (Web app delivery) -> S3 (Hosting) 
            - API Gateway (HTTP API) -> Cognito (Auth. JWT.) -> Lambda (Microservices) <-> DynamoDB (Table)
            - S3 (Assets) -> Step FUnction [Lambda (Processing services) & Textract (Document Analysis)] -> DynamoDB (Table)
            - Observabilitity. And CD. And Comminucation.
    - Preparing Your Computer For This Path:
        - Node.js/npm. LTS version. (Long term support.)
            ```javascript
                node -v
                npm -v
                npm install aws-cdk -g
                cdk --version
            ```
        - AWS Serverless Application Model
            - Install SAM CLI. Requires Docker and AWS CLI.
                - AWS Command Line Interface.
                - Docker Desktop.
            ```javascript
                aws --version
                docker -v
                sam --version
            ```

- BENEFITS AND CHALLENGES OF SERVERLESS:
    - Understanding The Benefits Of Serverless:
        - To achive the benefits of serverless, you will have to change the manner in which you create applications.
            1. Cost is directly tied to useage.
            2. Reduced maintenance over the life of the application. "Net New Value."
            3. Scalability is built-in to the services that you use. There are service limits.
            4. Eases integration into new technologies.
            5. Risk and compliance mitigation.
        - Costs tied to useage. 
            - On-demand mode pay per request.
            - Scaling is built-in. And high availability is built into the application at the same cost point.
        - "As a service:" Infrastructure. Platform. Containers. (Serverless =>) Functions. Software. (Cloud provider.)
        - "Just upload your code and Lambda takes care of everything required to run and scale your code with high availability."
        - Emerging technology adoption: e.g.:
            - DynamoDB enables organizations to adopt NoSQL scalability without infrastructure. (You will not shard. Scale, Etc.)
            - AI Services enable developers to utilize AI and ML without custom model creation.
            - QLDB provides a cryptographically verified ledger that is fully managed. e.g.: custom blockchain.
            - AWS IoT provides a suite of IoT services to enable deployment and analysis of seasons.
        - Compliance And Risk:
            - All services should be analyzed for compliance. e.g.: Healthcare.
            - Serverless enables less custom code. And, thusly, less risk. Key arease of risk can be transfered to the provider.
    - Serverless Economics:
        - Common areas of optimization. 
            - HTTP API. 1/3 of the cost. Use this over REST for cost-saving. Cache headers.
            - Step functions.
            - DynamoDB. Different approaches. Use on-demand/per request billing.
            - S3 buckets. Life cycle rules. And storage classes.
            - Lambda. Choose amount of resources available for a given function. 
                - Paying for duration of the calls, so additional resources may speed processing.
        - Poorly architecting an application in the cloud can be a costly mistake.
        - Serverless architecture and cost:
            - Architects will need to have knowledge of cost for serverless services on AWS.
            - This requires continual education on service changes and new offerings.
            - Organizations adopting serverless should include cost analysis in development process.
    - When Native Serverless Isn't The Right Fit:
    - Serverless development will require new tools and approaches for most all of the development chain.
        - Difficult serverless use cases:
            - Resource-intensive workflows:
                - Lambda has specific limits on compute resources and time.
                - Some tasks cannot easily fit within the constraints.
                - Serverless approaches may assit in orchestration of these workloads.
            - Vendor agnostic. Rethink the discussion around vendor lock-in. Goal? Move quickly?
                - Working on an abstraction layer means that you won't experience all cloud benefits.
                - This decision should be tied to your core hgoals as an organization.
                - Many of these solutions require additional maintenance work.
            - Multi-cloud.
                - Many services do not translate across providers.
                - Some third-party frameworks solve for this.
                - Ideally an application should be built for a single platform.
            - Existing toolset.