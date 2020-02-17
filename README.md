[![GoDoc](https://godoc.org/github.com/golang-migrate/migrate?status.svg)](https://github.com/pressly/goose)

# goose: golang migrations with sql

## Install
    
    $ go get -u github.com/pressly/goose/cmd/goose

This will install the `goose` binary to your `$GOPATH/bin` directory.

## Usage 
Check usage goose command.

    $ goose -h


### create

Create a new SQL migration.

    $ goose create add_some_column sql

### up

Apply all available migrations.

    $ goose mysql "user:password@/dbname?parseTime=true" up

### up-to

Migrate up to a specific version.

    $ goose mysql "user:password@/dbname?parseTime=true" up-to 20170506082420

### up-by-one

Migrate up a single migration from the current version

    $ goose mysql "user:password@/dbname?parseTime=true" up-by-one

### down

Roll back a single migration from the current version.

    $ goose down

### down-to

Roll back migrations to a specific version.

    $ goose down-to 20170506082527

### redo

Roll back the most recently applied migration, then run it again.

    $ goose redo

### status

Print the status of all migrations:

    $ goose status

### version

Print the current version of the database:

    $ goose version

## Migrations
goose supports migrations written in SQL or in Go.

### SQL Migrations
A sample SQL migration looks like:

```sql
-- +goose Up
CREATE TABLE post (
    id int NOT NULL,
    title text,
    body text,
    PRIMARY KEY(id)
);

-- +goose Down
DROP TABLE post;
```

See more documentation [`Pressly/Goose`](https://github.com/pressly/goose)