# networking

## architecture

![](https://github.com/ot-nemoto/aws-cloudformation-templates/blob/images/networking.png)

## parameters

|Name|Type|Default|Description|
|--|--|--|--|
|VpcCidrBlock|String|10.38.0.0/16|VPC CidrBlock|
|PvtSubnetCidrBlocks|CommaDelimitedList|10.38.0.0/24, 10.38.1.0/24|Private Subnet CidrBlocks|
|PubSubnetCidrBlocks|CommaDelimitedList|10.38.128.0/24, 10.38.129.0/24|Public Subnet CidrBlocks|

## deploy

[![](https://raw.githubusercontent.com/ot-nemoto/aws-cloudformation-templates/images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create/review?stackName=networking&templateURL=https://s3-ap-northeast-1.amazonaws.com/ot-nemoto.aws-cloudformation-templates/networking/template.yaml)

```sh
aws cloudformation create-stack \
    --stack-name networking \
    --template-body file://template.yaml
```
