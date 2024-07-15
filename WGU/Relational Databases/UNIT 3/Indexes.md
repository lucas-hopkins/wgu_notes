
### Types of Indexes

* **Hash Index** - Based on an order list of hash values. Typically we will have a hash algorithm that is used to create a hash value from a key column. This value then points to an entry in a hash table which then points to an actual location of the data row. Hash indexes can only handle simple equality operators and in most cases will be the first index to use when we use the equality operator = .

* **B-Tree Index** - This type of index has the data organized in an upside-down tree. The index tree is stored separately from the data itself. The B-tree index self-balances, meaning that it will take about the same amount of time to access any row in the index regardless of the size of the index.
	* This is the most common type of index in databases and generally is the most useful when we have limited repeating values. B-trees can handle equality and range queries quite well. If the query uses a <, <=, =, >= or > operator, a B-tree index if available could be used. It is generally also used for pattern matching (using the LIKE clause) as long as the pattern is constant and starts with the beginning of the string being set.

* ***Bitmap Index** - Uses a bit array of zeros and ones. These are useful to represent a value or condition that may be true or false.

* **Generalized Search Tree Index (GiST)** - This is a more complex type of index unique to PostgreSQL that is not used often but focuses on certain functionality like searching for a value closest to another value or finding pattern matching. As such, there are special types of operators that could be useful for this purpose like <<, &< &>, >>, <<|, &<|, |&>, |>> @<, @>, ~= and &&.

* **Generalized Inverted Index (GIN)** - This is a unique type of index for **PostgreSQL** that focuses on indexing array values and testing if a value exists. Operators you would see with this include <@, @>, = and &&.

### CREATE INDEX/ DROP INDEX

```
CREATE [UNIQUE] INDEX <indexname> <tablename> (<columnname>) [USING method];
```

```
CREATE UNIQUE INDEX idx_customer_email ON customer(email);
```

```
DROP INDEX [CONCURRENTLY] [IF EXISTS] <indexname> [CASCADE or RESTRICT];
```

IF EXISTS will only remove an index if it exists. Using IF EXISTS will not throw an error if the index does not exist.

```
DROP INDEX IF EXISTS idx_customer_country;
```

CASCADE will automatically drop any objects that depend on the index that we are dropping.

```
DROP INDEX idx_customer_country CASCADE;
```

RESTRICT is set by default, and will not drop the index if we have any objects that depend on it.

```
DROP INDEX idx_customer_country RESTRICT;
```