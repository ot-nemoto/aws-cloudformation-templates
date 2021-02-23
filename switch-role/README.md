# switch-role

## architecture

## Account to which you want to switch

- スイッチ先のロールを作成

### parameters

|Name|Type|Default|Description|
|--|--|--|--|
|SrcAccountIds|CommaDelimitedList|*Required*|Specify the AWS account IDs that allow switch roles, separated by commas.|

### deploy

```sh
aws cloudformation create-stack \
    --stack-name switch-role \
    --capabilities CAPABILITY_IAM \
    --parameters ParameterKey=SrcAccountIds,ParameterValue='123456789012\,234567890123' \
    --template-body file://dest/template.yaml
```

## Account from which you want to switch

- スイッチ先のアカウントのロールへスイッチするためのグループを作成
- 作成後、スイッチを許可するユーザを作成したグループへアタッチする

### parameters

|Name|Type|Default|Description|
|--|--|--|--|
|SwitchRoleArns|CommaDelimitedList|*Required*|Specify the SwitchRoleArn of the switch destination account, separated by commas.|
|AssumeGroupName|String|AssumeGroup|Assume IAM group name.|

### deploy

```sh
aws cloudformation create-stack \
    --stack-name assume-role \
    --capabilities CAPABILITY_NAMED_IAM \
    --parameters ParameterKey=SwitchRoleArns,ParameterValue='arn:aws:iam::123456789012:role/SwitchRoleName\,arn:aws:iam::234567890123:role/SwitchRoleName' \
    --template-body file://dest/template.yaml
```
