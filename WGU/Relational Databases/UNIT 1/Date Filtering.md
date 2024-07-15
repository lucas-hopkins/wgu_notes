
### PostgreSQL

PostgreSQL formats dates as yyyy-mm-dd
*NOTE*: Dates must be single quoted like a string

now() can be used to return the current date and time

```
SELECT now()
```

To get the date and not the time use:

```
SELECT now()::date;
```

Or just the time, by using:

```
SELECT now()::time;
```

## Date Formatting

Date formatting can be changed with the TO_CHAR function. 

TO_CHAR takes 2 parameters: the value we want to format and the template that defines the format.

```
SELECT TO_CHAR(now()::date, 'mm/dd/yyyy');
```

Example template patterns
- hh – Hour of the day (01-12)
- hh24 – Hour of the day (00-23)
- mi – minute
- ss – second
- ms – millisecond
- yyyy – year in 4 digits
- yy – last 2 digits of the year
- Month – the full month name with the capital first letter
- month – the full month name in lowercase
- Mon – the abbreviated month name
- MM – month number (01-12)
- Day – full capitalized day name
- dd – day of the month
- TZ – upper case time zone name


