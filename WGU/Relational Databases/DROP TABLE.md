DROP TABLE allows the removal of a table

*NOTE*: You can only drop a table if it is not the "one" side of a one-many relationship.

Using CASCADE allows the table to be dropped, but also removes an constraints that link to the table. 

```
DROP TABLE customer CASCADE;
```
