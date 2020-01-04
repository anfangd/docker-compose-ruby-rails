# docker-compose script for Rails & MySQL Development

## Software Stack

|Item|Description|
|:--|:--|
|Ruby|2.5.3|
|Ruby on Rails|Rails 5.2.2|
|bundler|Bundler version 2.0.2|
|MySQL|5.7|

## Content

```bash:Command
tree
├── docker-compose.yml
├── .env
├── mysql
│   ├── Dockerfile
│   ├── conf
│   │   └── etc
│   │      └── my.cnf
│   └── data
└── rails
    │── Dockerfile
    └── src
        │── Gemfile
        └── Gemfile.lock
```

## Set Up

```bash
docker-compose run web rails new . --force --database=mysql --skip-bundle
```

```yml:rails/src/config/database.ym
default: &default
  adapter: mysql2
  encoding: utf8
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password: root
  host: dc-db-mysql
```

```bash
# build
docker-compose build

# boot
docker-compose up -d
```

```bash
docker-compose run web rails db:create
```

```bash
docker-compose down
```

