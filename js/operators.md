## Opearators

In JavaScript, operators are symbols or keywords that perform operations on one or more operands (values) and produce a result. JavaScript supports a wide range of operators, including arithmetic operators, comparison operators, logical operators, assignment operators, and more. Let's go through each type of operator with explanations and examples:

**1. Arithmetic Operators:**
Arithmetic operators are used for basic arithmetic calculations.

- `+`: Addition
- `-`: Subtraction
- `*`: Multiplication
- `/`: Division
- `%`: Modulus (remainder after division)

Example:

```javascript
let a = 5;
let b = 2;
console.log(a + b); // Output: 7
console.log(a - b); // Output: 3
console.log(a * b); // Output: 10
console.log(a / b); // Output: 2.5
console.log(a % b); // Output: 1
```

**2. Comparison Operators:**
Comparison operators are used to compare two values and return a Boolean result (`true` or `false`).

- `==`: Equality
- `!=`: Inequality
- `===`: Strict Equality (also checks the data type)
- `!==`: Strict Inequality (also checks the data type)
- `>`: Greater than
- `<`: Less than
- `>=`: Greater than or equal to
- `<=`: Less than or equal to

Example:

```javascript
let x = 10;
let y = 5;
console.log(x == y); // Output: false
console.log(x != y); // Output: true
console.log(x === "10"); // Output: false (strict equality)
console.log(x !== "10"); // Output: true (strict inequality)
console.log(x > y); // Output: true
console.log(x <= y); // Output: false
```

**3. Logical Operators:**
Logical operators are used to perform logical operations and return a Boolean result.

- `&&`: Logical AND (returns `true` if both operands are truthy)
- `||`: Logical OR (returns `true` if at least one operand is truthy)
- `!`: Logical NOT (negates the truthiness of an operand)

Example:

```javascript
let isTrue = true;
let isFalse = false;
console.log(isTrue && isFalse); // Output: false
console.log(isTrue || isFalse); // Output: true
console.log(!isTrue); // Output: false
```

**4. Assignment Operators:**
Assignment operators are used to assign values to variables.

- `=`: Simple assignment
- `+=`: Addition assignment (e.g., `x += 5` is equivalent to `x = x + 5`)
- `-=`: Subtraction assignment (e.g., `x -= 2` is equivalent to `x = x - 2`)
- `*=`: Multiplication assignment
- `/=`: Division assignment
- `%=`: Modulus assignment

Example:

```javascript
let num = 10;
num += 5; // num is now 15
num -= 3; // num is now 12
num *= 2; // num is now 24
num /= 4; // num is now 6
num %= 5; // num is now 1
```

**5. Other Operators:**
There are several other operators in JavaScript, such as:

- Ternary (Conditional) Operator `?:`: A shorthand way of writing an `if-else` statement.
- Comma Operator `,`: Evaluates multiple expressions and returns the last one.

**a. Ternary (Conditional) Operator `?:`:**
The Ternary Operator, often referred to as the Conditional Operator, is a compact way of writing a simple `if-else` statement. It allows you to make decisions based on a condition and assign values or perform actions accordingly.

Syntax:

```javascript
condition ? expression1 : expression2;
```

Explanation:

- `condition`: A JavaScript expression that evaluates to a Boolean value (`true` or `false`).
- `expression1`: The value or expression to be returned if the condition is `true`.
- `expression2`: The value or expression to be returned if the condition is `false`.

Example:

```javascript
let age = 20;
let status = age >= 18 ? "Adult" : "Minor";
console.log(status); // Output: 'Adult'
```

In this example, if the condition `(age >= 18)` evaluates to `true` (which means `age` is greater than or equal to 18), the value `'Adult'` is assigned to the variable `status`. Otherwise, if the condition is `false`, the value `'Minor'` is assigned to `status`.

**b. Comma Operator `,`:**
The Comma Operator in JavaScript allows you to evaluate multiple expressions and return the result of the last expression. It is used primarily in situations where multiple expressions need to be executed in a single statement.

