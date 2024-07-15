
## Databases vs Flat Files

* Flat file - A data file that is not related to or does not contain any linkages to another file
	* Have issues with integrity, redundancy, flexibility

## Non-Relational Database Types

* Document-Oriented
* Key-Value Stores
* Wide-Column Stores
* Graph Stores

NoSQL - Approach to database design that enables the storage and querying of data outside the traditional structures found in relational databases.

Able to quickly scale out and out perform relational databases for certain tasks. The data model is flexible so the schema can be dynamically modified without downtime. 


### Data Warehouses vs Transactional Databases

A *transactional database* emphasizes consistent and correct data while keeping the speed of the operations in the database. Usually these databases focus on sensitivity. Data is normalized and in 3rd form to enable quick and properly executing transactions. 

Analytical databases are typically warehouses that support business metrics and reporting functionality where a user is not modifying the data, rather than analyzing it. Online analytical processing (OLAP) generally contains a set of tools that are used to process that data from the data warehouse.


## Database Innovation & Common Types

1. File system of the 1960s
	1. Used for record management on mainframes
2. Heirarchical Data Model of the 1970s
	1. Network Data Model  - lookup
3. Relational Models of the 1970s
	1. What is still used today
4. Object-Oriented of the 1980s
	1. Databases use a star schema to support data warehouses from analytical databases. 
		1. Versant, Objectivity, Oracle 12c
5. XML Hybrids of the 1990s
	1. Hybrid of relational and object databases. Helped supported unstructured data as well as having object/relational models for XML documents
6. NoSQL in the 2000s.
	1. These include a key-value store, wide-column store, document-oriented, and graph stores. These data models are meant to be distributed and are highly scalable. They are typically in the petabytes in terms of storage, and use a proprietary API to connect to them.


### Hierarchical & Network Data Models

Looks like upside down tree with levels/segments - set of one-to many relationships.
Each parent segment can have many children, but a child can have only one parent. 

The network work model was created to help with complex data relationships that cannot be represented by the hierarchical data model. A record in the network mode was to able to have more than one parent. 

The network model also helped create the schema, subschema, data manipulation language, and data definition language.

* *schema* - #term conceptual organization of the database
* *subschema* - #term part of the database that applications can see
* *data manipulation language* -  #term Represents commands used to work with the data like SELECT, UPDATE, and INSERT.
* *data definition language* - allows database administrators to create remove various schema components in the database with CREATE, ALTER, and DROP

### Relational Models

The relational model was introduced by E.F. Codd from IBM, who wrote a paper called “A Relational Model of Data for Large Shared Databanks” in the 1970s. Based on Set theory.

#### Model Features

Relational data models were implemented through a complex relational database management system (RDBMS). The RDBMS helps to hide the complexities of the relational model from the user, so that the user only sees the relational database as a collection of tables where the data is stored. All of the underlying physical features of the model are completely hidden.

The relationships in a relational model can be set up as one-to-one or one-to-many. Many-to-many relationships are broken down into two one-to-many relationships, with a table representing the transition between the many-to-many relationships.

The relational data model is where you start to see the use of Structured Query Language (SQL) with the Data Manipulation Language (DML) and Data Definition Language (DDL) statements that originated from the earlier network model.


### Entity-Relationship Model

Chen Notation #term 
	Introduced by Peter Chen. Each entity (a rectangle) is connected by a diamond that 
	contains the relationship name.

Chen Notation for a One-Many Relationship
	![[Pasted image 20240201094536.png]]

Chen Notation for a Many-Many relationship
	![[Pasted image 20240201094447.png]]

Crow's Foot Notation #term 
	Most widely used. One-One, One-Many, Many-Many is expressed with bisecting lines, or a crow's foot (for many)

Crow's Foot Notation for One-Many
	![[Pasted image 20240201094733.png]]

	
UML Notation #term

The connectivity is defined along the relationship line with symbols on each side, like 1..1 for one, and 1..* for many.

UML class diagram notation for a one-to-one relationship between table1 and table2 would look like the following:

