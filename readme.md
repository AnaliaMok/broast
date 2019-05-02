# Broast

A Laravel-based GraphQL endpoint meant to serve a front-end application for a coffee distribution company.

## Stack
* Laravel 5.8
  * Using this variant [https://github.com/autoidle/laravel-heroku](https://github.com/autoidle/laravel-heroku) which justs provides out of the box configuration for deployments to Heroku
* Postgres 10
* Redis (For as the Queue Driver) - May or may not be used

## Packages Worth Noting
* Laravel Nova
  * __WARNING__: If you would like to take advantage of the Nova resources provided, you will need a valid Nova 2.0 or lower license. Otherwise, check the [Nova docs](https://nova.laravel.com/docs/2.0/installation.html#installing-nova-via-composer) to remove the appropriate lines from the composer.json file.
* [Lighthouse PHP](https://lighthouse-php.com/)
  * Package used to configure and serve the graphql endpoint

## Setup
1. Have [Lando rc-2+](https://docs.devwithlando.io/installation/system-requirements.html) and Docker installed on your machine
2. Simply clone this repo and run `lando start` from this project's root directory
3. Next run `lando composer install` and then provide your Laravel Nova account credentials
4. Duplicate the given `.env.example` to create your `.env` file
    * Given that lando ships with the same credentials, the correct credentials have already been configured in the example file.
5. Next, generate a new `APP_KEY` with `lando artisan key:generate`
6. Next, generate the symlink to the local storage folder using `lando artisan storage:link` (Will add to lando recipe as an event)
7. Run `lando artisan migrate` to generate all tables.
8. To generate sample content, run the available seeders with `lando artisan db:seed`
5. Visit [https://broast.lndo.site](https://broast.lndo.site). You should see the default Laravel welcome screen.

### Links
* Navigate to [https://broast.lndo.site/nova](https://broast.lndo.site/nova) to log into the admin dashboard.
    * For first time login, run `lando artisan nova:user` and follow the prompts to create a new login.
* Navigate to [https://broast.lndo.site/telescope](https://broast.lndo.site/telescope) to open the debugging dashboard. __NOTE__: This project is preconfigured to install telescope only for local development.
* Navigate to [https://broast.lndo.site/graphql-playground](https://broast.lndo.site/graphql-playground) to open GraphQL Playground to test your queries.

Happy Hacking!