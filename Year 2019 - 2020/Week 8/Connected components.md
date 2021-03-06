
Implement the method numberOfConnectedComponents(g) which returns the number of connected components in an undirected graph g.

The following two interfaces are provided, which have full implementations in the hidden library code.

interface Vertex {
  int getId();
}

interface Graph {
  // Gets neighbours of v in this Graph
  public List<Vertex> getNeighbours(Vertex v);
  // Gets all vertices of this Graph
  public Collection<Vertex> getAllVertices();
}

The hidden library code also has a full implementation of the iterator from the first assignment. This iterator can be instantiated using new GraphIterator(Graph g, Vertex v). Furthermore, note that the iterator implements the Iterator<Vertex> interface, whose description can be found in the Java API documentation.

IMPORTANT: You are required to use the GraphIterator in your solution. In an exam setting, your code will be checked and if it is seen that you do not use it, your grade will be overridden to 1.

Again, you cannot label nodes or edges. Instead, you need to maintain the unexplored nodes in a collection unexplored, which can be initialized with g.getAllVertices(). To remove an explored node v from unexplored, you call unexplored.remove(v). To get the next unexplored node, you call unexplored.iterator().next().

```java
class Solution {
  public static int numberOfConnectedComponents(Graph g) {
    Collection<Vertex> unexplored = g.getAllVertices();

    for(int i = 0 ; ;i++) {
      Iterator<Vertex> explorer = unexplored.iterator();
      if(!explorer.hasNext()) return i;
       Iterator<Vertex> it = new GraphIterator(g, explorer.next());
  
       while(it.hasNext()) {
         unexplored.remove(it.next());
       }
       
     
    }
  }
}
```

