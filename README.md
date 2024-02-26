# Algorithms using JavaScript

### List of searching algorithms

1. Linear Search
```javascript
  function linearSearch(array, target) {
    for (let i = 0; i < array.length; i++) {
      if (array[i] === target) {
        return i; // Return the index if the target is found
      }
    }
    return -1; // Return -1 if the target is not found in the array
  }
  
  // Example usage:
  const myArray = [10, 20, 30, 40, 50];
  const targetValue = 30;
  const index = linearSearch(myArray, targetValue);
  if (index !== -1) {
    console.log(`Target ${targetValue} found at index ${index}.`);
  } else {
    console.log(`Target ${targetValue} not found in the array.`);
  }
```

2. Binary Search
```javascript
  function binarySearch(arr, target) {
    let left = 0;
    let right = arr.length - 1;
    while (left <= right) {
      let mid = Math.floor((left + right) / 2);
      if (arr[mid] === target) {
          return mid; // Target found, return its index
      } else if (arr[mid] < target) {
          left = mid + 1; // Continue searching in the right half
      } else {
          right = mid - 1; // Continue searching in the left half
      }
    }
    return -1; // Target not found
  }
  
  // Example usage:
  const myArray = [1, 3, 5, 7, 9, 11, 13, 15, 17];
  const targetValue = 11;
  const index = binarySearch(myArray, targetValue);
  if (index !== -1) {
    console.log(`Target ${targetValue} found at index ${index}.`);
  } else {
    console.log(`Target ${targetValue} not found in the array.`);
  }
```

3. Depth-First Search (DFS)
```javascript
  class Graph {
    constructor() {
      this.adjacencyList = {};
    }
    addVertex(vertex) {
      if (!this.adjacencyList[vertex]) {
        this.adjacencyList[vertex] = [];
      }
    }
    addEdge(vertex1, vertex2) {
      this.adjacencyList[vertex1].push(vertex2);
      this.adjacencyList[vertex2].push(vertex1); // for undirected graph
    }
    dfsRecursive(start) {
      const visited = {};
      const result = [];
      const dfsHelper = (vertex) => {
        if (!vertex) return null;
        visited[vertex] = true;
        result.push(vertex);
        this.adjacencyList[vertex].forEach((neighbor) => {
          if (!visited[neighbor]) {
            return dfsHelper(neighbor);
          }
        });
      };
      dfsHelper(start);
      return result;
    }
    dfsIterative(start) {
      const stack = [start];
      const visited = {};
      const result = [];
      visited[start] = true;
      while (stack.length) {
        const vertex = stack.pop();
        result.push(vertex);
        this.adjacencyList[vertex].forEach((neighbor) => {
          if (!visited[neighbor]) {
            visited[neighbor] = true;
            stack.push(neighbor);
          }
        });
      }
      return result;
    }
  }
  
  // Example usage:
  const graph = new Graph();
  graph.addVertex('A');
  graph.addVertex('B');
  graph.addVertex('C');
  graph.addVertex('D');
  graph.addEdge('A', 'B');
  graph.addEdge('A', 'C');
  graph.addEdge('B', 'D');
  graph.addEdge('C', 'D');
  console.log(graph.dfsRecursive('A')); // Output: ['A', 'B', 'D', 'C']
  console.log(graph.dfsIterative('A')); // Output: ['A', 'C', 'D', 'B']
```

4. Breadth-First Search (BFS)
```javascript
  class Graph {
    constructor() {
      this.adjacencyList = {};
    }
    addVertex(vertex) {
      if (!this.adjacencyList[vertex]) {
        this.adjacencyList[vertex] = [];
      }
    }
    addEdge(vertex1, vertex2) {
      this.adjacencyList[vertex1].push(vertex2);
      this.adjacencyList[vertex2].push(vertex1); // for undirected graph
    }
    bfs(start) {
      const queue = [start];
      const visited = {};
      const result = [];
      visited[start] = true;
      while (queue.length) {
        const vertex = queue.shift(); // Dequeue
        result.push(vertex);
        this.adjacencyList[vertex].forEach((neighbor) => {
          if (!visited[neighbor]) {
            visited[neighbor] = true;
            queue.push(neighbor); // Enqueue
          }
        });
      }
      return result;
    }
  }
  
  // Example usage:
  const graph = new Graph();
  graph.addVertex('A');
  graph.addVertex('B');
  graph.addVertex('C');
  graph.addVertex('D');
  graph.addEdge('A', 'B');
  graph.addEdge('A', 'C');
  graph.addEdge('B', 'D');
  graph.addEdge('C', 'D');
  console.log(graph.bfs('A')); // Output: ['A', 'B', 'C', 'D']
```
