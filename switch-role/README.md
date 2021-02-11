# switch-role

## architecture

## parameters

|Name|Type|Default|Description|
|--|--|--|--|
|SrcAccountIds|CommaDelimitedList|*Required*|Specify the AWS account IDs that allow switch roles, separated by commas.|

## deploy

```sh
aws cloudformation create-stack \
    --stack-name switch-role \
    --capabilities CAPABILITY_IAM \
    --parameters ParameterKey=SrcAccountIds,ParameterValue='123456789012\,234567890123' \
    --template-body file://dest/template.yaml
```
