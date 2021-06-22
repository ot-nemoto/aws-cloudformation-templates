# networking

- EC2インスタンスを起動します
- スタック名をインスタンス名として登録します
- Envで指定した環境によって次の差異が発生します

||Staging|Production|
|--|--|--|
|InstanceType|`t2.large`|`r4.xlarge`|
|EBS.VolumeType|gp3|io1|
|EBS.Iops|3000|15000|

## parameters

|Name|Type|Default|Description|
|--|--|--|--|
|Env|String|Staging|環境[`Staging`\|`Production`]|
|ImageId|AWS::EC2::Image::Id|*require*|マシンイメージID|
|SubnetId|AWS::EC2::Subnet::Id|*require*|インスタンスを配置するサブネット|
|KeyName|AWS::EC2::KeyPair::KeyName|*require*|キーペア名|
|SecurityGroupIds|List<AWS::EC2::SecurityGroup::Id>|*require*|セキュリティグループID|

## deploy

[![](https://raw.githubusercontent.com/ot-nemoto/aws-cloudformation-templates/images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create/review?stackName=networking&templateURL=https://s3-ap-northeast-1.amazonaws.com/ot-nemoto.aws-cloudformation-templates/ec2-instance/template.yaml)

```sh
aws cloudformation create-stack \
    --stack-name ec2-instance \
    --parameters ParameterKey=ImageId,ParameterValue=ami-01234567890123456 \
                 ParameterKey=SubnetId,ParameterValue=subnet-01234567 \
                 ParameterKey=KeyName,ParameterValue=KEY_NAME \
                 ParameterKey=SecurityGroupIds,ParameterValue='sg-01234567\,sg-89012345' \
    --template-body file://template.yaml
```
