![[Pasted image 20221206160235.png]]
Bought book out of pocket in Nov 2022 after completing the AWS Build Lab using AWS Neptune within GCC.

## Overall Notes:
* Book does comparisons with SQL 
* Book relies on Gremlin as query language
* Book introduces use cases for graphs and why graphs

## Why now?
**1980-2000s: Relational Databases (SQL)**
Situation that led to their development: 
* Storing data reliably is paramount
* Careful planning set of tables (ERD) and later execution based on that ERD

**2000-2020: No SQL**
Situation that led to their development:
* A lot more data than expected (in volume), mainly thanks to internet
* A lot of unexpected data with varying patterns, thanks to internet
* Existing fixed ERDs cannot handle variability of all these new data

**2020-?: GraphDB**
Situation that led to their development:
* There is untapped information in the relationship between data
* Current DB focuses on storing entities but not how they relate. ERDs and primary keys tend to care for that
* Graph technology focuses on storing relationships, not tables of similar items


## When to use graphs
![[Pasted image 20221206160152.png]]

## Key graph concepts:
* ***Graph***: Representation of data with two distinct elements: vertices and edges
* ***Vertex***: It represents a concept or entity in data
* ***Edge***: It represents a relationship or link from one vertex to another. Can be directed or bi-directional.
* ***Adjacency***: Two vertices are adjacent if they are connected by an edge
* ***Neighborhood***: All vertices adjacent to vertex v are in the neighborhood of vertex v, **N(v)**
* ***Distance***: Number of edges you must traverse from vertex A to vertex B. (same as hops)
* ***Degree***: Number of edges that touch a vertex. Can be further split into In-Degree (in-going edges) and Out-Degree (outgoing edges)
* ***Schema***: Described in terms of labels, it captures how vertices and edges are related. When discussing schema use "Vertex Label" and "Edge Label". Vertices and Edges are data.
* ***Property***: Describes a feature of a vertex or edge, such as name or age.   
* ***Cardinality*** : Number of elements in a set or collection
* ***Set*** : Abstract data type that stores unique values (like set ( ) in python)
* ***Collection***: Abstract data type that stores nonunique values (like a python list [] )


### Graph Use Case: Customer 360
Goal: There is a central object (a customer) and then there are many pieces of data coming from different business domains that say something about the customer. Payment details, demographic, past purchases, address, etc..

Relational Implementation
Achieving C360 using data warehouses has been done. The challenge comes when querying relationally as multiple JOINS are involved. Data is hard to follow, making query writing hard.

Graph implementation
The graph query to only get certain pieces of information is harder than getting the 360 view.

Data modelling is easier in graph, but at this point relational is very mature. Not a clear win for graph. Querying is significantly easier with graph. If the data is not complex enough, graph might not be better than relational. Use relational if just want to get a view of 360.

### Exploring Neighborhoods in Development

	Rule of Thumb#1 : If you want to start your traversal on some piece of data, make that data a vertex
	Rule of Thumb#2 : If you need the data to connect concepts, make that data an edge
	Rule of Thumb#3 : Vertex-Edge-Vertex should read like a sentence or phrase from your queries.
	Rule of Thumb#4 : Nouns or concepts should be vertex labels. Verbs should be edge labels.
	Rule of Thumb#5 : Let the direction of your edges reflect how you would think about the data in your domain.
	Rule of Thumb#6 : If you need to use data to subselect a group, make it a property.
	Pitfall #1: Using the word *has* as an edge label > replace with more specific *has_account* or even better *deposit_to*, following the typical flow of information in a sentence
	Pitfall #2: Using the word *id* as a property > replace with vertex information such as *customer_id*.
	Pitfall #3: Inconsistent use of casing > use *CamelCase* for vertex labels and *snake_case* for edge labels and property keys.
