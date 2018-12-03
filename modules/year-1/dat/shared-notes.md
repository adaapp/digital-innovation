#Databases Day 1 

##What is a database?

·      somewhere to store data
·      info about data -metadata
·      relationships/links
·      statistics
·      integrity
·      performance
·      structure
        - security


Functional dependency - There can be many cars with the same engine size but only one car for each registration. The unique car registration identifies the car, therefore ‘CarReg -> Engine Size’ (Engine Size is functionally dependant on Car Reg).

Relational databases use SQL (Structured Query Language)
According to Stack Overflow Developer Survey Results 2018, MySQL and SQL Server are the most commonly used databases...
·       MySQL: 58.7%
·       SQL Server: 41.2%
·       PostgreSQL: 32.9%
·       SQLite: 19.7%

NoSQL database examples
·       MongoDB. Open-source document database.
·       CouchDB. Database that uses JSON for documents, JavaScript for MapReduce queries, and regular HTTP for an API.
·       GemFire. ...
·       Redis. ...
·       Cassandra. ...
·       memcached. ...
·       Hazelcast. ...
·       HBase.


When an application storing data increments the ID by one it makes the URL more predictable and more vulnerable.
 
Secondary keys used to access accounts. Uniquely identifies that record in its table.
 
Foreign key used to access a different row with related information.
 
Differences between secondary Key and Foreign Key

secondary Key
Foreign Key
Secondary key uniquely identifies a record in the table.
Foreign key is a field in the table that is secondary key in another table. 
Secondary Key can't accept null values.
Foreign key can accept multiple null value.
By default, secondary key is clustered index and data in the database table is physically organized in the sequence of clustered index.
Foreign key does not automatically create an index, clustered or non-clustered. You can manually create an index on foreign key.
We can have only one secondary key in a table.
We can have more than one foreign key in a table.
 
 Avoid repetition and data redundancy across schemas.
Rules:
Each cell can only contain a single piece of information

##Databases Day 2


ID
name
city
postcode
1
AlexA
London
S4 123

id has no functional dependencies as it is unique and thus is used as the secondary key for the table. 
Name depends on the iD.
Postcode depends on City.
Composite key is used where more than one value is used as a secondary key

Atomic Values:

An atomic value is a value that cannot be divided. An example of a non-atomic value is an address as it models House Number, Street, Borough, City, Postcode. We could break these down into separate values to make the data atomic.

First Normal Form (1NF)

For a table to be in the First Normal Form, it should follow the following 5 rules:
It should only have single(atomic) valued attributes/columns.
Values stored in a column should be of the same domain
All the columns in a table should have unique names (No Repeating Groups).
And the order in which data is stored, does not matter.
Each row should be unique - with a unique primary key

In order to make data conform to the first normal form, then it may be needed to separate the data out into a second table - one for each entity/object.



Second Normal Form (2NF)

For a table to be in the Second Normal Form,
It should be in the First Normal form.
And, it should not have any Partial Dependencies.
No Redundant Columns
Each Column should depend on the primary key

Partial Dependency exists, when for a composite secondary key, any attribute in the table depends only on a part of the secondary key and not on the complete secondary key.
To remove Partial dependencies, we can divide the table, remove the attribute which is causing the partial dependency, and move it to some other table where it fits in well.


Third Normal Form (3NF)

A table is said to be in the Third Normal Form when,
It is in the Second Normal form.
And, it doesn't have any Transitive Dependencies.

Transitive Dependency Example

By its nature, a transitive dependency requires three or more attributes (or database columns) that have a functional dependency between them, meaning that Column A in a table relies on Column B through an intermediate Column C.

#AUTHORS

Author_ID
Author
Book
Author_Nationality
Auth_001
Orson Scott Card
Ender's Game
United States
Auth_001
Orson Scott Card
Ender's Shadow
United States
Auth_002
Margaret Atwood
The Handmaid's Tale
Canada

In the AUTHORS example above:

Book → Author: Here, the Book attribute determines the Author attribute. If you know the book name, you can learn the author's name. However, Author does not determine Book, because an author can write multiple books. For example, just because we know the author's name Orson Scott Card, we still don't know the book name.
Author → Author_Nationality: Likewise, the Author attribute determines the Author_Nationality, but not the other way around; just because we know the nationality does not mean we can determine the author.


