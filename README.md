Creating this for myself so I can easily setup a Laravel (and vue) project with the necessary tools and dependencies.

Copy these files into a new laravel project. For future reference, I used these commands to install the dependencies:
- for php code sniffing: `composer require --dev "squizlabs/php_codesniffer=*"`
- setting up eslint: `npm install eslint --save-dev` and then `npx eslint --init`
- installing vue, bootstrap 5 and popperjs(used by bootstrap)
    `npm install vue bootstrap@next @popperjs/core --save-dev`

Used docker to containerize the application

You can run `php artisan` commands inside docker like this: `docker-compose exec php php artisan`

Do the following to get started
* Run `docker-compose up -d` to build, create, start, and attach the docker containers.

Php
* Run `docker-compose exec php /bin/bash` to start using the bash shell inside the php container
* Run `composer install` to install all composer packages
* Create a new .env file and copy the contents of .env.example into it
* Run `php artisan key:generate` to set the Laravel application key
* Run `php artisan migrate:fresh --seed` to reset and seed the database
* Run the following commands, using [barryvdh/laravel-ide-helper](https://github.com/barryvdh/laravel-ide-helper) to create helper files for IDE autocompletion:
    * `php artisan ide-helper:generate`
    * `php artisan ide-helper:meta`
    * `php artisan ide-helper:models --nowrite`
* Run `php artisan storage:link` to create the symlinks specified in config/filesystems.php

Javascript/Css
* Run `docker-compose exec node /bin/bash` to start using bash inside the node container
* Run `npm install`

If the config for a docker image has been changed, the image needs to be rebuilt for docker to use the new config:
* First, stop the running docker containers with `docker-compose down`
* Run `docker image ls` to get a list of images
* Remove the image, for example 'blog_php_blog': `docker image rm blog_php_blog`
* Run `docker-compose up -d` and docker will automatically rebuild the missing image
