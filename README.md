# Quickstart for using Couchbase Capella with Netlify

This is a companion repository to the tutorial: "[Quickstart for using Couchbase with Netlify](https://developer.couchbase.com/tutorial-quickstart-netlify/)" at [developer.couchbase.com](https://developer.couchbase.com), which aims to get you up and running with Couchbase on [NextJS](https://nextjs.org/), connect to a Couchbase cluster, create, read, update, and delete documents, and how to write simple parameterized N1QL queries. It also covers creating a basic front-end using Next.js.

## Prerequisites

To run this prebuilt project, you will need:

- A Couchbase Capella account
- A Netlify account
- A GitHub account
- [Netlify CLI](https://docs.netlify.com/cli/get-started/)
- Node.js 16+

## Update environment variables appropriately

We've included a `.env.example` file with blank values for you to copy into a file called `.env` and fill in the values.
- `COUCHBASE_USERNAME` - The username of an authorized user on your cluster. Follow [these instructions](https://docs.couchbase.com/cloud/clusters/manage-database-users.html#create-database-credentials) to create database credentials on Capella
- `COUCHBASE_PASSWORD` - The password that corresponds to the user specified above
- `COUCHBASE_ENDPOINT` - The Couchbase endpoint to connect to. Use the endpoint of your Couchbase Capella database (formatted like `cb.<xxxxxx>.cloud.couchbase.com`)
- `COUCHBASE_BUCKET` - The bucket you'd like to connect to. Set this to `travel-sample` for this tutorial.

**NOTE on TLS:** The connection logic in this sample app ignores mismatched certificates with the parameter `tls_verify=none`. While this is super helpful in streamlining the connection process for development purposes, it's not very secure and should **not** be used in production. To learn how to secure your connection with proper certificates, see [the Node.js TLS connection tutorial](https://developer.couchbase.com/tutorial-nodejs-tls-connection).

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

Now we're ready to run our application:
```sh
netlify dev
```

If everything is configured properly, you should be able to navigate to localhost:8888 to see the example application.
