# aws-config/required-tags

- EC2インスタンスがCloudFormationで作成されたかどうかを検証するルール
- 検証はインスタンスのタグに `aws:cloudformation:logical-id` が含まれているかどうかで判定する
- SNSのサブスクリプションでデプロイ後に要設定（プロトコルは Email）

## deploy

[![](https://raw.githubusercontent.com/ot-nemoto/aws-cloudformation-templates/images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create/review?stackName=aws-config-required-tags&templateURL=https://s3-ap-northeast-1.amazonaws.com/ot-nemoto.aws-cloudformation-templates/aws-config/required-tags/template.yaml)

```sh
aws cloudformation create-stack \
    --stack-name aws-config-required-tags \
    --template-body file://template.yaml
```
