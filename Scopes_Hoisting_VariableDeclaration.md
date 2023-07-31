## Table of Contents

1. Introduction to JavaScript Variables
2. Variable Declaration and Hoisting
   - Variable Hoisting
   - Function Hoisting
   - Hoisting Edge Cases
3. Scopes in JavaScript
   - Global Scope
   - Local Scope
   - Lexical Scoping and Closures
4. Variable Shadowing And Temporal Dead Zone.
5. Best Practices

## 1. Introduction to JavaScript Variables

Variables are fundamental building blocks in JavaScript. They serve as containers to hold various types of data, such as numbers, strings, objects, and functions. Declaring variables involves using keywords like `var`, `let`, or `const`, depending on the scope and mutability requirements.

## 2. Variable Declaration and Hoisting

### Variable Declaration with `var`, `let`, and `const`

In traditional JavaScript (prior to ES6), the primary way to declare variables was using the `var` keyword. Variables declared with `var` have function scope, meaning they are accessible throughout the entire function in which they are declared. However, `var` has a unique behavior called "hoisting."

**Code Example:**

```javascript
console.log(x); // Output: undefined
var x = 10;
console.log(x); // Output: 10
```

In the above example, the variable `x` is hoisted to the top of its function scope during the compilation phase.
We can imagine hoisting working in the background as

```javascript
var x;
console.log(x); //undefined
x = 10;
console.log(x); //10
```

As a result, the first `console.log(x)` statement displays `undefined` since the variable `x` exists but hasn't been assigned a value yet. The second `console.log(x)` statement prints the correct value `10`.

## ES6 Changes

With the introduction of ES6, two new ways to declare variables were introduced: `let` and `const`. Both `let` and `const` have block scope, which means they are confined to the block in which they are declared, such as within loops or conditionals.

**Code Example:**

```javascript
console.log(y); // ReferenceError: y is not defined
let y = 20;
console.log(y); // Output: 20
```

In the above example, trying to access the variable `y` before its declaration results in a `ReferenceError`, demonstrating that `let` variables are not hoisted.

### Variable Hoisting

Variable hoisting is the process of moving variable declarations to the top of their respective scopes during the compilation phase. However, only the declarations are hoisted, not the initializations.

**Code Example:**

```javascript
console.log(a); // Output: undefined
var a = 5;
console.log(a); // Output: 5
```

In the above example, the declaration `var a;` is hoisted to the top, making the first `console.log(a)` display `undefined`. The assignment `a = 5;` remains in place, so the second `console.log(a)` outputs `5`.

### Function Hoisting

Function declarations are also hoisted along with variable declarations. This allows you to use functions before they appear in the code.

**Code Example:**

```javascript
console.log(getValue()); // Output: Hello!
function getValue() {
  return "Hello!";
}
```

In the above example, the function `getValue()` is hoisted to the top, allowing it to be invoked before its actual declaration in the code.

### Hoisting Edge Cases

Hoisting can sometimes lead to unexpected behavior, especially when mixing `var` and `let` or re-declaring variables in the same scope.

**Code Example:**

```javascript
console.log(a); // Output: undefined
let a = 20; // SyntaxError: Identifier 'a' has already been declared
// Some block of code .
var a = 10;
```

In this example, the variable `a` is hoisted, but the second `let a = 20;` statement results in a `SyntaxError` since `a` has already been declared using `var`.

## 3. Scopes in JavaScript

### Global Scope

Variables declared outside any function or block have global scope. They are accessible from anywhere in the script, including inside functions.

**Code Example:**

```javascript
var globalVar = "I'm global";

function globalScopeExample() {
  console.log(globalVar); // Output: I'm global
}
```

In this example, the variable `globalVar` has global scope and can be accessed from within the function `globalScopeExample`.

### Local Scope

Variables declared inside a function or block have local scope. They are accessible only within the function or block where they are declared.

**Code Example:**

```javascript
function localScopeExample() {
  var localVar = "I'm local";
  console.log(localVar); // Output: I'm local
}
```

