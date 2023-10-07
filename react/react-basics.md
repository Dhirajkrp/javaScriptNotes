## Interveiw questions:

### 1. What is React?

React is a widely used JavaScript library that was launched in 2011. It was created by developers at Facebook, and it is primarily used for front-end development. React uses the component-based approach, which ensures that you build components that possess high reusability.

React is well known for developing and designing complex mobile user interfaces and web applications.

#### Advantages of using React

The main advantage of using react is that it provides the jsx syntax which enables developers to use html like syntax directly inisde the javascript code , this enables developers to render dynamic content on the go to provide a seamless user interface.

### Follow Up: What is jsx?

jsx stands for javascript XML and it is an extension of the javascript syntax ,jsx works similar to xml and has tagnames attributes and children , it makes the code simpler and elegent to write , it not necessary to use the jsx for react but it makes a lot easier to create and manage the ui.

lets see how jsx is used in react and what it looks like without jsx.

with jsx :

```javascript
const Hello = () => {
  return;
  <div>
    <h1>Hello world!</h1>
  </div>;
};
```

without jsx:

for creating elements react provides us with the function createElement which at minimum takes 3 arguments

1. The element or tag to be rendered for example a div or a heading .
2. Any optional property , such as any props or classes or ids.
3. For this we need to specify the childer of the newly created element.

```javascript
const Hello = () => {
  return React.createElement("h1", null, "hello world");
};
```

this will create a h1 with the text hello world, lets say we want some nested elements , for example a div with a h1 and a button having a class as btn.
then the code will look something like

```javascript
const Hello = () => {
  return React.createElement(
    "div",
    null,
    React.createElement("h1", null, "This is a heading element"),
    React.createElement("button", { className: "btn" }, "This is a button")
  );
};
```

The same code can be written using jsx as

```javascript
const Hello = () => {
  return;
  <div>
    <h1>This is a heading element</h1>
    <button className="btn"></button>
  </div>;
};
```

Behind the scene the jsx syntax is also transpiled to the React.createElement syntax but the jsx syntax provides developer the ease to use the html like syntax directy in the react code.

### Disadvantages of using react

React is a very powerful library to develop single page applications but there are some drawbacks of using react

1. Since this is just a library and not a full fledged framework it has it dependencies for things like state management and routing etc.
2. Since this uses the es6 features along with the jsx syntax the learning curve for the beginners can be challenging
3. since it focuses on single page application as the application grows it becomes it becomes hard to optimize the performance.

### what are props ?

Props stands for properties these are readonly and immutable values provided along the componenet which defines their attributes, this is since react follows unidirectional data flow , using props we can send some data from the parent component to the child component.

### What is the difference between stateless and staful component in react

## Components :

Comonents represents parts of the UI , eg header , footer , sidenav etc .
They are re-usable and can be nested.

A component is usually placed inside a js file eg : App.js which holds all the other components
Others can be NavBar.js , Footer.js etc and can be used in different places as per the requirements.
Extension of the file can be .js or .jsx which is javaScript extended.

There are two types of Components

1. Stateless Functional Components or simply Functional Components :
   They are simply js functions which return an html. eg :

```javascript
const Welcome = function (name){
    return <H1> Hello ,{name}<H1>;
}
```

2. Stateful Class Components or simply Class Components :
   They are ES6 classes which extends the React.Components class and use a render funcion to return the html.
   eg:

```javascript
class Welcome extends React.Component {
    render(){
        return <H1> Hello ,{name}<H1>;
    }
}
```

The App.js is a Class compontent.
It extents the Component Class which comes from the React library.

## Functional Components

The can recieve object of properties called props , and return HTML (jsx).
It is preferred to use arrow functions to make functional components.

## Difference between default and named export.

default export :
When we use a default export we can import the functional component with any name
eg :

```javascript
const Greet = () => {
  <h1>Hello Dhiraj</h1>;
};
export default Greet;
```

for this greet component we can import is as
import MyComponent from './Components/Greet'

Named export
we simply use the export keyword before the const like

```javascript
export const Greet = ()=>{
    return <H1> Hello Dhiraj <h1>;
}
```

when we import named functional component we cannot use a different name,
we must use the named as defined in the component.

we use arrow functions to define functional components.

Also when we import it we use a curly braces .
eg:

```javascript
export const Greet = () => <h1> Hello Dhiraj</h1>;

import { Greet } from "./Components/Greet";
```

## Class Components:

They are ES6 classes , they can also receive optional props ,it can also maintain private state ,
i.e some private information which can then be used to define the UI.

For a class to be a component it has to extent the Component class so first we import it .

```jsx
import React, { Component } from "react";
```

Secondly ,it has to implement the render method which either returns null or some html elements.

## When To Use What

Functional Components are used more , than class components.
since we use arrow functions or functions epressions , 'this' keyword points to null
in the functional Components.

Solution without using states , thus they are also known as stateless components

Are mainly responsible for UI thus are also known as Presentatioal Components.

Class Components are more complex.
They can maintain private data also known as states.
Complex UI Logic
Provide Lifecycle hooks
Known as Stateful Components or smart omponents.

This was the case before the introduction of hooks in react ,after the introduction of hooks it is adviced to use functional components instead of using the old class components.

### Is there a way of sending data from the child component to the parent component?

Yes, you can send data from a child component to a parent component in React by using callback functions as props. This is a common pattern known as "lifting state up" in React.

Here's how you can achieve this:

