### Cloning Arrays

Implement the Java method clone, which copies all the double entries in a given two-dimensional array a to a newly created two-dimensional array of the same type and size. 
This method takes the array a as input and returns the new array with the copied values.

```java
class Solution {
  static double[][] clone(double[][] a) {
    double[][] b = new double[a.length][];
    for(int i =0; i < a.length; i++) {
      b[i] = new double[a[i].length];
      for(int j=0; j < b[i].length; j++) {
        b[i][j] = a[i][j];
      }
    }
    return b;
  }
}
```
