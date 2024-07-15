
## Subquery Performance

Each query plan consists of nodes, and they can be nested and executed from the inside out. 

Each of the nodes has a set of associated statistics, like the cost, the number of rows that are returned, the number of loops that are performed (if needed), and some other choices.

The most common ones node scans are as follows:

- Seq Scan – This is a sequential scan that is performed over a table within the database. It can be very slow if we’re retrieving many rows in a table, so it is best to avoid these types of nodes for large tables.
- Index Scan – A scan over an index can be much faster to find data. Think of it like searching through the table of contents or glossary in a book to point you to a specific page. This is much faster than looking at each page one at a time. Index scans tend to be the fastest means to search for data.
- Bitmap Index Scan and Bitmap Heap Scan – In terms of performance, the bitmap scans fall in between the sequential scan and the index scan. These can occur if we are reading too much data from an index scan, but too little from a sequential scan.

### EXPLAIN

EXPLAIN with attempt to create an estimation of the execution plan based on the statistics that it currently has. It will not run the query. This can be misleading.


### EXPLAIN ANALYZE

In PostgreSQL, this will allow the query to be executed as well.


```SQL
EXPLAIN ANALYZE
SELECT * FROM customer
WHERE support_rep_id IN
(SELECT employee_id FROM employee
WHERE reports_to = 1);
```

Returns

|QUERY PLAN|
|---|
|Hash Join (cost=11.01..21.78 rows=1 width=1142) (actual time=0.103..0.105 rows=0 loops=1)|
|Hash Cond: (customer.support_rep_id = employee.employee_id)|
|-> Seq Scan on customer (cost=0.00..10.60 rows=60 width=1142) (actual time=0.022..0.036 rows=59 loops=1)|
|-> Hash (cost=11.00..11.00 rows=1 width=4) (actual time=0.025..0.025 rows=2 loops=1)|
|Buckets: 1024 Batches: 1 Memory Usage: 9kB|
|-> Seq Scan on employee (cost=0.00..11.00 rows=1 width=4) (actual time=0.017..0.019 rows=2 loops=1)|
|Filter: (reports_to = 1)|
|Rows Removed by Filter: 6|
|Planning Time: 3.117 ms|
|Execution Time: 0.199 ms|

### Find Duplicate Rows

```SQL
SELECT phone, COUNT(*) FROM customer GROUP BY phone HAVING COUNT(*) > 1;
```

Use COUNT(\*\) to find duplicates of the grouped criteria

This can also be useful for finding something like how many customers a support rep has served

```SQL
SELECT support_rep_id, COUNT(*) F
ROM customer 
GROUP BY support_rep_id HAVING COUNT(*) > 1;
```


## UNION

UNION operator combines result sets of various queries

```SQL
SELECT first_name, last_name, email 
FROM employee 
UNION 
SELECT first_name, last_name, email FROM customer;
```

The above query would return the info for all employees AND customers in one result set

To use the UNION operator, the tables that we are querying from should have the same attribute characteristics, meaning that the number of columns and types of data between the two SELECT statements should match.

Multiple UNIONS can be used to combine many result sets

### UNION ALL

UNION ALL retains duplicates whereas UNION does not

### ANY / ALL

ANY operator returns true if ANY of the values in a subquery meets the condition, else false

ALL returns true if ALL of the conditions in a subquery meets the condition else false


- If we use > ALL, the expression evaluates to true if a value in the subquery is greater than the largest value returned by the subquery.
- If we use >= ALL, the expression evaluates to true if a value in the subquery is greater than or equal to the largest value returned by the subquery.
- If we use < ALL, the expression evaluates to true if a value in the subquery is less than the smallest value returned by the subquery.
- If we use <= ALL, the expression evaluates to true if a value in the subquery is less than or equal to the smallest value returned by the subquery.
- If we use = ALL, the expression evaluates to true if a value in the subquery is equal to every value returned by the subquery.
- If we use != ALL, the expression evaluates to true if a value in the subquery is not equal to any value returned by the subquery.



- If we use > ANY, the expression evaluates to true if a value in the subquery is greater than the smallest value returned by the subquery.
- If we use >= ANY, the expression evaluates to true if a value in the subquery is greater than or equal to the smallest value returned by the subquery.
- If we use < ANY, the expression evaluates to true if a value in the subquery is less than the largest value returned by the subquery.
- If we use <= ANY, the expression evaluates to true if a value in the subquery is less than or equal to the largest value returned by the subquery.
- If we use = ANY, the expression evaluates to true if a value in the subquery is equal to any value returned by the subquery. It works like the IN operator.
- If we use <> ANY, this expression is not the same as the NOT IN. Rather, if we had a scenario where we had column <> ANY (a, b, c), it would look like x <> a OR x <>b OR x<>c.