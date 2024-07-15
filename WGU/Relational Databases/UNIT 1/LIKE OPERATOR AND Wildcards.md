
% represents 0, 1, or more characters or numbers
_ represents a single character or number

If neither is used, LIKE operates as a =

If we have a string ‘abc’ in a table, the following search terms will return the associated results when compared against 'abc':

- ‘abc’ would return true, as the string matches exactly.
- ‘a%’ would return true, as it looks for the letter ‘a’ and 0 or more characters displayed afterward.
- ‘_b_’ would return true, as it looks for one character, then the letter b and the one more character.
- ‘c’ would return false, as it is only looking at the letter c.
- ‘_b’ would return false, as it looks for one character and then the letter b.
- ‘%c’ would return true, as it looks for any number of characters and then the letter c at the end.

## The % Operator

To returns the customer's table and list all of the customers whose name starts with the letter L:

```
SELECT * 
FROM customer 
WHERE first_name like 'L%';
```

If we wanted to list all of the customers who have their email in the domain gmail.com, we would have the % wildcard operator before @gmail.com:

```
SELECT * 
FROM customer
WHERE email like '%@gmail.com';
```


## The _ Operator

If we wanted to look for customers that have the state starting with C and having two characters, we can do the following:

```
SELECT *
FROM customer
WHERE state Like 'C_';
```

## Combining Wildcards

We can combine _ and % to filter specific masks. For example, to select all customer phone numbers, we can use 
```
'+ (___)___+____'
```

To find emails with a two character domain,

```
%.__
```


## Complex Expressions

```
SELECT * 
FROM customer
WHERE email like 'm%@a%.%';
```

In the parameter, we are looking for the letter m, then any number of characters before the @ sign followed by the letter a. Then any number of characters before the dot (.) followed by any number of characters.