In this example, the variable `localVar` has local scope and is not accessible outside the `localScopeExample` function.

### Lexical Scoping and Closures

JavaScript uses lexical scoping, also known as static scoping. Lexical scoping means that the visibility of a variable is determined by its position in the source code, and nested functions have access to variables declared in their outer (enclosing) functions.

**Code Example:**

```javascript
function outerFunction() {
  var outerVar = "I'm outer";

  function innerFunction() {
    console.log(outerVar); // Output: I'm outer
  }

  innerFunction();
}
outerFunction();
```

In this example, `innerFunction` has access to the `outerVar` variable defined in its outer function `outerFunction`.

### Closures

To understand this concept we should be aware how variables are allocated and deallocated for the call stack . in short life span of variables.
Block Variables are allocated when the execution of the block starts , i.e the variables inside a function is allocated in the call stack only after the function is called and as soon as the function funishes its execution , all its variables are deallocated , this is the reason why the variables are not available outside the funtion.

But Closures are a special case where you can use the variables of the function even after the function has finished its execution . This happenes in many cases ,the most common one being when we define an inner function.

More Formally , A closure is a function that "remembers" its lexical scope even when it is executed outside that scope.

**Code Example:**

```javascript
function outerFunction() {
  var outerVar = "I'm outer";

  function innerFunction() {
    console.log(outerVar);
  }

  return innerFunction;
}

var closureFunction = outerFunction();
closureFunction(); // Output: I'm outer
```

In this example, the `innerFunction` is returned from `outerFunction`, and even when executed outside `outerFunction`, it still has access to the variable `outerVar`, forming a closure.

## 4. Variable Shadowing and Temporal Dead Zone.

**Variable Shadowing:**

Variable shadowing is a concept in JavaScript where a variable declared in an inner scope (e.g., inside a function or block) has the same name as a variable declared in an outer scope. When this occurs, the inner variable "shadows" or takes precedence over the outer variable within its own scope, effectively hiding the outer variable.

**Example of Variable Shadowing:**

```javascript
var x = 10; // Outer variable x with value 10

function foo() {
  var x = 20; // Inner variable x with value 20, shadowing the outer variable
  console.log(x); // Output: 20 (Accesses the inner variable x)
}

foo();
console.log(x); // Output: 10 (Accesses the outer variable x)
```

In this example, the `foo()` function has an inner variable `x` declared with `var x = 20;`. This inner variable shadows the outer variable `x` declared with `var x = 10;`. Inside the `foo()` function, when we reference `x`, it accesses the inner variable with the value `20`. Outside the function, when we reference `x`, it accesses the outer variable with the value `10`.

**Temporal Dead Zone (TDZ):**

The Temporal Dead Zone (TDZ) is a specific behavior in JavaScript that occurs with variables declared using `let` and `const`. It is the period between entering a scope and the actual declaration of a variable. During this period, accessing the variable results in a `ReferenceError`, as the variable exists but has not been initialized.

**Example of Temporal Dead Zone (TDZ):**

```javascript
console.log(y); // Output: ReferenceError: Cannot access 'y' before initialization
let y = 30;
console.log(y); // Output: 30
```

In this example, when we try to log the value of `y` before the `let y = 30;` statement, it throws a `ReferenceError` due to the temporal dead zone. The variable `y` exists in the scope but is not initialized yet. After the declaration, the second `console.log(y)` outputs the initialized value `30`.

**Combining Variable Shadowing and Temporal Dead Zone:**

```javascript
var z = 40; // Outer variable z with value 40

function bar() {
  console.log(z); // Output: undefined (Variable z exists but not initialized)
  let z = 50; // Inner variable z with value 50, shadowing the outer variable
  console.log(z); // Output: 50 (Accesses the inner variable z)
}

bar();
console.log(z); // Output: 40 (Accesses the outer variable z)
```

