
# Most Common Functions
## AVG

The AVG calculates the average of non-null values
```
SELCT AVG(total)
FROM invoice;
```

## COUNT

The COUNT function returns the number of rows in a group including those that have NULL values.
```
SELECT COUNT(custormer_id)
FROM customer
WHERE country = 'USA'
```

## MAX

The MAX function returns the largest of the non-null values
```
SELECT MAX(total)
FROM invoice
WHERE invoice_data betweeen '2009-01-01' AND '2010-01-01'
```
## MIN

The MIN function returns the smallest of the non-null values
```
SELECT MIN(total)
FROM invoice
WHERE invoice_date < '2011-01-01'
```

### MIN MAX  & DATES
The MIN and MAX can also work for dates as well. Dates in databases are stored as a day number, which focuses on the number of days that have passed since a specific point in time. As a day number, the date for yesterday is one less than the day number for today. Older dates therefore end up being smaller numbers than future dates. So the oldest date is actually the MIN, or smallest date, whereas the most recent date is the MAX, or largest date.

## SUM

The SUM function returns the sum of all of the non-null values
```
SELECT SUM(quantity)
FROM invoice_line;
```

*NOTE*: Using the SUM function on a non-numeric column, an error will be thrown. If the query only returns NULL values or if no rows are returned, the SUM returns NULL rather than 0.

## GROUP BY

Helps divide the rows that are being returned from the SELECT statement into specific groups. Then we can apply an aggregate function to each group.

```
SELECT country, COUNT(*) 
FROM customer
GROUP BY country;
```

## HAVING

HAVING clause allows us to specify a search condition for a group or an aggregate. It functions similar to the WHERE clause. WHERE filters individual rows, but HAVING can filter groups of rows. 

```
SELECT billing_country, SUM(total) 
FROM invoice
GROUP BY billing_country
HAVING SUM(total) > 50;
```

```
SELECT country, COUNT(*),COUNT(fax) 
FROM customer
GROUP BY country
HAVING COUNT(*) > 5 AND COUNT(fax) > 2;
```


## Additional PostgreSQL Functions

### BOOL_AND

Returns true if all of the input values are true, else false

### BOOL_OR

Returns true if one of the input values is true, otherwise false.

### STDDEV

This function returns the standard deviation based on the non-null values

### VARIANCE

Returns the variance of the non-null values

### RANK

Returns the rank of the row based on the value. If a row has the same value as the prior row, it will returns the same rank.

### ROUND

```
SELECT customer_id, ROUND(AVG(total),2) 
FROM invoice
GROUP BY customer_id
ORDER BY customer_id;
```

## LIMIT 

Constrains the number of rows that are returned by a query. 

```
SELECT <column>
FROM <tablename>
LIMIT <rowcount>
```
## OFFSET

Used with the LIMIT clause to skip a number of returned rows. In the snippet below, the OFFSET would be used to return the next set of 5 rows from the invoice table. 

```
SELECT *
FROM invoice
ORDER BY total DESC
LIMIT 5
OFFSET 5;
```