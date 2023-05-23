# Apply AWS Glue Library in Development
### This is practical experiment that highly applying in big project and helping developer & tester to complete their works effectively.
## Benefit
This article is to share the context of using AWS glue library on local for benefit of:

    •	Development activities.
    •	Testing in any environment.
    •	Project cost saving.

## Context
At first, the technical approach is approved by client to implement AWS glue job for loading data from AWS S3 to Aurora RDS PostgreSQL. It's very interesting that it could be applied what we have researched by creating glue job, creating connection and creating everything need to be deployed for an ETL job. It is the most straightforward tasks to do.
## In Practical
However, life is not a dream that you have no authentication to create any glue job, databse connection, policies/roles, etc... like what you researched. In fact, if you create glue job, you must label the bill for payment. Therefore, DevOps mates will implement those tasks with minimum configurations, not developers. You may just provide information of needed configurations. What you need to do is developing a python script that will be integrated with glue job in a environment without AWS infra.
## Concern
Wait a minute. A hundred questions are waiting for the answers. How could you run glue job for testing? How to use AWS resource for development such as connection name, s3 bucket, etc... At the end of the day, in your hand, you optimistically have the glue job name, connection name and bucket name. They are precious ASW resource, well, let start developing python script.
## Solution Approach
Fortunately, there is an approach to use the AWS glue library on local for AWS glue-job. It needs a succeeded deployment that library to continue developing and self-test. The pre-requisite condition is installing WSL then Ubuntu version 20.04, it contains some built-in software such as PostgreSQL database & python 3.8. At last, the local AWS library could be settled and run with python very smoothly. The most struggle issue is to set up the environment when installing local AWS glue library, we were not familiar with Ubuntu enough, and so it took time.
## Conclusion
The benefit is obviously to help developer freely coding python without any dependencies to AWS resource. Moreover, QC team performs the test cases in different environment without AWS glue service easily. Hence, the client is not paying for AWS service and it is cost saving benefit.
Finally, this is not invention, just a way to support development work effectively.
```mermaid
flowchart LR
    ST((START)) --> A[Python\nscript]
    A --> |Integrate|X{AWS Glue\nREAL Infra} --> X1[Developer/Tester] --> XX[Non-Production]--> |charge everytime\ntrigger job|X2[High Cost]
    X1 --> XX2[Production] --> |charge everytime\ntrigger job|X2

    A --> |Integrate|Y{AWS Glue\nLOCAL Library} --> Y1[Developer/Tester] --> YY[DROP n env] --> |no charge|Y2[Low Cost]
    Y1 --> YY1[SIT] --> |no charge|Y2
    Y1 --> YY2[UAT] --> |no charge|Y2
    Y1 --> YY3[Pre-Production] --> |no charge|Y2

    X2 --> EN((END))
    Y2 --> EN

     classDef green fill:#9f6,stroke:#333,stroke-width:2px
     classDef orange fill:#f96,stroke:#333,stroke-width:4px
     class X orange
     class ST green
     class Y green
```
 
## Sample run
Run testing python script locally to process ETL pipeline using AWS Glue library for loading data from batch file in s3 to PostgreSQL without AWS Glue service

 ![execute_pythons](https://github.com/kukin315/blog/assets/44157055/ee15a893-7ca9-4c2c-8579-64efa758d14d)

### Using PySpark 3.1.1-amzn-0 and Maven
![py-spark](https://github.com/kukin315/blog/assets/44157055/f92d8195-b9e0-4fdd-bf1e-28910e339517)
### Using Java JVM 11
![jvm](https://github.com/kukin315/blog/assets/44157055/85ba6959-54ab-4e17-bdcd-a9ec1b508967)

## References
Document for installing AWS glue libs on local

https://github.com/awslabs/aws-glue-libs or https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-etl-libraries.html