Syntax:

```javascript
expression1, expression2, ..., expressionN
```

Explanation:

- `expression1, expression2, ..., expressionN`: A sequence of expressions, separated by commas.

Example:

```javascript
let x = 10,
  y = 5;
let result = ((x += 2), x + y);
console.log(result); // Output: 17
```

In this example, the expression `(x += 2, x + y)` is evaluated. First, `x` is incremented by `2`, and then the result of `x + y` (which is `12`) is returned and assigned to the variable `result`. The value of `x` is now `12`, but only the result of the last expression (`x + y`) is considered as the final value.

## Truthy and Falsy Values in JavaScript:

In JavaScript, values are categorized as either "truthy" or "falsy" based on their inherent boolean evaluation. These concepts are crucial when performing conditional checks and understanding how JavaScript treats different values in contexts that expect Boolean expressions. To better understand truthy and falsy values, let's delve into their definitions and how JavaScript handles them:

**1. Truthy Values:**
Truthy values are those that are considered as true when evaluated in a boolean context. In JavaScript, the following values are considered truthy:

- Non-empty strings: Any string with content, even a single character, is truthy. For example, `"hello"`, `"0"`, `"false"` are all truthy.

- `Numbers`: All non-zero numbers (both positive and negative) are truthy. Also, `Infinity` is truthy.

- `Non-empty arrays and objects`: Arrays and objects with at least one element or property are truthy.

- `Functions`: Any function is truthy.

**2. Falsy Values:**
Falsy values are those that are considered as false when evaluated in a boolean context. In JavaScript, the following values are considered falsy:

- `Empty strings`: The empty string `""` is falsy.

- `Number 0`: The number `0` is falsy.

- `NaN`: Not-a-Number is falsy.

- `null`: The value `null` is falsy.

- `undefined`: The value `undefined` is falsy.

- `false`: The boolean value `false` is falsy.

**3. Implicit Type Conversion and Truthy/Falsy Evaluation:**
JavaScript performs implicit type conversion when evaluating values in a boolean context. When using truthy/falsy values in conditional statements (e.g., `if`, `while`, `&&`, `||`), non-boolean values are automatically coerced to their corresponding truthy or falsy representations. This behavior allows for concise and expressive code, but it can also lead to unexpected results if not used carefully.

## Short Circuiting

**Truthy Coalescing (|| Operator):**
One common use case of truthy/falsy values is the truthy coalescing pattern using the `||` (OR) operator. It allows you to select the first truthy value from a list of operands. If all operands are falsy, the last operand is returned. This pattern is often used for default values:

```javascript
const name = inputName || "Default Name";
```

**Falsy Coalescing (&& Operator):**
Another common use case is the falsy coalescing pattern using the `&&` (AND) operator. It allows you to select the first falsy value from a list of operands. If all operands are truthy, the last operand is returned.

```javascript
const result = expensiveOperation() && defaultValue;
```

**Avoiding Implicit Type Conversion:**
While implicit type conversion can be helpful, it is essential to be cautious, especially when dealing with equality checks. To avoid implicit type conversion, use strict equality (`===`) or strict inequality (`!==`) operators, which check both value and type.

`Understanding the concept of truthy and fasly values and how variables ,objects and functions are coverted into booleans is the most important aspect in understanding how the short circuiting is evaluated.`

**Some Practice Quesitions for short circuiting**

1.

```javascript
let name = "";
let defaultName = name || "Guest";
console.log(defaultName);
```

**output:** Guest , since name is an empty string ,it will be fasle so the evaluation will move to the next value which is a truthy string value "Guest".

2.

```javascript
let a = 0;
let b = 5;
console.log(a || b);
```

**Output:** : 5 , since 0 is a falsy value.

3.

```javascript
let name = "";
let defaultValue = name || [] || "Ram";
console.log(defaultValue);
```

**Output:** [] The first value is falsy , but the second value is an empty array which is a truthy value thus the output will be an empty array.

