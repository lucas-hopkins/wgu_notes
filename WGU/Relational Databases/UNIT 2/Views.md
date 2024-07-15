
## Calculations in SELECT Statements

This section is largely about using generic calculations rather than a hard coded value so that it stays relevant across years, or whatever is being calculated.

```SQL
SELECT employee_id, hire_date, birth_date, ROUND(date_part('day',now() -birth_date)/365.25) 
FROM employee;
```

## VIEW

Named query to present a subset of data

```SQL
CREATE VIEW <viewname> AS SELECT <statement>;
```

```SQL
CREATE VIEW customer_contact_3 
AS 
SELECT first_name, last_name, email 
FROM customer 
WHERE support_rep_id = 3;
```

```SQL
CREATE VIEW customer_contact 
AS 
SELECT customer.*, employee.first_name as support_first_name, employee.last_name as support_last_name 
FROM customer, employee 
WHERE customer.support_rep_id = employee.employee_id;
```

Creating a view for a complex query allows you to simply query the view rather than make another complex query

```SQL
CREATE VIEW artist_album_track 
AS 
SELECT artist.name as artist_name, album.title as album_title, track.name as track_name FROM artist 
INNER JOIN album ON artist.artist_id = album.artist_id 
INNER JOIN track ON album.album_id = track.album_id;
```

Then 

```SQL
SELECT * FROM artist_album_track;
```

Rather than do the querying below every time

```SQL
SELECT artist.name as artist_name, album.title as album_title, track.name as track_name FROM artist 
INNER JOIN album ON artist.artist_id = album.artist_id 
INNER JOIN track ON album.album_id = track.album_id;
```

### CREATE / REPLACE VIEW

Can be used when some databases will not allow you to remove a column or add a column from a view. If a view already exists, the columns must be named the same with the same data types and in the same order.

```SQL
CREATE OR REPLACE VIEW invoice_information 
AS
SELECT invoice_id, total, employee.first_name, employee.last_name 
FROM invoice 
INNER JOIN customer ON invoice.customer_id = customer.customer_id 
INNER JOIN employee ON customer.support_rep_id = employee.employee_id;
```

If a data size needs to be altered before the view can be altered we can do 

```SQL
ALTER TABLE employee 
ALTER COLUMN first_name TYPE VARCHAR (40); 
ALTER TABLE employee 
ALTER COLUMN last_name TYPE VARCHAR (40);
```

### DROP VIEW

Use DROP VIEW to delete a view

If other objects use the view, you can use RESTRICT to prevent the view from being dropped. 

IF EXISTS can also be used to ensure the view exists before dropping

CASCADE can be used to automatically drop all of the objects that depend on a view AND all of the objects that depend on the other objects.

