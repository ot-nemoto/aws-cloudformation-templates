# templates-bucket

## architecture

## parameters

|Name|Type|Description|Default|
|--|--|--|--|
|BucketName|String|ot-nemoto.aws-cloudformation-templates|The name of the bucket to store the template.|

## deploy

```sh
aws cloudformation create-stack \
    --stack-name templates-bucket \
    --template-body file://template.yaml
```