`Note: One important thing to remember is that all the objects are truthy values and arrays are also a type of object thus it will be truthy  , so [] , {} , new Set() , all these are truthy values`.

4.

```javascript
let details1 = "";
let details2 = {};
let details3 = { name: "Ram", birthPalce: "Ayodhya" };
let defaultValue = details1 || details2 || details3;

console.log(defaultValue);
```

5.

```javascript
let user = { username: "john Doe", email: "john@example.com" };
let isValidUser = user.username && user.email;
console.log(isValidUser);
```

**Output:** `john@example.com ` since both the values are true the expression will return the last value, note this will not return true as you might get confused for.

6.

```javascript
let colors = ["red", "green", "blue"];
let color = colors[3] && colors[2];
console.log(color);
```

**Output:** You might think that it can give an error as `ArrayIndexOutOfBound` but js does not gives any such error if the array is out of bound it simply returns undefined .
Thus it will return the first falsy value that is `undefined` in this case.

7.

```javascript
let myFunction = () => {
  console.log("Executing function...");
};
let answer = myFunction && myFunction();
console.log(answer);
```

**Output:** Executing function... , as the first value is true , so it will move to another value and the it encounters a function call so it simply executes the function.
`The edge case here is that the second expression is a function call and not a value , the value of the variable answer will be the return value of the function , in this case since the function is not returing anything answer will be undefined.`

8.

```javascript
let user = { name: "Ram", birthPlace: "Ayodhya" };

function getUserName(user) {
  return user.name;
}

let data = user && getUserName();
console.log(data);
```

**Output:** `Ram` , this example reads as , if the user exists then get its UserName.

9.

```javascript
let a = 0;
let b = "";
let c = "Hello";
console.log(a || b || c);
```

**output:** `Hello` , as the other two values are falsy.

however if all the values are falsy , it will return the last value.

```javascript
let a = 0;
let b = "";
let c = undefined;
console.log(a || b || c);
```

**output:** `undefined.`

10.

```javascript
let user = { name: "John", age: 25 };
let userDetails = user.details && user.address;
console.log(userDetails);
```

**output: ** `undefined` , since the first value is undefined it returns undefined.

## The Number() function:

In JavaScript, the `Number()` function is used to convert a value to a numeric representation. It can be explicitly called as a function with the `Number()` syntax, or it can be used as a constructor to create a new number object.

**Syntax:**

```javascript
Number(value);
```

**Parameters:**

- `value`: The value that needs to be converted to a number. It can be a string, boolean, object, null, undefined, or any other primitive or non-primitive value.

**Return Value:**

- If the `value` can be converted to a valid number, the `Number()` function returns the numeric representation of the value.
- If the `value` cannot be converted to a valid number, the function returns `NaN` (Not a Number).

1. For Numeric value it will simply return the value.
2. For empty `string` , `undefined` or `null` it will return `0`.

```javascript
console.log(Number(32)); // 32
console.log(Number("")); //0
console.log(Number(null))); //0
console.log(Number(undefined)); //0
```

This happens implicitely whenever we perform any arithmatic operation.However there are some changes in the conversion when we do not use the `Number()` function , undefined is not converted to 0 rather it gives NaN.
`This mapping is important to remember as this will help in evaluating the arithmatic operations.`

**Operations With null**

```javascript
console.log(null + 2); // Output : 2
console.log(null - 2); // Output : -2
console.log(null * 2); // Output : 0
console.log(null / 2); // Output : 0
```

As null is converted to 0 , the expression becomes

```javascript
 0 + 2 -> 2
 0 - 2 -> -2
 0 * 2 -> 0
 0 / 2 -> 0
```

**Operations With undefined**

```javascript
console.log(undefined + 2); // Output :NaN
console.log(undefined - 2); // Output :NaN
console.log(undefined * 2); // Output :NaN
console.log(undefined / 2); // Output :NaN
```

**Operations With empty string**

```javascript
console.log("" + 2); // Output : 2
console.log("" - 2); // Output : -2
console.log("" * 2); // Output : 0
console.log("" / 2); // Output : 0
```

