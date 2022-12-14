article_type:: [[SQL]]
summary:: Concept on how to organize data across tables. Analysis have big tables, transactions many smaller tables.
keywords:: Concept, [[Online Transaction Processing (OLTP)]], [[Online Analytical Processing (OLAP)]], Redundancy, Integrity, Normalization, Denormalization


| Denormalize | Small volume of Big Transactions | [[Online Analytical Processing (OLAP)]] |
| ----------- | -------------------------------- | --------------------------------------- |
| Normalize   | Big volume of Small Transactions | [[Online Transaction Processing (OLTP)]]                                        |

# Normalization

Normalization is a concept. Its the process of efficiently organizing data with two goals:
* Controlling Redundancy
* Curate Data Dependencies

There are normal forms, which are guidelines for DB design. Guidelines are not rules.

The more normalization you do, the more:
* Reduce Redundancy
* Increase Integrity
* Reduce Table Size
* Increase Number of Tables

# Denormalization

Denormalizing tables may make sense when looking to analyze data. A bigger denormalized table is easier to analyze as is faster to read than performing many complicated joins 