
View All Nodes
START n=node(*) RETURN n
Delete a Node
START n = node(4) //Fetch a Node
DELETE n // Call delete
Remove a node and connected relationships
START n = node(3) MATCH n-[r]-() DELETE n, r // Call Delete
Remove a property
START n = node(2)
DELETE n.title
RETURN n
Fetch node by id
START n=node(1)
RETURN n
Fetch multiple nodes
START n=node(1, 2, 3)
RETURN n
Fetch Node by index lookup
START n=node:nodes(name = "A")
RETURN n
View All Relationships
START r=relationship(*) RETURN r;
Fetch Relationship by id
START r=relationship(0)
RETURN
Relationship by index lookup
START r=relationship:rels(name = "Andrés")
RETURN r
Fetch Node by index query
START n=node:nodes("name:A")
RETURN n
Fetch Multiple starting points
START a=node(1), b=node(2)
RETURN a,b
Delete all relations
start r=relationship(*) delete r;
Create a node
Create n
Create a node and set properties
CREATE n = {name : 'Andres', title : 'Developer'}
Create a relationship
START a=node(1), b=node(2) CREATE a-[r:RELTYPE]->b RETURN r
Create a relationship and set properties
START a=node(1), b=node(2)
CREATE a-[r:RELTYPE {name : a.name + '<->' + b.name }]->b
RETURN r
Create a full path
CREATE p = (andres {name:'Andres'})-[:WORKS_AT]->neo<-[:WORKS_AT]-(michael {name:'Michael'})
RETURN p
Create single node from map
create ({props})
This query can be used in the following fashion:

Map<String, Object> props = new HashMap<String, Object>();
props.put( "name", "Andres" );
props.put( "position", "Developer" );

Map<String, Object> params = new HashMap<String, Object>();
params.put( "props", props );
engine.execute( "create ({props})", params );
Create multiple nodes from maps
create (n {props}) return n

Eg.
Map<String, Object> n1 = new HashMap<String, Object>();
n1.put( "name", "Andres" );
n1.put( "position", "Developer" );

Map<String, Object> n2 = new HashMap<String, Object>();
n2.put( "name", "Michael" );
n2.put( "position", "Developer" );

Map<String, Object> params = new HashMap<String, Object>();
List<Map<String, Object>> maps = Arrays.asList( n1, n2 );
params.put( "props", maps );
engine.execute( "create (n {props}) return n", params );
