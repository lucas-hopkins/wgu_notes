
## Table Alias

```SQL
SELECT * FROM customer as c;
```

More complex example

```SQL
SELECT al.album_id, ar.artist_id, t.track_id, al.title, ar.name, t.name 
FROM track as t 
INNER JOIN album as al USING (album_id) 
INNER JOIN artist as ar USING (artist_id) 
ORDER BY al.album_id, ar.artist_id, t.track_id;
```

## Column Alias

Useful for aggregate functions where the result may not always make contextual sense.

```SQL
SELECT customer_id, SUM(total) as "Sum of Total", MAX(total) as "Max of Total" 
FROM invoice 
WHERE billing_country = 'USA' 
GROUP BY customer_id HAVING MAX(total) > 15 AND customer_id BETWEEN 20 AND 30;
```

In the example above, "Max of Total" would display rather than just *total*

