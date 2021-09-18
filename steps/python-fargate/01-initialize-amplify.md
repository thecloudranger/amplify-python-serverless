# Initialise Amplify

In this part of thr workshop we will use FastAPI to create a API based Python application, package it in a Docker container and deploy to ECS Fargate using the Amplify CLI.

## Initialize 

Create a new directory and initialize the the Amplify project.
```shell
mkdir fastapi-amplify-docker
cd fastapi-amplify-docker
amplify init
```

Initializing Amplify will prompt you with some questions. You can choose the default optoins.

```shell
Note: It is recommended to run this command from the root of your app directory
? Enter a name for the project fastapiamplifydocker
The following configuration will be applied:

Project information
| Name: fastapiamplifydocker
| Environment: dev
| Default editor: Visual Studio Code
| App type: javascript
| Javascript framework: none
| Source Directory Path: src
| Distribution Directory Path: dist
| Build Command: npm run-script build
| Start Command: npm run-script start

? Initialize the project with the above configuration? Yes
Using default provider  awscloudformation
? Select the authentication method you want to use: AWS profile

For more information on AWS Profiles, see:
https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html

? Please choose the profile you want to use default
Adding backend environment dev to AWS Amplify Console app: d24cxxtdn29mfk
⠧ Initializing project in the cloud...

```
Next, we'll enable the use of container-based deployments.

```shell
amplify configure project
```
Provide the answers to the questions as below:

```shell
? Which setting do you want to configure? Advanced: Container-based deployments
Using default provider  awscloudformation
? Do you want to enable container-based deployments? Yes

Successfully made configuration changes to your project.
```

Let's add the API next.

```shell
amplify add api
```

Answer the questions as below:

```shell
? Please select from one of the below mentioned services: REST
? Which service would you like to use API Gateway + AWS Fargate (Container-based)
? Provide a friendly name for your resource to be used as a label for this category in the project: fastapiamplifydocker
? What image would you like to use Custom (bring your own Dockerfile or docker-compose.yml)
? When do you want to build & deploy the Fargate task On every "amplify push" (Fully managed container source)
? Do you want to restrict API access No
Successfully added resource fastapiamplifydocker locally.
```

In the [next step](./02-containerize-python-app.md), let's containerize a FastAPI Python app. 
