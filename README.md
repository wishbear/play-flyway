# play-flyway

Flyway plugin for Play 2.1. It aims to be a substitute for play-evolutions.

## Install

In Build.scala/build.sbt

```scala
libraryDependencies += "com.github.tototoshi" %% "play-flyway" % "0.1.3"
```

and write play.plugins.

```
1000:com.github.tototoshi.play2.flyway.Plugin
```

## Usage

### Dev

Almost the same as play-evolutions.

Place your migration scripts in conf/db/migration/${dbName} .


![screenshot](/screenshot1.png)


For existing schema, Flyway has a option called 'initOnMigrate'. This option is enabled when -Ddb.${dbName}.migration.initOnMigrate=true.
For example,
```
$ play -Ddb.default.migration.initOnMigrate
```

Of course, You can write this in your `application.conf`.

### Test

In Test, migration is done automatically.



### Prod

In production mode, migration is done automatically if db.${dbName}.migration.auto is set to be true in application.conf.
Otherwise it failed to start when migration is needed.

