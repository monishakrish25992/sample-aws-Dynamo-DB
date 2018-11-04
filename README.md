AWS::DynamoDB::Table

The AWS::DynamoDB::Table resource creates a DynamoDB table. For more information, see CreateTable in the Amazon DynamoDB API Reference.

You should be aware of the following behaviors when working with DynamoDB tables:

AWS CloudFormation typically creates DynamoDB tables in parallel. However, if your template includes multiple DynamoDB tables with indexes, you must declare dependencies so that the tables are created sequentially. Amazon DynamoDB limits the number of tables with secondary indexes that are in the creating state. If you create multiple tables with indexes at the same time, DynamoDB returns an error and the stack operation fails. For an example, see DynamoDB Table with a DependsOn Attribute.

Updates to AWS::DynamoDB::Table resources that are associated with AWS::ApplicationAutoScaling::ScalableTarget resources will always result in an update failure and then an update rollback failure. The following ScalableDimension attributes cause this problem when associated with the table:

dynamodb:table:ReadCapacityUnits
dynamodb:table:WriteCapacityUnits
dynamodb:index:ReadCapacityUnits
dynamodb:index:WriteCapacityUnits
As a workaround, please deregister scalable targets before performing updates to AWS::DynamoDB::Table resources.

Topics

Syntax
Properties
Return Values
Examples
Syntax


Reference link:
  https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-dynamodb-table.html

To declare this entity in your AWS CloudFormation template, use the following syntax:

JSON

{
  "Type" : "AWS::DynamoDB::Table",
  "Properties" : {
    "[AttributeDefinitions](#cfn-dynamodb-table-attributedef)" : [ AttributeDefinition, ... ],
    "[GlobalSecondaryIndexes](#cfn-dynamodb-table-gsi)" : [ GlobalSecondaryIndexes, ... ],
    "[KeySchema](#cfn-dynamodb-table-keyschema)" : [ KeySchema, ... ],
    "[LocalSecondaryIndexes](#cfn-dynamodb-table-lsi)" : [ LocalSecondaryIndexes, ... ],
    "[PointInTimeRecoverySpecification](#cfn-dynamodb-table-pointintimerecoveryspecification)" : [PointInTimeRecoverySpecification](aws-properties-dynamodb-table-pointintimerecoveryspecification.md),
    "[ProvisionedThroughput](#cfn-dynamodb-table-provisionedthroughput)" : ProvisionedThroughput,
    "[SSESpecification](#cfn-dynamodb-table-ssespecification)" : SSESpecification,
    "[StreamSpecification](#cfn-dynamodb-table-streamspecification)" : StreamSpecification,
    "[TableName](#cfn-dynamodb-table-tablename)" : String,
    "[Tags](#cfn-dynamodb-table-tags)" : [ Resource Tag, ... ],
    "[TimeToLiveSpecification](#cfn-dynamodb-table-timetolivespecification)" : [TimeToLiveSpecification](aws-properties-dynamodb-table-timetolivespecification.md)
  }
}
