
Common Data Types
* REAL
* BLOB
* NULL
* INTEGER
* TEXT

If a string is entered into an integer column, SQLite will try to convert it. SQLite also stores the whole string without the concept of a character limit.

Booleans are represented as 0/1

If a date is stored as an integer, SQL stored the number in epoch time.

Tables can be created without any datatype!

```
CREATE TABLE myTable(a, b, c)
```

Primary keys can be NULL

After a table has been created, you can only RENAME TABLE. You can RENAME COLUMN, or ADD COLUMN. 
You cannot add any constraints nor drop/alter a column.

The only outer join is an OUTER LEFT with INNER, LEFT, CROSS, and OUTER.


# MYSQL /MariaDB

The creators of MySQL worried that Oracle would simply kill MySQL because it was a direct competitor to their own enterprise solution, so they created MariaDB as a fork off of the code. The database structure and indexes of MariaDB are the same as MySQL, which allows organizations to switch between the two databases without any change in code.

Incompatibilities can be seen here- https://mariadb.com/kb/en/mariadb-vs-mysql-features/

## Differences with ANSI SQL

```

UPDATE employee
SET pay = pay + 1, new_pay = pay;
```

Assume the original value for pay was 0. In ANSI SQL, the pay value will be set to 1, as it was set as pay = pay + 1. Since the original value for pay was 0, the pay is now 0 + 1, which is equal to 1. However, the value of new_pay would be set to 0, as that was the original value of pay.

In MySQL/Maria, with the same statement, pay would again be set to 1, as it was set as pay = pay + 1. Since the original value for pay was 0, the pay is now 0 + 1 which is equal to 1. However, when new_pay is being set to pay, MySQL/MariaDB uses the updated value. The new_pay is set to 1 instead of 0, unlike with ANSI SQL.

Comments in ANSI are /* */, but in Maria/MySQL, to dashes are used.
