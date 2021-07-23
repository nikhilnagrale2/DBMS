# DBMS

##### Note - This notes are made from videos of Sanchit Jain Youtube (Knowledge Gate). I will really suggest to watch those videos because he explained all these really well. I can guarantee that you will not get bored at any point.

1. E-R Diagram
2. Conversion of E-R diagram into relational model
3. Basics of relational model & functional dependancy
4. Idea about keys/types
5. Normalization (INF-BCNF)
6. Lossless decomposition & dependancy preserving
7. Indexing and Physical Structure (B, B+ Tree)
8. SQL, RA, RC
9. Transaction
10. Concurrency Control

## Basic Fundamentals

### Difference between Data Information Database

1. Data - Raw and Isolated facts about an entity (recorded). eg. text, audio, video, image, map, etc.
2. Information - Processed, meaningful, usable data
3. Database - Collection of similar / related data
4. DBMS - Software used to create, manipulate and delete data

### Disadvantage of File System

1. Data Redundancy - Data redundancy occurs when the same piece of data exists in multiple places
2. Data Inconsistency - Data inconsistency is when the same data exists in different formats in multiple tables
3. Difficulty in Accessing Data
4. Data Isolation - This problem arises due to the scattering of data in various files with various formats.
5. Security Problem - Read, Edit, View etc
6. Atomicity Problem - Atomicity is a feature of databases systems dictating where a transaction must be all-or-nothing. That is, the transaction must either fully happen, or not happen at all. It must not complete partially.
7. Concurrent Access Anomalies - Anomalies occur when changes made by one user gets lost because of changes made by other user.
8. Integrity Problem - Data integrity is the maintenance of, and the assurance of, data accuracy and consistency over its entire life-cycle and is a critical aspect to the design, implementation, and usage of any system that stores, processes, or retrieves data

### OLAP VS OLTP

|            | Online Analytical Processing | Online Transaction Processing |
| ---------- | ---------------------------- | ----------------------------- |
| type       | Historical Data              | Current Data                  |
| purpose    | Subject Oriented             | Application Oriented          |
| use        | decision making              | day to day operations         |
| Size       | TB, PB                       | MB, GB                        |
| who        | CEO MD GM                    | clerks, managers              |
| Operations | Read                         | Read/Write                    |

---

## 1. Entity Relationship Diagram

1. Introduction and Basics
2. Entity and Entity Set
3. Attributes and types
4. Relationship
5. Strong and weak Entity Set
6. Traps
7. Conversion

### Introduction and Basics

1. Introduced by Dr. Peter Chen in 1976
2. A non-technical design method works on conceptual level based on the perception of real world
3. Consists of Collection of basic objects called entities and of relationship among there objects and attributes which defines their properties.
4. Free from ambiguties and provides a standard and logical way of visualizing data
5. Basically it is a diagrammatic representation easy to understand even by non-technical user.

