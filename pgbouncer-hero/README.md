# PgBouncer Hero
PgBouncer Hero is an dashboard GUI to PgBouncer.

## PgBouncer Hero Official

[Click here](https://github.com/kwent/pgbouncer-hero)

## Versions

- PgBouncer Hero: 1.0.0
- Ruby: 2.5.0
- Alpine Linux: 3.7

## Usage

Clone:

- ```git clone https://github.com/danvincenzi/dockerfile.git```
- ```cd dockerfile/pgbouncer-hero/alpine/1.0.0```

Build:

- ```docker build --tag pgbouncer-hero:1.0.0 .```

Run:

- ```docker run --name pgbouncer-hero --publish 8080:8080 --detach pgbouncer-hero:1.0.0```
