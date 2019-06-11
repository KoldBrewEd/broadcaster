# AppSync Broadcaster

Simple app that broadcasts messages to multiple clients using Serverless GraphQL real-time subscriptions powered by AWS AppSync.

The API access is authenticated via API Key valid for 7 days. The demo takes advantage of GraphQL Subscriptions to send messages in real-time to different clients. Messages are saved to a DynamoDB data source.

![Screnshot](/media/broadcaster.png)

## Prerequisites

- [AWS Amplify CLI](https://github.com/aws-amplify/amplify-cli) `(npm install -g @aws-amplify/cli)`
- [Create React App](https://github.com/facebook/create-react-app) `(npm install -g create-react-app)`

## Deploy, Build and Host with One-Click to the Amplify Console

<p align="center">
    <a href="https://console.aws.amazon.com/amplify/home#/deploy?repo=awsed/broadcaster">
        <img src="https://oneclick.amplifyapp.com/button.svg" alt="Deploy to Amplify Console">
    </a>
</p>

## Manual Setup - Deploy, Build and Host

1. Clone the repository
2. Install the required modules:

   ```bash
   npm install
   ```

3. Init the directory as an amplify Javascript project using the React framework:

   ```bash
   amplify init
   ```

4. Add an AppSync GraphQL API with API Key for the API Authentication. Follow the default options. When prompted with "Do you have an annotated GraphQL schema?", select "NO" and copy/paste the schema from the file `schema.graphql` in this repo. It will use a [GraphQL Transform](https://aws-amplify.github.io/docs/cli/graphql?sdk=js) directive [@model](https://aws-amplify.github.io/docs/cli/graphql?sdk=js#model) to deploy and configure a DynamoDB table to store messages:

   ```bash
   amplify add api
   ```

5. Test locally with http://localhost:300 using multiple browsers

   ```bash
   amplify serve
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

Access the app from multiple devices or send the S3/CloudFront/AmplifyApp.com link to friends to test Serverless GraphQL real-time subscriptions
