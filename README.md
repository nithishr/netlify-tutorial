# Quickstart for using Couchbase Capella with Netlify

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/couchbase-examples/netlify-tutorial)

This is a companion repository to the tutorial: "[Quickstart for using Couchbase with Netlify](https://developer.couchbase.com/tutorial-quickstart-netlify/)" at [developer.couchbase.com](https://developer.couchbase.com), which aims to get you up and running with Couchbase on Netlify

## Prerequisites

To run this prebuilt project, you will need:

- A [Couchbase Capella](https://docs.couchbase.com/cloud/get-started/create-account.html) account (Get started for free with a trial database account)
- A [Netlify](https://www.netlify.com/) account (Get started for free by signing in with your GitHub account)
- A GitHub account
- [Netlify CLI](https://docs.netlify.com/cli/get-started/)
- Node.js 16+ setup and work with the CLI of your choice.

## Update environment variables appropriately

We've included a `.env.example` file with blank values for you to copy into a file called `.env` and fill in the values.
- `COUCHBASE_USERNAME` - The username of an authorized user on your cluster. Follow [these instructions](https://docs.couchbase.com/cloud/clusters/manage-database-users.html#create-database-credentials) to create database credentials on Capella
- `COUCHBASE_PASSWORD` - The password that corresponds to the user specified above
- `COUCHBASE_ENDPOINT` - The Couchbase endpoint to connect to. Use the endpoint of your Couchbase Capella database (formatted like `cb.<xxxxxx>.cloud.couchbase.com`)
- `COUCHBASE_BUCKET` - The bucket you'd like to connect to. Set this to `travel-sample` for this tutorial.

## Set up and Run The Application
The [main tutorial](https://developer.couchbase.com/tutorial-quickstart-netlify/) will walk you through the process of building a web application with Netlify Functions and Capella, but here we'll focus on just cloning and running this example repo.

Clone the source code:

```sh
git clone https://github.com/couchbase-examples/netlify-tutorial.git
```

Install required dependencies:
```sh
npm install
```

You'll have to manually create a database and import the `travel-sample` data.

## Set up your Couchbase Capella database

In this section, we will walk through how to setup Couchbase Capella with sample data called [`travel-sample`](https://docs.couchbase.com/ruby-sdk/current/ref/travel-app-data-model.html). If you do not have a Couchbase Capella account, follow the directions in this [blog article](https://www.couchbase.com/blog/get-started-couchbase-capella/). Please ensure you can sign into your Couchbase Capella account before continuing.

We need to set up a Couchbase Capella database with the sample data and configure the internet and user settings to allow Netlify Functions to access the database.

[Create your Couchbase Capella database](https://www.couchbase.com/blog/get-started-couchbase-capella/) and set up the sample data.

1. On the Couchbase Capella console, create a new database and navigate to it.
2. Click Import Data under the Start tab
3. Import the Travel Sample dataset

Next we need to set up internet settings to allow connections from all IP addresses. This is required for Netlify Functions to access the database for the purpose of this tutorial.

1. Navigate to the `Settings` tab on the database page.
2. Navigate to `Networking > Internet` on the sidebar

> NOTE: We will use the connection string displayed on this screen later in our code that will allow us to configure how to connect to Couchbase Capella via the Couchbase NodeJS SDK. Please copy this information and put it somewhere where you can access it later in the tutorial to save yourself from returning to this screen.

3. Click `Add allowed IP`
4. Allowlist `0.0.0.0/0` and save

Next, we will need to create a user account that can be used to access the database from our Serverless Function.

1. Confirm that you are on the `Settings` tab.
2. Navigate to `Security > Database Access` on the sidebar
3. Enter a memorable name and password as we'll need that later.
4. Select `travel-sample` for Bucket
5. Select `All Scopes` for Scopes
6. Select `Read/Write` for Access

You should now have a Couchbase Capella database, the `travel-sample` data loaded, network access configured, and a user account to access the data setup.

## Run the application

Now we're ready to run our application:

```sh
netlify dev
```

If everything is configured properly, you should be able to navigate to `localhost:8888` to see the example application.
