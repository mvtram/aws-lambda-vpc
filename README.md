# aws-lambda-vpc

create profile
serverless config credentials --provider aws --key awskey --secret secretkey --profile serverless-admin

create template
sls create --template aws-python --path hello-world-python

initial deploy full stack
sls deploy -v

sls deploy function -f hello  is faster than deploying entire stack of cloud formation

invoke function from local
sls invoke -f hello -l
- f is function name in serverles yaml file
and -l is for logs


we can set up timeout: 3 and memorySize: 512 inside provider in the top of serverless yaml file


Cloud formation Template for dynamo db
resources:
  Resources:
    TodosDynamoDbTable:
      Type: 'AWS::DynamoDB::Table'
      DeletionPolicy: Retain
      Properties:
        AttributeDefinitions:
          -
            AttributeName: id
            AttributeType: S
        KeySchema:
          -
            AttributeName: id
            KeyType: HASH
        ProvisionedThroughput:
          ReadCapacityUnits: 1
          WriteCapacityUnits: 1
        TableName: ${self:provider.environment.DYNAMODB_TABLE}
 
