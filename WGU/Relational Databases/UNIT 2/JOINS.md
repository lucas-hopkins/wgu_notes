
## Inner/Outer Joins
## Inner Joins

* Essentially used to see where data between two or more tables matches
## Outer Joins

Allows us to get data that may not fully match between two tables

### Left Join
- Finds data that exists in both tables, but also data in the left table that does not match.

### Left Outer Join
- Finds data that exists in the left table, but does not match with data in the right table.

### Right Join
- Finds data that exists in both tables along with the data that does not match from the right table.

### Right Outer Join
- Finds data that exists in the right table, but does not match with data in the left table.

## Natural Joins

Ability is dependent on whether two tables have a column with the same name. 

A natural join links tables together by choosing the rows with common values using their common attribute.

A natural join is a result of 3 stages:

- The first stage creates the product of the two tables together.
- The next stage  takes the output from the prior stage and only displays the rows in which the common attributes are equal to one another.
- Last stage, a PROJECT is performed on the results to have a single copy of each attribute, which removes the duplicate col;

```SQL
SELECT <column_list> FROM <table1> NATURAL [INNER, LEFT, RIGHT] JOIN <table2>
```

**Default is an INNER join**

**Disadvantage** Not always ideal, because they will join all common columns between the two tables.
## JOIN USING

Use JOIN Using to join two or more table by a ==common attribute (column shares the same name)==. This will only return data where the two columns match rather than in a natural join where all of the data is returned. 

USING performs an equality join and can only be used when the column names are identical.
```SQL
SELECT <columnlist> FROM <table1> INNER JOIN <table2> USING (<commonattribute>);
```

```SQL
SELECT * FROM product INNER JOIN category USING (category_id);
```

## JOIN ON

Use JOIN ON to join tables where there is ==no common attribute== 

```SQL
SELECT <columnlist> 
FROM <table1> 
INNER JOIN <table2> ON <table1column> = <table2column>;
```


## USING vs ON

Although we would use this method when the column names between the tables do not match, it does also work if the columns match (and therefore we could use the USING clause). Let's take a look at an example of the artist and album table with an inner join with the USING clause:

```SQL
SELECT title, name 
FROM album 
INNER JOIN artist USING (artist_id);
```

We could convert this by removing the USING clause and adding the artist_id prefixed with the table name:

```SQL
SELECT title, name 
FROM album 
INNER JOIN artist ON album.artist_id = artist.artist_id;
```

In both cases, the result set is the same. ==The only case where the result set would differ is when we use * in the SELECT clause.


# OUTER JOINS

Outer joins allow us to return data that does not exist in a table, or all of the queried tables.

### FULL OUTER JOIN

Returns essentially everything.

```SQL
SELECT * 
FROM representative
FULL OUTER JOIN department ON representative.representative_id = department.manager_id;
```

This will return the three records that match the representative_id from the representative table and the department_id from the department table. 

It will also return the rows from the department table that do not have a matching row in the representative table (4th and 5th row in the result set). It will also return the rows from the representative table that do not have a match in the department table (6th row)


## LEFT JOIN

```SQL
SELECT * 
FROM representative 
LEFT JOIN department ON representative.representative_id = department.manager_id;
```

The left join starts to select data from the left table.

It compares the *representative_id* from the representative table with the *manager_id* in the department table. 

If those values are equal, the left join creates a new row that contains the columns of both tables and adds the new row in the result set.

If the values are not equal, the left join also creates a new row containing columns from both tables, but fills in the columns of the right table (department) with a null value.

## RIGHT JOIN

Essentially the same as LEFT JOIN, but applied to the right table

```SQL
SELECT * 
FROM representative 
RIGHT JOIN department ON representative.representative_id = department.manager_id
```

The left join starts to select data from the right table.

It compares the *representative_id* from the representative table with the *manager_id* in the department table. 

If those values are equal, the right join creates a new row that contains the columns of both tables and adds the new row in the result set.

If the values are not equal, the right join also creates a new row containing columns from both tables, but fills in the columns of the left table (representative) with a null value.


# CROSS JOIN

* Creates a combination of every row from two different tables
	* Also called cross product / cartesian product


One example where we could use a cross join is if we wanted to get all of the potential combinations of a product, like all of its colors and sizes.