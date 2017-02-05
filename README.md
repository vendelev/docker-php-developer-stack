# PHP developer stack

This stack based on images: [Jinba-Pinba-Board](https://github.com/vendelev/docker-jinba-pinba-board), [PHP7-pinba](https://github.com/vendelev/docker-php7-pinba) and [MariaDB](https://github.com/choobs/docker-mariadb).

# Setup

1. Install [Docker](http://docker.io).
2. Install [Docker-compose](http://docs.docker.com/compose/install/).
3. Clone this repository.
4. Create and customize your configs using default configs (config/*.distr)
5. Create a symbolic link from your project folder to *src/php*
6. Correct MYSQL_ROOT_PASSWORD in the files: "docker-compose.yml" and "config/pinboard/parameters.yml"
7. Add to your "hosts" file "127.0.0.1 site.local pinboard.local jinba.local"

# Usage

Start the stack using *docker-compose*:

```bash
$ docker-compose up -d
```

By default, the stack exposes the following ports:
- 30002: Pinba Server
- 3307: Pinba MySQL
- 3306: MariaDB
- 80: Nginx

Now your can open your project: http://site.local/, Pinboard: http://pinboard.local/ and send Jinba request to http://jinba.local/
