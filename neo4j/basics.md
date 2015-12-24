Commands
=======

|  Command | Description  |
|---|---|---|---|---|
| View All Nodes  |  START n=node(*) RETURN n |
| Delete a Node  |  START n = node(4) //Fetch a Node <br>DELETE n // Call delete |
| Remove a node and connected relationships  |  START n = node(3) MATCH n-[r]-() DELETE n, r // Call Delete |
| Remove a property  |  START n = node(2)<br> DELETE n.title<br> RETURN n |
| Fetch node by id  |  START n=node(1)<br>RETURN n |
| Fetch multiple nodes  |  START n=node(1, 2, 3)<br>RETURN n |
| Fetch Node by index lookup  |  START n=node:nodes(name = "A")<br>RETURN n |
| View All Relationships  |  START r=relationship(*) RETURN r;<br>Fetch Relationship by id<br>START r=relationship(0)<br>RETURN |
| Relationship by index lookup  |START r=relationship:rels(name = "Andrés")<br>RETURN r |
| Fetch Node by index query  |  START n=node:nodes("name:A")<br>RETURN n |
| Fetch Multiple starting points  |  START a=node(1), b=node(2)<br>RETURN a,b |
| Delete all relations  |  start r=relationship(*) delete r; |
| Create a node  |  Create n |
| Create a node and set properties  |  CREATE n = {name : 'Andres', title : 'Developer'} |
| Create a relationship  |  START a=node(1), b=node(2) CREATE a-[r:RELTYPE]->b RETURN r |
| Create a relationship and set properties  |  START a=node(1), b=node(2)<br>CREATE a-[r:RELTYPE {name : a.name + '<->' + b.name }]->b<br>RETURN r |
| Create a full path  |  CREATE p = (andres {name:'Andres'})-[:WORKS_AT]->neo<-[:WORKS_AT]-(michael {name:'Michael'})<br>RETURN p |
| Create single node from map  | create ({props}) <br> This query can be used in the following fashion: <br> Map<String, Object> props = new HashMap<String, Object>(); <br> props.put( "name", "Andres" ); <br> props.put( "position", "Developer" ); <br><br> Map<String, Object> params = new HashMap<String, Object>(); <br> params.put( "props", props ); <br> engine.execute( "create ({props})", params ); |
| Create multiple nodes from maps  |  create (n {props}) return n <br> Eg.<br>Map<String, Object> n1 = new HashMap<String, Object>();<br>n1.put( "name", "Andres" );<br>n1.put( "position", "Developer" );<br><br>Map<String, Object> n2 = new HashMap<String, Object>();<br>n2.put( "name", "Michael" );<br>n2.put( "position", "Developer" );<br><br>Map<String, Object> params = new HashMap<String, Object>();<br>List<Map<String, Object>> maps = Arrays.asList( n1, n2 );<br>params.put( "props", maps );<br>engine.execute( "create (n {props}) return n", params ); |
