# Arrays in JavaScript:

## Create an Array

This example shows three ways to create new array

- using array literal notation,
- using the Array() constructor,
- using split() to build the array from a string.

```javascript
const fruits = ["Apple", "Banana"];
const fruits2 = new Array("Apple", "Banana");
const fruits3 = "Apple, Banana".split(", ");
```

## Create a String from an Array

This example uses the join method to create a stirng out of an array , this takes a seqeunce of characters and appends that character between the elements of the array.

```javascript
const fruits = ["Apple", "Banana"];
const fruitsString = fruits.join(", ");
console.log(fruitsString); // "Apple, Banana"
```

## Access an Array Item by Index

```javascript
const fruits = ["Apple", "Banana"];
console.log(fruits[0]); // "Apple"
console.log(fruits[1]); // "Banana"
```

## Find the Index of an Item in an Array

```javascript
const fruits = ["Apple", "Banana"];
console.log(fruits.indexOf("Banana")); // 1
```

## Check if an Array Contains a Certain Item

```javascript
const fruits = ["Apple", "Banana"];
console.log(fruits.includes("Banana")); // true
console.log(fruits.includes("Cherry")); // false
```

## Using push() and pop() operations.

This follows the `LIFO` principal adding and removing elements from the end of the array similar to a stack.

### Append an Item to an Array: push()

**push()** :This can take one or multiple values ,and returns the new length of the array.

```javascript
const fruits = ["Apple", "Banana"];
const newLength = fruits.push("Orange");
console.log(fruits); // ["Apple", "Banana", "Orange"]
console.log(newLength); // 3

const finalLength = fruits.push("Grapes", "Pineapple");
console.log(fruits); // ["Apple", "Banana", "Orange" , "Grapes" , "Pineapple"]
console.log(finalLength); // 5
```

### Remove the Last Item from an Array : pop()

**pop():** Removes the last element from an array and returns it. If the array is empty, undefined is returned and the array is not modified.

```javascript
const fruits = ["Apple", "Banana", "Orange"];
const removedItem = fruits.pop();
console.log(fruits); // ["Apple", "Banana"]
console.log(removedItem); // "Orange"
```

```javascript
const fruits = ["Apple", "Banana", "Orange"];
const removedItem = fruits.pop();
console.log(fruits); // ["Apple", "Banana"]
console.log(removedItem); // "Orange"
```

## Using unshift() and shift() operations.

`shift()` and `unshift()` are two array methods in JavaScript used to add and remove elements at the beginning of an array.

1. **`shift()`**:

   - The `shift()` method removes the first element from an array and returns that element.
   - This method modifies the original array in place, reducing its length by one.
   - If the array is empty, it returns `undefined`.

   **Syntax:**

   ```javascript
   const shiftedElement = array.shift();
   ```

   **Example:**

   ```javascript
   const fruits = ["Apple", "Banana", "Orange"];

   const shiftedElement = fruits.shift();
   console.log(fruits); // Output: ["Banana", "Orange"]
   console.log(shiftedElement); // Output: "Apple"
   ```

2. **`unshift()`**:

   - The `unshift()` method adds one or more elements to the beginning of an array and returns the new length of the array.
   - This method modifies the original array in place.
   - The elements are added in the order they appear in the argument list.

   **Syntax:**

   ```javascript
   const newLength = array.unshift(item1, item2, ..., itemN);
   ```

   **Example:**

   ```javascript
   const fruits = ["Apple", "Banana", "Orange"];

   const newLength = fruits.unshift("Strawberry", "Cherry");
   console.log(fruits); // Output: ["Strawberry", "Cherry", "Apple", "Banana", "Orange"]
   console.log(newLength); // Output: 5
   ```

**Use Cases:**

- `shift()`: Often used when you want to process the elements of an array one by one from the beginning.
- `unshift()`: Useful when you need to add elements at the beginning of an array, such as when implementing a queue .

