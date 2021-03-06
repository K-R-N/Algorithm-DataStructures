Implement a lazy iterator for a graph, which yields the nodes of an undirected graph in depth-first order. The iterator should return vertices at most once. The iterator does not necessarily iterate over all vertices in the graph, but only vertices that are connected to the starting vertex.

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

With this implementation, you cannot label nodes or edges. Instead, you need to maintain the colored nodes in a set colored. This set can be instantiated with a TreeSet, which stores the elements of a set in a height-balanced search tree. To add a node v to the set, you call colored.add(v). To check if a vertex is already contained in the set, you call colored.contains(v).

If there is a choice between multiple nodes, always pick the one with the lowest id.

```java
import java.util.*;

/**
 * Implements a Depth first traversal of the Graph, starting at contructor vertex v. It
 * should return nodes at most once. If there is a choice between multiple next nodes,
 * always pick the lowest id node.
 */
class GraphIterator implements Iterator<Vertex> {
  private Graph g;
 // private Vertex v; //still dunno what they wanted me to do with this
  private Stack<Vertex> stack;
  private Set<Vertex> colored;
  private int graphSize;

  public GraphIterator(Graph g, Vertex v) {
    stack = new Stack<Vertex>();
    colored = new TreeSet<Vertex>();
    stack.push(v);
    this.g = g;
    graphSize = g.getAllVertices().size();
  }

  @Override
  public boolean hasNext() {
    return (!stack.isEmpty() && (colored.size() != graphSize));
  }

  @Override
  public Vertex next() {
    Vertex result = stack.pop();
    ArrayList<Vertex> n = (ArrayList<Vertex>) g.getNeighbours(result);
    colored.add(result);
      for (int i = n.size() - 1; i >= 0; i--) {
      if (!colored.contains(n.get(i))) stack.push(n.get(i));
    }
    return result;
    
  }
}
```
