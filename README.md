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

## Entity Relationship Diagram

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

