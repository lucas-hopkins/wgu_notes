
## Module 1 
Boolean Logic Order of Operations

In the absence of parentheses
1. NOT
2. AND
3. OR

To evaluate p AND NOT(q OR r):
1. fill in values for p, q ,and r =  T ^ NOT(F OR T)
2.  T AND NOT (T)
3. T AND F
4. F

Problems where
- p is true
- q is true
- r is false

1.  p OR NOT q
	1. T OR F = T
2. NOT r AND (p OR NOT q)
	1. NOT r AND (T OR F)
	2. T AND (T) = T
3. NOT(p AND NOT r)
	1. NOT(T AND T) = F
4. (p OR  r ) AND NOT p
	1. (T OR F) AND F =  F


Describe the proposition in symbols using:
- *p*: The weather is bad
- *q*: The trip is cancelled
- *r:* The trip is delayed
**Proposition**: The trip is delayed and the weather is bad.
**Proposition in symbols**: r AND p


### Compound Statements in Truth Tables

A truth table for a compound statement will have a row for every possible combination of truth assignments for the statement's variables. If there are *n* variables, there are *2^n* rows. In the truth table for the compound proposition (p OR r) AND NOT q, there are three variables and 2^3 = 8 rows.

Compound Proposition: NOT q AND (p OR r)

| p   | q   | r   | NOT q | (p OR r) | NOT q AND (p OR r) |
| --- | --- | --- | ----- | -------- | ------------------ |
| T   | T   | T   | F     | T        | F                  |
| T   | T   | F   | F     | T        | F                  |
| T   | F   | T   | T     | T        | T                  |
| T   | F   | F   | T     | T        | T                  |
| F   | T   | T   | F     | T        | F                  |
| F   | T   | F   | F     | F        | F                  |
| F   | F   | T   | T     | T        | T                  |
| F   | F   | F   | T     | F        | F                  |

Complete the truth table for the proposition (p AND q) OR NOT r

| p   | q   | r   | p AND q | NOT r | (p AND q) OR NOT r |
| --- | --- | --- | ------- | ----- | ------------------ |
| T   | T   | T   | T       | F     | T                  |
| T   | T   | F   | T       | T     | T                  |
| T   | F   | T   | F       | F     | F                  |
| T   | F   | F   | F       | T     | T                  |
| F   | T   | T   | F       | F     | F                  |
| F   | T   | F   | F       | T     | T                  |
| F   | F   | T   | F       | F     | F                  |
| F   | F   | F   | F       | T     | T                  |

The propositional variables p, q, and s have the following truth assignments:
p = T, q= T, s =F. Give the truth value for each proposition
1. p OR NOT q = T
2. (p AND q) OR s = T
3. p AND (q OR s) = T
4. p AND NOT(q OR S) = F
5. NOT(q AND p AND NOT s) = T
6. NOT(p AND NOT(q AND s)) = F 

1. Describe in words when the expression p OR q OR r OR s OR t is true and when it is false
	1. The expression is true is any of the variables are True and false if all of the variables are false
2. Describe in words when the expression p AND q AND r AND s AND t is true and when it is false
	1. The expression is true if all of the variables are True and false if any of the variables are False

## Module 2

**Conditional Operation** is denoted with the symbol ->. The proposition p -> q is read "if p then q". The proposition p -> q is false if p is true and q is false; otherwise p -> q is true

A compound proposition that uses conditional operation is called a **conditional proposition**. When expressed in English, it can be referred to as a **conditional statement** - IF there is a traffic jam, then I will be late for work."

In p->q, the proposition q is called the **hypothesis**, and the proposition q is called the **conclusion**.

