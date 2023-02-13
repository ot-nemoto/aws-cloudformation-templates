# chatbot

- [AWS Chatbot](https://us-east-2.console.aws.amazon.com/chatbot/home?region=ap-northeast-1#/home) でSlackクライアントを作成

## deploy

[![](https://raw.githubusercontent.com/ot-nemoto/aws-cloudformation-templates/images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create/review?stackName=aws-config-required-tags&templateURL=https://s3-ap-northeast-1.amazonaws.com/ot-nemoto.aws-cloudformation-templates/chatbot/template.yaml)

### parameters

|Name|Type|Default|Description|
|--|--|--|--|
|SlackWorkspaceId|String|*require*|SlackワークスペースID.<br>AWS ChatbotのSlackクライアントから取得.|
|SlackChannelId|AWS::EC2::Image::Id|*require*|SlackチャネルID.|

```sh
aws cloudformation create-stack \
    --stack-name chatbot \
    --capabilities CAPABILITY_IAM \
    --parameters ParameterKey=SlackWorkspaceId,ParameterValue=XXXXXXXXX \
                 ParameterKey=SlackChannelId,ParameterValue=XXXXXXXXX \
    --template-body file://template.yaml
```