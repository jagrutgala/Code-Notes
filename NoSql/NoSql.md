# NoSQL

NoSQL refers to `"Non-Sql"` or `"Not Only Sql"`. It is a database that dosen't rely on relations or uses tabular format to store data. Basically any other data base that is not a Relational Database (RDB).

Example of NOSQL databases are as follows:
- Couchbase DB (Membase & CouchOne)
- Cosmos DB (Microsoft-Azure)
- Dynamo DB (Amazon-AWS)
- Cassandra DB (Apache)

## SQL VS NOSQL

|SQL DB|NOSQL DB|
|---|---|
|Structured Query Language Database.|Non Structured Query Language Database.|
|Stores data in a Tabular format.|Stores data in a key-value pairs or documents or graphs. Anything other than tables.|
|Must support ACID transactions.|May or may not support ACID transactions.|
|Can be scaled vertically but is expensive. Also horizontal scaling is possible but is lot more complex and is expensive to migrate.|Can be scalled both horizontally & vertically in a cost effective way.|
|Optimal for "Transactional Operations".|Optimal for "Low latency access".|

## Benefits of NOSQL Databsae
- Development of software with NOSql is faster as you store data in the format that it is going to be used in.
- NoSQL databases are designed in such a way that they are easy to scale horizontally and vertically.
- Very useful when schema of the data is constantly changing as NoSQL Databases usually don't have a schema to adhere to.

## Drawbacks of NOSQL Databsae
- Complex quering is difficult as data can only be accessed via the Primary Key.
- Each brand of NoSQL database uses its own unique schema. There is a lack of standardization, each unique NoSQL database has it own strengths and weaknesses.
- NoSQL databases have to make tradeoffs to provide unique features, hence it is not guaranteed that ACID priciples will be supported.
