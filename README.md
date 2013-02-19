# Dreamer Example

Example REST web service using the Dreamer framework.  We implement a web service for a web log.

## Installation and Setup

Install dependencies:

```bash
$ npm install
```

Inspect the schema:
```bash
$ node node_modules/dreamer/bin/dreamer schema
┌─────────────┬─────────┬───────┐
│ blogs       │ type    │ extra │
├─────────────┼─────────┼───────┤
│ name        │ string  │       │
│ description │ string  │       │
│ author_id   │ integer │       │
└─────────────┴─────────┴───────┘
...
```

Inspect resources listing:
```bash
$ node node_modules/dreamer/bin/dreamer resources
┌────────┬────────────────────────────────────────────┬────────┬──────────┐
│ method │ path                                       │ action │ model    │
├────────┼────────────────────────────────────────────┼────────┼──────────┤
│ POST   │ /authors                                   │ create │ authors  │
├────────┼────────────────────────────────────────────┼────────┼──────────┤
│ GET    │ /authors/:author_id                        │ read   │ authors  │
├────────┼────────────────────────────────────────────┼────────┼──────────┤
│ POST   │ /blogs                                     │ create │ blogs    │
├────────┼────────────────────────────────────────────┼────────┼──────────┤
...
```

Initialize the database:

```bash
$ node node_modules/dreamer/bin/dreamer schema-sync

Executing: CREATE TABLE IF NOT EXISTS `blogs` (`name` VARCHAR(255) NOT NULL, `description` VARCHAR(255) NOT NULL, `author_id` INTEGER NOT NULL, `id` INTEGER PRIMARY KEY AUTOINCREMENT);
Executing: CREATE TABLE IF NOT EXISTS `authors` (`name` VARCHAR(255) NOT NULL, `handle` VARCHAR(255) NOT NULL UNIQUE, `email` VARCHAR(255) NOT NULL, `website` VARCHAR(255), `signup_date` DATETIME NOT NULL, `id` INTEGER PRIMARY KEY AUTOINCREMENT);
Executing: CREATE TABLE IF NOT EXISTS `entries` (`title` VARCHAR(255) NOT NULL, `post_time` DATETIME NOT NULL, `content` VARCHAR(255) NOT NULL, `id` INTEGER PRIMARY KEY AUTOINCREMENT);
Executing: CREATE TABLE IF NOT EXISTS `comments` (`post_time` DATETIME NOT NULL, `author_id` INTEGER NOT NULL, `entry_id` INTEGER NOT NULL, `content` TEXT NOT NULL, `id` INTEGER PRIMARY KEY AUTOINCREMENT);
success
```

Start up the server:

```bash
$ node node_modules/dreamer/bin/dreamer run
```

## REST API

See the REST API in [docs/resources.md](docs/resources.md).  Let's try reading and writing some data.

Add an author:
```bash
$ curl -XPOST -H "Content-Type: application/json" http://localhost:3000/authors -d '{
    "name": "James Cooper",
    "email": "james@cooperindustries.biz",
    "handle": "jamez",
    "signup_date": "2013-01-01"
}'
```

Create a blog:
```bash
$ curl -XPOST -H "Content-Type: application/json" http://localhost:3000/blogs -d '{
    "name": "The Life of James Cooper",
    "description": "Trials",
    "author_id": "1"
}'
```

Create an entry:
```bash
curl -XPOST -H "Content-Type: application/json" http://localhost:3000/blogs/1/entries -d '{
    "title": "Waiting for Eighteen Hundred Hours",
    "content": "If you only knew...",
    "post_time": "2013-02-01"
}'
```

Read back what we wrote up in:

```bash
$ curl http://localhost:3000/authors
$ curl http://localhost:3000/blogs
$ curl http://localhost:3000/blogs/1/entries
```
## Where's the code?

There's no code!  It's Markdown all the way through.  The schema is defined in `docs/schema.md` and the interface in `docs/resources.md`.  See the Dreamer framework for more.

