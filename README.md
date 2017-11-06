Run Drupal 8 with Docker

Directory structure:

/data - the database files
/web - drupal source code

-----------------
First launch
------------

Start the containers with:

```docker-compose up```

If it's your first launch, this command will build your containers from the specified images.

Running the command this way instead of deamon mode will make it so that some of the container outputs, such as error logs, get printed to the terminal window.

From another terminal tab, log into the cli container to run composer and drush commands:

`docker-compose run --rm php-cli bash`

or `./cli.sh`

The project root is mounted at /var/www/html

Install a new drupal site with the following command from inside the cli container:

`composer create-project drupal/drupal web`

Drupal should be ready to install at http://127.0.0.1/

The database credentials are:

See the .env file for database credentials, which by default are:
* Database name = drupal)
* Database user=drupal
* Database password=drupal
* Host=db (the name of the container which runs MariaDB)

phpMyAdmin is available [http://127.0.0.1:8080/](http://127.0.0.1:8080/)

Other informations:

In the file .env, the USER_UID must match with the USER_UID of your personnal user to have the same right.

Verify your user id with the command:
`id -u`

and change the data in the .env if necessary. You can used an utility like [direnv](https://direnv.net/) or a global variable.
