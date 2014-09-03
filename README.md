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
    psql:console     <app>                     Launch a postgresql console for a given app
    psql:env         <app>                     Get generated environment variables for <app>
    psql:url         <app>                     Get DATABASE_URL for <app>
    psql:create      <app>                     Create a Postgresql database
    psql:delete      <app>                     Delete specified Postgresql database
    psql:link        <app> <another_app>       Give environment variable of database of <app> to <another_app>
    psql:unlink      <another_app>             Unlink <another_app> to a database
    psql:dump_sql    <app> > <filename.sql>    Dump database to SQL format
    psql:restore_sql <app> < <filename.sql>    Restore database from SQL format
    psql:dump_tar    <app> > <filename.tar>    Dump database to tar format
    psql:restore_tar <app> < <filename.tar>    Restore database from tar format
    psql:admin_console                         Launch a postgresql console as admin user
    psql:restart                               Restart the Postgresql docker container and linked app
    psql:start                                 Start the Postgresql docker container if it isn't running
    psql:stop                                  Stop the Postgresql docker container
    psql:status                                Shows status of Postgresql
    psql:list                                  List all databases
    psql:update                                Update this plugin
    psql:migrate                               Migrate
```

## Updating this plugin
Dokku doesn't handle plugin update. I made a pull request to dokku for that (https://github.com/progrium/dokku/pull/669)

So, each time you update this plugin with `git pull`, you need to call:
```
$ dokku psql:migrate
```

## Info
This plugin adds following environment variables to your app automatically:

* DATABASE_URL
* DB_HOST
* DB_PORT
* DB_NAME
* DB_USER
* DB_PASS

## Usage

### Start PostgreSQL:
```
$ dokku psql:start                 # Server side
..or..
$ ssh dokku@server psql:start      # Client side

```

### Stop PostgreSQL:
```
$ dokku psql:stop                  # Server side
..or..
$ ssh dokku@server psql:stop       # Client side

```

### Restart PostgreSQL:
```
$ dokku psql:restart               # Server side
..or..
$ ssh dokku@server psql:restart    # Client side

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
### Copy database foo to database bar using pipe:
```
$ dokku psql:dump foo | dokku psql:restore bar # Server side
```


## Link
You can link a database to an application :

- Create database:
```
$ dokku psql:create foo
```
- Push another_app to dokku and link it to foo with:
```
$ dokku psql:link foo another_app
```
- Environment variables for database foo will be available in another_app

## Unlink
```
$ dokku psql:unlink another_app # Server side
```