`Please dont get confused with the first operation it is actually concatenation and not 0 + 2`
`In all the other cases the empty string is converted to 0 except for + because strig concatenation has a higher precedence.`

```javascript
 "" + 2 -> "2"
 0 - 2 -> -2
 0 * 2 -> 0
 0 / 2 -> 0
```

So , except + ,all the other arithmetic opearators are valid in the string format of numbers.

```javascript
console.log("4" - "2"); // 2
console.log("4" * "2"); // 8
console.log("4" / "2"); // 2
console.log("4" % "2"); // 0
```

## Operators and their coersive nature

In simple words some operators can change the data type of the the variables , lets see three of them :

- -
- -
- !

**+ and - operator**

The `+` operator acts similar to the `Number()` function except for it cannot type cast the undefined value , apart from that that it will try to change the variable to a number.

eg:

```javascript
console.log(typeof Number("34"));
console.log(typeof +"34");
```

Both will give number , it it converts them to numbers.

Similar with the `-` operator .

```javascript
console.log(typeof -"");
console.log(typeof -null);
```

These will also give number.

**Some Example Questions**

```javascript
console.log(3 + +"4");
```

This will give 7 , as this is interpreted as

```javascript
console.log(3 + Number("4"));
```

Thus it will be 7 not 34.

```javascript
console.log(3 + +"3");

console.log(3 + 3 - 3);

console.log("3" + "3" - "3");
```

Try to guess the output for these 3 .

## The nullish coalescing operator

The nullish coalescing operator (`??`) is a relatively new addition to JavaScript, introduced in ECMAScript 2020 (ES11). It provides a convenient way to handle default values for cases where a variable is either `null` or `undefined`, without treating other falsy values (like `0`, `""`, `false`, etc.) as nullish values.

**Syntax:**

```javascript
const result = someVariable ?? defaultValue;
```

**Explanation:**

- If `someVariable` is not `null` or `undefined`, the expression `someVariable ?? defaultValue` evaluates to `someVariable`.
- If `someVariable` is `null` or `undefined`, the expression `someVariable ?? defaultValue` evaluates to `defaultValue`.

**Example:**

```javascript
let foo = null;
let bar = 0;
let baz = "Hello";
let defaultValue = "Default Value";

let result1 = foo ?? defaultValue;
let result2 = bar ?? defaultValue;
let result3 = baz ?? defaultValue;

console.log(result1); // Output: "Default Value"
console.log(result2); // Output: 0
console.log(result3); // Output: "Hello"
```

**Explanation:**

- In the example above, `foo` is `null`, so `result1` becomes `"Default Value"` as the nullish coalescing operator treats `null` as nullish and falls back to the `defaultValue`.
- `bar` is `0`, which is a falsy value but not nullish, so `result2` becomes `0`, as the nullish coalescing operator doesn't treat it as nullish and doesn't use the `defaultValue`.
- `baz` is `"Hello"`, which is a truthy value, so `result3` becomes `"Hello"`, as the nullish coalescing operator doesn't treat it as nullish and doesn't use the `defaultValue`.

**Advantages:**
The nullish coalescing operator is particularly useful when you want to provide a default value for variables that can be explicitly set to `null` or `undefined`, without affecting other falsy values.

**Comparison with the OR (`||`) Operator:**
The nullish coalescing operator differs from the OR (`||`) operator in how it handles falsy values other than `null` and `undefined`. The OR operator uses falsy values, such as `0`, `""`, `false`, etc., as well as `null` and `undefined`, to determine the result, which might not be the intended behavior when you specifically want to handle nullish values.

**Example:**

```javascript
let value = 0;
let result = value || "Default Value";
console.log(result); // Output: "Default Value"
```

In this case, the result is `"Default Value"` even though `value` is `0`, which might not be the expected behavior. Using the nullish coalescing operator (`??`) ensures that only `null` and `undefined` trigger the default value, while other falsy values retain their original value.
