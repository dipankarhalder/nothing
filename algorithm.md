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