But this table introduces a transitive dependency:
Book →Author_Nationality: If we know the book name, we can determine the nationality via the Author column.


Long story short, separate any repeated data into unique tables.

Mnemonic: “Every attribute should be a fact about the primary key, the whole key and nothing but the key - so help me Codd”

##Databases Day 4 - NOTES

ACID/CAP Theorem slides: https://docs.google.com/presentation/d/1Xv-rwqvCNReXItrvmD_WHMTLsMkoZsS4lQD3koq8snI/edit?usp=sharing 

ACID
Acid is a set of rules that a DBMS can follow to prevent inconsistency in the face of errors, power outages, etc.
It’s implemented through ‘transactions’. Typically it’s a set of SQL statements designed to run together as a single operation.

Example:
Visitor bought an item -> mark transaction as complete & decrease item amount.


Atomicity 
Entire action has to be treated as one unit (Either works or not).
An error at the end of a transaction will rollback all other changes
 in the transaction.

Consistency
Database must be in a valid state at the end of a transaction.
All constraints must be true at the end.
If they’re not - it’ll be rolled back.

Isolation 
Transactions are often executed concurrently.
The end result has to be the same as running them sequentially.
The order they happen in should not have an affect on 
the outcome.

Durability 
When a transaction is committed (completed without errors), 
it has to stay committed even if there’s a later problem.
That means the data has to be written to a disk.

Acidity test: Check it conforms to the above, or use a pH meter (This is a poor joke)
CAP Theorem

Distributed system
A system (program, service, app) that runs over more than one computer and relies on a network for communication.



The theorem: Consistency, availability & Partition tolerance - You can have two but not all three.



Consistency
Availability
Partition Tolerance
Every query gets the most up to date answer, or an error.
This is different to the version in acid. In this version, querying any nodes at the same time should give back the same answer.
Every request receives a non-error response.
Though we may not have the most up to date data
The system will stay online even if there are network issues.


Why only two?
As standard we want partition tolerance - so we can only really pick one other.

AP:
All nodes will be online but may not be consistent in their information
If we want availability, we could have each thing respond with the last thing it knew.

In the case of a network partition it’s impossible to update disconnected nodes, so we have a choice as to whether they respond with the last know entity or they don’t respond/give an error message

SQL Security
One way of locking down access to the database is to isolate it inside a VPN and then only allow read/write access via a server under your control or restricted to a specific IP address.



SQL Injection
https://www.owasp.org/index.php/SQL_Injection_Prevention_Cheat_Sheet
Primary Defenses to prevent SQL injection attacks:
Option 1: Use of Prepared Statements (with Parameterized Queries)
Option 2: Use of Stored Procedures
Option 3: Whitelist Input Validation
Option 4: Escaping All User Supplied Input

An example of an unsafe query command looks like the following - avoid writing this in your code.

Any sensitive data should be stored in a database in encrypted format - definitely not in plain text. Hash it or encrypt it some other way - just please don’t think it’s inherently safe because you built it. 


Databases Day 4 - LINKS 


Jade and Stuart’s - GRAPH DATABASES
https://docs.google.com/document/d/1xoObLeLJZX89uTSfDx4y3rCkZR8m1Bg3CUpYn_jG0Oo/edit 

Lewis’ Wide Column Store  
https://drive.google.com/open?id=13cOUr3as8Gnes74EpF-rM9ysAu4WapTU


Vivian Lopes - Search Engines https://docs.google.com/document/d/1_un7Yc9N4FyY5i40zR29Vt86zVZyX5rTLDus2SR92I8/edit

Paul Oladele Slide on Key Value Document Stores 
https://docs.google.com/presentation/d/1DwbQE55rI1SOKO15JBCXMPfRiKjcqvYkgWXtrY1KVR4/edit#slide=id.p


Kaltun Ahmed: Document based databases 
https://docs.google.com/presentation/d/1IIN3IIs5kavEmpgQtSq1_HPgcvIZTvSt9N_oBSpdX3A/edit?usp=sharing

Joe shahrukh and greg
https://docs.google.com/presentation/d/17GINI6eCghhhk3heydM-vYG1MFT8esf29Lp9cddfYNc/edit#slide=id.g1cce80a6f7_0_13

Link to original document:
https://docs.google.com/document/d/1UC7t5hLijrNw2u5y20U-U1K_WqVvPVoAA-WUthvaM38/edit
