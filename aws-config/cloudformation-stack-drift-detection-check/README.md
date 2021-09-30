# aws-config/cloudformation-stack-drift-detection-check

- CloudFormationのドリフト検出の結果、ドリフトしたかどうかを検証するルール
- SNSのサブスクリプションでデプロイ後に要設定（プロトコルは Email）

## deploy

[![](https://raw.githubusercontent.com/ot-nemoto/aws-cloudformation-templates/images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create/review?stackName=aws-config-cloudformation-stack-drift-detection-check&templateURL=https://s3-ap-northeast-1.amazonaws.com/ot-nemoto.aws-cloudformation-templates/aws-config/cloudformation-stack-drift-detection-check/template.yaml)

```sh
aws cloudformation create-stack \
    --stack-name aws-config-cloudformation-stack-drift-detection-check \
    --capabilities CAPABILITY_NAMED_IAM \
    --template-body file://template.yaml
```
