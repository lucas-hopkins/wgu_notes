+

## One-to-One

* FK constraint - Record must exist in the parent table before a related record can be added to the child table. 

## One-To-Many

Same idea as the one to one. The parent must exist before the child references it.

## ALTER TABLE

A foreign key can be added to a table with the ALTER TABLE 

```SQL
ALTER TABLE <childtablename> 
ADD CONSTRAINT <constraintname> 
FOREIGN KEY (<fk_column>) 
REFERENCES <parenttablename> (<parent_key_column>);
```

## ON DELETE

We can add ON DELETE SET NULL, which will set the value to null in the child table if the parent record is deleted. This means that the foreign key column would have to allow NULL values to be used.

We can also use the ON DELETE SET DEFAULT clause and pass in a specific value. This means that if the parent record is deleted, the child record would update to a set value. For example, if a manager is deleted, the department could automatically be moved under a specific generic employee and reallocated later on.

The ON DELETE CASCADE clause can be a dangerous one, but it has common uses. Using this clause, a delete on a parent record would also delete all of the referencing rows in the child table.
	For example, in our database, let's assume we used the ON DELETE CASCADE clause on the support_rep_id in the customer table. If this was the case, and we deleted employee_id 1 from the employee table, rather than throwing an error due to the foreign key constraint, it would instead attempt to delete all of the customer records that had the support_rep_id. Subsequently, if we used ON DELETE CASCADE on all of the foreign keys of all of our tables, the database would then try to delete all the invoices that reflected those customers that had the support_rep_id equal to 1. Then it would also delete the invoice_line records that reflect the deleted invoices.

## FOREIGN KEY

Must be inserted in a specific order

1. Start with the tabled that do not have foreign keys to other tables in any order
2. Next, look at the tables that reference those tables
3. Next, we can identify that the following tables are linked to the ones at the prior level and do not have other dependencies:

Deleting foreign key is essentially the same but in reverse order


### Candidate Key

If a foreign key should be linked to something other than the primary key, we can link it to a column with a UNIQUE constraint. 

A candidate key is not a specific type of constraint that can be set in a database. Instead, it is a set of attributes that can uniquely identify a record in a table.

A tale could have multiple candidate keys where one is the primary key for a table. 


### Properties of a candidate key

- The column data should be unique.
- The key can consist of multiple columns.
- It should not contain any null values.
