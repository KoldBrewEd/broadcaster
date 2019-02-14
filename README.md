# AppSync Broadcaster

Simple app that broadcasts messages to multiple clients using Serverless GraphQL real-time subscriptions powered by AWS AppSync.

The API access is authenticated via API Key valid for 7 days. The demo takes advantage of GraphQL Subscriptions to send messages in real-time to different clients. Messages are saved to a DynamoDB data source.

![Screnshot](/media/broadcaster.png)

## Prerequisites

- [AWS Amplify CLI](https://github.com/aws-amplify/amplify-cli) `(npm install -g @aws-amplify/cli)`
- [Create React App](https://github.com/facebook/create-react-app) `(npm install -g create-react-app)`

## Setup

1. Create a React App and access the folder: 
   
   ```bash
   create-react-app broadcaster
   cd broadcaster
   ```
2. Replace the content of the files `src/App.js` and `package.json` with the ones in this repository
3. Install the required modules:

    ```bash
    npm install
    ```

4. Init the directory as an amplify Javascript project using the React framework:
   
    ```bash
    amplify init
    ```

5. Add an AppSync GraphQL API with API Key for the API Authentication. Follow the default options. When prompted with "Do you have an annotated GraphQL schema?", select "YES" and provide the schema in the file `schema.graphql`. It will use a [GraphQL Transform](https://aws-amplify.github.io/docs/cli/graphql?sdk=js) directive [@model](https://aws-amplify.github.io/docs/cli/graphql?sdk=js#model) to deploy and configure a DynamoDB table to store messages:

    ```bash
    amplify add api
    ```

6. Execute 

    ```bash
    amplify add hosting
    ``` 

    from the project's root folder and follow the prompts to create an S3 bucket (DEV) and/or a CloudFront distribution (PROD). If you are deploying a CloudFront distribution, be mindful it needs to be replicated across all points of presence globally and it might take up to 15 minutes to do so. More info on the [Amplify CLI docs](https://aws-amplify.github.io/docs/cli/hosting?sdk=js).
7. Build, deploy, upload and publish the application with a single command:

   ```bash
   amplify publish
   ```

## Using it with the [Amplify Console](https://aws.amazon.com/amplify/console/)

1. Fork this repository into your own GitHub account
2. Commit the changes to your forked repository. A new folder `amplify` will be commited with the project details.
3. Connect your repository to the [Amplify Console](https://console.aws.amazon.com/amplify/home?#/create) as per the instructions [here](https://docs.aws.amazon.com/amplify/latest/userguide/getting-started.html), making sure the name of the branch in your repository matches the name of the environment configured on `amplify init` (i.e. master). When prompted with "_We detected a backend created with the Amplify Framework. Would you like Amplify Console to deploy these resources with your frontend?_", select **"YES"** and provide or create an IAM role with appropriate permissions to build the backend resources
4. Wait for the build, deployment and verification steps
5. Deploy and access your app (xxxxxxxx.amplifyapp.com)




Access the app from multiple devices or send the S3/CloudFront/AmplifyApp.com link to friends to test Serverless GraphQL real-time subscriptions
