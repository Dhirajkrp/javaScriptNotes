## Destructiring

Destructuring is a feature introduced in ECMAScript 6 (ES6) that allows you to extract values from arrays or objects and assign them to variables in a more concise and readable way. It simplifies the process of extracting data from complex structures like arrays and objects, making your code cleaner and more expressive.

There are two types of destructuring in JavaScript:

1. **Array Destructuring:**
   Array destructuring enables you to unpack values from an array and assign them to variables. The syntax uses square brackets `[]` on the left-hand side of the assignment.

**Syntax:**

```javascript
const [variable1, variable2, ..., variableN] = array;
```

**Example:**

```javascript
const numbers = [1, 2, 3];
const [a, b, c] = numbers;

console.log(a); // Output: 1
console.log(b); // Output: 2
console.log(c); // Output: 3
```

Note that array destructuring is sequential , i.e we take values one by one starting from the first index.
We cannot directly access any values from the array using desctrictirng , however we can omit some of the values from it.

One extra thing we can do with destructuring is that we can delare new variables.

**Example:**

```javascript
const numbers = [1, 2, 3];
const [a] = numbers; //taking the first value.
const [, b] = numbers; // skipping the first value and taking the second value.
const [, , c] = numbers; // skipping two valules and taking the third value.
const [i, j, k, l = 10] = numbers; // declaring a new variable while destructuring values from the array.

console.log(a); // Output: 1
console.log(b); // Output: 2
console.log(c); // Output: 3
```

2. **Object Destructuring:**
   Object destructuring allows you to extract values from an object and assign them to variables using their property names. The syntax uses curly braces `{}` on the left-hand side of the assignment.

Note this is different from array destructuring , in array we had sequential access to the values but since objects do not have any indexes we can only access them through the key or the property name.

**Syntax:**

```javascript
const { property1, property2, ..., propertyN } = object;
```

**Example:**

```javascript
const person = { name: "John", age: 30, city: "New York" };
const { name, age, city } = person;

console.log(name); // Output: "John"
console.log(age); // Output: 30
console.log(city); // Output: "New York"
```

but if we try to access a property which does not exist that value will simply be undefined.

**Example:**

```javascript
const person = { name: "John", age: 30, city: "New York" };
const { contact } = person;

console.log(contact);
```

**Default Values in Destructuring:**
You can provide default values when destructuring in case the value is `undefined`.

**Example:**

```javascript
const person = { name: "John", age: 30 };
const { name, age, city = "Unknown" } = person;

console.log(name); // Output: "John"
console.log(age); // Output: 30
console.log(city); // Output: "Unknown" (city is not present in the object, so the default value is used)
```

**Rest Pattern in Destructuring:**
The rest pattern allows you to collect the remaining elements of an array or object into a new array or object. It uses the `...` (spread) operator.

**Example:**

```javascript
const numbers = [1, 2, 3, 4, 5];
const [first, second, ...rest] = numbers;

console.log(first); // Output: 1
console.log(second); // Output: 2
console.log(rest); // Output: [3, 4, 5]
```

One common use of the spread operator is to merge arrays or objects
**Example:**

```javascript
const nums1 = [1, 2, 3, 4, 5];
const nums2 = [6, 7, 8, 9, 10];
const numbers = [...nums1, ...nums2];

console.log(numbers);
```

**Example:**

```javascript
const nestedArray = [1, [2, 3], 4];
const [x, [y, z], w] = nestedArray;

console.log(x); // Output: 1
console.log(y); // Output: 2
console.log(z); // Output: 3
console.log(w); // Output: 4
```

**Example:**

```javascript
const personalInfo = { name: "Peter Parker", age: 17 };
const heroInfo = { heroName: "Spider Man", skill: "shooting webs" };
const superHero = { ...personalInfo, ...heroInfo };

console.log(superHero);
/*
{
  name: 'Peter Parker',
  age: 17,
  heroName: 'Spider Man',
  skill: 'shooting webs'
}
*/

//creating nested objects ,not destructuring properties one by one .
const data = { personalInfo, heroInfo };
console.log(data);

/*
{
  personalInfo: { name: 'Peter Parker', age: 17 },
  heroInfo: { heroName: 'Spider Man', skill: 'shooting webs' }
}
*/
```

When we merge two or more objects , the dublicate properties simply overrides the existing the value of the property.

**Example:**

```javascript
const personalInfo = { name: "Peter Parker", age: 17 };
const heroInfo = { name: "Spider Man", skill: "shooting webs" }; //both having name property.
const superHero = { ...personalInfo, ...heroInfo };

console.log(superHero);
/*
{ name: 'Spider Man', age: 17, skill: 'shooting webs' }
*/
// his real name should be a secret ;)
```

Destructuring is a powerful feature that simplifies working with complex data structures in JavaScript and is widely used in modern JavaScript development. It improves code readability and makes it easier to extract and work with specific values from arrays and objects.