## Splice()

The `splice()` method in JavaScript is a powerful array method that allows you to modify an array by adding or removing elements at a specific index position. It can be used to perform various array operations, such as adding new elements, removing elements, or replacing elements, all in a single method call. The method modifies the original array in place and returns an array containing the removed elements (if any).

**Syntax:**

```javascript
array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
```

**Parameters:**

- `start`: The index at which to start changing the array. If negative, it indicates an offset from the end of the array.
- `deleteCount`: The number of elements to remove from the array. If set to 0, no elements are removed.
- `item1, item2, ...`: Elements to add to the array at the `start` position. If you don't want to add any elements, you can omit these parameters.

**Return value:**
An array containing the elements that were removed. If no elements are removed, an empty array is returned.

**Example:**

```javascript
const fruits = ["Apple", "Banana", "Orange", "Mango"];

// Remove two elements starting from index 1 and add "Strawberry" and "Cherry"
const removedItems = fruits.splice(1, 2, "Strawberry", "Cherry");

console.log(fruits); // Output: ["Apple", "Strawberry", "Cherry", "Mango"]
console.log(removedItems); // Output: ["Banana", "Orange"]
```

**Explanation:**
In the example above, we started modifying the `fruits` array from index 1. We removed two elements ("Banana" and "Orange") and added "Strawberry" and "Cherry" in their place. After the `splice()` method is executed, the `fruits` array is modified accordingly, and the elements "Banana" and "Orange" are returned in the `removedItems` array.

**Common Use Cases:**

1. Removing elements from an array at a specific index.
2. Adding new elements at a specific index in an array.
3. Replacing a range of elements in an array with new elements.
4. Splicing an array to remove a slice of elements based on a condition.

## Remove Multiple Items from the End of an Array

```javascript
const fruits = ["Apple", "Banana", "Strawberry", "Mango", "Cherry"];
const start = -3;
const removedItems = fruits.splice(start);
console.log(fruits); // ["Apple", "Banana"]
console.log(removedItems); // ["Strawberry", "Mango", "Cherry"]
```

## Truncate an Array Down to Just Its First N Items

```javascript
const fruits = ["Apple", "Banana", "Strawberry", "Mango", "Cherry"];
const start = 2;
const removedItems = fruits.splice(start);
console.log(fruits); // ["Apple", "Banana"]
console.log(removedItems); // ["Strawberry", "Mango", "Cherry"]
```

## Remove the First Item from an Array

```javascript
const fruits = ["Apple", "Banana"];
const removedItem = fruits.shift();
console.log(fruits); // ["Banana"]
console.log(removedItem); // "Apple"
```

## Remove Multiple Items from the Beginning of an Array

```javascript
const fruits = ["Apple", "Strawberry", "Cherry", "Banana", "Mango"];
const start = 0;
const deleteCount = 3;
const removedItems = fruits.splice(start, deleteCount);
console.log(fruits); // ["Banana", "Mango"]
console.log(removedItems); // ["Apple", "Strawberry", "Cherry"]
```

## Add a New First Item to an Array

```javascript
const fruits = ["Banana", "Mango"];
const newLength = fruits.unshift("Strawberry");
console.log(fruits); // ["Strawberry", "Banana", "Mango"]
console.log(newLength); // 3
```

## Remove a Single Item by Index

```javascript
const fruits = ["Strawberry", "Banana", "Mango"];
const start = fruits.indexOf("Banana");
const deleteCount = 1;
const removedItems = fruits.splice(start, deleteCount);
console.log(fruits); // ["Strawberry", "Mango"]
console.log(removedItems); // ["Banana"]
```

## Remove Multiple Items by Index

```javascript
const fruits = ["Apple", "Banana", "Strawberry", "Mango"];
const start = 1;
const deleteCount = 2;
const removedItems = fruits.splice(start, deleteCount);
console.log(fruits); // ["Apple", "Mango"]
console.log(removedItems); // ["Banana", "Strawberry"]
```

