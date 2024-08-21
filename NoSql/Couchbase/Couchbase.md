# Couchbase Database

Couchbase is a database created by Membase and CouchOne in 2011. It aims to provide SQL features in a NoSQL database. Features like ACID, Transactions and SQL like syntax, etc...

## Couchbase Features

- Data Storage
- Query
- Indexes
- Eventing
- Analytics

## Couchbase Data Storage

Couchbase has `Buckets` which have a max memory limit assigned to them. Below Buckets we have `Scopes` & `Collections` which we can use to organize data according to our application needs.

```mermaid
flowchart LR
    A["Buckets"] --> B["Scopes"]
    B --> C["Collections"]
    C --> D["Documents (JSON)"]
```


