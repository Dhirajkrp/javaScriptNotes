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

## Some Practice Questions and their answers:

**Question 1:**

```javascript
console.log(1 + "2" + "2");
```

**Output:** "122"
**Explanation:** In this expression, the `+` operator is used for string concatenation when at least one operand is a string. So, the number `1` is converted to a string and concatenated with the other two strings `"2"` and `"2"`, resulting in the string `"122"`.

**Question 2:**

```javascript
console.log(1 + +"2" + "2");
```

**Output:** "32"
**Explanation:** The first `+` is the addition operator between the number `1` and the result of `+"2"`, which is converting the string `"2"` to a number (`2`). The second `+` is the string concatenation operator, so the number `3` is concatenated with the string `"2"`, resulting in the string `"32"`.

**Question 3:**

```javascript
console.log(1 + -"1" + "2");
```

**Output:** "02"
**Explanation:** The first `+` is the addition operator between the number `1` and the result of `-"1"`, which is converting the string `"1"` to a negative number (`-1`). The second `+` is the string concatenation operator, so the negative number `-1` is concatenated with the string `"2"`, resulting in the string `"02"`.

**Question 4:**

```javascript
console.log(+"1" + "1" + "2");
```

**Output:** "112"
**Explanation:** The `+` before the first `"1"` is the unary plus operator, which converts the string `"1"` to the number `1`. The second and third `+` are the string concatenation operators, so the number `1` is concatenated with the two strings `"1"` and `"2"`, resulting in the string `"112"`.

**Question 5:**

```javascript
console.log("A" - "B" + "2");
```

**Output:** "NaN2"
**Explanation:** The `"A"` and `"B"` are not numbers, so the subtraction operation between two non-numeric strings results in `NaN` (Not-a-Number). The second `+` is the string concatenation operator, so `NaN` is concatenated with the string `"2"`, resulting in the string `"NaN2"`.

**Question 6:**

```javascript
console.log("A" - "B" + 2);
```

**Output:** NaN
**Explanation:** Similar to the previous question, the `"A"` and `"B"` are not numbers, so the subtraction operation between two non-numeric strings results in `NaN`. The second `+` is the addition operator, and when adding `NaN` to the number `2`, the result is still `NaN`.

**Question 7:**

```javascript
console.log(typeof typeof 1);
```

**Output:** "string"
**Explanation:** The inner `typeof 1` returns `"number"`, and then the outer `typeof "number"` returns `"string"`. The outer `typeof` always returns a string representation of the type of the operand.

**Question 8:**

```javascript
console.log(2 ** (3 ** 2));
```

**Output:** 512
**Explanation:** The right-to-left evaluation is performed for the exponentiation operators. First, `3 ** 2` is evaluated as `9`, and then `2 ** 9` is evaluated as `512`.

**Question 9:**

```javascript
console.log(true === "true");
```

**Output:** false
**Explanation:** Strict comparison (`===`) checks both the value and the type. `true` is a boolean value, and `'true'` is a string. Since they have different types, the result is `false`.

**Question 10:**

```javascript
console.log([] == ![]);
```

**Output:** true
**Explanation:** The right-hand side (`![]`) is evaluated first. The `!` operator converts `[]` (an empty array) to a boolean value `true` and negates it, resulting in `false`. Now, we have `[] == false`. In loose comparison, an empty array is coerced to an empty string, and `false` is coerced to `0`. So, we have `"" == 0`. Since both operands are of the same type (string and number) and their values are loosely equal, the result is `true`.

Remember that these tricky questions can sometimes exploit the nuances of JavaScript's type coercion, so it's always essential to understand the rules of loose and strict comparison to predict the output accurately.
