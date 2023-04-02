# dokku-litestream example - Rails

This is an example application for the [dokku-litestream plugin](https://github.com/AxelTheGerman/dokku-litestream).

It is based on a brand new Rails 7 application, extended with a `Post` scaffold and tweaks for deployment on Dokku.

## How to use

You can use this simply as a reference for bringing your SQLite app onto Dokku, use it as sample app to try out the [dokku-litestream plugin](https://github.com/AxelTheGerman/dokku-litestream) or even as a starting point for your next application.

### Step 1: Create a new application on your Dokku server

```
# Create an app on your Dokku host
$ dokku apps:create my-litestream-rails

# Create a persistent storage directory
$ dokku storage:ensure-directory my-litestream-rails--db

# Mount the storage to your app
$ dokku storage:mount my-sqlite-application /var/lib/dokku/data/storage/my-sqlite-application--db:/app/db/litestream
```

### Step 2: Clone this repository and deploy the application

```
git pull https://github.com/AxelTheGerman/dokku-litestream-example-rails.git
cd dokku-litestream-example-rails
git remote add dokku dokku@dokku.me:my-litestream-rails
git push dokku
```

### Step 3: Configure dokku-litestream

Your application should be fully usable at this point - including persistent database across application restarts, deployments and in one-off dokku tasks.

**But any production ready application needs database backups.**

Follow the instructions over at [dokku-litestream](https://github.com/AxelTheGerman/dokku-litestream) for the latest setup instruction.
