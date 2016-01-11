## Objectives

* Understand what Heroku is
* Understand what an environment variable is
* Be able to use the `dotenv` core module
* Be able to deploy an Node/Express app to Heroku using the CLI
* Be able to connect your app to a postgres database on heroku

## EXERCISE SUMMARY

__STEP 1:__
Included in this repo is a CRUD app that uses a local Postgres database. Your mission will be to deploy the included repo to Heroku and connect it to a Heroku provided Postgres database.

__STEP 2:__
Deploy your Restaurants CRUD app to Heroku and update your README to include the url for your deployed app.

## What is Heroku?

Google `how does heroku work` and click on the `https://devcenter.heroku.com` link. Read the documentation through __RELEASES__ and stop. Then, use the documentation to answer the following questions:

1. What dependency file does Heroku use to deploy your Node.js app?
1. How does Git relate to Heroku?
1. How does Heroku associate your repo to its platform?
1. What is a slug?
1. What is a dyno?
1. What is a config variable?
1. What is a release?

Using [draw.io](https://www.draw.io/) Draw a diagram that illustrates how Heroku works and incorporate the above components. Then, add a `your-name.md` file to
this repo and add your answers to each of the above questions. Add your diagaram, `add`, `commit`, `push` and submit a PR.

## Getting Started with Heroku

1. Sign up for [Heroku](https://signup.heroku.com/)
1. Download the Heroku [Toolbelt](https://toolbelt.heroku.com/)
1. Login - `heroku login`

## Deploying to Heroku From the Command Line

```sh
$ heroku create
```

This command sets up your app, with a random name, on Heroku as well as a Git remote called `heroku`. Alertantively, you can pass in a name as a command line argument to create your own name:

```sh
$ heroku create restaurants-martha (replace the end with your first name)
```

You can also rename your app by running the command:

```sh
$ heroku apps:rename <name-you-want-to-use-instead>
```

## .gitignore

Make sure you have a .gitignore file:

```
/node_modules
npm-debug.log
.DS_Store
/*.env
```

Now you can deploy using Git:

```sh
$ git add -A
$ git commit -m "prep for deployment"
$ git push heroku master
```

Open your Heroku deployed app using:

```
heroku open
```
Click through the app to confirm that everything is working as it should. Is it broken? If so, how can we gain insight about why the app is broken?

## Debugging Heroku

For starters, _always_ confirm that your app is working locally as it should. Then, if all is well locally, continue to debug heroku.

The below command will print out a log of your apps launch process. Sift through it and look for clues about what's going wrong. When you spot a line that looks helpful, grab it a throw it into Google to help you decipher the error.

```
heroku logs
```

## Using the `dotenv` core module to config environment variables

Google `npm dotenv` and read the docs to help you get up and running with a `.env` file in your Node.js app.

1. add a `.env` file to your app
1. update your database configuration to use environment variables

```
process.env.DATABASE_URL || 'postgres://localhost/library'
```

## Connect to a Heroku Hosted Postgres Database

First, run the below command to see if you have any configured envirnment variables. It should be empty, but let's confirm

```
heroku config
```
Ok, now run the below command to tell Heroku you want to connect a database to this app.

```
heroku addons:create heroku-postgresql
```

Check your config variables again. What do you see?

```
heroku config
```

You should see an environment variable called `DATABASE_URL` with a value that is a very long url to a postgres database.

`add`, `commit`, `git push heroku master` and check your app again.

## Getting into your Heroku database

```
heroku pg:psql
```

This drops you into your Heroku database. You can execute raw `sql` here just as you do locally.

Continue the debugging process until you're app is up and running as it should.
