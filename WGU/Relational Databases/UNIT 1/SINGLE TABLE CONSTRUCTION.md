- The table and column names must start with a letter.
- The table and column names can only contain letters, numbers, and underscores.
- The table and column names should not contain spaces (though some databases may allow this).
- The table and column names have a limited length of characters that can be used.

## Common Column Data Types

- Boolean: Stores true, false, or null (no value).
- CHAR(n): A fixed-length character of length n with space added. If a string is added to the column that is shorter than the fixed length, PostgreSQL pads extra spaces up to the length (n) of the column. If we try to insert a value that is longer than the length of the column, an error will be generated.
- VARCHAR(n): A variable-length character string that can store up to n characters. Note that with VARCHAR, unlike CHAR, PostgreSQL does not pad the spaces when the stored string is shorter than the length of the column.
- TEXT: A variable-length character string that has unlimited length.
- SMALLINT: A small integer is a 2-byte signed integer that has a range between -32,768 to 32,767.
- INT: An integer is a 4-byte integer that has a range between -2,147,483,648 to 2,147,483,647.
- SERIAL: The serial is the same as an integer but PostgreSQL will automatically generate and populate the values into this column. We’ll cover this in an upcoming tutorial.
- Float(n): This is a floating-point number that specifies precision that can be up to 8 bytes.
- Real: A 4-byte floating-point number.
- Numeric(p,s): A real number that has p digits, with s number of digits that are displayed after the decimal point.
- Date: Stores the dates on its own.
- Time: Stores the time of day values.
- Timestamp: Stores both the date and time values.

## CREATE TABLE

Syntax

```
CREATE TABLE <table name> ( <column1> <datatype> [constaint], <column2> <datatype> [constaint], etc.)
```

For example

```
CREATE TABLE contact( contact_id int PRIMARY KEY, username VARCHAR(50), password VARCHAR(50) );
```

# TABLE CONSTAINTS

## PRIMARY KEY

## NOT NULL

## UNIQUE
