_Example code for debugging composer/docker performance issues_

Timings of running composer inside the container vs. on the host:

    $ time docker-compose run composer install
    real	12m28.002s
    user	0m1.240s
    sys	0m0.279s

    $ time composer install
    real	1m32.133s
    user	0m2.721s
    sys	0m3.256s


# Installation of container

1. Make sure you clone the repository to your home directory. So we don't clash with macOS permission.
2. Run `$ docker-compose up -d` in the root to fetch all Docker requirements.
3. Start the container with `$ docker-compose start` and `$ docker-compose stop` to stop it.

- You can edit the `php.ini` inside `docker/php/php.ini`, you need to restart the containers with `$ docker-compose restart`
- All logs of the webserver container are exposed in the automatically created `log/` directory, PHP/Apache logs are inside `log/s/apache2/`

# Composer

## via Docker

`$ docker-compose run composer [update|require|…]`

Reload composer.json: `$ docker-compose run composer dump-autoload`

