### Database
- A collection of interrelated data -> retrieval, insertion, deletion
- eg. University database: students, faculty, admin staffs

### Database Management System (DBMS)
- the software is designed to operate the database
- eg. MySQL, SQL server, Oracle

### SQL
- structured query language -> view and change the database
- SELECT FROM
- INSERT
- UPDATE
- WHERE
- ...

### Minor diff in DBMS sql
- mysql
  - select **character_length**(data_string) from tableName
- MS SQL server
  - select **len**(data_string) from the tableName

### File System
- a way of arranging the files in the storage medium like hard disk

### Difference Between File System and DBMS
| File System | DBMS |
| ----------- | ---- |
| manage the files and organize the files in storage medium | managing the db |
| redundant(冗余数据；在多个表中存储的重复数据) data | no redundant data |
| no backup and recovery of data if it's lost | backup and recovery of data if it's lost |
| no efficient(有效率的) query processing | efficient query processing |
| less data consistency(一致性) | more data consistency because of normalization |
| less security | more secure |
| less expensive | high cost |

### The process to build database (asked in the interview)
- ideas -> high level design -> relational database schema -> relational DBMS
- example:
  - university information management system
    - student
    - course
    - professor
- ER model
  - entity relationship model -> entity relationship diagram
  - Entity: a component of data -> represent by a rectangle
  - Attribute -> describes the property of an entity
    - key attribute: uniquely identify
      - e.g. student id
    - composite attribute: combination of other attributes
      - e.g. address, which contains city, street, zip code
    - multivalued(多值的) attributes: hold multiple values
      - e.g. student phone number
    - derived(导出的，衍生的) attribute: **dynamic** and **detived** form another attribute
      - e.g. age, because we know the birth date, we could get the student age
  - relationship 
    - degree of relationship: number of different entities participating
      - unary relationsjip
      - binary relationship
      - n-ary relationship
  - Cardinality(基数): the number of times of an entity participates in a relationship set
    - One to One
    - Many to One
    - Many to Many
  - participation constraint
    - total participation: each entity **must** participate in the relationship; use 2 lines to present
    - partial participation: the entity **may or may not** participate in the relationship; use 1 line to present
  - constraints(约束) in relational model
    - domain constraints: each field of table should be atmoic value(not composite, not multivalued)
    - key constraints: primary key unique define each row
    - referential(有所指的) integrity(完整，诚实， 正直) constraints
- map from ER diagram to relational model
  - case1: binary relationship with 1 to 1 cardinality with total participation of entity
    - step1: entity/relationship -> table
    - step2: optimize
  - case2: binary relationship with 1 to 1 cardinality with partial participation of both entity
  - case3: binary relationship with many to 1 cardinality
  - case4: binary relationship with many to many cardinality

### Database Normalization
- eliminate redunant data and ensure data is stored logically
- 6 in total, but achieves its best in 3rd normal form
- 1 Normal Form
  - each table cell contains a single value
  - each record need to be unique
- 2nd Normal Form
  - be in 1st normal form
  - single column primary key
- 3rd Normal Form
  - be in 2nd normal form
  - has no transitive dependency( when changing a non-key column, might cause any of the other non-key columns to change)
- normalization -> split table into several tables -> need more join -> reduce performance
  - it means sometimes the higher normalization, it may bring in low performance
- de-normalization 
