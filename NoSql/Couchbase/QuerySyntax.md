# Query Syntax

Couchbase though being a NoSQL database supports SQL++ like syntax. This SQL like syntax query language for Couchbase is "N1QL".

N1QL supports SELECT, WHERE, JOINS, GROUP BY, ORDER BY & SubQueries. N1QL also introduces new clauses like NEST & USE KEYS.


## SELECT

```sql
SELECT tutorial.* FROM tutorial
```

```sql
SELECT tutorial.fname || ' '  || tutorial.lname as full_name, tutorial.age, tutorial.email FROM tutorial
```

## Documents not rows

```sql
SELECT tutorial.children[0].fname AS child_name
    FROM tutorial

SELECT tutorial.children[*].fname AS children_names
    FROM tutorial
```

## WHERE

```sql
SELECT fname, email
    FROM tutorial
        WHERE email LIKE '%@gmail.com'
```

## Nested Array with ANY

**Problem Statment**: "Find all the names and emails with a gmail and at-least 1 of their children's age should be 10 0r greater."

```sql
SELECT fname as name, email, children
    FROM tutorial 
        WHERE ANY child IN tutorial.children SATISFIES child.age > 10 END
            AND email LIKE '%@gmail.com' 
```

## Nested Array with EVERY

**Problem Statment**: "Find all the names and emails with a gmail and all their children's age should be 10 0r greater."

```sql
SELECT fname as name, email, children
    FROM tutorial 
        WHERE EVERY child IN tutorial.children SATISFIES child.age > 10 END
            AND email LIKE '%@gmail.com' 
```

## USE KEYS

**Problem Statment**: "Use the 'USE KEYS' clause to retrieve fname and email of 'dave' and 'ian'."

```sql
SELECT fname, email
    FROM tutorial 
        USE KEYS ["dave", "ian"]
```

## LIMIT & OFFSET

**Problem Statment**: "Retrieve 5 documents from the tutorial collection but skip the first 5 documents."

```sql
SELECT fname, email
    FROM tutorial
    LIMIT 5
    OFFSET 5
```

## GROUP BY & HAVING

**Problem Statment**: "Retireve all relations and show how many documents are there against each type of relation."

```sql
SELECT tutorialt.relation, COUNT(tutorial.*) AS count
    FROM tutorial
        GROUP BY relation
        HAVING COUNT(*) > 1
```

## ORDER BY

**Problem Statment**: "Retrieve all the emails with the corresponding count of their children and order them by the number of children they have."

```sql
SELECT tutorial.email, LENGTH(tutorial.children) as children_count
    FROM tutorial
    ORDER BY LENGTH(tutorial.children) DESC
```

## JOINS

**Problem Statment**: "Retreive all products and their reviews. The product must have at-least 20 reviews. Use JOIN."

```sql
SELECT p.productId, p.name, r AS public_reviews
  FROM product p 
  JOIN reviews r ON (META(r).id IN p.reviewList)
  WHERE ARRAY_COUNT(p.reviewList) >= 20
  ORDER BY r.reviewedAt DESC
```

## NEST & UNEST

**Problem Statment**: "Retreive all products and their reviews. The product must have at-least 20 reviews. Nest the reviews into the corresponding product document result."

```sql
SELECT p.productId, p.name, r AS public_reviews
  FROM product p 
  NEST reviews r ON (META(r).id IN p.reviewList)
  WHERE ARRAY_COUNT(p.reviewList) >= 20
  ORDER BY r.reviewedAt DESC
```

**Problem Statment**: "Find the products with the most reviews. Show products with at least 20 reviews."

```sql
SELECT product.name, product.productId, count(reviewID) AS  numReviews 
    FROM product 
        UNNEST reviewList AS reviewID
        GROUP BY product.productId, product.name 
        HAVING count(reviewID) >= 20 
        ORDER BY numReviews desc
```

## SUB-QUERY

**Problem Statment**: ""

```sql
SELECT COUNT(*) AS row_count FROM (
  SELECT r.*
    FROM reviews r
    WHERE productId = 'product0'
    ORDER BY r.reviewedAt DESC
    LIMIT 100
 ) data
```

# Update Query
