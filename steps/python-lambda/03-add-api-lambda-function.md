# Add API and Lambda function


## Add an API and a Lambda function

Now we need an API endpoint that can accept requests and forward it to a Python Lambda function. To add an API, use the command `amplify add api`.

You will be prompted with questions. You may choose to answer them similar to the example below:

```shell
? Please select from one of the below mentioned services: REST
? Provide a friendly name for your resource to be used as a label for this category in the project: carApi
? Provide a path (e.g., /book/{isbn}): /car
```
Then you will be asked to create a new Lambda function. Python will be the choice.

```shell
? Choose a Lambda source Create a new Lambda function
? Provide an AWS Lambda function name: carapi
? Choose the runtime that you want to use: Python
Only one template found - using Hello World by default.

Available advanced settings:
- Resource access permissions
- Scheduled recurring invocation
- Lambda layers configuration
- Environment variables configuration
- Secret values configuration
```
We’ll also need to configure some advanced settings in order to provide access to our database. Use your space bar to select storage and all CRUD actions.

```shell
? Do you want to configure advanced settings? Yes
? Do you want to access other resources in this project from your Lambda function? Yes
? Select the categories you want this function to have access to. storage
? Select the operations you want to permit on carStorage create, read, update, delete

You can access the following resource attributes as environment variables from your Lambda function
        ENV
        REGION
        STORAGE_CARSTORAGE_ARN
        STORAGE_CARSTORAGE_NAME
        STORAGE_CARSTORAGE_STREAMARN
? Do you want to invoke this function on a recurring schedule? No
? Do you want to enable Lambda layers for this function? No
? Do you want to configure environment variables for this function? No
? Do you want to configure secret values this function can access? No
? Do you want to edit the local lambda function now? No
Successfully added resource carapi locally.
```

Run `amplify push-y` to deploy. This will create a new API Gateway endpoint with the base as `car` that will in-turn route any HTTP reuests to a Lambda function that will host our Python code.

Copy the API endpoint printed in the output to use in the next step for testing.

In the [next step](./04-edit-deploy-flask-app.md), let's setup our Flask app on Lambda. 