# aws-lambda-task-orchestration

Execute a glue spark ETL job and make an entry in a dynamodb audit table AFTER the completion of the glue job. 
It is critical that the dynamodb audit entry is made AFTER the completion of the glue job because DynamoDB streams defined on the audit table invoke a lambda function that cleanup an S3 bucket, which is the source for the glue job. So we need to ensure we do not cleanup the S3 bucket before or during the glue job processing.
