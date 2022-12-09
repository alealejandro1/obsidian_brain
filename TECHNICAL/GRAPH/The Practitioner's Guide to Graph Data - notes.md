asset_type:: Book
type_book:: Non-Fiction
title::The Practitioner's Guide to Graph Data
read_when::2022
good_about_book:: Graph introduction, describe business cases suitable for graphs, comparisons with RDBMS
bad_about_book:: Focused on Gremlin and Cassandra
my_score::3.5
keywords:: Graph, Graph Database, Gremlin, Complex Problems
reminded_me_of::

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
* ***Degree***: Number of edges that touch a vertex. Can be further split into In-Degree (in-going edges) and Out-Degree (outgoing edges) -> **Supernodes** have disproportionately high degree.
* ***Schema***: Described in terms of labels, it captures how vertices and edges are related. When discussing schema use "Vertex Label" and "Edge Label". Vertices and Edges are data.
* ***Property***: Describes a feature of a vertex or edge, such as name or age.   
* ***Cardinality*** : Number of elements in a set or collection
* ***Set*** : Abstract data type that stores unique values (like set ( ) in python)
* ***Collection***: Abstract data type that stores nonunique values (like a python list [] )


## Graph Use Case: Customer 360
Goal: There is a central object (a customer) and then there are many pieces of data coming from different business domains that say something about the customer. Payment details, demographic, past purchases, address, etc..

Relational Implementation
Achieving C360 using data warehouses has been done. The challenge comes when querying relationally as multiple JOINS are involved. Data is hard to follow, making query writing hard.

Graph implementation
The graph query to only get certain pieces of information is harder than getting the 360 view.

Data modelling is easier in graph, but at this point relational is very mature. Not a clear win for graph. Querying is significantly easier with graph. If the data is not complex enough, graph might not be better than relational. Use relational if just want to get a view of 360.

## Exploring Neighborhoods in Development

	Rule of Thumb#1 : If you want to start your traversal on some piece of data, make that data a vertex
	Rule of Thumb#2 : If you need the data to connect concepts, make that data an edge
	Rule of Thumb#3 : Vertex-Edge-Vertex should read like a sentence or phrase from your queries.
	Rule of Thumb#4 : Nouns or concepts should be vertex labels. Verbs should be edge labels.
	Rule of Thumb#5 : Let the direction of your edges reflect how you would think about the data in your domain.
	Rule of Thumb#6 : If you need to use data to subselect a group, make it a property.
	Pitfall #1: Using the word *has* as an edge label > replace with more specific *has_account* or even better *deposit_to*, following the typical flow of information in a sentence
	Pitfall #2: Using the word *id* as a property > replace with vertex information such as *customer_id*.
	Pitfall #3: Inconsistent use of casing > use *CamelCase* for vertex labels and *snake_case* for edge labels and property keys.

## Exploring Neighborhoods in Production

	Rule of Thumb #7 : Properties such as timestamps can be duplicated onto edges and vertices. This is to reduce the number of elements to process in a query (by creating duplicated information). For example on bank transfers you can have the date of transfer on the edge connected to an account vertex and on the vertex for the specific transaction.
	Denormalization  : Improving read performance of a database at the expense of losing write performance, by adding redundant copies of data grouped differently.
	Rule of Thumb #8 : Let the direction you want to walk/traverse your edge labels determine the key indeces you need on edge labels in your graph schema. -> know what queries you want to do before you create the graph!
	Rule of Thumb #10: Keep only the edges and indexes you need for your production queries.

## Using Trees in Development : Hierarchical Data
* Hierarchical Data represents concepts that naturally organize into a nested structure of dependencies.

Examples of Hierarchical Data:
* **Bill of Materials**: Boeing 737 contains [Right Wing, Left Wing], Right Wing contains : [Turbine Engine 1, ...]  .. contains [screw 435, screw 436,..]
	* Potential query: How many screws in a Boeing 737?
* **Git version control Data**: A branch contains a number of commits. Each commit contains a Tree, each Tree contains File. The newer commit always is connected to the previous commit.

