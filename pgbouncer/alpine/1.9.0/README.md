# PgBouncer
This is a minimal PgBouncer image, based on Alpine Linux.

## PgBouncer Official
PgBouncer is an Lightweight connection pooler for PostgreSQL.

[Click here](https://pgbouncer.github.io)
 
## Versions

- PgBouncer: 1.9.0
- Alpine Linux: 3.8

## Features

* Very small, quick to pull (just 15.3MB);
* Using LibreSSL;
* Uses standard PgBouncer port 6432;
* Includes PostgreSQL client tools such as psql, pg_isready.

## Usage

Clone:

- ``` git clone https://github.com/danvincenzi/dockerfile.git ```
- ``` cd dockerfile/pgbouncer/alpine/1.9.0 ```

Build:

- ``` docker build --tag pgbouncer:1.9.0 . ```

Run:

- ``` docker run --name pgbouncer --publish 6432:6432 --detach pgbouncer:1.9.0 ```
