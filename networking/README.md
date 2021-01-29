# networking

## architecture

## parameters

|Name|Type|Description|Default|
|--|--|--|--|
|VpcCidrBlock|String|10.38.0.0/16|VPC CidrBlock|
|PvtSubnetCidrBlocks|CommaDelimitedList|10.38.0.0/24, 10.38.1.0/24|Private Subnet CidrBlocks|
|PubSubnetCidrBlocks|CommaDelimitedList|10.38.128.0/24, 10.38.129.0/24|Public Subnet CidrBlocks|

## deploy

```sh
aws cloudformation create-stack \
    --stack-name networking \
    --template-body file://template.yaml
```
