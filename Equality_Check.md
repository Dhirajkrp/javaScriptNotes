## Strict And Loose Comparision

## 1. Loose Comparision or Abstract Equality.

Loose comparison, also known as abstract equality, is performed using the == operator. In loose comparison, JavaScript attempts to convert the operands to the same type before making the comparison. This means that if the operands are of different types, JavaScript will try to coerce them to a common type and then compare their values.

1. If the operands have the same type, they are compared as follows:

   - _Object_: return true only if both operands reference the same object.
   - _String:_ return true only if both operands have the same characters in the same order.
   - _Number:_ return true only if both operands have the same value. +0 and -0 are treated as the same value. If either operand is `NaN`, return - false; so, `NaN` is never equal to `NaN`.
   - _Boolean:_ return true only if operands are both true or both false.
   - _BigInt:_ return true only if both operands have the same value.
   - _Symbol:_ return true only if both operands reference the same symbol.

2. If one of the operands is null or `undefined`, the other must also be null or `undefined` to return `true`. Otherwise return `false`.

3. If one of the operands is an `object` and the other is a `primitive`, convert the `object` to a `primitive`.
   At this step, both operands are converted to primitives **(one of String, Number, Boolean, Symbol, and BigInt)**.
   The rest of the conversion is done case-by-case.

   - If they are of the same type, compare them using step 1.
   - If one of the operands is a `Symbol` but the other is not, return false.
   - If one of the operands is a `Boolean` but the other is not, convert the `boolean` to a `number`: `true` is converted to `1`, and `false` is converted to `0`. Then compare the two operands loosely again.
   - `Number to String:` convert the `string` to a `number`. Conversion failure results in `NaN`, which will guarantee the equality to be - `false`.
   - `Number to BigInt:` compare by their numeric value. If the number is `±Infinity` or `NaN`, return `false`.
   - `String to BigInt`: convert the `string` to a `BigInt` using the same algorithm as the `BigInt()` constructor. If conversion fails, return `false`.

   Loose equality is symmetric: `A == B` always has identical semantics to `B == A` for any values of A and B (except for the order of applied conversions).

The most notable difference between this operator and the strict equality (===) operator is that the strict equality operator does not attempt type conversion. Instead, the strict equality operator always considers operands of different types to be different. The strict equality operator essentially carries out only step 1, and then returns false for all other cases.

**Code Examples**

```javascript
console.log(5 == "5"); // Output: true (The string "5" is converted to a number and compared with the number 5)
console.log(true == 1); // Output: true (The boolean true is converted to the number 1 and compared with the number 1)
console.log([] == ""); // Output: true (The array is converted to an empty string and compared with an empty string)
console.log(null == undefined); // Output: true (Both null and undefined are considered equal in loose comparison)
```

- In the first example, 5 == "5" returns true because the string "5" is converted to the number 5 before comparison.
- In the second example, true == 1 returns true because the boolean true is converted to the number 1 before comparison.
- In the third example, [] == "" returns true because the array is converted to an empty string before comparison.

## 2. Strict Comparison:

In strict comparison, JavaScript compares the operands without performing any type conversion. It checks if both the values and types of the operands are the same. If the operands have different types, they are considered not equal without any conversion. If the operands are of the same type, strict comparison performs a regular comparison based on their values.

Rules for Strict Comparision

1. If the operands have the same type, they are compared as follows:

   - _Object_: return true only if both operands reference the same object.
   - _String:_ return true only if both operands have the same characters in the same order.
   - _Number:_ return true only if both operands have the same value. +0 and -0 are treated as the same value. If either operand is `NaN`, return - false; so, `NaN` is never equal to `NaN`.
   - _Boolean:_ return true only if operands are both true or both false.
   - _BigInt:_ return true only if both operands have the same value.
   - _Symbol:_ return true only if both operands reference the same symbol.

2. If the operands have different types return false.

```javascript
console.log(5 === 5); // Output: true (Both operands are numbers and have the same value)
console.log(5 === "5"); // Output: false (The operands have different types - number and string)
console.log(true === 1); // Output: false (The operands have different types - boolean and number)
console.log([] === ""); // Output: false (The operands have different types - object and string)
console.log(null === undefined); // Output: false (The operands have different types - null and undefined)

//examples for objects

let arr1 = [1, 2, 3];
let arr2 = [1, 2, 3];

console.log(arr1 === arr2); //false
```

The reason why the array comarisions return false is that , even though they are or same type , i.e arrays and also have the same values ,
because they are two different objects having diffferent references in the memory , the `===` will return false.

for objects we can get true if we copy the reference of the object instead of making a new object .

```javascript
let arr1 = [];
let arr2 = arr1;

console.log(arr1 === arr2); //true ,since both are referencing same object in the memory.
```

```javascript
let a = [];
let b = [];

console.log(a == b);
console.log(a === b);
```

Both the comaprators will give false ,because since both the operands have same type , `==` will also work as `===`.
