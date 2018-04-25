### Description

Prepare a Rails application in a container ready to be started. It was created to be used as a part of a more complex docker config to start a Rails application.

## What it includes?

- Ruby 2.4.1
    
## Run

Without database
```javascript
$ docker container run -it -p 3000:3000 \
                           -v APPLICATION_PATH:/usr/src/app/rails-app \
                           --entrypoint /usr/bin/remove_server_pid \
                           IMAGE_NAME \
                           bash
```

With database (you need to configure the database.yml of your project to access your DB container)
```javascript
$ docker container run -it -p 3000:3000 \
                           -v APPLICATION_PATH:/usr/src/app/rails-app \
                           --link YOUR_DB_CONTAINER_NAME \
                           --entrypoint /usr/bin/remove_server_pid \
                           --entrypoint /usr/bin/run_migrate \
                           IMAGE_NAME \
                           bash
```