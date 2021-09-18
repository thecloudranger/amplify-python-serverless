# Python serverless with AWS Amplify CLI

This workshop shows how to get started with the [AWS Amplify CLI]() and how you can build and deploy Python serveless apps on AWS using it.

## Prerequisites

To complete this workshop, you will need:

* [Python 3](https://www.python.org/downloads/). Ensure the python version installed is >=3.8.
  
  > If you are using Windows you will need to restart your machine after installing to ensure you can use Python and Pip from the command line.

* [Virtualenv](https://virtualenv.pypa.io/en/latest/)
* [Pipenv](https://pipenv.pypa.io/en/latest/)
* [Visual Studio Code](https://code.visualstudio.com/)
* The [Python Extension for Visual Studio Code](https://marketplace.visualstudio.com/itemdetails?itemName=ms-python.python). This can be installed from inside VS Code using the *Extensions* tab.
* A laptop/PC (with internet connection for intial setup).

This workshop works on MacOS and Windows.

## Code format

All code in this sample is shown in code blocks like this one:

```python
print('Here is some code')
```

Ellipses will be used to indicate other code, removed to make new code or the code that is being discussed easier to see. For example a code block like this:

```python
def func():
  ...
  print('end of the suite')
```

means that the `print('end of the suite')` will need to go inside the `func` function, but *after* all existing code in this function

## Steps

This workshop will cover 2 projects using the Amplify CLI: 
- Deploy Python app to Lambda
- Deploy Python app to Fargate (packaged as a Docker container). 

The steps for this workshop are:

### Lambda based 
1. [Initialise Amplify](./steps/python-lambda/01-initialize-amplify.md)
2. [Add storage](./steps/python-lambda/02-add-storage.md)
3. [Add API and Lambda function](./steps/python-lambda/03-add-api-lambda-function.md)
4. [Edit and deploy Flask app](./steps/python-lambda/04-edit-deploy-flask-app.md)
5. [CRUD routes and DynamoDB](./steps/python-lambda/05-crud-routes-dynamodb.md)
6. [Integrate React app](./steps/python-lambda/06-integrate-react-app.md)

### Fargate (serverless container) based   
1. [Initialize Amplify](./steps/python-fargate/01-initialize-amplify.md)
2. [Containerize Python app](./steps/python-fargate/02-ontainerize-python-app.md)
3. [Deploy with Amplify](./steps/python-fargate/03-deploy-with-amplify.md)