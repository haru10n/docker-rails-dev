# docker-rails-dev
Docker template for Rails app or Rails + MySQL development.

# Versions
- Ruby 2.5.0
- Rails 5.2.0
- MySQL 5.7

# Usage
1. Copy env.sample to .env and edit the .env
```
$ cp .env.sample .env
```
2. Run following command
```
$ docker-compose run app rails new . --force --database=mysql --skip-bundle
```
3. Modify config/database.yml as following
```
default: &default
  adapter: mysql2
  encoding: utf8
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password: xxxxxx # <- Modify here.
  host: db # <- Modify here.
```
4. Run 
```
docker-compose up -d
```
5. Finally, you need to create the database. Run
```
docker-compose run app bin/rake db:create
```
6. Open http://localhost:3000/

To stop container then run following command
```
$ docker-compose stop
```
To start container again then run following command
```
$ docker-compose start
```
