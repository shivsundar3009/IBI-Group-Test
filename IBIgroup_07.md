We can use the `Array.reduce()` method to reverse the given array. The `reduce()` method iterates through the array and accumulates the elements in reverse order. Here's how we can do it:

```

const arr = [1, 2, 3, 4, 5];

const reversedArr = arr.reduce((acc, current) => {
  // Add the current element to the beginning of the accumulator array
  acc.unshift(current);
  return acc;
}, []);

console.log(reversedArr); // Output: [5, 4, 3, 2, 1]

```

In this example:

1. The `reduce()` method takes a callback function as its first argument and an initial value (empty array `[]`) as its second argument.
2. The callback function is called for each element in the array.
3. Inside the callback function, the `unshift()` method is used to add the current element to the beginning of the accumulator array (`acc`).
4. The accumulator (`acc`) is returned in each iteration to be used in the next iteration.
5. Once all elements have been processed, the final result, which is the reversed array, is returned.