![UML Class Diagram Notation for One-to-One Relationship](https://sophialearning.s3.amazonaws.com/markup_pictures/11503/file/6c8199976c164629efbd4d5c536f38c3.png "UML Class Diagram Notation for One-to-One Relationship")

UML class diagram notation for a one-to-many relationship between table1 and table2 would look like the following:

![UML Class Diagram Notation for One-to-Many Relationship](https://sophialearning.s3.amazonaws.com/markup_pictures/11504/file/3189c1cea6a58921518369faa8005475.png "UML Class Diagram Notation for One-to-Many Relationship")

UML class diagram notation for a many-to-many relationship between table1 and table2 would look like the following:

![UML Class Diagram Notation for Many-to-Many Relationship](https://sophialearning.s3.amazonaws.com/markup_pictures/11505/file/581414bad0eaef2055da1d9857ea4f8f.png "UML Class Diagram Notation for Many-to-Many Relationship")


## Object & Hybrid Relational Models

Object Oriented Database Management System (OODBMS).

Tried to closely represent the real world with classes organized in class heirarchy that resembles an upside down tree. Similar in organization to the heirarchical model.

XML is used to store and exchange structured/unstructured data. 
A challenge is fitting current data (Social media) into a structure like a row/column. This is where NoSQL came about. 

In the conceptual design phase, there is a focus on the global view of the entire database to describe the main objects while avoiding the details. The conceptual model uses entities and relationships. The conceptual model should provide a bird's eye view of the data environment, provide identification and high-level descriptions of the main data objects, and avoid database model-specific details. The conceptual model does not depend on any database management software or hardware and should have no primary keys in its entities.

|**Logical Model Elements**|   |
|---|---|
|**Strong Entities**|An entity that is not dependent on any other entity in the schema. A strong entity will always have a primary key.|
|**Weak Entities**|An entity that doesn’t have sufficient attributes to require its own primary key. It depends on a strong entity.|
|**Supertypes/Subtypes**|A supertype entity has smaller groups (subtypes) that connect to it but add specialized attributes common to the specific subtype, while the supertype has attributes that are common to all of the subtypes. For example, a supertype might be 'People' with a subtype for 'Employees', 'Vendors', and 'Customers'.|
|**Binary Relationships**|The type of relationship between two separate entities. When a binary relationship exists, it can be one-to-one, one-to-many, many-to-one, or many-to-many.|
|**Higher-degree Relationships**|A ternary relationship can occur between three entities. Larger numbers of relationships are possible but not recommended.|

A weak entity is one whose existence is dependent on the strong entity. In the same example of a Dog or a Cat entity, both of those would be weak entities, as they would inherit the primary key from the Pet entity to use as a foreign key. They would also be dependent on the Pet entity to exist; that is, a record in the Dog table could not exist without a related record in the Pet table.

Next, you would work through all of the binary relationships between two entities. For example, you would map out the one-to-many relationships between the product and category tables, as well as the customer and order tables. Once you have those relationships mapped, you would move on to define the relationships between three or more entities, until all of the relationships are defined. In our example, we had a many-to-many relationship between the order and product tables that needed to be resolved. We will get into that level of detail in a future tutorial. For now, make note that for any many-to-many relationship in a conceptual model, it must be resolved by having a bridge in the form of an intermediary table that creates two one-to-many relationships.

At the logical model level, we also define the primary keys and foreign keys as part of the relationships between entities, and validate the model through normalization. We typically also define the integrity constraints of the data, if needed. For example, we may define that the quantity of a numeric value must be an integer and must be greater than zero.

Typically, we won’t define the data types and sizes in the logical model, as this stage of database design is not meant to be database-system-specific. However, it is acceptable to generalize the data types in the logical model. For example, identifying which attributes are a 'number' data type versus a 'text' data type.


### Physical Design of a Database
The physical design focuses on data storage, security measures, and performance measures. Before we can define the data storage organization, we have to know the volume of the data and usage patterns. The column data types and sizes are also defined here, so it is important to be aware of the nature of the data. We will also determine the indexes for each table beyond the primary keys, depending on the usage patterns or performance requirements. If there are any anticipated views to create for the database, they would be useful to define now.

With respect to security, we take the time to define the group roles and user roles that can access this database and what level of privileges they should have for each object. This goes beyond the physical data model itself, but it is a crucial step to take when planning for the physical database design. All of the constraints we have defined as part of the logical data model, such as unique or NOT NULL constraints, would also be implemented as part of the physical data model. Once this model has been created, it should be ready to be implemented in the database.