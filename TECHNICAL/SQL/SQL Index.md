article_type:: [[SQL]]
summary:: Non-Unique indeces used to faster read, but slower write. Clustered indeces can be organised like the data itself.
keywords:: Non-Unique Index, [[B-Tree]], Read Fast, Write Slow, Optimization


# Clustered Index
This type of index is organised like the data itself, like in a library starting with IDs.
There can only be 1 clustered index per table, you can't organize the data in 2 different ways simultaneously. 
You can have multiple indeces, but they don't need to necessarily be organised like the data itself.

# Non-Unique Index

Why adding more indexes to a table?
More indeces mean:
* Read Faster -> Faster to find ordered data
* Write slower -> When data is inserted, need to modify index. Sometimes leading to index re-balancing. Related to [[B-Tree]] data structures

Note: No silver bullets. Forcing indexes can sometimes be worse than having no index.

An index must be created with a query in mind. Infrequent queries are OK to be slow. Indexing is a Database Developer's concern.

You always want to avoid having to read the entire table, so you search the index. Worse than reading ALL of the table, is creating a bad index that is not optimized