# Edit and deploy Flask app

Change into the function directory:

```shell
cd amplify/backend/function/carapi
```

Install the following packages using `pipenv`:
* `aws-wsgi` allows us to use Flask routing inside the Lambda function
* `boto3` enables interaction with AWS services in Python
* `flask` the web framework of choice for this part of the workshop
* `flask-cors` for handling CORS in the flask app

```shell
pipenv install aws-wsgi boto3 flask flask-cors
```

Open `src/index.py` to edit the Lambda function. Delete all the 'Hello World' boiler plate code. First, we need to initialize a Flask application. We’ll also use `flask-cors` to handle CORS and `awsgi` to use WSGI in the handler function.

```python
import awsgi
from flask_cors import CORS
from flask import Flask, jsonify, request

app = Flask(__name__)
CORS(app)

def handler(event, context):
    return awsgi.response(app, event, context)
```

Next, lets add our first route before the handler.

```python
@app.route(BASE_ROUTE, methods=['GET'])
def list_cars():
  return jsonify(message="hello world")
```

Run `amplify push -y` to deploy your changes.

Open a new browser tab and use the API endpoint printed in the previous step and append the base `/car` to see the output `hello world`.


In the [next step](./05-crud-routes-dynamodb.md), let's add CRUD based routes and connect to DynamoDB. 

