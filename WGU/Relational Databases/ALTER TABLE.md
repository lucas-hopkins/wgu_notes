
## Changing Columns: Data Type

```
ALTER TABLE <tablename>
ALTER COLUMN <columnname>
TYPE <newtype>;
```

## Changing Columns: Data Characteristics

We can assign characteristics like fields size as follows

```
CREATE TABLE registration(
 registration_id int PRIMARY KEY,
 first_name VARCHAR(10),
 last_name VARCHAR(10),
 email VARCHAR(30),
 fee NUMERIC(4,2)
 );
```


In a built table, we can use to insert values

```
INSERT INTO registration VALUES (3, 'Joseph'...);
```

then we can use ALTER TABLE ALTER COLUMN to alter the size or data type

```
ALTER TABLE registration
ALTER COLUMN first_name
TYPE VARCHAR(50),
ALTER COLUMN email
TYPE VARCHAR(100);
```

*NOTE*: We cannot alter a column's data type that has foreign key reference to another table. If there is a foreign key reference, the data type and size have to be the same as the primary key. 

For example, if we tried to alter the artist_id in the album table, due to the foreign key to the artist)id in the artist table, we would get an error.