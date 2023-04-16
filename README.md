# JSON-to-CSV-conversion-using-AWS-Glue-and-Lambda
It is a 2 part setup where we upload a JSON file into S3 through API Gateway and then covert it into CSV using a Glue Job.

## Part-1: Uploading JSON file into S3 using API Gateway.
1. Setup the source S3 bucket where the raw JSON file will land.
2. Setup a Lambda function with a role that has permissions to access S3, API Gateway and Cloud Watch (see "lambda_api_s3_code.txt" for the code).
3. Setup a API Gateway (HTTP API) that integrtes with the Lambda function that we just created.
4. Pass the URL for the API Gateway, that points to the Lambda function, in Postman and set the method as POST.

Resource for Postman: https://upload.io/blog/postman-upload-file-cheat-sheet/
Resource for setting up S3 with API Gateway: https://repost.aws/knowledge-center/api-gateway-upload-image-s3

## Part-2: Flattening the JSON document into a CSV.
1. Setup a destination S3 bucket where the final CSV file shall be stored.
2. Setup a Lambda function (with a role that has permissions to access S3, Glue and Cloud Watch) that listens to the source S3 bucket for any new files and triggers a Glue Job that starts the Flattening process (see "lambda_json_s3_code.txt" for the code).
3. Setup a Glue job that reads the JSON file and flattens it into a columnar format (CSV) and then puts the converted file into the destination S3 bucket (see "glue_code_pyspark.txt" for the code).
 
 
 
