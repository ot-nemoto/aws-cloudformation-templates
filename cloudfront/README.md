# cloudfront

*Deploy*

```sh
aws cloudformation create-stack \
    --stack-name cloudfront-sample \
    --parameters ParameterKey=ResasApiKey,ParameterValue=<API_KEY> \
    --capabilities CAPABILITY_IAM CAPABILITY_AUTO_EXPAND \
    --template-body file://template.yaml \
    --region us-east-1
```

*Upload files*

```sh
s3_bucket=$(aws cloudformation describe-stacks \
  --stack-name cloudfront-sample \
  --query 'Stacks[].Outputs[?OutputKey==`S3Bucket`].OutputValue' \
  --output text \
  --region us-east-1)

aws s3 sync files/ s3://${s3_bucket}/
```
