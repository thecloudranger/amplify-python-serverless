# Add storage

## Add a database

Next, let's add a DynamoDB database to the project with the command `amplify add storage` and selecting NoSQL.

```shell
? Please select from one of the below mentioned services: NoSQL Database

Welcome to the NoSQL DynamoDB database wizard
This wizard asks you a series of questions to help determine how to set up your NoSQL database table.

? Please provide a friendly name for your resource that will be used to label this category in the project: carStorage
? Please provide table name: cars

You can now add columns to the table.

? What would you like to name this column: id
? Please choose the data type: string
? Would you like to add another column? Yes
? What would you like to name this column: name
? Please choose the data type: string
? Would you like to add another column? Yes
? What would you like to name this column: year
? Please choose the data type: string
? Would you like to add another column? Yes
? What would you like to name this column: link
? Please choose the data type: string
? Would you like to add another column? No

Before you create the database, you must specify how items in your table are uniquely organized. You do this by specifying a primary key. The primary key uniquely identifies each item in the table so that no two items can have the same key. This can be an individual column, or a combination that includes a primary key and a sort key.

To learn more about primary keys, see:
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html#HowItWorks.CoreComponents.PrimaryKey

? Please choose partition key for the table: id
? Do you want to add a sort key to your table? No

You can optionally add global secondary indexes for this table. These are useful when you run queries defined in a different column than the primary key.
To learn more about indexes, see:
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html#HowItWorks.CoreComponents.SecondaryIndexes

? Do you want to add global secondary indexes to your table? No
? Do you want to add a Lambda Trigger for your Table? No
✅ Successfully added resource carStorage locally

```

Lets deploy our database by running `amplify push-y`.

In the [next step](./steps/python-lambda/03-add-api-lambda-function.md), let's add an API and a function to the project. 

