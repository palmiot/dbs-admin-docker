# dbs-admin-docker

This is a little and portable ecosystem for store or manage SQL and NoSQL databases using docker-compose.


## Usage

Firstly you need made a copy of the next files for customize later as your preferences:

- `.env.example` to `.env`.
- (optional) `conf/mongod.conf.example` to `conf/mongod.conf`.
- (optional) `conf/php.ini.example` to `conf/php.ini`.
- (optional) `conf/sql.cnf.example` to `conf/sql.cnf`.

Using `docker-compose` becouse it's easy implement all.

```
$ cd /path-to-this-cloned-repo/dbs-admin-docker
$ docker-compose up -d
```

NOTE :: You can remove the argument `-d` if you want see the logs output of containers.

If you want remove all implement, you can use the next command;

```
$ docker-compose down
```

## The panels

Once running the containers, you can see the admin panels using any browser. For this you need know the host and type with correct port into your browser. Example

```
http://172.20.0.6:80 ( PhpMyAdmin for SQL databases)
http://172.20.0.8:8081 ( Mongo-express for NoSQL databases)
```

or

```
http://locahost:30080 ( PhpMyAdmin for SQL databases)
http://localhost:30081 ( Mongo-express for NoSQL databases)
```

The port can be define into `.env` file for both services.


## Customize

You can set customized options into the file `.env` and optional configurations for services into `./conf/` directory. For first, you can follow the next table for understand the fields;


### Environment variables summary for `.env` file.

| Variables | description | default |
| ------------- | ------------- | ------------- |
| DBS_NAME | name of implementation, is irrelevant. | dbs-admin |
| DBS_SHARED_SQL | (path) directory of SQL storage. | /tmp/databases/sql |
| DBS_SHARED_NOSQL | (path) directory of NoSQL storage. | ./databases/nosql |
| DBS_SERVERS_SQL_IMAGE | (image:tag) Docker of SQL server. | mysql:latest |
| DBS_SERVERS_SQL_ROOT_PASSWORD | (string) the password for root user. | root |
| DBS_SERVERS_NOSQL_IMAGE | (image:tag) Docker of NoSQL server. | mongo:latest |
| DBS_SERVERS_NOSQL_ROOT_PASSWORD | (string) the password for root user. | root |
| DBS_PANELS_SQL_IMAGE | (image:tag) Docker of PhpMyAdmin. | phpmyadmin/phpmyadmin:latest |
| DBS_PANELS_SQL_PORT | (integer) port of endpoint access. | 30080 |
| DBS_PANELS_NOSQL_IMAGE | (image:tag) Docker of Mongo-Express. | mongo-express:latest |
| DBS_PANELS_NOSQL_PORT | (integer) port of endpoint access. | 30081 |


### Files into the directory `./conf/*`

This files means a basic implement of attributes of `my.cnf`, `mongodb.conf` and `php.ini` configuration files. You can add here your rules for these files.
