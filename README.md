# PostgreSQL plugin for Dokku

Project: https://github.com/progrium/dokku

## Installation

```
cd /var/lib/dokku/plugins
git clone https://github.com/ohardy/dokku-psql psql
dokku plugins-install
```


## Commands
```
$ dokku help
    psql:console     <app>            Launch a postgresql console for a given app
    psql:create      <app>            Create a Postgresql database
    psql:delete      <app>            Delete specified Postgresql database
    psql:dump_sql    <app> <filename> Dump database to SQL format
    psql:restore_sql <app> <filename> Restore database from SQL format
    psql:dump_tar    <app> <filename> Dump database to tar format
    psql:restore_tar <app> <filename> Restore database from tar format
    psql:admin_console                Launch a postgresql console as admin user
    psql:start                        Start the Postgresql docker container if it isn't running
    psql:stop                         Stop the Postgresql docker container
    psql:status                       Shows status of Postgresql
    psql:list                         List all databases
```

## Usage

### Start PostgreSQL:
```
$ dokku psql:start                 # Server side
..or..
$ ssh dokku@server psql:start      # Client side

```

### Create a new database:
```
$ dokku psql:create foo            # Server side
..or..
$ ssh dokku@server psql:create foo # Client side
```

### Dump database to SQL:
```
$ dokku psql:dump_sql foo filename.sql # Server side
```

### Restore database from SQL:
```
$ dokku psql:restore_sql foo filename.sql # Server side
```

### Dump database to tar:
```
$ dokku psql:dump_tar foo filename.tar # Server side
```

### Restore database from tar:
```
$ dokku psql:restore_tar foo filename.tar # Server side
```
