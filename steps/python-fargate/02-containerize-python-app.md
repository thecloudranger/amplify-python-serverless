# Containerize Python app and deploy

## Dockerfile

Create the following files at `amplify/backend/api/<api-name>/src/`
* `Dockerfile`
* `app/main.py`


## Dockerfile

```docker
# Dockerfile
FROM tiangolo/uvicorn-gunicorn-fastapi:python3.8

# for Amplify 
# https://docs.amplify.aws/cli/usage/containers#deploy-a-single-container
EXPOSE 80

COPY ./app /app
```

## FastAPI Python

Add API logic in the `main.py` file within `app/`.

```python
# main.py

from typing import Optional
from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def read_root():
    return {"Hello": "World"}


@app.get("/items/{item_id}")
def read_item(item_id: int, q: Optional[str] = None):
    return {"item_id": item_id, "q": q}


```

## Test locally

Change directory to where the `Dockerfile` is located and build the image.

```shell
docker build -t fastapi .
```

Run the image locally on port 80.

```shell
docker run -d --name fastapi -p 80:80 fastapi
```
Open http://127.0.0.1/redoc or http://127.0.0.1/docs in the browser to see the auto-generated API documentation.

## Deploy to Amplify

Let's push this to Amplify.
```shell
amplify push -y
```

Once complete, you should see the following output.
```shell
✔ All resources are updated in the cloud

REST API endpoint: https://<id>.execute-api.<region>.amazonaws.com
```

Take the output URL and paste in the browser to see the message `"Hello": "World"` printed. You can also open the auto-generated docs by appending `/docs`.

In the [next step](./02-containerize-python-app.md), let's containerize a FastAPI Python app. 
