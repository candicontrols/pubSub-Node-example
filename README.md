# Description
    This sample Node.js app allows you to:

    1. Receive pushed data from Google Pub/Sub as a POST request. Example works from https://{yourDomain}/devices/_ah/push-handlers/time-series/telemetry
    2. Pull data from Google Pub/Sub. Example code is commented out by default and located in api.js 
    3. List all data that has been pushed or pulled from https://{yourDomain}/devices

# Google Pub/Sub Overview Documentation
    https://candicontrols.atlassian.net/wiki/spaces/PAR/pages/190873601/Google+Pub+Sub+Overview

# Simple Setup instructions

1.  Install [Node.js](https://nodejs.org/en/).

    * Optional: Install [Yarn](https://yarnpkg.com/).

1.  Install [git](https://git-scm.com/).
1.  Create a [Google Cloud Platform project](https://console.cloud.google.com).
1.  Install the [Google Cloud SDK](https://cloud.google.com/sdk/).

    * After downloading the SDK, initialize it:

            gcloud init

1.  Acquire local credentials for authenticating with Google Cloud Platform
    services:

        gcloud beta auth application-default login

1.  Clone the repository:

        git clone https://github.com/your-repo.git

1.  Change directory:

        cd your-repo

1.  Create a `config.json` file (copied from the `config-default.json` file):

        cp config-default.json config.json

    * Set `GCLOUD_PROJECT` in `config.json` to your Google Cloud Platform
      project ID.
    * Set `DATA_BACKEND` in `config.json` to one of `"datastore"`, `"cloudsql"`,
      or `"mongodb"`. Note that This example uses datastore.

1.  Install dependencies using NPM or Yarn:

    * Using NPM:

            npm install

    * Using Yarn:

            yarn install

1.  Configure the backing store:

    * If `DATA_BACKEND` is set to `"cloudsql"`:

        1.  Create a Cloud SQL instance, and download and start the Cloud SQL
            proxy:

            Instructions for doing so: https://cloud.google.com/nodejs/getting-started/using-cloud-sql#creating_a_cloud_sql_instance
        1.  Set `MYSQL_USER` in `config.json`, e.g. `"my-cloudsql-username"`.
        1.  Set `MYSQL_PASSWORD` in `config.json`, e.g. `"my-cloudsql-password"`.
        1.  Set `INSTANCE_CONNECTION_NAME` in `config.json`, e.g. `"YOUR_PROJECT_ID:YOUR_REGION:YOUR_INSTANCE_ID"`.
        1.  Run the script to setup the table:

            * Using NPM:

                    npm run init-cloudsql

            * Using Yarn:

                    yarn run init-cloudsql

    * If `DATA_BACKEND` is set to `"mongodb"`:

        1.  Set `MONGO_URL` in `config.json`, e.g. `"mongodb://username:password@123.45.67.890:27017"`.

1.  Start the app using NPM or Yarn:

    * Using NPM:

            npm start

    * Using Yarn:

            yarn start

1.  View the app at [http://localhost:8080](http://localhost:8080).

1.  Stop the app by pressing `Ctrl+C`.

1.  Deploy the app:

        gcloud app deploy

1.  View the deployed app at [https://YOUR_PROJECT_ID.appspot.com](https://YOUR_PROJECT_ID.appspot.com).