### Differing from neighborhoods, trees have their own concepts:
* ***Tree*** : A connected graph with no ***cycles***. Every vertex has only one edge pointing to it. >> this doesn't mean that only one edge can come out of a vertex. Think of family tree or corporate tree.
* ***Parent Vertex***: One step higher in the hierarchy. 
* ***Child Vertex***: One step below a parent in the hierarchy.
* ***Root***: The topmost parent vertex. The beggining of the dependency chain within a hierarchy.
* ***Leaf***: The last child vertex within a hierarchy. Leaf has degree of one.
* ***Depth***: In a hierarchy, depth is the distance of any vertex to its root.
* ***Walk***: Sequence of visited vertices and edges, elements of which can be repeated.
*  ***Path***: Sequence of visited vertices and edges, elements of which cannot be repeated.
* ***Cycle***: A path a where the ending and starting vertex are the same. Multiple edges.
* ***Loop***: Is an edge that starts and ends at the same vertex. One edge.
* ***Branching Factor*** : Expected or average number of edges for any vertex.

### Power Company: Hierarchical example

Sensors monitor homes and communicate with other sensors > Towers monitor sensors > Network of Towers controls all.

Note that is important to have communication redundancy in case a sensor or tower goes down. This means that the hierarchical structures are dyanmic and changing as towers and sensors go down/up. Note that the number of vertices is fixed, but the number of edges changes dynamically.

![[Pasted image 20221207104200.png]]
Because sensors connect to sensors, there can be cycles in this hierarchy. 

The book goes on to explain the intricacies of looking for paths using Gremlin.

### Considering time in the sensor data

Now we can consider that communication takes place in timesteps. So at timestep =0 something happens, at timestep =1 something else happens. The image below showcases this:
![[Pasted image 20221207111403.png]]

Timesteps mean that not all walks are valid walks, because they need to be consistent with the communication timing along the way. Think of speed and distance. You miss the train if you get there too early or too late.

	Consideration #1: Add time to edges when monitoring time series.
	Consideration #2: Time goes up one way and down the other way. Else path is invalid. This should be considered when querying.

Business challenge to address regarding timeseries and power towers:
* If Tower X should fail, what sensors, if any, would we lose connection to?
This can be unpacked as:
	* Query: All sensors connected to tower X
	* Query: For all those sensors, which towers they connected with?
This can be reframed as:
	* Get a list of sensors that connected with Tower X in any timewindow
	* For each sensor, query the network to see if they used a different tower in that timewindow

Ideal output is:
{
"sensor123":[Tower X, Tower Y, Tower Z],
"sensor124":[Tower X, Tower W]
"sensor 125":[Tower X]
}
Therefore, sensor 125 is at risk if Tower X fails.

## Finding Paths

>Distance between concepts quantifies trust.

Route optimization is one of the most popular usages of graphs. 

Challenge: Naive pathfinding can quickly become very expensive computationally. If you don't specify the length, it can become an exponentially longer query.
Path Concepts:
* ***path***: Sequence of consecutive edges in a graph
* ***Length***: Number of edges in the path. Considers no weights.
* ***Shortest Path***: The path that connects two vertices (A and B) and has the shortest length of all possible paths.
* ***Distance***: The number of edges in a shortest path > the minimum length. Considers no weights.

### Optimization Strategy

Path Problems:
* **Single Source Shortest Path** : Discover the smallest distance between vertex A to all other vertices in the graph
* **All-pairs shortest path**: Discover the smallest distance walk between any two vertices in the graph.

Depth-First Search DFS:
Algorithm for traversing graph data structures. Explores a path as deep as possible along each branch before backtracking.
DFS uses Last-In First-Out (LIFO= stack)

Breadth-First Search BFS:
Explores all of the neighbor vertices at the present depth prior to moving to the vertices at the next depth level.
BFS uses First-In First-Out (FIFO= queue)

DFS and BFS are considered when estimating how much data will be visited in a traversal. More data, more computationally expensive.

> **Minimum Cost Path or Shortest Weighted Path** : Add weight or cost to steps along a path
> Definition: The shortest path between two vertices such that the sum of the edge's weight is minimum. --> we are not counting edges, but aggregating their weight as we traverse.

Shortest path considering edge weights -> Bounded minimum optimization problem

Typical Graph path algorithms:
* A* (A star)
* Floyd-Warshall
* Dijkstra

**Lowest Cost optimization**: It excludes an edge if the edge's destination is reachable via a lower cost path
**Supernode Avoidance:** It excludes a vertex if its degree would increase the search space complexity over a threshold.
**Global Heuristic:**  Excludes an edge if the edge's weight causes the path's total weight to exceed a treshold.

### Finding highest trust : Product of edges weights
Edge ~ 10 : Highest trust
Edge ~ -10 : No trust
Additionally, because original edge_weight went [-10 , 10], it needs to be normalized to [0,1]. However there is a challenge with adding up edges so that the longer paths will get a higher total value. This will encourage to reward longer paths, when what we want is shorter paths.

