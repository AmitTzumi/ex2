In this task we will improve task 1, by generalizing the data structure we have developed so that it can also support directed weighted graphs.
After adjusting the data structure, we will try to implement a number of algorithms on the directed weighted graph, including the ability to save and load the graph from Json file, calculate a short directed trajectory, find the shortest trajectory and check the connectivity in the directed weighted graph.
We were asked to implement the DWGraph_DS class that implements the directed_weighted_graph interface, and we need to do so by implementing the node_data interface as an internal class which describes the properties of Vertex in the graph.

We have created an internal class within DWGraph_DS called NodeData that implements the node_data interface and has the following features: int key, double weight, String info, int tag, GeoLocation gl, HashMap<Integer,edge_data> out_edges,  HashSet<Integer> in_edges.
Also in this NodeData class we have created a number of methods such as:
NodeData(int key) - The constructor.
Collection<edge_data> getNi_out () - This method returns a collection with all the out edges of this node_data.
HashSet<Integer> getNi_in () - This method returns a HashSet with all the in edges of this node_data.
edge_data getNiEdge(int dest) - This method returns a specific edge of this node_data.
void addNi_out(int dest, double w) - This method adds the out_edge to this node_data.
void addNi_in(int src) - This method adds the in_edge to this node_data.
boolean hasNi_out(int dest) - return true iff this<==>key are adjacent, as an edge between them.
edge_data removeEdge_out(int key) - Removes the out edge of this-key.
void removeEdge_in(int key) - Removes the in edge of this-key.
int getKey () - Return the key (id) associated with this node.
geo_location getLocation () - Return the location of this node, if none return null.
void setLocation(geo_location p) - Allows changing this node's location.
double GetWeight () - Returns the weight associated with this node.
void setWeight(double w) - Allows changing this node's weight.
String getInfo () - return the remark (meta data) associated with this node.
void setInfo (String s) - Allows changing the remark (meta data) associated with this node.
int getTag () - Temporal data (aka color: e,g, white, gray, black) which can be used be algorithms 
void setTag (int t) - Allow setting the "tag" value for temporal marking an node - common.
boolean equals(Object o) - equals function - return true if the two object are equals. else, return false.

In addition, we were asked to implement another interface called directed_weighted_graph using the DWGraph_DS class,where we created a number of attributes which are: HashMap <Integer, node_data> nodes, int numofEdges, int ModeCount.
Also in this WGraph_DS class we have created a number of methods such as:
DWGraph_DS () - The constructor.
node_data getNode (int key) - return the node_data by the key.
edge_data getEdge(int src, int dest) - returns the data of the edge (src,dest), null if none.
void addNode(node_data n) - adds a new node to the graph with the given node_data.
boolean hasEdge (int src, int dest) - return true iff (if and only if) there is an edge between src and dest.
void connect(int src, int dest, double w) - Connects an edge with weight w between node src to node dest.
Collection<node_data> getV() - This method returns a pointer (shallow copy) for the collection representing all the nodes in the graph.
Collection<edge_data> getE(int node_id) - This method returns a pointer (shallow copy) for the collection representing all the edges getting out of  the given node (all the edges starting (source) at the given node).
node_data removeNode(int key) - Deletes the node (with the given ID) from the graph - and removes all edges which starts or ends at this node.
edge_data removeEdge(int src, int dest) - Deletes the edge from the graph.
int nodeSize () - return the number of vertices (nodes) in the graph.
int edgeSize () - Returns the number of edges (assume directional graph).
int getMC () - return the Mode Count - for testing changes in the graph.
boolean equals(Object o) - equals function - return true if the two object are equals. else, return false.

Furthermore, we were asked to implement another interface called dw_graph_algorithms using the DWGraph_Algo class,where we created several attributes which are: directed_weighted_graph dwg_alg, HashMap<Integer, double> d1, HashMap<Integer, node_data> p1.
Also in this WGraph_Algo class we have created a number of methods like: 
DWGraph_Algo () - Default constructor.
DWGraph_Algo (directed_weighted_graph g) - The constructor.
void init (directed_weighted_graph g) - Init the graph on which this set of algorithms operates on.
directed_weighted_graph getGraph () - Return the underlying graph of which this class works.
directed_weighted_graph copy () - Compute a deep copy of this directed weighted graph.
void SpecialDFS(int i, int low_link[],int ids[], boolean OnStack[], Stack<Integer> st, int sccCount,int id) - Compute the number of binding elements of the graph.
boolean isConnected () - Returns true if and only if (iff) there is a valid path from each node to each other node.
void Dijkstra(node_data s) - Dijkstra's algorithm is an algorithm for finding the shortest paths between nodes in a graph.
double shortestPathDist (int src, int dest) - returns the length of the shortest path between src to dest.
List <node_data> shortestPath (int src, int dest) - returns the the shortest path between src to dest - as an ordered List of nodes.
boolean save(String file) - saves this weighted (directed) graph to the given file name - in JSON format.
boolean load(String file) - this method load a graph to this graph algorithm. if the file was successfully loaded - the underlying graph of this class will be changed (to the loaded one), in case the graph was not loaded the original graph should remain "as is".
Also, I created Node class thats implements Comparator to fill the QriorityQueue by distance order.