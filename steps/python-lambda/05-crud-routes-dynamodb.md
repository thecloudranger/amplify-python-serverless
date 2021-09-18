# CRUD Routes and DynamoDB

Let's add code to connect with DynamomDB and edit the `list_cars` function to query the DynamoDB table for a list of cars.

```python

client = boto3.client("dynamodb")
TABLE = os.environ.get("STORAGE_CARSTORAGE_NAME")
BASE_ROUTE="/car"

@app.route(BASE_ROUTE, methods=['GET'])
def list_cars():
  return jsonify(data=client.scan(TableName=TABLE))
  
```

Next we will add a route to handle POST requests where a new record will be saved in DynamoDB with the fields `id`, `name`, `year` and `link`. The `id` field will use a randomly generated uuid.

```python
@app.route(BASE_ROUTE, methods=['POST'])
def create_car():
    request_json = request.get_json()
    client.put_item(TableName=TABLE, Item={
        'id': { 'S': str(uuid4()) },
        'name': {'S': request_json.get("name")},
        'year': {'S': request_json.get("year")},
        'link': {'S': request_json.get("link")},
    })
    return jsonify(message="item created")
```

With the create functionality ready lets add the routes for `PUT` and `DELETE`.
```python
@app.route(BASE_ROUTE + '/<car_id>', methods=['PUT'])
def update_car(car_id):
    client.update_item(
        TableName=TABLE,
        Key={'id': {'S': car_id}},
        UpdateExpression='SET #name = :name, #year = :year, #link = :link',
        ExpressionAttributeNames={
            '#name': 'name',
            '#year': 'year',
            '#link': 'link'
        },
        ExpressionAttributeValues={
            ':name': {'S': request.json['name']},
            ':year': {'S': request.json['year']},
            ':link': {'S': request.json['link']},
        }
    )
    return jsonify(message="item updated")

@app.route(BASE_ROUTE + '/<car_id>', methods=['DELETE'])
def delete_car(car_id):
    client.delete_item(
        TableName=TABLE,
        Key={'id': {'S': car_id}}
    )
    return jsonify(message="car deleted")    
```

And we'll add our last route for `GET` again to fetch a specific car record by `id`.

```python
@app.route(BASE_ROUTE + '/<car_id>', methods=['GET'])
def get_car(car_id):
    item = client.get_item(TableName=TABLE, Key={
        'id': {
            'S': car_id
        }
    })
    return jsonify(data=item)
```
Run `amplify push -y` to deploy the changes.


In the [next step](./06-integrate-react-app.md), let's integrate the React app created in the beginning with the API endpoint and test out the requests. 