## Replace Multiple Items in an Array

```javascript
const fruits = ["Apple", "Banana", "Strawberry"];
const start = -2;
const deleteCount = 2;
const removedItems = fruits.splice(start, deleteCount, "Mango", "Cherry");
console.log(fruits); // ["Apple", "Mango", "Cherry"]
console.log(removedItems); // ["Banana", "Strawberry"]
```

## Iterate Over an Array

1. **For Loop:**

   - Return Type: N/A (Doesn't return any value)
   - Parameters: It uses a loop variable (`i` in the example) to iterate through the array indices. The loop variable is initialized with an initial value, and the loop continues as long as the condition (`i < fruits.length`) is true. The loop variable is typically used to access array elements using `fruits[i]`.

   **Example:**

   ```javascript
   const fruits = ["Apple", "Banana", "Orange"];
   for (let i = 0; i < fruits.length; i++) {
     console.log(fruits[i]);
   }
   ```

2. **For...of Loop:**

   - Return Type: N/A (Doesn't return any value)
   - Parameters: It uses the loop variable (`fruit` in the example) to directly access each element of the array (`fruits` in the example) in a more concise and readable way. Unlike the traditional `for` loop, it doesn't require explicit index manipulation.

   **Example:**

   ```javascript
   const fruits = ["Apple", "Banana", "Orange"];
   for (const fruit of fruits) {
     console.log(fruit);
   }
   ```

3. **forEach() Method:**

   - Return Type: N/A (Doesn't return any value)
   - Parameters: The `forEach()` method takes a callback function as its only parameter, which is called for each element in the array. The callback function can take up to three arguments: the current element being processed, its index, and the array itself (in the example, we only use the first argument `fruit`).

   **Example:**

   ```javascript
   const fruits = ["Apple", "Banana", "Orange"];
   fruits.forEach((fruit) => {
     console.log(fruit);
   });
   ```

4. **map() Method:**

   - Return Type: A new array containing the results of applying the provided function to each element in the original array.
   - Parameters: The `map()` method takes a callback function as its only parameter, which is called for each element in the array. The callback function can take up to three arguments: the current element being processed, its index, and the array itself. The returned array will have the same length as the original array.

   **Example:**

   ```javascript
   const numbers = [1, 2, 3];
   const squares = numbers.map((num) => num * num);
   console.log(squares); // Output: [1, 4, 9]
   ```

5. **filter() Method:**

   - Return Type: A new array containing all elements of the original array that pass the test implemented by the provided function.
   - Parameters: The `filter()` method takes a callback function as its only parameter, which is called for each element in the array. The callback function can take up to three arguments: the current element being processed, its index, and the array itself. The returned array may have fewer elements than the original array, depending on the condition in the callback function.

   **Example:**

   ```javascript
   const numbers = [1, 2, 3, 4, 5];
   const evenNumbers = numbers.filter((num) => num % 2 === 0);
   console.log(evenNumbers); // Output: [2, 4]
   ```

6. **reduce() Method:**

   - Return Type: The accumulated result after applying the provided function to each element of the array.
   - Parameters: The `reduce()` method takes two parameters: a callback function and an initial value for the accumulator. The callback function is called for each element in the array and takes four arguments: the accumulator, the current element being processed, its index, and the array itself.

   **Example:**

   ```javascript
   const numbers = [1, 2, 3, 4];
   const sum = numbers.reduce(
     (accumulator, currentValue) => accumulator + currentValue,
     0
   );
   console.log(sum); // Output: 10
   ```

7. **every() Method:**

   - Return Type: A Boolean value that indicates whether all elements in the array pass the test implemented by the provided function.
   - Parameters: The `every()` method takes a callback function as its only parameter, which is called for each element in the array. The callback function can take up to three arguments: the current element being processed, its index, and the array itself. It stops iterating and returns `false` as soon as any element fails the test.

   **Example:**

   ```javascript
   const numbers = [2, 4, 6];
   const allEven = numbers.every((num) => num % 2 === 0);
   console.log(allEven); // Output: true
   ```

8. **some() Method:**

   - Return Type: A Boolean value that indicates whether at least one element in the array passes the test implemented by the provided function.
   - Parameters: The `some()` method takes a callback function as its only parameter, which is called for each element in the array. The callback function can take up to three arguments: the current element being processed, its index, and the array itself. It stops iterating and returns `true` as soon as any element passes the test.

   **Example:**

   ```javascript
   const numbers = [2, 3, 5];
   const hasEven = numbers.some((num) => num % 2 === 0);
   console.log(hasEven); // Output: true
   ```

9. **for...in Loop:**

   - Return Type: N/A (Doesn't return any value)
   - Parameters: The `for...in` loop is primarily used for iterating over object properties. However, when used with arrays, it iterates over the indices of the array rather than the array elements. The loop variable (`index` in the example) represents the index of each element in the array.

   **Example:**

   ```javascript
   const fruits = ["Apple", "Banana", "Orange"];
   for (const index in fruits) {
     console.log(fruits[index]);
   }
   ```

## Reversing and Sorting the Array.

1. **Reverse an Array:**
   To reverse the order of elements in an array, you can use the `reverse()` method. This method modifies the original array in place and returns the reversed array.

   **Example:**

   ```javascript
   const fruits = ["Apple", "Banana", "Orange"];
   fruits.reverse();
   console.log(fruits); // Output: ["Orange", "Banana", "Apple"]
   ```

2. **Sort an Array:**
   To sort the elements of an array, you can use the `sort()` method. By default, it converts elements to strings and sorts them based on their Unicode code points. The `sort()` method modifies the original array in place and returns the sorted array.

   **Example:**

   ```javascript
   const fruits = ["Banana", "Orange", "Apple"];
   fruits.sort();
   console.log(fruits); // Output: ["Apple", "Banana", "Orange"]
   ```

   However, it's important to note that the default sorting may not produce the expected order for all elements. For example, numbers are sorted as strings, leading to unexpected results.

   **Example with Numbers:**

   ```javascript
   const numbers = [10, 2, 5, 1];
   numbers.sort();
   console.log(numbers); // Output: [1, 10, 2, 5]
   ```

   To sort numbers correctly, you need to provide a compare function to the `sort()` method.

   **Sorting Numbers Correctly:**

   ```javascript
   const numbers = [10, 2, 5, 1];
   numbers.sort((a, b) => a - b);
   console.log(numbers); // Output: [1, 2, 5, 10]
   ```

   The compare function takes two arguments, conventionally named a and b, which represent two elements being compared during the sorting process. The function should return a negative value if `a` should come before `b` in the sorted array, a positive value if a should come after b, or zero if a and b are considered equal and their relative order should remain unchanged.

In the above eg: (a,b) => a-b : if a is smaller a-b will be -ve , so the position will not change , if a is grater than b , a-b will be positive thus the values will swap.

Additionally, if you want to sort in descending order, you can reverse the comparison logic in the compare function.

**Sorting Numbers in Descending Order:**

```javascript
const numbers = [10, 2, 5, 1];
numbers.sort((a, b) => b - a);
console.log(numbers); // Output: [10, 5, 2, 1]
```

It's important to remember that the `sort()` method sorts elements in place and returns the sorted array, so the original array will be modified. If you want to preserve the original array, make a copy before sorting it.

**Example with a Copied Array:**

```javascript
const fruits = ["Banana", "Orange", "Apple"];
const sortedFruits = fruits.slice().sort();
console.log(sortedFruits); // Output: ["Apple", "Banana", "Orange"]
console.log(fruits); // Output: ["Banana", "Orange", "Apple"]
```

## Merge Multiple Arrays Together

**Using the concat operator**

```javascript
const fruits = ["Apple", "Banana", "Strawberry"];
const moreFruits = ["Mango", "Cherry"];
const combinedFruits = fruits.concat(moreFruits);
console.log(combinedFruits); // ["Apple", "Banana", "Strawberry", "Mango", "Cherry"]
```

**Using the spread operator**

```javascript
const fruits = ["Apple", "Banana", "Strawberry"];
const moreFruits = ["Mango", "Cherry"];
const combinedFruits = [...fruits, ...morefruits];
console.log(combinedFruits); // ["Apple", "Banana", "Strawberry", "Mango", "Cherry"]
```

## Copy an Array

In JavaScript, there are multiple ways to copy an array. Each method has its advantages and use cases. Here are some common ways to copy an array:

1. **Using the Spread Operator (...):**
   The spread operator `...` can be used to create a shallow copy of an array. It spreads the elements of the original array into a new array, effectively copying them.

   ```javascript
   const originalArray = [1, 2, 3];
   const copiedArray = [...originalArray];
   ```

   Note that this creates a shallow copy, meaning that if the original array contains objects or nested arrays, only references to those objects or arrays will be copied. Changes made to the objects or arrays inside the copied array will also affect the original array and vice versa.

2. **Using the slice() Method:**
   The `slice()` method can also be used to create a shallow copy of an array. It returns a new array containing a portion of the original array. If called without any arguments, it copies the entire array.

   ```javascript
   const originalArray = [1, 2, 3];
   const copiedArray = originalArray.slice();
   ```

   Like the spread operator, `slice()` creates a shallow copy of the array.

3. **Using the Array.from() Method:**
   The `Array.from()` method can be used to create a shallow copy of an array from an iterable object or an array-like object (e.g., NodeList). When used with an array, it also creates a copy.

   ```javascript
   const originalArray = [1, 2, 3];
   const copiedArray = Array.from(originalArray);
   ```

   `Array.from()` can also be useful when you want to create an array from a non-array iterable.

4. **Using JSON.stringify() and JSON.parse():**
   For creating a deep copy of an array (where nested objects and arrays are also copied), you can use the `JSON.stringify()` and `JSON.parse()` methods. This method works well for arrays containing primitive data types (numbers, strings, booleans) and simple objects, but it won't work with functions, undefined, and other special objects.

   ```javascript
   const originalArray = [1, 2, [3, 4]];
   const copiedArray = JSON.parse(JSON.stringify(originalArray));
   ```

   However, keep in mind that this method is not efficient for large arrays or arrays containing complex objects due to the stringification and parsing process.

## Mutable and Immutable Methods

1. **Mutable Methods:**
   Mutable methods are array methods that directly modify the original array, altering its content in place without creating a new array. These methods have the potential to cause side effects, as the original array is changed. Mutable methods can be useful when you need to modify the existing array without creating a new one, which can be more efficient in terms of memory and performance.

   Examples of mutable methods include:

   - `reverse()`: Reverses the order of elements in the array.
   - `sort()`: Sorts the elements of the array in place.
   - `push()`: Adds one or more elements to the end of the array.
   - `pop()`: Removes the last element from the array.
   - `splice()`: Adds or removes elements from the array.
   - `shift()`: Removes the first element from the array.
   - `unshift()`: Adds one or more elements to the beginning of the array.

2. **Immutable Methods:**
   Immutable methods are array methods that do not modify the original array but instead return a new array with the desired modifications. The original array remains unchanged, and these methods do not cause side effects. Immutable methods are useful when you want to avoid modifying the existing array and ensure data integrity, especially in functional programming or when working with state management systems.

   Examples of immutable methods include:

   - `concat()`: Concatenates two or more arrays, returning a new array.
   - `slice()`: Extracts a portion of the array and returns it as a new array.
   - `filter()`: Creates a new array with elements that pass a test (based on a provided callback function).
   - `map()`: Creates a new array by applying a transformation function to each element of the original array.
   - `forEach()`: Iterates over the array without modifying it (used for performing actions on elements).
   - `reduce()`: Reduces the array to a single value through a provided callback function.
   - `reduceRight()`: Same as `reduce()`, but starts from the right end of the array.
   - `Array.from()`: Creates a new array from an iterable or array-like object.

Using immutable methods helps maintain the integrity of data and makes it easier to reason about the flow of your code. It's important to choose the appropriate method based on whether you need to modify the original array or create a new array with the desired changes.

## Side Effects

**Definition of Side Effect:**
In computer programming, a side effect refers to any observable change or action that occurs as a result of executing a function or method. Side effects typically modify the state of a program beyond the function's return value, introducing potential unpredictability and making code harder to reason about.

**Example:**
Consider the following function that modifies an array directly, leading to a side effect:

```javascript
const numbers = [1, 2, 3];

function squareAndAssign(array) {
  for (let i = 0; i < array.length; i++) {
    array[i] = array[i] ** 2; // Modifying the array directly (side effect)
  }
}

squareAndAssign(numbers);
console.log(numbers); // Output: [1, 4, 9]
```

**Drawbacks of Side Effects:**

1. **Unintended Consequences:** Side effects can lead to unexpected behavior and bugs when multiple parts of code rely on shared state, making it difficult to predict the outcome of function calls.

2. **Code Maintainability:** Code with side effects is harder to understand and maintain, as it becomes challenging to track changes in data across functions.

3. **Concurrency Issues:** In multi-threaded environments, side effects can introduce race conditions and data inconsistencies.

**Examples of Avoiding Side Effects:**

1. **Immutable Functions:** Use functions that do not modify the original data but return a new result, leaving the original data unchanged.

2. **Functional Programming:** Embrace functional programming principles, such as pure functions, to minimize side effects and create more predictable code.

3. **Using Array Methods:** Prefer using immutable array methods like `map()`, `filter()`, and `reduce()` instead of modifying arrays directly with mutable methods like `push()` and `splice()`.

4. **State Management:** Centralize and manage the state of an application using state management libraries like Redux, which helps avoid side effects by maintaining a single source of truth.

By avoiding side effects and favoring immutability, developers can write more maintainable, predictable, and scalable code, making debugging and testing more manageable and improving the overall quality of the software.

Let's see how these concepts apply to the array methods and their alternate immutable options:

| Array Method    | Mutability | Alternate Immutable Option              |
| --------------- | ---------- | --------------------------------------- |
| `reverse()`     | Mutable    | - `toReversed()`                        |
| `sort()`        | Mutable    | - `toSorted()`                          |
| `push()`        | Mutable    | -                                       |
| `pop()`         | Mutable    | -                                       |
| `splice()`      | Mutable    | - `toSpliced()`                         |
| `shift()`       | Mutable    | -                                       |
| `unshift()`     | Mutable    | -                                       |
| `concat()`      | Immutable  | `spread operator (...)`, `Array.from()` |
| `slice()`       | Immutable  | `spread operator (...)`, `Array.from()` |
| `filter()`      | Immutable  | `filter()` (creates a new array)        |
| `map()`         | Immutable  | `map()` (creates a new array)           |
| `forEach()`     | Immutable  | -                                       |
| `reduce()`      | Immutable  | `reduce()` (creates a new array)        |
| `reduceRight()` | Immutable  | `reduceRight()` (creates a new array)   |
| `Array.from()`  | Immutable  | `spread operator (...)`, `slice()`      |

Choosing between mutable and immutable methods depends on the specific use case. If you want to avoid side effects and maintain data integrity, you may prefer using immutable methods and creating new arrays when necessary. However, for performance-critical scenarios, mutable methods can be more efficient as they modify the original array directly without creating additional memory overhead.