![Entity Relationship Model](https://miro.medium.com/max/700/1*jnG2OLB8Zc9DveIfbx9vRw.png)

### Entity, Entity Sets and its types

1. Entity - An entity is a thing or an object in the real world that is distinguishable from other objects based on the values of the attributes it possess.

2. Types of Entities :-

   - Tangible: Entities which physically exist in real world eg. Car, Pen, BankLocker
   - Intangible: Entities which exists logically eg. Account

3. Entity Sets - Collection/Set of same types of entities ie. that show same properties or attributes called entity set.

### ER diagram and relationship model

| ER diagram                                                               | Relational Model                                                        |
| ------------------------------------------------------------------------ | ----------------------------------------------------------------------- |
| 1. Entity can not be represented in an ER diagram as it is instance/data | 1. Entity can be represented in an relational model by row/tuple/record |
| 2. Entity set is represented by rectangle in ER diagram.                 | 2. Entity set in represnted by table in relational model.               |

### Attributes

- Attributes - are the units that describe the characteristics of entities.

1. For each attribute there is a set of permitted values called domains (ex- roll no should be numeric).
2. In ER diagram represented by ellipse or oval, while in relational model by a separate column.

#### Types of Attributes

| Sr. No. | Simple-Composite                                                                                | Single-Multivalued                                                                                                                                     | Stored-Derived                                                                                                                  |
| ------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| 1.      | Simple cannot be divided further, represented by simple oval                                    | Single can have only one value at a instance of time (eg. college ID)                                                                                  | Stored how value is stored in the data base, represented by simple oval                                                         |
| 2.      | Composite can not be divided further simple attributes, represented by oval connected to a oval | Multivalued can have more than one value at a instance of time (eg. Email), represented by double oval, need to create separate table with primary key | Derived how value can be computed in run time using stored attribute, represented by dotted attribute (age calculated from dob) |

### Relationship in a ER Diagram

- **Relationship** - is an association between two or more entities of same or different entity set.

1. No representation in ER diagram as it is an instance or data.
2. In relational model represented either using a row in a table.

- **Relationship type/set** - A set of similar type of relationship

1. In ER diagram represented by a diamond
2. In relational model either by a separate table or by separate column (foreign key)
3. Every relationship type has three components
   - Name
   - Degree
   - Cardinality ratio/Participation Constraints

### Degree of a relationship in a ER diagram

- **Degree of a Relationship Set** - means the number of entity set associated (participated) in the relationship set.
- Most of relationship sets in the ER diagram are binary. Occasionally however relationship sets involve more than two entity sets.
- eg. Binary, Ternary, Quaternary, N-ary

### Cardinality Ratio and Mapping Cardinalities

1. Express the number of entities to which other entity can be related via a relationship.
2. can be used in decscribing relationship set of any degree but is most useful in binary relationship.
3. Mapping Cardinalities
   - One to One
   - One to Many
   - Many to One
   - Many to Many

- Every one to one relationship is also a one to many and many to one, many to many relationship

### Participation Constraints

- **Participation Constraints**

1. Specifies weather the existance of an entity depends on its being related to another entity via a relationship type
2. these constraints specify the minimum and maximum number of relationship instance that each entity can/must participates in.

- **Max Cardinality**

1. It defines the maximum number of times on entity occurence participating in a relationship.

- **Min Cardinality**

1. It defines the minimum number of times on entity occurence participating in a relationship.

- **Types of Participation**

1. Partial Participation - Not all entities are involved in the relationship. Partial participation is represented by single lines.
2. Total Participation - Each entity is involved in the relationship. Total participation is represented by double lines

---

## 3. Functional Dependency

1. Functional Dependencies, Keys
2. Normalization
3. Indexing, Physical Structures
4. Transaction

### Functional Dependencies, Keys

- **Functional Dependencies**
- The functional dependency is a relationship that exists between two attributes. It typically exists between the primary key and non-key attribute within a table.
- X → Y
- The left side of FD is known as a determinant, the right side of the production is known as a dependent.

### Types of Functional dependency

1. Trivial functional dependency
   A → B has trivial functional dependency if B is a subset of A.
   The following dependencies are also trivial like: A → A, B → B
2. Non-trivial functional dependency
   A → B has a non-trivial functional dependency if B is not a subset of A.
   When A intersection B is NULL, then A → B is called as complete non-trivial.

### Closure of Attribute Set

- Attribute closure of on attribute set A can be defined as a set of attribute which can be functionally determined from it denoted by F^+.

### Armstrong's Axiom/Rule

- Armstrong axioms holds on every relational database can be used to generate closure set

### Primary Rules (RAT)

```ruby
Reflexivity : if Y is subset of X, then X -> Y
Augmentation : if X -> Y, then XZ -> YZ
Transitivity : if X -> Y && Y -> Z, then X -> Z
```

### Secondary Rules

```ruby
Union : if X -> Y && X -> Z, then X -> YZ
Decomposition : if X -> YZ, then X -> Y && X -> Z
Pseudo_Transitivity : if X -> Y && WY -> Z, then WX -> Z
Composition : if X -> Y && Z -> W, then XZ -> YW
```

### Equivalency of Functional Dependency

---

### Canonical Cover, Minimal Set, Irreducible set of FD

---

## 4. Types of Keys

### **Keys**

- A key in DBMS is an attribute or a set of attributes that help to uniquely identify a tuple (or row) in a relation (or table). Keys are also used to establish relationships between the different tables and columns of a relational database. Individual values in a key are called key values.

### **Super Key**

- Super Key is the set of all the keys which help to identify rows in a table uniquely. This means that all those columns of a table than capable of identifying the other columns of that table uniquely will all be considered super keys. Super Key is the superset of a candidate key

### **Candidate Key**

- Candidate keys are those attributes that uniquely identify rows of a table. The Primary Key of a table is selected from one of the candidate keys. So, candidate keys have the same properties as the primary keys. There can be more than one candidate keys in a table.

### **Primary Key**

- A primary key is a column of a table or a set of columns that helps to identify every record present in that table uniquely. There can be only one primary Key in a table. Also, the primary Key cannot have the same values repeating for any row. Every value of the primary key has to be different with no repetitions.

- The PRIMARY KEY (PK) constraint put on a column or set of columns will not allow them to have any null values or any duplicates. One table can have only one primary key constraint. Any value in the primary key cannot be changed by any foreign keys which refer to it.

---

## 5. Normalization

### Insertion Deletion and Updation

- ### Idea

  - In the table student info we have tried to store entire data about student.

- ### Result

  - Entire branch date of a branch must be repeated for every student of the branch

- ### Disadvantages

  1. Insertion, Deletion and Modification Anomalies
  2. Inconsitency (data)
  3. Increase in database size and increase in time (slow)

- ### Insertion anomalies

  - When certain data (attribute) cannot be inserted into database, without the presence of other data.

- ### Deletion anomalies

  - If we delete some data (unwanted), it cause deletion of some other data (wanted)

- ### Updation/Modification Anomalies
  - When we want to update a single piece of data, but it must be done all of its copies.

### Normalization

- As one paragraph contains a singel idea similary are table must contain direct & main data about on Entity.
- Normalization (Decomposition of tables) of table is done on the basis of functional dependencies.
- Normalization is a process which we use to remove redundancy.

### 1NF First Noraml Form

- A table is said to be in first normal form if very cell contain atomic value.
- Each table cell should contain a single value.
- Each record needs to be unique.

### 2NF Second Normal Form

- Rule 1- Be in 1NF
- Rule 2- Single Column Primary Key that does not functionally dependant on any subset of candidate key relation. It must not have partial dependency.

  ### Prime Non-Prime Attribute

  - An attribute that is not part of any candidate key is known as non-prime attribute. An attribute that is a part of one of the candidate keys is known as prime attribute

  ### Partial Dependency

  - Partial Dependency occurs when a non-prime attribute is functionally dependent on **part** of a candidate key. The 2nd Normal Form (2NF) eliminates the Partial Dependency.

### 3NF Third Normal Form

- Rule 1- Be in 2NF
- Rule 2- Has no transitive functional dependencies

  ### Transitive Dependency:

  - A functional dependency from A->B is called if A->B belongs to non-prime.

- Every Dependency from A->B must follow this rules to be in 3rd Normal Form
  1. Either A is superkey
  2. or B is a prime attribute

### BCNF

- BCNF (Boyce-Codd Normal Form)
  Even when a database is in 3rd Normal Form, still there would be anomalies resulted if it has more than one Candidate Key.
  Sometimes BCNF is also referred as 3.5 Normal Form.
  - Every A->B, A must be SuperKey, if it is then BCNF

## 6. Lossless join Decomposition/ Non-Additive

- This property guarantees that the extra or less tuple generation problem does not occur after decomposition.
- It is mandatory property must always holds good.
- If a relation R is decomposed into two relative R1 R2 then it will be loss-less iff
  1. attr(R1) U attr(R2) = attr(R)
  2. attr(R1) intersection attr(R2) not equal phi
  3. attr(R1) intersection attr(R2) -> attr(R1) or
     attr(R1) intersection attr(R2) -> attr(R2)

### Dependency Preserving Decomposition

- If a table R having FD set F, is decomposed into two tables R1 and R2 having FD set F1 and F2 then
  F1 subset of F+
  F2 subset of F+
  (F1UF2)+ = F+

---

## 8. SQL

### Query Languages

- After Designing of database. ie. ER Diagram design then converting it into relational model followed by normalization and indexing now task is how to store, retrieve and modify data in database.

- **Query Languages** - Languages in which user request some information from databse.

- **Procedural Query Language** - Here user instruct the system to perform sequence of operations in order to produre desired result. User tell what data to be retrieved and how to be retrieved.

- **Non-Procedural Query Language** - Here user descrive the desired information without giving the specific procedure for obtaining that information.

### Relational Algebra

- In practice we use RDBMS(Practical Implementation of relational model)
- SQL is used to write query on it.
- So Relational Model is a conceptual/theoritical framework and RDBMS is it implementaion.
- Relational Algebra(Procedural) and Relational Calculus (non-procedural) are mathematical system are query language used on Relational model.

Query Language - Procedural and Non-Procedural
Procedural - Relational Algebra
Non-Procedural - Relational Calculus
Relational Algebra and Relational Calculus = SQL

|                  |           |
| ---------------- | --------- |
| Relational Model | RDBMS     |
| RA, RC           | SQL       |
| Algo             | Code      |
| Conceptual       | Reality   |
| Theoretical      | Practical |

### Relational Algebra

- Relational Algebra is one of the two formal query language associated with relational model.
- Like any other mathematical system is defines a number of operators and use relational (tables) as operands.
- Every operator in relation algebra take one or two relations are input argument and generate a single relation as a result without a name.
- RA do not consider duplicacy as it's based on set theory.
- In each query we describes a step by step procedure for computing the desired result so procedural QL.
- No use of English Keywords.

| Basic/Fundamental Operators | Derived Operators  |
| --------------------------- | ------------------ |
| Select ( σ )                | Natural Join ( ⋈ ) |
| Project ( π )               | Intersection ( ∩ ) |
| Union ( ∪ )                 | Division ( ÷ )     |
| Set Diffrence ( - )         |                    |
| Cartesian Product ( X )     |                    |
| Rename ( ρ )                |                    |

### SELECT Operator ( σ )

- Select is a unary operator so can take only one table at a time.
- It is a fundamental Operator.
- Main idea of select is to find these tuples/rows in a relation which satisfied given condition.
- Syntax => σ condition/predicate^(table name)
- It is same function as of where clause in SQL.
- min number of selected is 0.
- max number of selected is all the tuples.

### Project Operator ( π )

- Unary Operator, take one table at a time.
- Fundamental Operator
- Main idea of project is select desired column
- Syntax π column name ^ (table name)
- It works as select clause of SQL

### Union Intersection and set difference

### Cross Product and Cartesian Product

- Binary Operator, takes two tables at a time.
- Funadamental Operator
- Allow us to combine information between two tables.
- |R1| = m, |R2| = n, |R1xR2| = mn
- R1(A,B,C), R2(C,D,F), R1xR2(A,B,C,D,F) no.of column

---

### Introduction to SQL

- Number of query languages are in use/around 50 are popular, both commercially and research.
- The most popular and widely accepted query language is SQL (Structures Query Language)
- SQL is domain specific not general purpose used in design and management of data held in RDBMS.
- Can do much more than just query a database can define structure of data, modify data in data base specify securiity constraints and number of other tasks.
- Based on relational algebra and tuple relational calculus.
- IBM developed original version of SQL called SEQUEL in Project R in early 1970
- Name later changed to SQL becuase of trademark issues.
- In 1986, American National Standard Institute (ANSI) and ISO published SQL Standard called SQL-86
- Next version, 1989, 1992, 1999, 2003, 2006, 2008, 2011 and most recently 2016.

- **Data Definition Language** - provide commands for defining relation schemas, deleting relation and modifying relation schemas.

  - **Integrity** - Provide commands for integrity constraints on the data stored in DB. eg. Primary key cannot be null, foreign key reference.
  - **View definition** - command for defining views. eg. sorting the result according to same attribute.
  - **Authorization** - commands for access right. eg. read only, R/W grants etc.

- **Data Manipulation Language** - provides the ability to query information from the DB, and insert tuple, delete tuples, and modify tuples in the database eg. insert, delete commands, etc.
  - **Transaction Control** - SQL includes commands for specifying the beginning and ending of transactions. eg. commit, rollback, squ points, etc.
  - **Embedded SQL and Dynamic SQL** - how SQL statemnet can be embedded with in general purpose programming language such as C, C++, Java, etc.

### Data Retrieval

- for data retrival in SQL i/p and o/p both are relations.
- no. of relation i/p to query will be at least are but o/p will always be a singel relation without any name unless specified.
- Basic structure of SQL query consist of these clauses. (SELECT FROM WHERE)
- It should noted that SELECT and FROM mandatory and if not required, then not necessary to write WHERE
- SQL in general is not case sensitive
- SQL allows duplication in a i/p relation as well as in the result of SQL expression.

### SELECT Clause

- is used to pick columns required in result of the query out of all columns in i/p relation.
- order in which column are represented in the select closure will be same in which column will appear in the result.
- if all columns are required then \* can be used.
- may also contains arithmetic expression involving operators like +, -, /, \* etc however it does not change to the database.
- DISTINCT keyword to remove duplicacy

### SELECT with WHERE

- where clause in SQL is used to specify conditions/predicates.
- where closure can have expression involving comparisons operator <,<=,>,>=,=,<> etc.
- SQL allows use of logical connectives and, or, not etc.
- allows 'between' comparision operator to simplify where clause which specify >= to some value and <= to some other value.
- similarly can use 'not between'.

### Set Operations

- SQL provides set operations Union, Intersect, except/minus/set difference which correspons to the mathematical set operations.
- Here union, intersect, minus automatically eliminates duplicate tuple.
- if we want to retain duplicate tuple we write [all' after operators.
- set operations are only applicable between two relations if they are compatible ie. having same number of columns with correspondingly same domain.

### Queries on multiple relations(Cartesian Product)

- so for we have worked on simple query requires only one relation.
- Queries often need more than one realtion for information and to do that are simole idea is cartesian product.
- CP combine two relation into one by Concatenation each tuple of first relation with every possible tuple of second relation.
- CP is commutative in nature so order does not matter
- if same attribute name appears as in both relation, we prefix the name of relation from which attribute originally comes.

### Queries on multiple relations (Natural Join)

- Basically natural join work same as cartesian product but consider only three pair of tuples with the same value on these attribute that appear in the schemas of both relation.
- Notice that common attribute comes only once and prev is also not required as we allow only same value
- commutative in nature.
- may lead to data loss if attributes to be match have different names,or some values occur only in one table.

### Join/Inner Join

- is an operation which works same as cartesian product if used alone.
- but if join is used with keyword using it provides additional functionality.
- provides ability to explicitly share column which must be used by join for comparision and removal of redundant tuples.
- if there are more than one column common between two tables but we do not want each of them to be considered, then we specify which are to be considred by using operator.

### Join with on

- In SQL join with 'on' allows us to use a general pedicate over the relations being joined.
- this predicate is written like a where predicate except for the use of the keyowrd on rather than where
- like CP here we must specify which attribute must be matched.
- more powerful as predicate of where can also be written with on
- on condition can express any SQL predicate
- it imoproves the readability of the query.
- in case of outer join on condition behave differently from where

### Outer join

- One problem with natural join is only those value that appear in both relation will manage to reach find table.
- but if some data is explicitly in table one as table two then that will be lost.
- there are three from of outer join
  - left outer join (left join)
  - right outer join (right join)
  - full outer join (full join/ complete join)

### Rename Operation (as)

- SQL aliases are used to give table or column of a table or column of a table a temporary name.
- Aliases only exists for the duration of the query.
- Uses as clause can appear both in select and from clause.
- often used to name more readable meaning full as smaller
- used for comparing a table with it self.
- new temporary name of table know as table aliases/corelation varibles/tuple variable.
- Just creates a new copy but do not change anything in database.

### String Operations

- SQL specifies strings by enclosing them in single quotes 'Knowledge Gate'
- Equality operation on string may or may not be case sensitive. eg. most of the Db system are case sensitive but MySQL and SQL server are not we can change the behaviour in settings.
- Number of operations are available on string such as conatenation substrings finding length of strings converting string to uppercase or lowercase, etc
- exact set of operations may change from system to system.
- pattern matching can be performed on a string using 'like' operator.
- two special character -> Percent(): match any substring
  -> underscore(): matches with any character
- Pattern matching is case sensitive
- if single quote is part of a string, it must be specified by two singel quote
- for pattern which includs pattern we use escape character just before the special character.

### Ordering the display of tuple

- SQL offer the user some control over the order in which tuples in a relation are displayed
- OrderBy clause causes the tuple in the result of a query to appear in sorted order
- By default order by clause lists items in ascening order we may specify asc for ascending order and desc for descending order.
- ordering can be performed on multiple attribute ie. if there is a tie on the first attribute we sorted according to second attribute.
