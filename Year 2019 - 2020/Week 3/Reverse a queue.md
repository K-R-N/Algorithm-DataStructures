### Reverse a queue

Implement the method reverse recursively for the Queue ADT, without using any additional data structure.

The code shows the skeleton for the method reverse. Below that (after the point, DO NOT MODIFY), you see the interface for the Queue ADT. All described methods of this ADT have full implementations in the library code, which is hidden.

```java
import java.util.*;

abstract class MyQueue<T> implements Queue<T> {
  /**
   * Reverses the queue itself. NB: This method should be recursive.
   */
  public void reverse() {
    if(isEmpty()) return;
    T temp = this.dequeue();
    reverse();
    this.enqueue(temp);
  }
}

/**
 * Interface for a Queue.
 * <p>
 * DO NOT MODIFY
 *
 * @param <T>
 *     Type of elements the queue can hold
 */
interface Queue<T> {
  /**
   * @return true iff it contains no elements.
   */
  public boolean isEmpty();

  /**
   * @return the number of elements in the queue.
   */
  public int size();

  /**
   * Add an element to the end of the queue
   *
   * @param e
   *     element to add.
   */
  public void enqueue(T e);

  /**
   * Removes the first element from the queue.
   *
   * @return the first element.
   * @throws NoSuchElementException
   *     iff the queue is empty
   */
  public T dequeue() throws NoSuchElementException;

  /**
   * @return the first element (does not remove it).
   * @throws NoSuchElementException
   *     iff the queue is empty
   */
  public T front() throws NoSuchElementException;
}
```
