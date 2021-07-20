# DBMS

## Note - This notes are made from videos of Sanchit Jain Youtube (Knowledge Gate). I will really suggest to watch those videos because he explained all these really well and funny way. I can guarantee that you will not get bored at any point.

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
4. DBMS - used to create, manipulate and delete data

### Disadvantage of File Processing in DBMS

#### Disadvatage of file system

1. Data Redundancy - Data redundancy occurs when the same piece of data exists in multiple places
2. Data Inconsistency - Data inconsistency is when the same data exists in **different** formats in multiple tables
3. Difficulty in Accessing Data
4. Data Isolation - This problem arises due to the scattering of data in various files with various formats.
5. Security Problem - Read, Edit, View etc
6. Atomicity Problem - Atomicity is a feature of databases systems dictating where a transaction must be all-or-nothing. That is, the transaction must either fully happen, or not happen at all. It must not complete partially.
7. Concurrent Access Anomalies - Anomalies occur when changes made by one user gets lost because of changes made by other user.
8. Integrity Problem - Data integrity is the maintenance of, and the assurance of, data accuracy and consistency over its entire life-cycle and is a critical aspect to the design, implementation, and usage of any system that stores, processes, or retrieves data

### OLAP VS OLTP

| | Online Analytical Processing | Online Transaction Processing |
| --- | --- | --- |
| type | Historical Data | Current Data |
| purpose |  Subject Oriented | Application Oriented |
| use | decision making | day to day operations |
| Size | TB, PB | MB, GB |
| who | CEO MD GM | clerks, managers |
| Operations | Read | Read/Write |