1. **Define a Callback Function in the Parent Component:**
   In the parent component, define a function that will be used as a callback to receive data from the child component.

   ```jsx
   // ParentComponent.js
   import React, { useState } from "react";
   import ChildComponent from "./ChildComponent";

   function ParentComponent() {
     const [childData, setChildData] = useState(null);

     // Callback function to receive data from the child component
     const receiveDataFromChild = (data) => {
       setChildData(data);
     };

     return (
       <div>
         <h1>Parent Component</h1>
         <ChildComponent sendDataToParent={receiveDataFromChild} />
         {childData && <p>Data received from child: {childData}</p>}
       </div>
     );
   }

   export default ParentComponent;
   ```

2. **Pass the Callback Function as a Prop:**
   In the parent component, pass the callback function (`receiveDataFromChild` in this example) as a prop to the child component.

   ```jsx
   // ParentComponent.js
   // ... (previous code)

   return (
     <div>
       <h1>Parent Component</h1>
       <ChildComponent sendDataToParent={receiveDataFromChild} />
       {childData && <p>Data received from child: {childData}</p>}
     </div>
   );
   ```

3. **Use the Callback Function in the Child Component:**
   In the child component, use the passed-in callback function (`sendDataToParent` in this example) to send data to the parent component.

   ```jsx
   // ChildComponent.js
   import React, { useState } from "react";

   function ChildComponent({ sendDataToParent }) {
     const [childData, setChildData] = useState("");

     const handleButtonClick = () => {
       // Send data to the parent using the callback function
       sendDataToParent(childData);
     };

     return (
       <div>
         <h2>Child Component</h2>
         <input
           type="text"
           value={childData}
           onChange={(e) => setChildData(e.target.value)}
         />
         <button onClick={handleButtonClick}>Send Data to Parent</button>
       </div>
     );
   }

   export default ChildComponent;
   ```

In this example, when the "Send Data to Parent" button is clicked in the child component, it calls the `sendDataToParent` callback function passed as a prop, passing the `childData` as an argument. The parent component receives and updates the data in its state, and you can see the updated data in the parent component's rendering.

This pattern allows you to pass data and trigger actions in the parent component based on events or user interactions in the child component, effectively communicating from child to parent in a React application.

### what is the difference between DOM and Virtual DOM?

The DOM (Document Object Model) and the Virtual DOM in React are related concepts, but they serve different purposes in web development:

1. **DOM (Document Object Model):**

   - The DOM is a programming interface provided by web browsers to represent and manipulate the structure and content of web documents, typically HTML and XML.
   - It is a tree-like structure that represents the elements and their relationships in a web page.
   - Changes to the DOM directly affect the web page's visual representation and can be slow and inefficient when dealing with frequent updates or complex user interfaces.
   - Traditional web development involves directly manipulating the DOM to update web page content, which can lead to performance bottlenecks, especially in large and dynamic applications.

2. **Virtual DOM (in React):**
   - The Virtual DOM is a concept used specifically in the React library, which is a JavaScript library for building user interfaces.
   - React introduces the Virtual DOM as an abstraction layer on top of the actual DOM.
   - When you make changes to a React component's state or props, React doesn't immediately update the real DOM. Instead, it creates a virtual representation of the DOM in memory, called the Virtual DOM.
   - React then compares the previous Virtual DOM with the updated Virtual DOM to determine the minimal number of changes needed to update the real DOM efficiently.
   - After computing the differences (diffing), React applies these changes to the real DOM in a batch process, which is much faster than directly manipulating the DOM for each change.
   - This approach helps optimize the performance of React applications by reducing unnecessary updates and rendering only the parts of the page that have changed.

In summary, while the DOM represents the actual structure of a web page and can be slow to manipulate directly, the Virtual DOM is a strategy employed by React to optimize the updating of the real DOM by performing updates in a more efficient and controlled manner. React's Virtual DOM minimizes direct interaction with the real DOM and provides better performance for building complex and dynamic user interfaces.

## Installation :

1. npx create-react-app <app_name>
   installs and compiles all the required packages for a react application

2. npm install create-react-app -g
   installs the create-react-app package
   after installation we can run
   create-react-app <app_name>

## Folder Structure:(Basics)

1. public Folder :
   This includes the index.html file and the favicon for the website.
   The index.html file contains a div having an id as root , which is used by react to render all the components

2. Src

   This folder has the App.js which is where we write our code , the code /components which we add here
   goes to the root div of the index.html page.

3. package.json :
   This file contains the information about our application , including the dependencies of the project and the
   package versions.
   This also contains the scripts such as the 'start' script which can be used to start the project,
   using the 'npm start'.

## React 16.7.0 - alpha update

Introduction to Hooks.
We can use hooks which provide with states without having to use classes.

## JSX

JavaScript XML
Write XML Like code for elements and components.
JSX tags have a name ,attrubutes,and children.
It is not necessary for making React Application.
JSX makes your code simpler and elegant.
It ultimately compiles to js in the browser.

```javascript
import React from "react";

const Hello = () => {
with jsx
return <div className="hello"  id= "hello">

<h1> HEllo Dhiraj from Hello.js</h1>
</div>;

```

this is the actual js code i.e without jsx
we cannot append more than one html element at a time i.e for every child node we have to call the createElement.

```javascript
return React.createElement("div", null, "h1", "Hello Dhiraj from Hello.js");

for a div and an h1 we use

return React.createElement(
    "div",
    null,//we can use an object to pass the attributes to the element such as its id or class etc
    React.createElement("h1", null, "Hello Dhiraj")
);

return React.createElement(
"div",
{ id: "hello", className: "hello" },
React.createElement("h1", null, "Hello Dhiraj")
);
//this can go crazy real soon
};

export default Hello;
```

since we use the jsx version of the code we import React form the react package.

## JSX Differences

```javascript
    class -> className
    for -> htmlFor
    onclick -> onClick
    tabindex -> tabIndex
```