In this example, the `bar()` function has an inner variable `z` declared with `let z = 50;`. When we try to log the value of `z` before the `let z = 50;` statement, it outputs `undefined` due to the temporal dead zone. The inner variable `z` shadows the outer variable `z`, and inside the `bar()` function, it accesses the inner variable with the value `50`. Outside the function, it accesses the outer variable with the value `40`.

**Summary:**

Variable shadowing occurs when a variable declared in an inner scope has the same name as a variable declared in an outer scope, effectively hiding the outer variable within the inner scope. The temporal dead zone refers to the period between entering a scope and the actual declaration of a variable using `let` or `const`, during which accessing the variable results in a `ReferenceError`.

## 4. Best Practices

- Minimize the use of `var` and prefer `let` and `const` for better scoping and to avoid hoisting-related issues.
- Declare variables as close to their first use as possible to improve code readability and maintainability.
- Always declare variables with `const` when their value will remain constant throughout the program execution to prevent accidental reassignment.

## Some Practice Questions.

**Question 1:**

```javascript
var a = 10;
if (true) {
  var a = 20;
}
console.log(a);
```

- Ans : 20 , because the if condition is always true and var does not have block scope . , thus it will treat both the variables as same variable updating its. value to 20

**Question 2:**

```javascript
let b = 30;
if (true) {
  let b = 40;
}
console.log(b);
```

- Ans :30 , since the let keyword has block scope , these are treated as two variables with different scope and the global variable b never changes.

**Question 3:**

```javascript
const c = 50;
if (true) {
  const c = 60;
}
console.log(c);
```

Ans : 50 , same reason as let.

**Question 4:**

```javascript
function testVar() {
  console.log(a);
  if (true) {
    var a = 70;
  }
  console.log(a);
}
testVar();
```

- Ans : The first console.log() gives undefined , as the value of a is not defined yet , and the next console.log gives 70.

**Question 5:**

```javascript
function testLet() {
  console.log(b);
  if (true) {
    let b = 80;
  }
  console.log(b);
}
testLet();
```

- Ans : Both the console.log() gives refernece error , since the variale b is limited to the if block , there is no variable as b in the global scope.

**Question 6:**

```javascript
function testConst() {
  console.log(c);
  if (true) {
    const c = 90;
  }
  console.log(c);
}
testConst();
```

**Question 7:**

```javascript
var d = 100;
function testFunctionVar() {
  console.log(d);
  var d = 110;
  console.log(d);
}
testFunctionVar();
console.log(d);
```

- Ans : first output: undefined , second output : 110 , third output : 100
  This can be a bit tricky , all functions have access to the global variables so you might think the output must be 100. for the first output.
  It will be 100 if the code is something like

```javascript
var d = 100;
function testFunctionVar() {
  console.log(d); // this will print 100.
}
```

but due to hoisting the above code will be something like

```javascript
var d = 100;
function testFunctionVar() {
  var d; // the varible is declared but not defined yet.
  console.log(d); // reading the local scoped d which is undefined.
  d = 110; //setting the value of d.
  console.log(d); // reading the value of d as 110.
}
testFunctionVar();
console.log(d); //accessing the global d and reading value 100.
```

**Question 8:**

```javascript
let e = 120;
function testFunctionLet() {
  console.log(e);
  let e = 130;
  console.log(e);
}
testFunctionLet();
console.log(e);
```

- Ans : Reference Error for the first console.log() , the 130 , then 120.
  See Variable Shadowing and Temporal Dead Zone example.

**Question 9:**

```javascript
const f = 140;
function testFunctionConst() {
  console.log(f);
  const f = 150;
  console.log(f);
}
testFunctionConst();
console.log(f);
```

- Same as Question 8.

**Question 10:**

```javascript
var x = 160;
function testFunctionScopeVar() {
  console.log(x);
}
function testFunctionScopeLet() {
  let x = 170;
  console.log(x);
}
testFunctionScopeVar();
testFunctionScopeLet();
```

- Ans : 160 and 170;
