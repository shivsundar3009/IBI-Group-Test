Promise chaining is a technique used in JavaScript to handle asynchronous operations using Promises in a sequential and more readable manner. With promise chaining, multiple asynchronous operations can be executed one after the other, and the result of each operation can be passed on to the next operation in the chain.

To understand promise chaining, let's go through an example:

Suppose we have three asynchronous functions, `asyncFunction1`, `asyncFunction2`, and `asyncFunction3`, which return Promises. We want to call them one after the other and perform some operations with their results.

```

// Three asynchronous functions that return Promises
function asyncFunction1() {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve(10), 1000); // Resolves with value 10 after 1 second
  });
}

function asyncFunction2(value) {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve(value * 2), 1000); // Resolves with value*2 after 1 second
  });
}

function asyncFunction3(value) {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve(value + 20), 1000); // Resolves with value+20 after 1 second
  });
}

```

Now, let's use promise chaining to execute these functions sequentially:

```

// Promise chaining
asyncFunction1()
  .then((result1) => {
    console.log("Result 1:", result1);
    return asyncFunction2(result1);
  })
  .then((result2) => {
    console.log("Result 2:", result2);
    return asyncFunction3(result2);
  })
  .then((result3) => {
    console.log("Result 3:", result3);
    console.log("Final result:", result3);
  })
  .catch((error) => {
    console.error("Error:", error);
  });
  
```

In the above code:

1. We call `asyncFunction1` and handle the result using the first `then` method.
2. Inside the first `then` block, we call `asyncFunction2` with the result of `asyncFunction1`.
3. We handle the result of `asyncFunction2` using the second `then` method, and inside it, we call `asyncFunction3` with the result of `asyncFunction2`.
4. Finally, we handle the result of `asyncFunction3` using the third `then` method, and we have access to the final result.
5. If any of the Promises in the chain gets rejected (e.g., an error occurs), the control jumps to the nearest `catch` block.

With promise chaining, we can perform a series of asynchronous operations in a clear and sequential manner, avoiding nested callback hell. It allows for more structured and maintainable code, making it easier to reason about the flow of asynchronous operations.