Solution: Frame the scale as a shortest path problem -> We want the highest trust path.
* Use logarithms, so multiplication becomes addition --> important in probabilities
* Multiply end result by -1 so that the maximum becomes the minimum

Interpretation: Chance(a) and Chance(b) = Chance(a) * Chance(b)
If you half trust A, and A half trust's B --> you 1/4 trust B.

Log(A)+Log(B) = Log (A * B) ==>> this means we can just add up the log values, and that is like computing the productory of the trust.

| Trust | Normalized | Log(Normalized) | Adjusted Final Value |
| ----- | ---------- | --------------- | -------------------- |
| -10   | 0          | -infinity       | 100                  |
| -1    | 0.45       | -0.39           | 0.39                 |
| 1     | 0.5        | -0.3            | 0.3                  |
| 10    | 1          | 0               | 0                   |

So adding nodes of low trust, is like adding a higher weight --> so we should aim for the "lowest weight" path using the adjusted final values.

# Recommendations

People you might know in LinkedIn: The most connected friends of friends. --> Somewhat shallow graph.

Same for recommending products in e-commerce:
![[Pasted image 20221209140947.png]]
Products bought by someone else who bought the same product you bought, become "Products you might want".

### Recommender System: Collaborative Filtering
	A type of recommendation system that predicts new content (filtering) by matching the interests of the individual with the preference of many users (collaborative).

* Recommender Systems
	* Content-Based ~ based on user preference
	* Social Data Mining ~ historical trends from community (individual user not involved)
	* Hybrid Models
	* Collaborative Filtering ~ combines invidual + community prefrences
		* User-based ~ find similar users
		* Item-based ~ find similar items
		* Hybrid Models

### Ranking Recommendations: Path Counting, Net Promoter Score, Normalized NPS
In the example of movie recommendations by users, you can rank your recommendations by the following approaches:
**Path Counting**: Count how many edges with 5-star rating were done by users who also voted 5-star the movie you voted 5-star. Only involved 5 star ratings.
**Net Promoter Score**: It considers all edges (not only 5 star), substracting (score <=4) and adding (score>4). 
**Normalized Net Promoter Score**: High degree movies are popular, so if you are trying to recommend less popular options, consider normalizing NPS by degree of movie.

Also, instead of keeping the numerical value of the rating, you can bucketize the numerical value using something like: 
* rating>= 4.5 --> LIKED
* 4.5 > rating >= 3 --> NEUTRAL
* rating > 3 --> DISLIKED

### Entity resolution: Inferring who's who -> Not really graph related
Although this process can be done in graphs, this process can entirely be done in RDBMS.

From a mathematical definition of entity resolution, given a,b items of D: 
	if $f(a,b) \geq T \rightarrow a=b$

![[Pasted image 20221209152035.png]]

When resolving entity resolution for 2 datasets of movies, one of the ways that vertices considered about movies was actors and directors related to the movie. One addition that was made in the book, was to create the edge "COLLABORATED IN YEAR" between actors.

Note: When merging data sources with their respective Ids, take note of the distribution of strong identifiers in each system. Example is comparing MovieLens and Kaggle movie datasets.


# Strategies in production for Reccomendations: Shortcut Edges

Because in reality, no one will wait for multiple-second or even minutes of searches when users want a recommendation in a website, there are few approaches to consider:

* Shortcut edges : Contains a precomputed result of a multi-hop query from vertex $a$ to vertex $n$ to be stored directly $a \rightarrow n$ 
* Precomputation: Ahead of time, run expensive multi-hop queries and create shortcut edges for later.
* Pruning Techniques: Can prune to avoid expensive computation, but there is a cost. Can decide based on score, number of results or domain knowledge expectations.

The naive Net Promoter Score calculation for the image below will not scale because of the branching factor and supernodes.
![[Pasted image 20221209162921.png]]

In the recommendations, the big problems for scale are the following supernodes:
* Super-users
* Super-popular content
How to address --> Shortcut Edges.

Unpacking pruning techniques:
* By score thresholds : If there is a hard numerical limit you can escape the query
* By total number of recommendations: Defining a hard limit (N=100) of total number of edges you are going to use in production. Means you store up the 100 top recomendations.
* By domain knowledge filters: If your user likes drama, include dramas.

Production decision: When to update 