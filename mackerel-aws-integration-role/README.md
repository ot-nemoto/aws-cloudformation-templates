# mackerel-aws-integration-role

- Mackerelエージェント用のIAMを作成します

## parameters

|Name|Type|Default|Description|
|--|--|--|--|
|ExternalId|String|*require*|Mackrel AWSインテグレーションの外部ID|

## deploy

[![](https://raw.githubusercontent.com/ot-nemoto/aws-cloudformation-templates/images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create/review?stackName=mackerel-aws-integration-role&templateURL=https://s3-ap-northeast-1.amazonaws.com/ot-nemoto.aws-cloudformation-templates/mackerel-aws-integration-role/template.yaml)

```sh
aws cloudformation create-stack \
    --stack-name mackerel-aws-integration-role \
    --capabilities CAPABILITY_NAMED_IAM \
    --parameters ParameterKey=ExternalId,ParameterValue=EXTERNAL_ID \
    --template-body file://template.yaml
```
