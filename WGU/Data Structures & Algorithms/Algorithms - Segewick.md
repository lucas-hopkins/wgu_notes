                                                                                                 
## Dynamic Connectivity Problem

### Union Find

Given a set of N objects
- Union command - connects two objects
- Find/connected query - is there a path connecting two objects

Applications of this problem
- Pixels in a digital photo
- Computers in a network
- Friends in a social network
### Modeling the Connections

We assume *is connected to* is an equivalence relation:
- Reflexive - *p* is connected to *p*
- Symmetric: if *p* is connected to *q*, then *q* is connected to *p*
- Transitive: if *p* is connected to *q* and *q* is connected to  *r*, then *p* is connected to *r*

Connected Components - Maximal set of objects that are mutually connected

## Implementing the Operations

Find query - Check if two objects are connected
Union command - Replace components containing two objects into their union

## Goal
Define a data structure for union-find
- Number of objects N can be huge
- Number of operations M can be huge
- Find queries and union commands may be intermixed





### Quick Find

Data structure
- Integer array id[] of size N
- Interpretation: p and q are connected iff they have the same id

Find
- Check if p and q have the same id

Union
- To merge components containing p and q, change all entries whose id equal id[p] to id[q]





