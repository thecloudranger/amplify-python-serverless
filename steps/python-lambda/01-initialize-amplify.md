# Initialise Amplify

## React boilerplate app

Lets start by creating a React boilerplate app.

```shell
npx create-react-app car-api
cd car-api
```

## Initialize Amplify

```shell
amplify init
```
Initializing Amplify will prompt you with some questions. You can choose the default optoins.

```shell
Note: It is recommended to run this command from the root of your app directory
? Enter a name for the project carsapi
The following configuration will be applied:

Project information
| Name: carsapi
| Environment: dev
| Default editor: Visual Studio Code
| App type: javascript
| Javascript framework: react
| Source Directory Path: src
| Distribution Directory Path: build
| Build Command: npm run-script build
| Start Command: npm run-script start

? Initialize the project with the above configuration? Yes
Using default provider  awscloudformation
? Select the authentication method you want to use: AWS profile

For more information on AWS Profiles, see:
https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html

? Please choose the profile you want to use default
Adding backend environment dev to AWS Amplify Console app: d2gltg2gizyktk
⠦ Initializing project in the cloud...

```

In the [next step](./steps/python-lambda/02-add-storage.md), let's add a DynamoDB database to the project. 
