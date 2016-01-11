## What dependency file does Heroku use to deploy your Node.js app?
For us, package.json because we are using Node.js
## How does Git relate to Heroku?
Heroku uses Git as the primary means for deploying applications; also creating a new Heroku app creates a new git remote
## How does Heroku associate your repo to its platform?
Using a new git remote
## What is a slug?
Application source code + fetched dependencies + output of Heroku's build phase are assembled into a slug
## What is a dyno?
Dyno is a secure, virtual environment that is preloaded with our slug
## What is a config variable?
The place we will put all of our secret things to later access via environment variables
Looks like an object
Allows us to set key value pairs for things likely to change between environments
## What is a release?
Releases are an append-only ledger of versions = slugs + config vars
