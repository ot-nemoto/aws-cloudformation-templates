# switch-role

## architecture

## 切り替え先

- スイッチ先のロールを作成
- 作成するスイッチロールには `AdministratorAccess` ポリシーを付与

### parameters

|Name|Type|Default|Description|
|--|--|--|--|
|SrcAccountIds|CommaDelimitedList|*Required*|Specify the AWS account IDs that allow switch roles, separated by commas.|
|SwitchRoleName|String|AdminAccessRole|Switch role name.|

### deploy

[![](https://raw.githubusercontent.com/ot-nemoto/aws-cloudformation-templates/images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create/review?stackName=switch-role&templateURL=https://s3-ap-northeast-1.amazonaws.com/ot-nemoto.aws-cloudformation-templates/switch-role/dest/template.yaml)

```sh
aws cloudformation create-stack \
    --stack-name switch-role \
    --capabilities CAPABILITY_NAMED_IAM \
    --parameters ParameterKey=SrcAccountIds,ParameterValue='123456789012\,234567890123' \
    --template-body file://dest/template.yaml
```

## 切り替え元

- スイッチ先のアカウントのロールへスイッチするためのグループを作成
- 作成後、スイッチを許可するユーザを作成したグループへアタッチすること

### parameters

|Name|Type|Default|Description|
|--|--|--|--|
|SwitchRoleArns|CommaDelimitedList|*Required*|Specify the SwitchRoleArn of the switch destination account, separated by commas.|
|AssumeGroupName|String|AssumeGroup|Assume IAM group name.|

### deploy

[![](https://raw.githubusercontent.com/ot-nemoto/aws-cloudformation-templates/images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create/review?stackName=assume-role&templateURL=https://s3-ap-northeast-1.amazonaws.com/ot-nemoto.aws-cloudformation-templates/switch-role/src/template.yaml)

```sh
aws cloudformation create-stack \
    --stack-name assume-role \
    --capabilities CAPABILITY_NAMED_IAM \
    --parameters ParameterKey=SwitchRoleArns,ParameterValue='arn:aws:iam::123456789012:role/SwitchRoleName\,arn:aws:iam::234567890123:role/SwitchRoleName' \
    --template-body file://src/template.yaml
```
