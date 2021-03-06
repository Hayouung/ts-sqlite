# tofulite

tofulite is an SQL query wrapper library with support for [sqlite3](https://www.npmjs.com/package/sqlite3) written in TypeScript because SQL scripts are hard to remember.

![CI Status](https://travis-ci.org/Hayouung/tofulite.svg?branch=master)

## API

Usage examples can be found in the test files.

### Query objects

There are 5 total query objects for the following SQL operations:

- Create table (`CreateTableQuery`)
- Drop table (`DropTableQuery`)
- Insert\* (`InsertQuery`)
- Select\* (`SelectQuery`)
- Delete\* (`DeleteQuery`)

Each of these can be turned into an SQL query in string format by calling `sql()` so they could be used for other databases besides sqlite as they are fairly basic queries.

Queries marked with \* are parameterised - these return the string format with ?s in them for any value when you call `sql()` and you can get the values separately by calling `parameters()`.

### Session

`Session` is simply a class that wraps an instance of a `sqlite3.Database`. You can use this class to run the query objects without turning them into strings/raw SQL. `Session` serves more as a helper class - it is completely possible to use all the query objects without ever touching this class.

If you want to make use of `Session`, you will need to make sure you have `sqlite3` installed as a dependency yourself as it is a peer dependency of this package.

You can instantiate a new instance of `Session` in 4 different ways:

- `new Session(db)` - takes an existing `sqlite3.Database` object as param
- `Session.inMemory()` - equivalent to `new sqlite3.Database(":memory:")`
- `Session.anonymous()` - equivalent to `new sqlite3.Database("")`
- `Session.fromFile(filename)` - equivalent to `new sqlite3.Database(filename)`

### Stuff for future

- definitely need to make wheres better
- joins
- constraints
- alter
- jsdoc comments
- update this readme more
