<img src="https://i.imgur.com/VunmGEq.jpg">

# Intro to React & Components

## Learning Objectives

|Students Will Be Able To:|
|---|
| Explain the Use Case of React |
| Explain What Components Are |
| Explain How React Renders a User Interface |
| Compose a UI Using Components |
| Use React DevTools |

## Road Map

1. What is React?
2. Why Use React?
3. Creating a React App
4. Components
5. How a React App is Loaded and Renders
6. Designing User Interfaces Using Components
7. Let's Define a Component
8. Practice Exercise: Define Another Component
9. Install and Open React Developer Tools 
10. References

## 1. What is React?

- An open-source JavaScript library used to **build and render user interfaces** in the browser.
- It was open-sourced in May of 2013.
- Created by Jordan Walke, a Facebook engineer.
- Now being used by companies such as Netflix, Imgur, Airbnb, Walmart, and many more.
- React Native, a separate library, can be used to develop native iOS and Android mobile apps.

## 2. Why Use React?

[React](https://reactjs.org/) is the most popular (by far) front-end library for building highly dynamic user interfaces used in today's modern single-page applications.

> 👀 A single-page application (SPA) updates its UI "in-place" vs. the traditional multi-page web apps we've built thus far where the browser replaces the entire web page each time the user interacts with it.

Most importantly, you want to learn to use React because...

<figure>
  <img src="https://i.imgur.com/vGlFRHq.png">
  <figcaption>Source: <a href="https://www.devjobsscanner.com/blog/the-most-demanded-frontend-frameworks-in-2022/">devjobsscanner.com</a></figcaption>
</figure>
<figure>
  <img src="https://i.imgur.com/FfSLt6b.png">
  <figcaption>Source: <a href="https://www.devjobsscanner.com/blog/the-most-demanded-frontend-frameworks-in-2022/">devjobsscanner.com</a></figcaption>
</figure>

## 3. Creating a React App

### `npx create-react-app <app name>`

The React team has developed a wonderful script for generating React apps.

The following command will create a skeleton React app within a new directory:

```
npx create-react-app <app name>
```

> 👀 `npx` is a "package runner" and comes with `npm` versions 5.2.0 and later and is now the recommended approach to running `create-react-app`.  Be aware that you will find many React tutorials that show installing and running `create-react-app` without using `npx`. 

However, before you start creating a bunch of React apps, note that each bare-bones React app consumes approximately 270MB of disk space!  This is due to the sheer number of Node modules a React project requires due to its dependency on build tools, its development server, etc.

Although using<br>`npx create-react-app <app name>`<br>is a great way to start an actual React project, we can save our disk space when learning and experimenting by using the most excellent code playground, [CodeSandbox](https://codesandbox.io/)...

### CodeSandbox Starting React App

You'll want to set up a new account and create a new React sandbox...

<img src="https://i.imgur.com/zD5bcS5.png">

CodeSandbox itself is a React app and uses the underlying editor of VS Code - so put those shortcut keys you've learned to work!

We can manage the project's files in the left-pane, edit code another pane, and see the live output in a pane or in its own browser tab (which is excellent for debugging).

Let's rename our sandbox to something like "React To-Do" by editing the temporary name:

<img src="https://i.imgur.com/iiu7JXl.png">

> 👀 It's possible to lose work in CodeSandbox if files are not saved.  You may want to access File/Preferences, search for "autosave" and select your preferred option.

### React Apps Are 100% JavaScript

Despite its purpose being to render User Interfaces, React applications are written entirely using 100% JavaScript.

Sure, a React app uses CSS for styling rendered elements, but there's no HTML anywhere in a React app.

But what about that HTML-looking code you ask...

```js
<div className="App">
  <h1>Hello CodeSandbox</h1>
  <h2>Start editing to see some magic happen!</h2>
</div>
```

Well, that's not HTML, it's JSX!

JSX is fundamental to React and we'll cover it in detail in the next lesson.

Let's start a React Fundamentals Chart study guide that we can add to as the lessons unfold...

| React Fundamental | Summary |
|---|---|
| [React](https://reactjs.org/) | <ul><li>A JS library for building dynamic UIs using components</li></ul> |
| [JSX](https://reactjs.org/docs/introducing-jsx.html) | <ul><li>A syntax extension to JS that looks like HTML and makes defining UIs more intuitive vs. pure JS</li></ul> |

Let's make some changes by editing the JSX as follows:

```js
<div className="App">
  <h1>React To-Do</h1>
  <ul>
    <li>Learn React</li>
    <li>Learn the MERN-Stack</li>
  </ul>
</div>
```

### Modern JavaScript

CodeSandbox's starting React app uses modern JavaScript.

As React developers, we frequently use the latest features of JavaScript such as the **spread syntax**, **destructuring assignment**, etc.

For example, note the use of `import` at the top of **index.js**.  Similar to how we used `require` in Node, `import` allows us to access the functionality that is exported by other JavaScript files (modules).

The newer [JavaScript Module](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) syntax was introduced with ES2015 and they're really cool. However, you're probably wondering if they're so cool, why haven't we used them yet. The answer is that their use, until recently, required tooling known as a "module bundler", the most popular being [webpack](https://webpack.github.io/), used by React projects created using CRA.

### ❓ Review Questions - React (1 min)

<details>
<summary>
(1) What is the purpose of the React library?
</summary>
<hr>

**To render highly dynamic user interfaces using components**

<hr>
</details>

<details>
<summary>
(2) True or False: React uses HTML to define user interfaces.
</summary>
<hr>

**False.**  It may look like HTML, but it's a similar markup language known as **JSX**.

<hr>
</details>

## 4. Components

### What Are Components?

Components are the building block of User Interfaces and are fundamental to today's front-end libraries/frameworks, including [React](https://reactjs.org/), [Angular](https://angular.io/) & [Vue](https://vuejs.org/).

Let's contrast the two different kinds of components in React:

- User-defined components that we as developers define
- Built-in components that are part of the React library

### User-Defined Components

We code user-defined components and use them to compose the application's user interface.

In the "React To-Do" sandbox, there is a single user-defined component, `<App>`, that's defined and exported in the **App.js** module:

```js
export default function App() {
  return (
    <div className="App">
      <h1>React To-Do</h1>
      <ul>
        <li>Learn React</li>
        <li>Learn the MERN-Stack</li>
      </ul>
    </div>
  );
}
```

> 👀 User-defined components must be named using UpperCamelCasing.

A component may be defined using a JS function or class.  Since the introduction of "React hooks" in version 16.8, the trend has been to code components exclusively using functions.

Our user-defined components typically render other user-defined components and/or React's built-in components...

### React Elements

**React Elements** are components built into React.

A React Element exists for each HTML element we're familiar with and thus, are easily recognizable in the JSX.

> 👀 React Elements will always be named using lowercase.

#### 👉 You Do - Identify the React Elements within the JSX of the "React To-Do" sandbox so far (1 min)

<details>
<summary>
Don't peek! 
</summary>
<hr>

There are the following React Elements (components):
- A single <code><div></code> component
- A single <code><h1></code> component
- A single <code><ul></code> containing two <code><li></code> components

<hr>
</details>

When a React Element is rendered, its corresponding HTML element will be created in the page (DOM).

Using Chrome DevTools, open the output of the sandbox in its own tab and observe the HTML elements created by the `<App>` component's JSX:

<img src="https://i.imgur.com/bTGpR8b.png">

Yep, each React Element in the JSX results in its corresponding HTML element being rendered in the DOM!

> 👀 User-defined components themselves, e.g., `<App>` do not render an HTML element in the DOM - after all, a browser wouldn't know what the heck an `<App>` HTML element is.

### HTML/Component Hierarchy

In a React app, the tree-like hierarchy of the HTML elements in the browser document is a result of a hierarchy of components being rendered.

At the top of that component hierarchy is, by convention, a user-defined component named `<App>`.

Let's see how the `<App>` component is rendered for the first time when the React app loads...

## 5. How a React App is Loaded and Renders

Here's what happens when a user browses to a web app that uses React for its front-end UI:

<img src="https://i.imgur.com/7aVwb9k.png">

When React renders a Function Component, it simply runs that function and renders what the function returns.

Similarly, a Class Component's `render` method is invoked, and like a Function Component, React renders what the `render` method returns.

### High-Performance Rendering of Components

Rendering happens frequently in a React app (whenever state changes), but thanks to React's ingenious design, it's very fast and efficient because React does not render components directly into the browser's DOM and manipulating the DOM is relatively CPU intensive.

Instead, React:

1. Renders all React Element components into a [Virtual DOM](https://reactjs.org/docs/faq-internals.html#gatsby-focus-wrapper).
2. After all components have been rendered, React compares the current Virtual DOM to the previous Virtual DOM and computes what is called the "diff".
3. React uses the "diff" to make only the necessary changes to the actual DOM in the browser.
  <img src="https://i.imgur.com/LC7wclE.jpg">

Time to add to our React Fundamentals chart...

| React Fundamental | Summary |
|---|---|
| ... | ... |
| Components  | <ul><li>A user interface is defined by a hierarchy of components</li></ul>|
| User-Defined Component | <ul><li>May be defined as a function or class but must be named using UpperCamelCasing</li><li>May hold and manage application state</li><li>May contain or utilize application logic such as fetching data, implementing the win/loss logic of a game, etc.</li></ul> |
| React Elements | <ul><li>React's built-in components, such as `<div>`, that render their corresponding HTML element into the DOM</li><li>Are always named using lowercase</li></ul> |
| [`root.render()`](https://reactjs.org/docs/react-dom.html#render) method | <ul><li>Renders the React app's top-level component for the first time when the app's JS is loaded in the browser</li></ul> |
| When a Component's State is Updated | <ul><li>The component is re-rendered</li><li>All children components are also rendered, and so on until there are no more components to render</li></ul> |

### ❓ Review Questions - Components (2 mins)

<details>
<summary>
(1) True or False:  User-defined components must be named in lowercase.
</summary>
<hr>

**False**.  They are named using **UpperCamelCasing**.

<hr>
</details>

<details>
<summary>
(2) True or False:  A Function Component is a component that is written as a JS function and returns its user interface as JSX.
</summary>
<hr>

**True**

<hr>
</details>

<details>
<summary>
(3) True or False:  When a component is rendered, all of its children are also rendered.
</summary>
<hr>

**True**

<hr>
</details>

<details>
<summary>
(4) After a React app is rendered for the first time by the <code>root.render()</code> method, components re-render when ________ is updated.
</summary>
<hr>

**State**

<hr>
</details>

<details>
<summary>
(5) True or False: A div tag placed inside of jsx(react component) is an html div element?
</summary>
<hr>

**False** - A div tag, or really any traditional html tag (&#60;p&#62;, &#60;li&#62;, &#60;span&#62;, etc.), placed inside of jsx is in fact a react component meant to represent its respective html element in react's virtual DOM.

<pre>
<code>
function MyComponent() {
    return (
      &#60;div&#62;This div tag not an html div element, but a react component meant to represent an html div element in react's virtual DOM&#60;/div&#62;
    );
}
</code></pre>

<hr>
</details>

## 6. Designing User Interfaces Using Components

To develop a React application, we compose the UI using a hierarchy of components.

For example, take the following wireframe/app:

<img src="https://i.imgur.com/hL1T2tH.png">

The above could be broken into the following components:

<img src="https://i.imgur.com/TqerRDf.png">

<details>
<summary>
❓ Which top of the component-hierarchy component is missing from the above diagram?
</summary>
<hr>

**`<App>`**

<hr>
</details>

<details>
<summary>
❓ What are the names of the two components being rendered by the "missing" <code>&lt;App&gt;</code> component?
</summary>
<hr>

**<code>&lt;Network&gt;</code>** and **<code>&lt;Predictions&gt;</code>**

<hr>
</details>


We must get used to thinking about our UI in terms of components. This "Component Thought" requires us to:

- Break the UI into several smaller components to make the code more manageable.
- Compose (combine) these components into other components.
- Compose page-level components that render according to which client-side route is active.

## 7. Let's Define a Component

Let's refactor "React To-Do" so that the `<App>` component renders a `<ToDoList>` component instead of the `<ul>` and its contents...

### Define a `ToDoList.jsx` Module

Click on the **src** folder in the sandbox and use its GUI to create a new file named **ToDoList.jsx**.

Modules should be named the same as the component, i.e., using UpperCamelCasing.

> 👀 By using `.jsx` as the module's extension, we'll get better code completion and a cool React icon by the filename.

### Note: Importing the React Library is No Longer Necessary

Prior to React version 17+, we used to have to import React at the top of every component module like this:

```js
import React from 'react';
```

However, this is no longer required and is being mentioned here because there's a lot of projects out there pre-version 17.

### Stub up and export the Function Component

Let's stub up `<ToDoList>` as follows:

```jsx
export default function ToDoList() {

}
```

Note that you may also see components exported using another line of code like this:

```jsx
function ToDoList() {

}

export default ToDoList;
```

Cool.  So ultimately, a Function Component must `return` its UI as JSX.

As planned, let's move the `<ul>` and its contents from **App.js** to our new component and `return` it:

```jsx
export default function ToDoList() {
  // Application logic, etc. goes here
  return (
    <ul>
      <li>Learn React</li>
      <li>Learn the MERN-Stack</li>
    </ul>
  );
}
```

> 👀 Saving the file (`command/ctrl + s`) in the sandbox will auto-format the code because "Prettier" is configured by default.

### Update `<App>` to Render the `<ToDoList>` Component

Now let's import and render the `<ToDoList>` component in **App.js**:

```jsx
// Default imports can be named anything
import ToDoList from "./ToDoList";

export default function App() {
  return (
    <div className="App">
      <h1>React To-Do</h1>
      <ToDoList />
    </div>
  );
}
```

> 👀 If a component is empty (does not have any content), it must be self closed using `/>` or less commonly as `<ToDoList></ToDoList>`.

The app should now be rendering the same as before the `<ToDoList>` refactor:

<img src="https://i.imgur.com/6oktFlu.png">

Navigate to the next page where you will complete and submit the following exercise...

### 8. 💪 Practice Exercise: Define and Render Another Component (10 mins)

Your turn to create and render another component:

- Refactor "React To-Do" so that the `<ToDoList>` component renders two `<ToDoListItem>` components instead of the two `<li>` components.
- Define the `<ToDoListItem>` component in its own JS module using the proper naming convention.
- Simply have the `<ToDoListItem>` component render `<li>To Do Item</li>`. In the next lesson you will learn how to render data passed to the component.
- Submit the link to your sandbox in the Assignment Submission's input box.

This is what you will see when finished:

<img src="https://i.imgur.com/2WIctBO.png">

## 9. Install and Open React Developer Tools 

You may have noticed that CodeSandbox has a **React DevTools** tab used to troubleshoot components.

We definitely want to be able to do the same in Chrome!

Browse to the [React Developer Tools extension](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi) and install it.

Now when DevTools are open, you'll find a **Components** option available on the far right (you may have to click the `>>` to see it):

<img src="https://i.imgur.com/4bt00fX.png">

Clicking it reveals an amazing tool for browsing the component hierarchy and inspecting the details of a component's state and props (yet to be discussed).

<img src="https://i.imgur.com/m0OtmYn.png">

## 10. References

[The Completed Fundamentals of React Chart](https://gist.github.com/jim-clark/cbc87fdf01c22f412737ca121ef70761)

[React Docs](https://facebook.github.io/react/)




<img src="https://i.imgur.com/pg98OTd.png">

# React Dev Skills Lab - Part 1

## Intro

Now that you've learned a bit about components in React, let's practice defining and rendering a few more.

##### This lab, combined with Parts 2, 3 & 4 is a Deliverable

## Exercises

The goal of the lab is to put in a rep doing everything that you did during the _React Intro & Components_ lesson.

Create a new React sandbox in [codesandbox.io](https://codesandbox.io) named "react-dev-skills".

Code the app so that it renders the following UI:

<img src="https://i.imgur.com/a1YSt4R.png">

Using the following component hierarchy:

<img src="https://i.imgur.com/Z7yRF8b.png">

### Legend

- React Elements are outlined in blue.
- The components are as follows:

  | Component | Renders |
  |---|---|
  | `<App>` | `<h1>`<br>`<SkillList>`<br>`<hr>`<br>`<NewSkillForm>` |
  | `<SkillList>` | `<ul>`<br>`<SkillListItem>` x 3 |
  | `<SkillListItem>` | `<li>` with "SkillListItem" as its content |
  | `<NewSkillForm>` | `<form>` |
  | `<form>` in `<NewSkillForm>`  | `<label>` with "Skill" and `<input>` as its content<br>`<label>` with "Level" and `<select>` as its content<br>`<button>` with "ADD SKILL" as its content |
  | `<select>` in<br>`<form>` above | `<option>` x 5 with content of "1" thru "5"` |

### This lab combined with Parts 2, 3 & 4 is a deliverable



<!-- {% raw %} -->

<img src="https://i.imgur.com/VunmGEq.jpg">

# React Fundamentals - JSX & Props

## Learning Objectives

|Students Will Be Able To:|
|---|
| Explain the Use Case of JSX |
| Explain the Benefits that JSX Provides |
| Use JSX to Define a Component's UI |
| Render JS Expressions Into the DOM Using JSX |
| Include Props in JSX |
| Render an Array of Components |
| Style Components Using the `className` & `style` Prop |

## Road Map

1. Setup
2. JSX - What & Why?
3. Review: JS Expressions
4. Writing JS Expressions Into the DOM Using JSX
5. JSX Itself is a JS Expression!
6. What Are Props?
7. Properly Rendering Arrays of Components
8. Props for React Elements
9. React Elements
10. Essential Questions
11. Bonus Practice Exercise

## 1. Setup

This lesson builds upon the "React To-Do" sandbox we created in the previous lesson in [codesandbox.io](https://codesandbox.io/):

<img src="https://i.imgur.com/KgHpiqD.png">

## 2. JSX - What & Why?

### What?

- **JSX** is an XML-like syntax extension to JavaScript. [XML](https://en.wikipedia.org/wiki/XML) is short for _extensible markup language_ and JSX is one of those extensions - just like HTML is.
- Created by Facebook for use in React.
- It provides a way to concisely define tree structures with attributes - perfect for defining a DOM tree!
- It is transpiled into pure JavaScript.

  <details>
  <summary>❓ What is transpiling</summary>
  <hr>
  
  Transpiling converts source code of one language into source code of another language.  They are often referred to as source-to-source compilers. Compilers on the the other hand, convert source code into a form of executable code.
  
  <hr>
  </details>

### Why JSX?

- It's simple and clear. Compared to pure JavaScript, JSX provides a more concise and better way to define a UI.

- JSX resembles HTML, which allows us to more easily visualize the UI its JavaScript will create.

- 99.99% (a guess) of React apps are developed today using JSX to define the UI, not vanilla JS.

## 3. Review: JS Expressions

Before we learn how to render the result of a JS expression within JSX, let's review what JS expressions are...

JavaScript expressions evaluate to a single value/thing.

They can be used wherever a value is used, for example:

- Assigned to a variable
- Provided as an argument to a function call
- Returned from a function

Statements on the other hand, perform actions. A program's statements such as `if` statements and `for`/`while` loops are not expressions.

## 4. Writing JS Expressions Into the DOM Using JSX

To write the result of a JS expression into the DOM within the JSX, we simply need to **enclose the expression within curly braces**.

Let's experiment by typing the the following within `<ToDoList>` in our sandbox and observe the output:

```jsx
// ToDoList.jsx

export default function ToDoList() {
  const str = "SEI";
  const score = 94;
  return (
    <ul>
      <ToDoListItem />
      <ToDoListItem />
      <li>Number: {score}</li>
      <li>String: {str}</li>
      <li>Math.random(): {Math.random() * 100}</li>
      <li>Template Literal: {`${str} Rocks`}</li>
      <li>Ternary: {score > 90 ? "A" : "B or less"}</li>
      <li>Booleans, null & undefined: {true}{false}{null}{undefined}</li>
      <li>Logical &&: {score > 90 && <div>Got an 'A'!</div>}</li>
    </ul>
  );
}
```

The fact that React does not output the value of booleans, `null` or `undefined` can really come in handy, e.g., when using the logical `&&` scenario for writing out an expression or not.

Objects and most of the [built-in Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects) (Date, Functions, RegExp, etc.) cannot be rendered as is - just their properties can be rendered.  The practical exception are Arrays which we'll look at shortly.

## 5. JSX Itself is a JS Expression!

Developing real-world React apps requires tooling to:

- Transpile the JSX into pure JS
- Import CSS
- Bundle the JS modules

The most popular transpiler for JSX is [Babel](https://babeljs.io/). The following shows what a JSX expression transpiles into:

<img src="https://i.imgur.com/8vLLr1Y.gif">

As you can see, JSX transpiles into a function call: `React.createElement(...)`, which returns an object used by the React library.

Because JSX results in a function call that returns an object, JSX is a JavaScript expression!  Thus, JSX can be assigned to variables, used in ternary expressions, etc.!

### A Component Must Return a Single Root JSX Node

Because a function can only return a single expression, we must be sure to return a single root JSX node using the `return` statement.

For example, the following will fail to compile:

```jsx
function Whoops() {
  return (
    <h1>Whoops</h1>
    <h2>No Dice!</h2>
  );
}
```

The function above is attempting to return two things, i.e., two objects which just isn't possible in JavaScript (or any other popular programming language).

The only solution used to be to wrap the sibling components with a single React Element such as a `<div>`:

```jsx
function GoodToGo() {
  return (
    <div>
      <h1>Good To Go</h1>
      <h2>Dice Please!</h2>
    </div>
  );
}
```

The downside of the above approach is that this results in an extra, and perhaps unwanted `<div>` rendered to the DOM which could impact layout/styling.

A better alternative if you don't want or need an extra wrapping React Element is [React Fragments](https://reactjs.org/docs/fragments.html) added in version 16.2 of React:

```jsx
function GoodToGo() {
  return (
    <>
      <h1>Good To Go</h1>
      <h2>Dice Please!</h2>
    </>
  );
}
```

> 👀 The `<> </>` syntax is shorthand for `<React.Fragment> </React.Fragment>`

### 👉 You Do - Render an Array (3 minutes)

1. Define an array named `misc` before the `return` statement that has the following elements:

  - A string of your choosing
  - A number of your choosing
  - A boolean of `true` or `false`
  - A React Element, e.g., a `<div>` with some content

2. In **ToDoList.jsx** Add an `<li>` React Element and render the array as its content.

As you can see, React can render arrays.  In fact, it's very common to render arrays of components, which we'll do in a bit.

## 6. What Are Props?

Very simply, **props** are used to pass information to components.

> 👀 "Information" can be any JS expression such as variables, functions, etc.

### Basic Syntax

The syntax of passing props to a child component is much like defining attributes in an HTML element, for example, we can pass a simple string to a component like this:

```jsx
<Person firstName="Fred" />
```

In the above example, the name of the prop is `firstName`.

Because JSX is transpiled into pure JS, we use lowerCamelCasing to name props.  This is contrary to the convention of kebob-casing used to name attributes in HTML.

Like HTML attributes, there should be no spaces before or after the `=` sign.

There is no limit to the number of props that can be passed:

```jsx
<Person
  firstName="Fred"
  age={21}
/>
```

**Any** JS expression can be passed, however, expressions other than simple strings (excludes template literals), are passed within curly braces. Thus, the `age` prop will have the value set to the **number** `21`.

Each prop becomes a property on a "props" object that's passed to the child component.

The next example shows how you can pass an object literal and even a function:

```jsx
function handleRaise(name, amount) {
  // Give the person a raise!
}

<Person
  name={{first: "Fred", last: "Arroyo"}}
  age={21}
  handleRaise={handleRaise}
/>
```

Don't let those double-curly braces (`{{ ... }}`) confuse you.  The outer curly braces simply say, "here comes a JS expression"; and the inner curly braces represent an object literal. 

### How the Child Components Access Props

A props object is passed to Function Components as an argument:

```jsx
function Person(props) {
  return (
    <div>
      <p>First: {props.name.first}</p>
      <p>Last: {props.name.last}</p>
      <p>Age: {props.age}</p>
      <button onClick={() => props.handleRaise(props.name, 9999)}>Give Raise!</button>
    </div>
  );
}
```

By convention, we name the parameter `props` instead of `tuna`, `mamaMia`, etc.

As you can see, each passed prop becomes a property on the `props` object that's passed to the Function Component as an argument.

If no props are passed to a component, `props` will be an empty object.

> 👀 IMPORTANT: A prop's value should never be changed.  Instead, a different value should be assigned to the prop at the source (the component that "owns" the info being passed).

### Destructuring the `props` Object

In modern JavaScript, it is common to create variables from properties on objects or elements in an array using [Destructuring Assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment).

The syntax is similar to "unpacking" in Python.

Here's a simple example of using destructuring assignment to create variables for an object's properties:

```js
const car = {
  make: 'Tesla',
  model: 'Model S',
  year: 2020
};

let {make, year} = car;

console.log(make, year);  //=>  "Tesla"  2020
```

We can also use destructuring assignment to destructure parameters. Accordingly, it's common to destructure the `props` object passed to a Function Component.

Using destructuring, the `Person` component refactors to:

```jsx
function Person({ name, age, handleRaise }) {
  return (
    <div>
      <p>First: {name.first}</p>
      <p>Last: {name.last}</p>
      <p>Age: {age}</p>
      <button onClick={() => handleRaise(name, 9999)}>Give Raise!</button>
    </div>
  );
}
```

As you can see, the advantage is more concise code in the component's function.

Be sure to check [the docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) to learn more about destructuring objects and arrays!

### Using Props in "React To-Do"

Currently in "React To-Do", the `<ToDoList>` component is rendering two hard-coded `<ToDoListItem>` components - this isn't very useful.

Instead, we typically would be passing actual data down via props...

Let's refactor "React To-Do" so that:

1. **App.js** defines a `todos` array of strings representing the to-dos.
2. Pass the `todos` array to the `<ToDoList>` component as a prop.
3. Refactor **ToDoList.jsx** to accept props.
4. Use React Developer Tools to verify the prop in `<ToDoList>`.
5. Create and render a `<ToDoListItem>` component for each element (to-do) in the `todos` array.
6. Pass each "todo" string as a prop to the `<ToDoListItem>`.
7. Refactor the `<ToDoListItem>` component to destructure the `todo` prop and render it instead of the "To Do Item" placeholder text.

#### 1. Define a `todos` array in **App.js**:

We can define the array outside of or within the function...

```jsx
// App.js
import ToDoList from "./ToDoList";

// Add the todos array
const todos = [
  'Have Fun',
  'Learn React',
  'Learn the MERN-Stack'
];

export default function App() {
```

> 👀 If we were to define the `todos` array within the Function Component, it would be "reset" (reassigned) every time the component rendered!

#### 2. Pass the `todos` array to the `<ToDoList>` component as a prop:

```jsx
export default function App() {
  return (
    <div className="App">
      <h1>React To-Do</h1>
      {/* Pass todos as a prop */}
      <ToDoList todos={todos} />
    </div>
  );
}
```

The name of the prop, `todos`, can be anything you want (it does not have to match the value being assigned).

> 👀 Comments can be added within JSX by using the inline/multi-line syntax (`/* comment */`) wrapped with curly braces. 

#### 3. Refactor **ToDoList.jsx** to accept props:

Now that `<ToDoList>` is being passed a prop, it will need to be able to access it.

As previously discussed, Function Components need to define a parameter that by convention is named `props`:

```jsx
export default function ToDoList(props) {
  return (
    <ul>
      <ToDoListItem />
      <ToDoListItem />
    </ul>
  );
}
```

#### 4. Use React Developer Tools to verify the prop in `<ToDoList>`

Open React Developer Tools and verify that the array has been passed!

<img src="https://i.imgur.com/FXzMPfe.png">

#### 👉 You Do - Destructuring (1 minute)

- Destructure the `props` object in the parameter list of **ToDoList.jsx**.

  > Hint: The name of the prop to destructure is `todos`.

#### 5. Create and render a `<ToDoListItem>` component for each element (the to-do string) in the `todos` array

Our goal is to create and render a `<ToDoListItem>` component for each string in the `todos` array.

<details>
<summary>❓ What's the best array iterator method for <strong>transforming</strong> the elements of a source array into a new array?</summary>
<hr>

**<code>Array.prototype.map</code>**

<hr>
</details>

Here's one approach:

```jsx
export default function ToDoList({ todos }) {
  // Create an array of <ToDoListItem> components
  const toDoListItems = todos.map(t => <ToDoListItem />);
  return (
    <ul>
      {toDoListItems}
    </ul>
  );
}
```

The above approach is clean and it works.  However, since calling the `map()` method is a JS expression that results in an array, it's possible to perform the mapping within the JSX like this:

```jsx
export default function ToDoList({ todos }) {
  return (
    <ul>
      {todos.map(t => <ToDoListItem />)}
    </ul>
  );
}
```

Both approaches are acceptable.

#### 6. Pass each "todo" string as a prop to the `<ToDoListItem>`

#### 👉 You Do - Pass a `todo` Prop (1 minute)

- From `<ToDoList>`, pass each "todo" string as a prop named `todo` to each `<ToDoListItem>`.

  > Hint: In the mapping, the `t` parameter is the "todo" string

- Use React Developer Tools to verify:

  <img src="https://i.imgur.com/Zqf0Mpb.png">

#### 7. Refactor the `<ToDoListItem>` component to destructure the `todo` prop and render it instead of the "To Do Item" placeholder text

#### 👉 You Do - More Prop Destructuring (1 minute)

- You got this!

Nice!

<img src="https://i.imgur.com/gcD27dk.png">

## 7. Properly Rendering Arrays of Components

Even though the array of `<ToDoListItem>` components is rendering fine, the Console shows the following warning:

<img src="https://i.imgur.com/HrUWSAD.png">

Whenever an array of components is rendered, React wants a special `key` prop added to each component so that it can more efficiently track changes when re-rendering.

The value assigned to the `key` prop must be unique among the array of components being rendered.

Since the user might enter the same To Do string, we can resort to using the index of the iteration:

```jsx
export default function ToDoList({ todos }) {
  return (
    <ul>
      {todos.map((t, idx) => (
        <ToDoListItem todo={t} key={idx} />
      ))}
    </ul>
  );
}
```

In this case, we are using the index of iteration as the `key`'s value because we can't guarantee that the to-do strings would be unique.  However, if the data, for example, had an `id`, or another unique property, you should assign that value to the `key` instead.

> 👀 The `key` prop is internal to React and cannot be accessed by the component it's being passed to.

## 8. Props for React Elements

<details>
<summary>
❓ What are React Elements?
</summary>
<hr>

**React Elements are React's built-in components that emit DOM elements into the page.**

<hr>
</details>

Many props provide the same purpose as their corresponding HTML attributes.

For example, if you wanted to assign an `id` to a `<div>`:

```jsx
<div id="board">
  {/* contents of the board */}
</div>
```

However, some props have [differences as compared to their HTML equivalents](https://reactjs.org/docs/dom-elements.html#differences-in-attributes).

For example, we can style React Elements using two props similar to their HTML counterparts:

- **`className`**: Works like the HTML `class` attribute, simply named differently.
- **`style`**: Performs styling using the HTML `style` attribute, but must be passed an object.

## 9. Intro to Styling React Elements

<details>
<summary>❓ Only React Elements can be styled, not user-defined components - why?
</summary>
<hr>
User-defined components do not actually find their way into the DOM, only React Elements do.  For example, you would never see a <code>&lt;ToDoList&gt;</code> tag in the DOM 🙂
<hr>
</details>

<br>
Let's take a look at the basics of styling in React...

### Including CSS Stylesheets in a React App

CSS stylesheets can be included in a React app by simply importing them as shown in **App.js**:

<code>
import "./styles.css";
</code>

<br>

This is only made possible by the tooling, in this case, [Webpack](https://webpack.js.org/), has been configured.

When imported as shown above, all defined CSS rules will be included "globally".

For example, let's create a **ToDoListItem.css** stylesheet in the "React To-Do" project:

<img src="https://i.imgur.com/1SeQ8k7.png">

Next, using the same syntax as used in **App.js**, let's import **ToDoListItem.css** in **ToDoListItem.jsx**:

```jsx
// ToDoListItem.jsx
// Import the styles - making them available globally 

import "./ToDoListItem.css";
``` 

Again, importing a stylesheet includes its styles **globally** - it does not matter which component module the stylesheet is imported in. Also, it does matter not how many times the same stylesheet is imported, its styles will only be bundled in the resulting global CSS once.

<details>
<summary>
❓ Why bother creating stylesheets for components since we can just put all of the styles in a single stylesheet like <code>styles.css</code>?
</summary>
<hr>

It's a great way to organize CSS rules that apply only to a given component!

Whereas <code>styles.css</code> is a great place for general, application-wide CSS.

<hr>
</details>

### Styling With the `className` Prop

Note the outer `<div>` in the `<App>` component:

```jsx
export default function App() {
  return (
    <div className="App">
      <h1>React To-Do</h1>
      <ToDoList todos={todos} />
    </div>
  );
}
```

The `className` prop is used to assign a CSS class or classes to a React Element.

`className` is used instead of since `class` because it's a reserved word in the JS language. So React uses  `className` instead which just happens to be the same property name used on DOM elements. 

If you accidentally use a prop of `class` instead of `className`, the component will still render as expected, however, a warning will appear in the Console.

Let's add some CSS rules within **ToDoListItem.css**:

```css
.ToDoListItem {
  margin: 4vmin;
  padding: 2vmin;
  border: 1vmin solid purple;
  list-style: none;
  font-size: 6vmin;
}
```

<details>
<summary>❓ Why are we defining a class named <code>ToDoListItem</code> instead of using a simpler name such as <code>list</code>?
</summary>
<hr>

<strong>To prevent name collisions between classes defined elsewhere.</strong>

<hr>
</details>

Finally, let's add the `ToDoListItem` CSS class to the `<li>` React Element in **ToDoListItem.jsx**:

```jsx
export default function ToDoListItem({ todo }) {
  return (
    <li className="ToDoListItem">{todo}</li>
```

That's better!

<img src="https://i.imgur.com/PMm3UpT.png">

> 👀 Tip:  We don't have to assign a simple string to `className`.  We can compute and assign CSS class name(s) dynamically by using any JS expression within curly braces - ternary expressions, template literals, etc.!

#### 👉 You Do - Use Another Stylesheet (5 minutes)

Although the list is looking better, notice that the it's slightly shifted to the right.  This is because HTML `<ul>` elements have some left padding by default.

1. Create a new stylesheet for the `<ToDoList>` component following the same conventions used above.

2. Import the new stylesheet into **ToDoList.jsx**.

3. In the stylesheet, define a CSS class that sets `padding-left` to `0`.

4. Apply that class to the `<ul>` React Element.

### Styling Using the `style` Prop

The use of the `className` prop is generally the go to for styling, however, in cases where individual CSS property values might change with every render, the `style` prop provides maximum flexibility for highly dynamic styling!

The `style` prop in React differs from its HTML counterpart in that it must be assigned a **JS object** instead of a string value.

To demo its use, let's say we want to alternate the background color of each To Do based on whether its index is odd or even.

So the next thing we need to ask ourselves is:<br>**_How will each `<ToDoListItem>` component know if its odd or even?_**<br>Well, we're certainly going to have to pass an additional prop from its parent, `<ToDoList>`.

Further, we have two options, we can pass the actual index of the iteration or pass a computed prop like `isOdd`.

The first option, passing the index, provides a bit more flexibility because maybe we'll want to use it for other purposes, like displaying the number of the To Do.

#### 👉 You Do - Pass the Index of the Iteration (2 minutes)

1. Pass the index of the map iteration (`idx` parameter) to each `<ToDoListItem>` component using a prop named `index`.

2. In **ToDoListItem.jsx**, destructure the `index` prop being passed to it.

<hr>

Now let's use the `style` prop, assigning it an object literal to style the background color of the `<ul>`:

```jsx
export default function ToDoListItem({ todo, index }) {
  return (
    <li
      className="ToDoListItem"
      style={{
        backgroundColor: index % 2 ? "lavender" : "plum"
      }}
    >
      {todo}
    </li>
  );
}
```

Of course, you can use any named color, hex code, or `rgba()` value you wish - just be sure to quote it. Also, any numeric value assigned to a CSS property uses `px` as its unit by default.

<img src="https://i.imgur.com/CqKVnzc.png">

Using Chrome DevTools confirms that the `style` prop results in a `style` attribute being added to the DOM elements.

### Styling Using **CSS Modules**

**CSS Modules** provide an alternative to importing stylesheets the `way we have done thus far.

Classes defined in CSS Modules are dedicated to the component they are imported within, thus they have the advantage of avoiding name collisions.

However, they are not as flexible because they only work with class selectors.

Read [this article](https://create-react-app.dev/docs/adding-a-css-modules-stylesheet/) to learn more.

## Updated **Fundamentals of React** Chart

Before wrapping up with the Essential Questions, let's review the following updates to the [Fundamentals of React Chart](./react-fundamentals.md)...

| React Fundamental | Summary |
|---|---|
| ... | ... |
| [JSX](https://reactjs.org/docs/introducing-jsx.html) | A syntax extension to JS that looks like HTML and makes defining UIs more intuitive vs. pure JS.JSX emits text in the page when a JS expression is surrounded with curly braces<br><code>&LT;div>{/* JS Expression */}&LT;/div></code>.<br><br>JSX transpiles into a function call that returns a JS object, thus, JSX can be assigned to variables, passed as arguments to functions, etc.<br><br>JSX can render an array of components, however, each component needs a `key` prop with a unique value.<br><code>const catList = cats.map(c => &LT;div key={cat.id}>{cat.name}&LT;/div>);</code>. |
| ... | ... |
| Props | Props are used to pass information (any JS expression) to a child component.<br><br>Function Components are passed a `props` object as an argument.Props should never be updated - consider them immutable.<br><br>React Elements can be passed props that correspond to HTML attributes, e.g., `id`, `placeholder`, `pattern`, etc.  However, some are named or used slightly differently. |
| Styling | Only React Elements such as <code>&LT;div></code>, <code>&LT;form></code>, etc. can be styled because user-defined components aren't rendered to the DOM.<br><br>The `className` prop is used to assign classes and may be a JS expression resulting in a string of class name(s).<br><br>The `style` prop is used when styling needs to be computed each time the component renders and must be assigned a JS object with keys representing the camelCased names of CSS properties. |

## 10. ❓ Essential Questions (3 mins)

<details>
<summary>
(1) True or False: JSX provides a clear, declarative approach to defining user interfaces.
</summary>
<br>

<strong>True</strong>

<hr>
</details>

<details>
<summary>
(2) True or False: React Elements are built-in components that become actual HTML elements in the page's DOM.
</summary>
<br>

<strong>True</strong>

<hr>
</details>

<details>
<summary>
(3) Information is passed down through the component hierarchy using _______.
</summary>
<br>

<strong>Props</strong>

<br>
</details>


<hr>

```jsx
function ListItem({ item, index }) {
  index = index + 1;
  return (
    <div>{index}: {item}</div>
  );
}
```
<details>
<summary>
(4) What is wrong with the above code?
</summary>
<br>

<strong>Props such as</strong> <code>index</code> <strong>are immutable - we don't update them.</strong>

<br>
</details>


<hr>

```jsx
const colors = ['red', 'green', 'blue'];

function ColorList() {
  return colors.map(c => <div>{c}</div>);
}
```
<details>
<summary>
(5) The above <code>&lt;ColorList&gt;</code> component will render as expected, however, a warning will appear in the Console - why?
</summary>
<br>

<strong>Components rendered as an array need a unique</strong> <code>key</code> <strong>prop.</strong> 

<br>
</details>


<hr>

```jsx
function BookItem({ book }) {
  return (
    <article class="BookItem">
      <div>Title - {book.title}</div>
      <div>Author - {book.author}</div>
    </article>
  );
}
```
<details>
<summary>
(6) The above <code>&lt;BookItem&gt;</code> component will render as expected, however, a warning will appear in the Console - why?
</summary>
<br>

<strong>The </strong><code>class</code> <strong>prop should be</strong> <code>className</code><strong>.</strong>

<hr>
</details>

<br>

## 11. 💪 Bonus Exercise - Display the To Do Number

Prior to beginning the next React lesson, do your best to:

1. Number each To Do sequentially - make it one-based 🙂

2. Style each To Do so that they look something like this:

    <img src="https://i.imgur.com/xlpHy55.png">
<details>
<summary> <strong>Hint</strong> </summary>
One word - flexbox!
</details>
<br>

## References

- [React Docs - Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)

- [React Docs - JSX In Depth](https://reactjs.org/docs/jsx-in-depth.html)

- [Destructuring Assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

<!-- {% endraw %} -->



<img src="https://i.imgur.com/pg98OTd.png">

# React Dev Skills Lab - Part 2

## Intro

Now that you know quite a bit about JSX, props and how to style React Elements, time to apply your new knowledge by continuing to build the React Dev Skills app.

##### This lab, combined with Parts 1, 3 & 4 is a Deliverable

## Exercises

1. Open your "react-dev-skills" sandbox that you created in Part 1.

2. Add a `skills` array like the following above `<App>`:

    ```jsx
    const skills = [
      { name: "HTML", level: 5 },
      { name: "CSS", level: 3 },
      { name: "JavaScript", level: 4 },
      { name: "Python", level: 2 },
    ];

    export default function App() {
    ```

3. Refactor the code so that the renders the "skill" objects similar to the following:

    <img src="https://i.imgur.com/z1ZMjrG.png">

    > Feel free to style different colors, however, layout should be similar.


## Hints

<details><summary>Updated styles.css</summary>
<p>

<pre><code>
.App {
  font-family: sans-serif;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.padding-0 {
  padding: 0;
}

.teal-text {
  color: teal;
}
</code></pre>

</p>
</details>

<details><summary>Example SkillListItem.css</summary>
<p>

<pre><code>
.SkillListItem {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0.5rem;
  padding: 0.2rem 0.6rem;
  border: 0.2rem solid coral;
  border-radius: 0.3rem;
  list-style: none;
  color: teal;
  font-size: 1rem;
  font-weight: bold;
}

.SkillListItem > .level {
  margin-left: 5rem;
  padding: 0.3rem 0.8rem;
  color: white;
  background-color: teal;
  border-radius: 0.8rem;
  font-size: 0.8rem;
  font-weight: normal;
}
</code></pre>

</p>
</details>

<details><summary>Example NewSkillForm.css</summary>
<p>

<pre><code>
.NewSkillForm {
  display: grid;
  grid-template-columns: auto auto;
  gap: 1rem;
  align-items: center;
  font-size: 1rem;
  font-weight: bold;
  color: teal;
  text-align: left;
  border: 0.2rem solid coral;
  border-radius: 0.3rem;
  padding: 1rem;
}

.NewSkillForm > input,
.NewSkillForm > select {
  font-size: 1rem;
  font-weight: bold;
  color: teal;
  padding: 0.2rem;
  border: 0.2rem solid coral;
  border-radius: 0.3rem;
  outline: none;
}

.NewSkillForm > button {
  grid-column: span 2;
  font-size: 1rem;
  font-weight: bold;
  color: white;
  padding: 0.2rem;
  background-color: teal;
  border: 0.2rem solid teal;
  border-radius: 0.3rem;
}
</code></pre>

</p>
</details>

## This lab combined with Parts 1, 3 & 4 is a Deliverable




<img src="https://i.imgur.com/fx2orT2.png">

# Floor Plan Lab

## Intro

In the _Intro to JSX_ lesson, you saw the following React basics:

- How to define components as functions
- How to return a function component's UI defined using JSX
- How to pass props to components
- How to access the properties on props within a component

## Setup

Please complete this lab in a React [CodeSandbox](https://codesandbox.io) named "Floor Plan".

## Minimum Requirements

1. Define each component in its own file. The naming convention to use for a component's file is UpperCamelCase, for example, a `<CodeSandbox>` component's file would be named `CodeSandbox.js` (`CodeSandbox.jsx` also works).

2. Export each component from its module. For example:

	```js
	// CodeSandbox.js
	
	export default function CodeSandbox(props) {
	  return (
	    <div>
	      <h1>CodeSandbox</h1>
	    </div>
	  );
	}
	```

3. Define the following components as functions and code them such that they fulfill their responsibilities:

	| Component | Responsibilities |
	|---|---|
	| `<FloorPlan>` | Rendered by `<App>`.<br>Renders the following components:<br>- A `<Kitchen>` component<br>- A `<LivingRoom>` component<br>- Three `<Bedroom>` components<br>- Two `<Bath>` components<br>**Render the components in any order you wish to make the floor plan more interesting.** |
	| `<Kitchen>` | Renders the text "Kitchen" and the following components:<br>- A `<Oven>` component<br>- A `<Sink>` component |
	| `<LivingRoom>` | Renders the text "Living Room" |
	| `<Bedroom>` | Accepts a `bedNum` prop and renders the text "Bedroom [bedNum]" (substituting the value of the `bedNum` prop) |
	| `<Bath>` | Accepts a `size` prop and renders the text "[size] Bath", i.e., "Half Bath", "Full Bath" |
	| `<Oven>` | Renders the text "Oven" |
	| `<Sink>` | Renders the text "Sink" |

Add the following CSS inside of **styles.css** to style each component's wrapping `<div>` to make it easier to visualize the components:

```css
div {
  border: 1px solid grey;
  margin: 5px;
  padding: 5px;
}
```

With the minimum requirements complete, the output should resemble:

<img src="https://i.imgur.com/K8eVbuC.png">

#### Hints

- If a component accepts a prop, that prop must be passed to it by the component that renders it, in other words, parent components pass props to their children components.

## Bonus

Style the components to make the output look like a floor plan:

<img src="https://i.imgur.com/AHq1tCF.png">

#### Hints

- Use `className` and/or `id` on React Elements (`<div>`, `<p>`, `<span>`, etc.) to apply CSS styling using CSS rules in the **styles.css** module.

- Styling the `<FloorPlan>` component as a CSS Grid is a great way to layout its children (grid items).

- Use props being passed in to generate a unique `id` on an element that can be used to target that element for custom styling. For example:

	```js
	<div className='bedroom' id={`bed-${props.bedNum}`}>
	```
	Would result in this `<Bedroom>` having a wrapping `<div>` like:
	
	```js
	<div class="bedroom" id="bed-2">
	```
	if it was rendered as:
	
	```js
	<Bedroom bedNum={2} />
	```

## Not a Deliverable

This lab is not a deliverable.

## Solution

Don't peek unless you HAVE to:

[Possible solution](https://codesandbox.io/s/floor-plan-solution-fn0v9m?file=/src/App.js)


<img src="https://i.imgur.com/VunmGEq.jpg">

# React Fundamentals - Using and Updating State

## Learning Objectives

|Students Will Be Able To:|
|---|
| Add State to a Function Component |
| Pass State to Children Components |
| Update State |
| Explain Why Not All Data Needs to be State |

## Road Map

1. Setup
2. Previous Lesson's Bonus Challenge
3. Review of State
4. Intro to React Hooks
5. Add State to a Function Component Using the `useState` Hook
6. Using the Value of the State
7. Updating State Using the `useState` Hook's Setter Function
8. More About State
9. Not All Data Needs to Be State
10. React Fundamentals Chart Update
11. Essential Questions
12. Further Study

## 1. Setup

This lesson continues to build upon the "React To-Do" sandbox we've been working with during the last couple of lessons in [codesandbox.io](https://codesandbox.io/):

<img src="https://i.imgur.com/BiuKtr9.png">

## 2. Previous Lesson's Bonus Challenge

If you didn't have a chance to complete the challenge exercise of numbering the to-dos, make the following changes:

1. Add a `<div>` to `<ToDoListItem>` before the `{todo}`:

    ```jsx
    <div className="flex-ctr-ctr">{index + 1}</div>
    {todo}
    ```

2. Add that general purpose `flex-ctr-ctr` class to **styles.css**:

    ```css
    .flex-ctr-ctr {
      display: flex;
      justify-content: center;
      align-items: center;
    }
    ```

3. Update **ToDoListItem.css** to the following:

    ```css
    .ToDoListItem {
      display: flex;
      justify-content: flex-start;  <!-- default -->
      align-items: center;
      margin: 4vmin;
      padding: 2vmin;
      border: 1vmin solid purple;
      list-style: none;
      font-size: 6vmin;
    }

    .ToDoListItem div {
      width: 8vmin;
      height: 8vmin;
      margin-right: 4vmin;
      background-color: black;
      color: white;
      border-radius: 50%;
    }
    ```

## 3. Review of State

Just in case you haven't gotten it tattooed yet...

#### State is the data a program needs to "remember" while it's running.

State, the facts 😁:

- State is the single-source of truth of an application.
- State changes due to user interaction or when other events occur such as when a timer ticks.
- When state is updated, the user interface needs to be re-rendered to reflect the new state of the program - this fundamental concept might sound familiar from Unit 1.
- React state is immutable, this means that it cannot be changed, you cannot change the value of a state object or change the value of its properties unless you use the setState function created with the given state object when you use the 'useState' function. When you update state using a set state method, you are in fact creating a new version of that state to be used instead of the older version, so think of set state more as creating an updated version of your state object and not that it is updating the existing state object.

<details>
<summary>
❓ What state do we have in "React To Do"?
</summary>
<br>

The <code>todos</code> array

<hr>
</details>
<br>

> 👀 In a React app, UI-related state is used to make a user interface render dynamically. For example, if we wanted to hide/show a `<PlayerDetails>` component, we would use a piece of state like `showPlayerDetails` to track whether or not to render the component.

<br>

## 4. Intro to React Hooks

Hooks were added to React in version 16.8.

**Hooks allow components defined as functions to perform functionality that used to require that the components be defined as a class.**

Consider what happens when React renders a Function Component:

1. React calls the function passing to it props as an argument.
2. The function runs and ultimately returns its UI (the JSX).
3. React uses the object returned by the JSX to render the UI.

Now consider that when a function finishes running and returns, its scope is destroyed, thus any data held in variables is forgotten!

So, how can a Function Component remember state?

Some of you might be thinking to yourselves - _What about using closures?_

Exactly!  Indeed, it's closures that enable hooks to remember state, as well as implement other stateful behavior!

Some facts about React hooks:

- Hooks are a way to add reusable stateful behavior to Function Components, not class-based components.
- Hooks themselves are functions and must be named beginning with the word `use`, e.g., `useState`.
- Hooks must be called at the top-level of the component's function and cannot be called conditionally. For example, a hook cannot be called within an `if` statement.  Basically, React must be able to depend on every hook being called in the exact same order every time the component renders (is invoked by React).
- It's possible to create custom hooks if the built-in hooks don't satisfy our needs, in fact, lots of custom hooks are just a google away!

## 5. Add State to a Function Component Using the `useState` Hook

React's [useState Hook](https://reactjs.org/docs/hooks-state.html) is used to remember and update state in a Function Component.

Let's briefly review the doc linked to above.  As you can see, the Function Component is more concise and likely easier to reason about.

Also, Function Components eliminate having to worry about the proper binding of `this`, which definitely becomes an issue when a Class Component needs to invoke an event handler.

### Adding the `todos` Array as State

Although the current `todos` array in **App.js** can be updated using `push`, etc., a very important thing **won't** happen if we do.

<details>
<summary>
❓ What won't happen?
</summary>
<hr>

<strong>A re-render will not be triggered!</strong>

<hr>
</details>

Before state can be added to a component, we need to import the `useState` named export from the `React` library: 

```jsx
// App.js
import { useState } from "react";
```

The above syntax is used to import **named** exports.  JS modules can have any number of **named** exports and only a single **default** export.

Next, inside of the Function Component we invoke `useState` and provide the initial value of the state as an argument:

```jsx
export default function App() {
  const [todos, setTodos] = useState([
    "Have Fun",
    "Learn React",
    "Learn the MERN-Stack"
  ]);
  ...
```

> 👀 The initial value argument is only used to set the state's value when the component is rendered for the **first time**

The `useState` hook/function always returns an array with two elements where:

- The 1st element is the current value of the state
- The 2nd element is the setter function used to update the state's value

<details>
<summary>
❓ So what's that? --> <code>[todos, setTodos] = ...</code>
</summary>
<br>

Yes, that's <a href="https://javascript.info/destructuring-assignment#array-destructuring">array destructuring assignment</a>!
<br>
The call to <code>useState()</code> always returns an array with two elements and now we have two variables we can use to easily access those elements.

<hr>
</details>

## 6. Using the Value of the State

Did you notice that the To-Dos have continued to render just fine?

Using the value of the state is as simple as using the first element returned by `useState()`, which in our case, has been destructured into a variable named `todos` - and that variable (`todos`) continues to be passed to the `<ToDoList>` components as a prop.

We are free to use the variable holding the state's value any way we want, pass it as a prop, render it, etc.

However, we **do not** modify the state's value by reassigning to the state variable.  Instead, updating state is the job of the setter function...

## 7. Updating State Using the `useState` Hook's Setter Function

When we invoked `useState()`, we destructured the returned array naming the second element `setTodos` because it is a setter function used to update the `todos` state to whatever we pass to that setter function.

By convention, we always name the setter function by pre-pending the word `set` to the name we assigned to the state value variable and adjusting the camelCasing.

For example, if you wanted to track the state of the board in a Tic-Tac-Toe app:

```jsx
export default function App() {
  const [board, setBoard] = useState([0, 0, 0, 0, 0, 0, 0, 0, 0]);
  ...
}
```

<details>
<summary>
❓ What line of code could you use to define state to track whose turn it is in a Tic-Tac-Toe app?
</summary>
<br>

<pre><code>
// 1 represents player 1; -1 is player 2

const [turn, setTurn] = useState(1);
</code></pre>

<hr>
</details>

We'll wait until the next lesson to update `todos`. For now, we'll practice with a different piece of state... 

### 👉 You Do - Add a New Piece of State (1 min)

- Add a `showTodos` state to "React To-Do" and initialize it to `true`;

### Rendering Conditionally

Now we can use the `showTodos` state to conditionally render the `<ToDoList>` component:

```jsx
export default function App() {
  ...

  return (
    <div className="App">
      <h1>React To-Do</h1>
      {/* Conditionally render ToDoList */}
      {showTodos && <ToDoList todos={todos} />}
    </div>
  );
}
```

We told you in Unit 1 how handy those logical operators like `&&` would be!  `&&` is used extensively in React to conditionally render a component or not.

<details>
<summary>
❓ What kind of JS expression would we use to render one of two components?
</summary>
<br>

A <strong>ternary expression</strong>!  For example:
<pre><code>export default function App() {
  const [user, setUser] = useState(getUser());

  return (
    &#60;div className="App"&#62;
      {user ? &#60;HomePage /&#62; : &#60;LoginPage /&#62;}
    &#60;/div&#62;
  );
}</code></pre>

<hr>
</details>

Cool, the To-Dos are still being rendered because `showTodos` is `true`.

Let's use React Developer Tools to update the state:

<img src="https://i.imgur.com/sGHlL3A.png">

Toggling between `true`/`false` will result in `<ToDoList>` being rendered or not - very cool!

> 👀 React Developer Tools have no way of knowing what we named our state - all it knows is the order in which the `useState` hooks were called.

### Replace, Don't Mutate State

Invoking the setter function will **replace** the value of the state.

Replacing primitive data types, e.g., numbers, strings & booleans, is gravy.  However, we should always **replace** objects/arrays (reference types), as well.

For example, in the next lesson we will be adding new to-dos to the `todos` state array. When doing so, we will not use the `push` method, which mutates the array instead of replacing it with a new array.

The modern approach is to use [spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) for creating new arrays and objects from existing ones.

Here's a preview of how we might add a new to-do:

```jsx
function handleAddTodo(todo) {
  // Create a new array that includes the new todo
  const newTodos = [...todos, todo];
  // Update state and re-render
  setTodos(newTodos);
}
```

The `...` is the spread syntax and is used similarly to "spread" out the existing properties in objects.

The important thing to remember here though is to replace objects/arrays, not mutate them!

### Updating State is an Asynchronous Operation

Calling the `useState` hook's setter function is an asynchronous operation.

This means that any synchronous code following the call to the setter will be accessing the "current" value of the state variable, not the updated value.

The state's value won't actually be updated until the subsequent render.

[This sandbox](https://codesandbox.io/s/updating-state-is-asynchronous-k6jbv?file=/src/App.js) demonstrates this asynchronous behavior.

### Triggering a Re-Render

**A component will re-render when a state's value is updated by calling its setter function!**

<details>
<summary>
❓ When a component renders its child components in its JSX, what do those child components do?
</summary>
<hr>

<strong>They render their children and so on...</strong>

<hr>
</details>

## 8. More About State

### State/Information Can Only Be Passed Down

<details>
<summary>
❓ State can only be passed DOWN the component hierarchy via _______.
</summary>
<hr>

<strong>Props</strong>

<hr>
</details>

<img src="https://i.imgur.com/6CT8foa.jpg">

Typically, you'll find that most state needs to be defined in the `<App>` component.

However, we can avoid unnecessary "prop drilling" by moving state to the nearest parent component in common with the other components that need to use that state.

<details>
<summary>
❓ If a piece of state needed to be used only by the green and black components, where should the state be defined?
</summary>
<hr>

In the <strong>green component</strong>

<hr>
</details>

<details>
<summary>
❓ If a piece of state needed to be used by the dark blue and light blue components, where would the state be defined?
</summary>
<hr>

In the <strong>top (yellow) component</strong>, which typically would be <code>&#60;App&#62;</code>.

<hr>
</details>

### Categorizing State

We can think of there being three categories of state:

- Data-related state
- UI-related state
- Computed state

### Data-Related State

Data-related state holds the data that the application is about. For example, in "React To-Do", it's the `todos` array.

It's common to define all state that represents data first in `<App>`.  This makes it possible to pass that state to any component that needs it.

Then later, the app can be refactored to move state down the hierarchy to avoid having to pass the same prop through multiple components that don't need it and are simply passing the prop down the hierarchy to its ultimate destination.  This is known in React as "Prop Drilling".

"Prop Drilling" is the way React is designed to work, however, it can be a bit tedious and has led to alternative approaches to delivering state directly to the component that needs it vs. being passed down the hierarchy via props.  Some alternative approaches are listed in the Further Study section.

### UI-Related State

UI-related state is state used to control the dynamic rendering of the UI. For example, you click an [EDIT] button and an `<input>` is displayed instead of a `<div>`.

<details>
<summary>
❓ We've actually defined UI-related state already. What's the name of the variable holding the UI-related state?
</summary>
<br>

<strong><code>showTodos</code></strong>

<hr>
</details>

UI-related state is usually defined in the component that uses it and since no other component would likely need to access its value.

However, if for some reason the UI-related state needed to be accessed higher up in the hierarchy, then it would need to be defined high enough to be accessed by all components that need to access it.

### Computed State

Some state has its value computed from other state.

A good example of computed state would be `winner` state in the game of Tic-Tac-Toe.

<details>
<summary>
❓ What state would be used to compute <code>winner</code>?
</summary>
<br>

**`board`**

<hr>
</details>

Since computed state is derived from other state, computed state does NOT have to be defined using `useState` (see example below).

### How Many State Variables Can We Use?

A Function Component can call `useState` as many times as necessary. For example:

```jsx
export default function App() {
  const [board, setBoard] = useState([0, 0, 0, 0, 0, 0, 0, 0, 0]);
  const [turn, setTurn] = useState(1);
  // winner is computed using board state
  const winner = getWinner(board);
  ...
}
```

However, it's not always necessary to break up state into multiple `useState()` calls because a single state can be a JS object which would hold any number of values in its properties.

For example, if we needed to hold the state for a sign up form, we can do this:

```jsx
export default function SignUpPage() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    password: '',
    pwConfirm: '',
  });
}
```

Instead of this:

```jsx
export default function SignUpPage() {
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [pwConfirm, setPwConfirm] = useState('');
}
```

Grouping related state can result in less code required to update that state (fewer setter functions) and also makes it easier to send that state to the backend.

## 9. Not All Data Needs to Be State

Not all data needs to be defined as state.

Consider the Tic-Tac-Toe app where we might use a `WINNING_COMBOS` array that held nested arrays with winning index patterns.

<details>
<summary>
❓ Why wouldn't <code>WINNING_COMBOS</code> need to be defined as state?
</summary>
<br>

<code>WINNING_COMBOS</code> is a constant lookup data structure that never changes. 

<hr>
</details>

> 👀 Only data that you want to cause a re-render when it changes should be defined as state.

### How to Persist Non-State Data

Since variables are forgotten after a function returns, how we do we persist non-state data?

It depends upon whether a component needs its own copy of that data or not...

#### Component Does **NOT** Need Its Own Copy of the Non-State Data

When there only needs to be one copy of some data because it can be shared by all components, we can simply define a variable outside of the Function Component.

For example:

```jsx
const WINNING_COMBOS = [
  [0, 1, 2],
  [3, 4, 5],
  [6, 7, 8],
  [0, 3, 6],
  [1, 4, 7],
  [2, 5, 8],
  [0, 4, 8],
  [2, 4, 6]
];

export default function App() {
  const [board, setBoard] = useState([0, 0, 0, 0, 0, 0, 0, 0, 0]);
  const [turn, setTurn] = useState(1);
  // winner is computed using board state
  const winner = getWinner(board);
  ...
}
```

#### Each Component Needs Its Own Copy of the Non-State Data

If a Function Component needs to remember its own copy of non-state data between renders, it **can't** define a variable in or outside of the function.

An example of this situation might be a list of components that each have their own timer created with `setInterval`.  It would be necessary for each component to remember the id of its timer so that it can `clearInterval` at some point. 

There is another hook for this scenario:  [useRef](https://reactjs.org/docs/hooks-reference.html#useref).

There's no need to cover it now, but it's good to know that the `useRef` hook allows a Function Component to remember non-state data between renders. Also, data remembered using a "ref" is mutable and can be updated without triggering a re-render.

## 10. React Fundamentals Chart Update

Yup, time to update our [React Fundamentals Chart](https://gist.github.com/jim-clark/cbc87fdf01c22f412737ca121ef70761) before wrapping up with the Essential Questions.

| React Fundamental | Summary |
|---|---|
| ... | ... |
| State | When a component's state is updated, the component re-renders.<br><br>Most state is data-related, i.e., related to the purpose of the application. However, a component can use UI-related state to control the dynamic rendering of its UI.<br><br>The `useState` hook is used to manage state in a Function Component.<br><br>Invoking `useState(<initial value of the state>)` returns an array whose first element is the state's current value and whose second element is a setter function used to update the state's value.<br><br>Only data that you want to cause a re-render when it changes should be defined as state. |

## 11. ❓ Essential Questions (2 mins)

<details>
<summary>
(1) In general, why were hooks added to React?
</summary>
<hr>

Hooks allow Function Components to "remember" state and implement stateful behavior that used to require Class Components.

<hr>
</details>

<details>
<summary>
(2) What React hook is used to manage state in a Function Component?
</summary>
<hr>

<strong><code>useState</code></strong>

<hr>
</details>

<details>
<summary>
(3) How do we update the value of state?
</summary>
<hr>

<strong>By calling the state's setter function.</strong>

<hr>
</details>

<details>
<summary>
(4) True or False:  Only data that you want to cause a re-render when it changes should be defined as state.
</summary>
<hr>

<strong>True</strong>

<hr>
</details>

## 12. Further Study

### Learn More About Hooks

To learn more about hooks, read [Introducing Hooks](https://reactjs.org/docs/hooks-intro.html) in the docs.

### Built-in Hooks and their use cases:

| Hook | Use Case |
|---|---|
|[`useState()`](https://reactjs.org/docs/hooks-reference.html#usestate)|Used to manage state in a Function Component.|
|[`useEffect()`](https://reactjs.org/docs/hooks-reference.html#useeffect)|Used to implement "side effects", e.g., fetching data, using timers, subscriptions, etc.<br>`useEffect()` implements the functionality of class components' `componentDidMount`, `componentDidUpdate` & `componentWillUnmount` with a single hook!|
|[`useRef()`](https://reactjs.org/docs/hooks-reference.html#useref)|In addition to how refs are used to access DOM elements in class components, `useRef()` can be used more generally to "remember" any non-state data that needs to be persisted between renders similar to how we use instance properties in class components. |
|[`useReducer()`](https://reactjs.org/docs/hooks-reference.html#usereducer)|An alternative to `useState()` for when the state is more complex.  It uses a reducer function and "actions" to update state - similar to how Redux does (but not as comprehensive).|
| Other built-in hooks|[`useContext()`](https://reactjs.org/docs/hooks-reference.html#usecontext)<br>[`useMemo()`](https://reactjs.org/docs/hooks-reference.html#usememo)<br>[and other less common hooks here...](https://reactjs.org/docs/hooks-reference.html#useimperativehandle)|

### Alternative State Management Approaches

Note that although there are alternatives to using the `useState` hook, be aware that there's a learning curve with each alternative and that no alternative should be considered until you have mastered the fundamentals of React.

Some alternatives to using `useState` are:

- [Redux](https://redux.js.org/) is a popular real-world state management alternative.  However, it requires quite a bit of setup and is overkill for most apps. Although still popular, Redux has been falling out of favor lately.

- React's [Context API](https://reactjs.org/docs/context.html) can be combined with the [useReducer hook](https://reactjs.org/docs/hooks-reference.html#usereducer) to provide a lighter-weight alternative to Redux.

- [MobX](https://mobx.js.org/README.html) is another popular alternative, like Redux, it's popularity has probably peeked.

## References

- [React Docs - Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)

- [React Docs - JSX In Depth](https://reactjs.org/docs/jsx-in-depth.html)


<img src="https://i.imgur.com/pg98OTd.png">

# React Dev Skills Lab - Part 3

## Intro

This lab will simply ask you to use the `useState` hook to add state to the React Dev Skills app.

Updating that state will be an exercise in part 4.

##### This lab, combined with Parts 1, 2 & 4 is a Deliverable

## Exercises

1. Open your "react-dev-skills" sandbox that you created in Part 1.

2. Use the `useState` hook to add a state value named `skills`.

3. Be sure to name the setter function according to the convention discussed in the lesson.

4. Initialize the state using the same array of skill objects used in part 2.

5. When finished, the skills should continue to be displayed without error:

    <img src="https://i.imgur.com/z1ZMjrG.png">

## This lab combined with Parts 1, 2 & 4 is a Deliverable



<img src="https://i.imgur.com/KBwhRtk.png">

# React "Students" Lab

## Intro

This lab will provide some practice doing the following:

- Creating a UI using a hierarchy of components
- Adding state to a function component with the `useState` hook.
- Passing data as props from a parent to a child component
- Mapping arrays of data into arrays of components

**This lab is a DELIVERABLE**

## Setup

Please complete this lab in a React [CodeSandbox](https://codesandbox.io) named "React Students".

## Minimum Requirements

**The layout and styling of the markup is left up to your discretion.**

1. Use the `useState` hook to add a `students` state value to the `<App>` component and initialize it with the following array of "student" data:

```js
[
  {
    name: 'Cait Yomorta',
    bio: 'Lorem ipsum, dolor sit amet consectetur adipisicing elit. Natus placeat nostrum explicabo? Voluptatibus expedita saepe officia optio, commodi totam ratione laudantium ipsum porro molestias, quasi nulla minus vitae laboriosam corrupti Delectus inventore explicabo est odit incidunt rem a recusandae eum pariatur. Aperiam doloremque blanditiis harum voluptate animi fugit beatae asperiores quo, dignissimos sed illum veniam eum accusantium nulla quod voluptatum',
    scores: [
      {
        date: '2018-02-08',
        score: 77
      },
      {
        date: '2018-04-22',
        score: 92
      },
      {
        date: '2018-09-15',
        score: 68
      }
    ]
  },
  {
    name: 'Holly Baird',
    bio: 'Eum molestiae explicabo deserunt, maiores quod eaque omnis tenetur vero ducimus, magnam autem! Quia facere quaerat eum repudiandae dolorum eligendi iure quae. Eos id possimus accusantium, earum animi modi hic.',
    scores: [
      {
        date: '2018-12-14',
        score: 88
      },
      {
        date: '2019-01-09',
        score: 79
      },
      {
        date: '2019-02-23',
        score: 91
      },
      {
        date: '2019-03-01',
        score: 95
      }
    ]
  },
  {
    name: 'Wes Mungia',
    bio: 'Repudiandae veritatis recusandae quidem tenetur impedit, numquam incidunt enim, adipisci id cupiditate asperiores nam perferendis. Facere odit laborum ipsum autem repellendus natus eius doloremque ullam perferendis. Enim repellendus ut veniam?',
    scores: [
      {
        date: '2018-10-11',
        score: 62
      },
      {
        date: '2018-11-24',
        score: 74
      },
      {
        date: '2018-12-19',
        score: 85
      }
    ]
  }
]
```

2. Code the `<App>` component's JSX to display a `<Student>` component for each student object in the `students` state.

3. Create and code a `<Student>` component that:

    - Accepts a student object as a prop.
    - Renders the student's `name` & `bio` properties.
    - Renders a `<Score>` component for each score object in the student's `scores` property.

4. Create and code the `<Score>` component so that it renders the score object's `date` & `score` properties.

#### This Lab is a Deliverable

As usual, please submit the link to your sandbox as directed.



<img src="https://i.imgur.com/VunmGEq.jpg">

# React Fundamentals - Handling Input and Events

## Learning Objectives

|Students Will Be Able To:|
|---|
| Handle Events in React |
| Optionally Pass Arguments to Event Handlers |
| Use "Controlled Inputs" in React |
| Prevent a `<form>` From Being Submitted to the Server |
| Properly Update Objects/Arrays in State |

## Road Map

- Setup
- Attaching Event Handlers Using Event Props
- Using "Controlled Inputs" in React
- Adding the New To-Do
- Using `<form>` React Elements
- Preventing a `<form>` From Being Submitted
- Validating Data In a `<form>`
- Using State to Handle Multiple Inputs
- The Keys to Programming in React
- Final Version of the Fundamentals of React Chart
- Essential Questions
- Further Study
- References

## Setup

This lesson will build upon the "React To-Do" sandbox we've been working with during the last couple of lessons in [codesandbox.io](https://codesandbox.io/):

<img src="https://i.imgur.com/EPPyLEw.png">

## Attaching Event Handlers Using Event Props

### Browser Events in React

**❓ What are some common browser events we've worked with during SEI so far?**

In case you need to be reminded, [here you go!](https://developer.mozilla.org/en-US/docs/Web/Events).

Like many things in React, event handling is a little different than what we are used to.

Let's see how...

### Connecting Handler Code to Events in React

In React, we do not add event listeners using JavaScript's `addEventListener` method.

Instead, we assign event handling functions to "event" props, e.g., `onClick`, on React Elements (`<div>`, `<p>`, etc.).

> Note: React supports any browser event you will ever need as documented by [this list of supported events](https://reactjs.org/docs/events.html#supported-events)

Let's start by adding a `<button>` to for hiding/showing the to-dos when clicked:

```jsx
return (
  <div className="App">
    <h1>React To-Do</h1>
    {/* Add  button below */}
    <button>{showTodos ? 'HIDE' : 'SHOW'}</button>
    ...
```

> Note that any type of React Element can respond to click events, not just buttons.

Now we can use the `onClick` prop to attach an event handler, **which must be a function (this is important)**:

```jsx
<button onClick={alert}>{showTodos ? 'HIDE' : 'SHOW'}</button>
```

We're just passing the built-in `alert` function as a baby step.  When the button is clicked, React's event system will invoke the provided function, passing to it an event object.

Our goal is to toggle the boolean `showTodos` state value.  We have two approaches we can take:

1. Invoke the existing `setShowTodos` setter function inline, or
2. Write a separate function and provide that to the `onClick`

Since we don't have any significant logic to perform, we'll use option 1 and use option 2 for adding to-dos later.

<details><summary>❓ Due to something important mentioned above, why won't the following approach work?</summary>
<p>

**We need to provide a function, not invoke a function.**

</p>
</details>

```jsx
<button onClick={setShowTodos(!showTodos)}>{showTodos ? 'HIDE' : 'SHOW'}</button>
```

### Passing Arguments to Event Handlers

So, what's the solution if we need to pass arguments to an event handler function?  Check this out:

```jsx
<button onClick={() => setShowTodos(!showTodos)}>{showTodos ? 'HIDE' : 'SHOW'}</button>
```

As you can see, the fix is to wrap the call to `setShowTodos` with a function - thanks to their conciseness, arrow functions are great for this purpose!

Toggle those to-dos!

### Event Handling Summary

- The names for event props are camelCased (`onClick`). In HTML, the attribute would be `onclick`. Here's the [list of events](https://facebook.github.io/react/docs/events.html#supported-events) supported by React.

- The JS expression (always within curly braces) assigned to an event prop must evaluate to a **function**. A function type, **not** a function call (unless that function call returns a function).

- React automatically implements event delegation and makes event handling more efficient in a React app by managing events internally - check out React's [Synthetic Event Object](https://reactjs.org/docs/events.html) to learn more.

## Using "Controlled Inputs" in React

### Adding New To-Dos

To add new to-dos, we could just add additional JSX to the `<App>` component.

However, a better approach would be to create a separate component responsible for inputting a new to-do...

#### 💪 Practice Exercise - Create a new `<NewToDoForm>` Component (5 minutes)

1. Create a `<NewToDoForm>` component in its own module (named according to best practices).

2. `<NewToDoForm>` should just render an `<h2>New To-Do</h2>` for now.

3. In **App.js** below the `<ToDoList>` component, render an `<hr />` followed by the `<NewToDoForm>` component like this:

  <img src="https://i.imgur.com/lHw9V7D.png">

### Forms in React Are Not Required

Forms are not required to wrap input elements in SPAs because we send data to the server using AJAX, not by submitting a form. In fact, we need to prevent forms from being submitted to the server because it will cause the page to reload which SPAs avoid.

However, we often still use forms in React for validation, layout/styling using CSS frameworks, etc.

We'll begin by adding a to-do without using a form. Then, we'll add a form later to perform validation and to learn how to prevent them from accidentally triggering a full-page refresh when submitted.

### Controlled Components (`<input>`)

In a typical HTML page, input elements such as `<input>`, `<textarea>` and `<select>`, maintain their own internal state.

However, handling input the "React way" is different...

  <img src="https://i.imgur.com/YcDo3iJ.png">

1. The value of an input, i.e., what is displayed, is maintained by our own state in the component.

2. When React renders the input, it overrides the input's internal `value` property by binding to the `value` prop.

3. Updating the input's state value requires assigning an event handler function to the `onChange` prop.


This scenario, is what React refers to as a [controlled component/input](https://reactjs.org/docs/forms.html#controlled-components).

### Adding a Controlled `<input>`

Let's add the following JSX to **NewToDoForm.jsx**:

```jsx
export default function NewToDoForm() {
  return (
    <>
      <h2>New To-Do</h2>
      <input placeholder="New To-Do" />
      <button>ADD TO-DO</button>
    </>
  );
}
```

> Reminder: React Elements have props such as `placeholder` that provide the functionality of their HTML attribute equivalents.

Now let's make it a controlled input by first adding state for the `<input>` as mentioned in bullet point number `1.` above.

#### 💪 Practice Exercise - Add `newTodo` State (3 minutes)

1. Use the `useState` hook to add state named `newTodo`.

    > Hint: Don't forget to import `useState`

2. Initialize `newTodo` to an empty string.

3. You know what to name the setter - right?

### The Key to Controlled Inputs:  `value` & `onChange` Props 

All controlled inputs must include the following two props:

- `value`: This prop is used to bind the state to the input's value (what is displayed).

- `onChange`: This event prop will call the provided callback function whenever the user types in the input. Within the callback, we need to update the state variable bound to `value`.

### Bind State to the `value` Prop

Let's start by binding the `newToDo` state you just defined to the `value` prop of the `<input>` in **NewToDoForm.jsx**:

```jsx
<input value={newTodo} placeholder="New To-Do" />
```

Easy peasy - to check it out, try initializing the state to something other than empty string.

### Handling the `onChange` Event

You just saw how the `<input>` displays the value of the state it is bound to using the `value` prop.

However, try typing in the input - nothing happens because we need to update the state as the user types.

Here's a simple way for now:

```jsx
export default function NewToDoForm() {
  const [newTodo, setNewTodo] = useState("");
  return (
    <>
      <h2>New To-Do</h2>
      <input
        value={newTodo}
        onChange={(evt) => setNewTodo(evt.target.value)}
        placeholder="New To-Do" />
      <button>ADD TO-DO</button>
    </>
  );
}
```

When React invokes the handler (function), it passes in an event object as an argument for which we defined a parameter, `evt`. Then, just like in vanilla JS, the event object can be used to access the input's internal value via `evt.target.value`.

### ❓ Review Questions

1. What is wrong with the following code?

    ```jsx
    <div onClick={setStateValue(newValue)}>Click Me!</div>
    ```

2. True or False:  In a SPA, forms are required to send data to the server.

3. What are the two props that must be added to a controlled input in React?

## Adding the New To-Do

Now that we have the `<input>` working and know how to respond to events in React, we can add new to-dos by:

- Adding an `onClick` handler to the [ADD TO-DO] button.

- When the button is clicked, add the new to-do using the `setTodos` setter function.

- Clearing the input for a better UX.

### Adding the `onClick` Handler to the [ADD TO-DO] Button

We're not going to be able to perform all of the required logic inline this time, instead let's write an additional function within **NewToDoForm.jsx**:

```jsx
export default function NewToDoForm() {
  const [newTodo, setNewTodo] = useState("");

  // Add this new handler
  function handleAddTodo() {
    alert(newTodo);
  }

  ...
```

We're alerting the `newTodo` state value as a baby step.

Now let's attach the new handler by adding an `onClick` prop to the button:

```jsx
<button onClick={handleAddTodo}>ADD TO-DO</button>
```

<details><summary>❓ Why didn't we have to wrap <code>handleAddTodo</code> with an arrow function in this case?</summary>
<p>

**We don't need to provide any arguments to `handleAddTodo` when invoking it, thus we can simply provide the function itself.**

</p>
</details>

### Updating the `todos` State

A few questions...

<details><summary>❓ Which component "owns" the <code>todos</code> State?</summary>
<p>

**`<App>`**

</p>
</details>

<details><summary>❓ Which component "owns" the setter function used to update the <code>todos</code> State?</summary>
<p>

**`<App>`**

</p>
</details>

<details><summary>❓ Does the <code>&LT;NewToDoForm></code> have access to the <code>setTodos</code> setter function?</summary>
<p>

**No**

</p>
</details>

So, we could solve our dilemma by passing a reference to `setTodos` as a prop.  However, we also would need to pass a reference to the `todos` state as well to use with the spread operator.

We certainly could pass those props without much hassle, however, it just doesn't feel right - instead, it's a better practice to always update state within the component that owns that state, in this case, `<App>`.

Let's add a new function within **App.js** that we can then pass to `<NewToDoForm>` as a prop:

```jsx
const [showTodos, setShowTodos] = useState(true);

// Add this function
function addTodo(todo) {
  // Replace state, don't mutate it
  setTodos([...todos, todo]);
}
```

As discussed in the last lesson, we are using the spread syntax to include (spread) the current elements of the `todos` array within a new array literal, adding the new todo at the end.

#### 💪 Practice Exercise - Pass `addTodo` to the `<NewToDoForm>` Component (2 minute)

1. Pass the `addTodo` function from **App.js** to the `<NewToDoForm>` component using a prop with the same name.

2. Update `<NewToDoForm>` to destructure the `addTodo` prop being passed to it.

<hr />

Now we're ready to add the to-do by updating the `handleAddTodo` function in **NewToDoForm.jsx**:

```jsx
function handleAddTodo() {
  // alert(newTodo);
  addTodo(newTodo);
}
```

Try it out!

Now let's improve the UX...

#### 💪 Practice Exercise - Reset the `<input>` Back to an Empty String (1 minute)

- Improve the UX by adding a single line of code to `handleAddTodo` that clears out the value displayed in the `<input>`.

  > Hint:  Controlled inputs get their displayed value from state!

## Using `<form>` React Elements

Now that we've shown that using a `<form>` in React is optional, let's refactor "React To-Do" to use a `<form>` so that we can learn how to prevent them from being submitted to the server, etc.

### Add the `<form>` React Element

Let's start by refactoring to use a `<form>`:

```jsx
<form onSubmit={handleAddTodo}>
  <input
    value={newTodo}
    onChange={(evt) => setNewTodo(evt.target.value)}
    placeholder="To-Do"
  />
  <button type="submit">ADD TO-DO</button>
</form>
```

> Key Point: Forms in React will never have an `action` or `method` prop/attribute because they are never submitted to a server!

Note that we've:

- Removed the `onClick` from the button and changed its type to `type="submit"`

- Added the `onSubmit` event prop to the form - this is a more typical approach when working with forms.

With the above refactor, a new to-do will only appear for a second before the form triggers a refresh when the submit button is clicked...


## Preventing a `<form>` From Being Submitted

To prevent a form from being submitted, we need to invoke the `preventDefault()` method on the event object.

First we need to add a parameter to the `handleAddTodo` function to accept the event object that React passes automatically:

```jsx
//
function handleAddTodo(evt) {
  ...
```

Next, we invoke the `preventDefault()` method first thing:

```jsx
function handleAddTodo(evt) {
  evt.preventDefault();
  addTodo(newTodo);
  setNewTodo("");
}
```

Now there's no more page refresh when adding a new to-do!

## Validating Data In a `<form>`

Because all of the data for a form's inputs will be held in state, it's possible to validate that state every time it changes using code in the handler; setting additional state, e.g, `isValid`, accordingly.

However, we can easily take advantage of the form's HTML5 validation capabilities to ensure that data has been entered as desired.

As we saw in the lesson on Regular Expressions, we can add a `required` and `pattern` attribute to HTML inputs to validate their data. React works with those props work too!

For example, let's prevent empty to-dos from being created:

```jsx
<input
  value={newTodo}
  onChange={(evt) => setNewTodo(evt.target.value)}
  placeholder="To-Do"
  required
  pattern=".{4,}"
/>
```

Now, thanks to built-in HTML5 validation, the form cannot be submitted unless at least 4 characters are entered!

We've only scratched the surface of validation built-into browsers.  You can begin to learn more by reading about the comprehensive [constraint validation Web API here](https://developer.mozilla.org/en-US/docs/Web/API/Constraint_validation).

## Using State to Handle Multiple Inputs

We've seen how to handle a single input within a form.  However, we'll usually need to use several inputs for gathering all of the data we need.

Since "React To-Do" is a wrap, let's create a new sandbox where we can add a form with multiple inputs that will also help you with the lab.

### Set Up the New Form

Copy and paste this into the **App.js**:

```jsx
import "./styles.css";

export default function App() {
  return (
    <div className="App">
      <form>
        <label>NAME</label>
        <input name="name" />
        <label>EMOTION</label>
        <select name="emotion">
          <option value="😁">Happy</option>
          <option value="😐">Neutral</option>
          <option value="😠">Angry</option>
        </select>
      </form>
    </div>
  );
}
```

We are only using a `<form>` as a "container" for the inputs - there isn't even a submit button.

Sure, there's only two inputs in this example, but the approach we're going to use applies to any number of inputs.

Here's just a bit of CSS to add to **App.css**:

```css
form {
  display: grid;
  grid-template-columns: auto auto;
  gap: 0.5rem;
  width: 20rem;
  text-align: left;
  font-size: 1.5rem;
}
```

### Do We Really Need a State Variable For Each Input?

Imagine that we had a form with a dozen or more inputs.  Based on what you've seen thus far you might think that you would need to have a dozen or more state variables with their own setter functions, etc.

Having dedicated state for each input is not only verbose, it's also not convenient when having to send that data to a server.

Instead, as we learned in the lesson about state, a single state can be anything, including an object and that's our ticket:

```jsx
export default function App() {
  const [formData, setFormData] = useState({
    name: "",
    emotion: "😁"
  });
  ...
```

It's no coincidence that the name of the properties on the `formData` object match the names assigned to the `name` props on the inputs. Doing so allows for the following concise `onChange` handler that will update the state for any number of inputs.

### Add the `onChange` Handler Function

Here's the only handler function we need:

```jsx
export default function App() {
  const [formData, setFormData] = useState({
    name: "",
    emotion: "😁"
  });

  function handleChange(evt) {
    // Replace with new object and use a computed property
    // to update the correct property
    const newFormData = { ...formData, [evt.target.name]: evt.target.value };
    setFormData(newFormData);
  }
  ...
```

> [Computed property names](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#Computed_property_names) allow for a JS expression to dynamically determine the key of the property.

Similar to how we used the spread operator with arrays, we're using it here to first spread all of the existing properties within a new object literal.  Then, any additional properties are comma separated and are either added to the object, or used to updated existing properties.

### Bind the Handler to the `onChange` Event

Each input needs to have an `onChange` prop added so that the handler is invoked:

```jsx
<input name="name" onChange={handleChange} />
...
<select name="emotion" onChange={handleChange}>
```

> Note: We don't use event delegation in React because React's event system is implementing it automatically behind the scenes.

That's all it takes!  We could use React Developer Tools to verify it's working, but let's add an `<h1>` to display the results instead:

```jsx
...
</form>
<h1>{formData.name} is {formData.emotion}</h1>
```

## The Keys to Programming in React

Now that you've worked a bit with the fundamentals of React, let's look a few **key** thoughts every React developer considers when developing a React application - whether they know it or not:

1. **We code components to render (visualize) application-state**, for example, render a `<ToDoListItem>` component for each to-do in the `todos` application-state array.
2. **We can code components to render other components based upon UI-state**, for example, hide/show a component based upon `showDetails` UI-state, disable a button based upon `isValid`, etc.
3. **In response to user-interaction, we apply any necessary program logic and/or calculations and ultimately update all impacted state causing the components to re-render.**

## Final Version of the Fundamentals of React Chart

Here is the completed [Fundamentals of React Chart](./../react-fundamentals.md) that is excellent to review from time-to-time, make flash cards from, or read before bedtime 😃

The following has been added from this lesson...

| React Fundamental | Summary |
|---|---|
| ... | ... |
| Event Handling | <ul><li>Instead of using `addEventListener`, in React we connect event handlers (functions) to events using event props on React Elements.</li><li>Examples of event props are: `onClick`, `onChange`, `onSubmit`, etc.</li></ul> |
| Handling Input | <ul><li>[Controlled Inputs](https://reactjs.org/docs/forms.html#controlled-components) are the React way to gather input from the user with `<input>`, `<select>` or `<textarea>` React Elements.</li><li>A controlled input must include both `value` & `onChange` props.</li><li>Forms are optional in a SPA but they can be beneficial for validation & CSS layout/formatting. If forms are used, be sure to prevent them from being submitted to the server by calling `preventDefault()` on the event object from within the `onSubmit` event handler.</li></ul> |
| **The Keys to Programming in React** | <ul><li>**We code components to render (visualize) application-state**, for example, render a `<ToDoListItem>` component for each to-do in the `todos` application-state array.</li><li>**We can code components to render other components based upon UI-state**, for example, hide/show a component based upon `showDetails` UI-state, disable a button based upon `isValid`, etc.</li><li>**In response to user-interaction, we apply any necessary program logic and/or calculations and ultimately update all impacted state causing the components to re-render.**</li></ul> |

#### Congrats on Handling Input and Events in React!

## ❓ Essential Questions

1. A controlled input displays the value of the state assigned to its ________ prop.

2. A controlled input must use a ________ prop to bind a handler function.

3. What must the above handler function's code update?

4. What method needs to be invoked to prevent a form from triggering a full-page refresh?

## References

- [React Docs - Synthetic Events](https://reactjs.org/docs/events.html)


<img src="https://i.imgur.com/pg98OTd.png">

# React Dev Skills Lab - Part 4

## Intro

This lab provides an opportunity to practice:

- Using the `value` and `onChange` props to implement controlled inputs.
- Implementing event handlers.
- Updating state by replacing objects instead of mutating them.
- Passing a method from a parent component to a child component via a prop.

##### This lab, combined with Parts 1, 2 & 3 is a Deliverable

## Exercises

1. Open your "react-dev-skills" sandbox that you created back in Part 1.

2. Add state to the existing `<NewSkillForm>` component that will be used to manage the form's state. The state should be initialized as an object with two properties: `name` and `level` - by design, these properties match the names of the properties of the skill objects held in state (App.js). The `name` property should be initialized to an empty string and the `level` property should be initialized to a number of `3`.

3. Add `value` props to each `<option>` tag and assign the **numbers** 1 thru 5 like this:

    ```jsx
    <option value={1}>1</option>
    ```
    > Remember, unlike attributes in HTML which always hold strings, props in React can hold any type of data.

4. Following the steps in the lesson, make the `<input>` and `<select>` controlled inputs that update the form's state you created in step 2.

    > Hint:  As in the lesson, use computed property names so that a single onChange handler can be used for any number of inputs.

5. Make the form's button a submit button and add an `onSubmit` prop to the `<form>`.  Assign an event handler to `onSubmit` and ensure that the form does not trigger a full-page refresh when the button is clicked!

6. Following the steps in the lesson, code the app so that when the [ADD SKILL] button is clicked, the new Dev Skill is added to the `skills` state held in **App.js**. The app should re-render and display the new skill.

    > Hint: App.js needs a function that will update the state and that function will need to be passed to the `<NewSkillForm>` component.

7. For a better UX, after the new skill is added, the form should reset to the same values used to initialized the state.

## This lab combined with Parts 1, 2 & 3 is a Deliverable



<!-- {% raw %} -->

<img src="https://i.imgur.com/VunmGEq.jpg">

# React To-Do - Practice Lab

## Intro

You've learned the basics of a React app including:

- How to compose an app's UI using Function Components 
- How to define a component's UI using JSX
- How to pass props from a parent to a child component
- How to style React Elements
- How to encapsulate state within a component using the `useState` hook
- How to update state with the setter function provided by the `useState` hook
- How to use forms and controlled inputs
- How to handle browser events

This lab will provide you the opportunity to practice the above skills by adding the following user stories to the existing React To-Do app:

- AAU, I want to be able to mark to-dos as completed so that I can remove them from the list.
- AAU, I want to see the text of a completed to-do rendered with a line through it.
- AAU, I want to be able to remove a completed to-do from the list.

## Setup

Continue to build upon the "React To-Do" sandbox we've been working with during the lessons in [codesandbox.io](https://codesandbox.io/):

<img src="https://i.imgur.com/BHDBkZM.png">

## Exercises & Hints

### AAU, I want to be able to mark to-dos as completed so that I can remove them from the list

#### Hints:

- Since each to-do needs to track whether or not it's completed, start by refactoring the `todos` state from being an array of simple strings to an array of to-do objects like the following:

  ```jsx
  const [todos, setTodos] = useState([
    {text: "Have Fun", completed: true},
    {text: "Learn React", completed: false},
    {text: "Learn the MERN-Stack", completed: false}
  ]);
  ```

- The above refactor requires a minor change to `<ToDoListItem>` because the `todo` prop it's receiving is now an object instead of a string - `<ToDoListItem>` should now render the `text` property of `todo`.

- Now when adding a new to-do, an object should be added with a `completed` property set to `false` and its `text` property set to the text of the new to-do.  The app should now be working again - a refresh of the sandbox may be required if it gets "stuck".

- The UI should display a button with a ❌ used to delete the to-do if the to-do is completed.  Otherwise, display a button with a ✔️ used to update the to-do as completed: 

  <img src="https://i.imgur.com/eyyt7Xy.png">

  > The styling is up to you. The only change necessary to display the above is to update `justify-content` to `space-between` in **ToDoListItem.css**:

  <img src="https://i.imgur.com/HLy4DMd.png" width="70%">

- Update a to-do's `completed` property to `true` when the  ✔️ is clicked.  We should update the `todos` state from within the `<App>` component - refer to the existing code that adds a to-do.

- You'll need to pass the function responsible for updating the to-do from `<App>` all the way down to `<ToDoListItem>`. Don't forget to destructure the props!

- Because a to-do is now an object, when updating it, both the `todos` array and the to-do object should be replaced, not mutated. The `map` method can be handy here.<br>
  <details><summary>Don't Peek Unless You Have To...</summary>

  ```js
  function completeTodo(todoIdx) {
    const newTodos = todos.map((t, idx) =>
      idx === todoIdx ? { text: t.text, completed: true } : t
    );
    setTodos(newTodos);
  }
  ```

  </details>

### AAU, I want to see the text of a completed to-do rendered with a line through it

#### Hints:

- Use either the `style` prop or dynamically apply a CSS class with a declaration of<br>`text-decoration: line-through`.

- Regardless of the approach you take, you'll want to wrap the to-do's text with a `<span>` React Element and apply the styling to the `<span>`.<br>

  <details><summary>Don't Peek Unless You Have To...</summary>

  ```js
  <span style={{ textDecoration: todo.completed && "line-through" }}>
    {todo.text}
  </span>
  ```

  </details>

  <img src="https://i.imgur.com/iwMBSi4.png">

### AAU, I want to be able to remove a completed to-do from the list

- Very much like marking a to-do as complete, however, the `filter` method is your go to in this case. 

Congrats!

<img src="https://i.imgur.com/hY21Tbu.png">

## Deliverable?

This lab is **not** a deliverable.

<!-- {% endraw %} -->






<img src="https://i.imgur.com/VunmGEq.jpg">

# React Fundamentals - Using and Updating State

## Learning Objectives

|Students Will Be Able To:|
|---|
| Add State to a Function Component |
| Pass State to Children Components |
| Update State |
| Explain Why Not All Data Needs to be State |

## Road Map

1. Setup
2. Previous Lesson's Bonus Challenge
3. Review of State
4. Intro to React Hooks
5. Add State to a Function Component Using the `useState` Hook
6. Using the Value of the State
7. Updating State Using the `useState` Hook's Setter Function
8. More About State
9. Not All Data Needs to Be State
10. React Fundamentals Chart Update
11. Essential Questions
12. Further Study

## 1. Setup

This lesson continues to build upon the "React To-Do" sandbox we've been working with during the last couple of lessons in [codesandbox.io](https://codesandbox.io/):

<img src="https://i.imgur.com/BiuKtr9.png">

## 2. Previous Lesson's Bonus Challenge

If you didn't have a chance to complete the challenge exercise of numbering the to-dos, make the following changes:

1. Add a `<div>` to `<ToDoListItem>` before the `{todo}`:

    ```jsx
    <div className="flex-ctr-ctr">{index + 1}</div>
    {todo}
    ```

2. Add that general purpose `flex-ctr-ctr` class to **styles.css**:

    ```css
    .flex-ctr-ctr {
      display: flex;
      justify-content: center;
      align-items: center;
    }
    ```

3. Update **ToDoListItem.css** to the following:

    ```css
    .ToDoListItem {
      display: flex;
      justify-content: flex-start;  <!-- default -->
      align-items: center;
      margin: 4vmin;
      padding: 2vmin;
      border: 1vmin solid purple;
      list-style: none;
      font-size: 6vmin;
    }

    .ToDoListItem div {
      width: 8vmin;
      height: 8vmin;
      margin-right: 4vmin;
      background-color: black;
      color: white;
      border-radius: 50%;
    }
    ```

## 3. Review of State

Just in case you haven't gotten it tattooed yet...

#### State is the data a program needs to "remember" while it's running.

State, the facts 😁:

- State is the single-source of truth of an application.
- State changes due to user interaction or when other events occur such as when a timer ticks.
- When state is updated, the user interface needs to be re-rendered to reflect the new state of the program - this fundamental concept might sound familiar from Unit 1.
- React state is immutable, this means that it cannot be changed, you cannot change the value of a state object or change the value of its properties unless you use the setState function created with the given state object when you use the 'useState' function. When you update state using a set state method, you are in fact creating a new version of that state to be used instead of the older version, so think of set state more as creating an updated version of your state object and not that it is updating the existing state object.

<details>
<summary>
❓ What state do we have in "React To Do"?
</summary>
<br>

The <code>todos</code> array

<hr>
</details>
<br>

> 👀 In a React app, UI-related state is used to make a user interface render dynamically. For example, if we wanted to hide/show a `<PlayerDetails>` component, we would use a piece of state like `showPlayerDetails` to track whether or not to render the component.

<br>

## 4. Intro to React Hooks

Hooks were added to React in version 16.8.

**Hooks allow components defined as functions to perform functionality that used to require that the components be defined as a class.**

Consider what happens when React renders a Function Component:

1. React calls the function passing to it props as an argument.
2. The function runs and ultimately returns its UI (the JSX).
3. React uses the object returned by the JSX to render the UI.

Now consider that when a function finishes running and returns, its scope is destroyed, thus any data held in variables is forgotten!

So, how can a Function Component remember state?

Some of you might be thinking to yourselves - _What about using closures?_

Exactly!  Indeed, it's closures that enable hooks to remember state, as well as implement other stateful behavior!

Some facts about React hooks:

- Hooks are a way to add reusable stateful behavior to Function Components, not class-based components.
- Hooks themselves are functions and must be named beginning with the word `use`, e.g., `useState`.
- Hooks must be called at the top-level of the component's function and cannot be called conditionally. For example, a hook cannot be called within an `if` statement.  Basically, React must be able to depend on every hook being called in the exact same order every time the component renders (is invoked by React).
- It's possible to create custom hooks if the built-in hooks don't satisfy our needs, in fact, lots of custom hooks are just a google away!

## 5. Add State to a Function Component Using the `useState` Hook

React's [useState Hook](https://reactjs.org/docs/hooks-state.html) is used to remember and update state in a Function Component.

Let's briefly review the doc linked to above.  As you can see, the Function Component is more concise and likely easier to reason about.

Also, Function Components eliminate having to worry about the proper binding of `this`, which definitely becomes an issue when a Class Component needs to invoke an event handler.

### Adding the `todos` Array as State

Although the current `todos` array in **App.js** can be updated using `push`, etc., a very important thing **won't** happen if we do.

<details>
<summary>
❓ What won't happen?
</summary>
<hr>

<strong>A re-render will not be triggered!</strong>

<hr>
</details>

Before state can be added to a component, we need to import the `useState` named export from the `React` library: 

```jsx
// App.js
import { useState } from "react";
```

The above syntax is used to import **named** exports.  JS modules can have any number of **named** exports and only a single **default** export.

Next, inside of the Function Component we invoke `useState` and provide the initial value of the state as an argument:

```jsx
export default function App() {
  const [todos, setTodos] = useState([
    "Have Fun",
    "Learn React",
    "Learn the MERN-Stack"
  ]);
  ...
```

> 👀 The initial value argument is only used to set the state's value when the component is rendered for the **first time**

The `useState` hook/function always returns an array with two elements where:

- The 1st element is the current value of the state
- The 2nd element is the setter function used to update the state's value

<details>
<summary>
❓ So what's that? --> <code>[todos, setTodos] = ...</code>
</summary>
<br>

Yes, that's <a href="https://javascript.info/destructuring-assignment#array-destructuring">array destructuring assignment</a>!
<br>
The call to <code>useState()</code> always returns an array with two elements and now we have two variables we can use to easily access those elements.

<hr>
</details>

## 6. Using the Value of the State

Did you notice that the To-Dos have continued to render just fine?

Using the value of the state is as simple as using the first element returned by `useState()`, which in our case, has been destructured into a variable named `todos` - and that variable (`todos`) continues to be passed to the `<ToDoList>` components as a prop.

We are free to use the variable holding the state's value any way we want, pass it as a prop, render it, etc.

However, we **do not** modify the state's value by reassigning to the state variable.  Instead, updating state is the job of the setter function...

## 7. Updating State Using the `useState` Hook's Setter Function

When we invoked `useState()`, we destructured the returned array naming the second element `setTodos` because it is a setter function used to update the `todos` state to whatever we pass to that setter function.

By convention, we always name the setter function by pre-pending the word `set` to the name we assigned to the state value variable and adjusting the camelCasing.

For example, if you wanted to track the state of the board in a Tic-Tac-Toe app:

```jsx
export default function App() {
  const [board, setBoard] = useState([0, 0, 0, 0, 0, 0, 0, 0, 0]);
  ...
}
```

<details>
<summary>
❓ What line of code could you use to define state to track whose turn it is in a Tic-Tac-Toe app?
</summary>
<br>

<pre><code>
// 1 represents player 1; -1 is player 2

const [turn, setTurn] = useState(1);
</code></pre>

<hr>
</details>

We'll wait until the next lesson to update `todos`. For now, we'll practice with a different piece of state... 

### 👉 You Do - Add a New Piece of State (1 min)

- Add a `showTodos` state to "React To-Do" and initialize it to `true`;

### Rendering Conditionally

Now we can use the `showTodos` state to conditionally render the `<ToDoList>` component:

```jsx
export default function App() {
  ...

  return (
    <div className="App">
      <h1>React To-Do</h1>
      {/* Conditionally render ToDoList */}
      {showTodos && <ToDoList todos={todos} />}
    </div>
  );
}
```

We told you in Unit 1 how handy those logical operators like `&&` would be!  `&&` is used extensively in React to conditionally render a component or not.

<details>
<summary>
❓ What kind of JS expression would we use to render one of two components?
</summary>
<br>

A <strong>ternary expression</strong>!  For example:
<pre><code>export default function App() {
  const [user, setUser] = useState(getUser());

  return (
    &#60;div className="App"&#62;
      {user ? &#60;HomePage /&#62; : &#60;LoginPage /&#62;}
    &#60;/div&#62;
  );
}</code></pre>

<hr>
</details>

Cool, the To-Dos are still being rendered because `showTodos` is `true`.

Let's use React Developer Tools to update the state:

<img src="https://i.imgur.com/sGHlL3A.png">

Toggling between `true`/`false` will result in `<ToDoList>` being rendered or not - very cool!

> 👀 React Developer Tools have no way of knowing what we named our state - all it knows is the order in which the `useState` hooks were called.

### Replace, Don't Mutate State

Invoking the setter function will **replace** the value of the state.

Replacing primitive data types, e.g., numbers, strings & booleans, is gravy.  However, we should always **replace** objects/arrays (reference types), as well.

For example, in the next lesson we will be adding new to-dos to the `todos` state array. When doing so, we will not use the `push` method, which mutates the array instead of replacing it with a new array.

The modern approach is to use [spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) for creating new arrays and objects from existing ones.

Here's a preview of how we might add a new to-do:

```jsx
function handleAddTodo(todo) {
  // Create a new array that includes the new todo
  const newTodos = [...todos, todo];
  // Update state and re-render
  setTodos(newTodos);
}
```

The `...` is the spread syntax and is used similarly to "spread" out the existing properties in objects.

The important thing to remember here though is to replace objects/arrays, not mutate them!

### Updating State is an Asynchronous Operation

Calling the `useState` hook's setter function is an asynchronous operation.

This means that any synchronous code following the call to the setter will be accessing the "current" value of the state variable, not the updated value.

The state's value won't actually be updated until the subsequent render.

[This sandbox](https://codesandbox.io/s/updating-state-is-asynchronous-k6jbv?file=/src/App.js) demonstrates this asynchronous behavior.

### Triggering a Re-Render

**A component will re-render when a state's value is updated by calling its setter function!**

<details>
<summary>
❓ When a component renders its child components in its JSX, what do those child components do?
</summary>
<hr>

<strong>They render their children and so on...</strong>

<hr>
</details>

## 8. More About State

### State/Information Can Only Be Passed Down

<details>
<summary>
❓ State can only be passed DOWN the component hierarchy via _______.
</summary>
<hr>

<strong>Props</strong>

<hr>
</details>

<img src="https://i.imgur.com/6CT8foa.jpg">

Typically, you'll find that most state needs to be defined in the `<App>` component.

However, we can avoid unnecessary "prop drilling" by moving state to the nearest parent component in common with the other components that need to use that state.

<details>
<summary>
❓ If a piece of state needed to be used only by the green and black components, where should the state be defined?
</summary>
<hr>

In the <strong>green component</strong>

<hr>
</details>

<details>
<summary>
❓ If a piece of state needed to be used by the dark blue and light blue components, where would the state be defined?
</summary>
<hr>

In the <strong>top (yellow) component</strong>, which typically would be <code>&#60;App&#62;</code>.

<hr>
</details>

### Categorizing State

We can think of there being three categories of state:

- Data-related state
- UI-related state
- Computed state

### Data-Related State

Data-related state holds the data that the application is about. For example, in "React To-Do", it's the `todos` array.

It's common to define all state that represents data first in `<App>`.  This makes it possible to pass that state to any component that needs it.

Then later, the app can be refactored to move state down the hierarchy to avoid having to pass the same prop through multiple components that don't need it and are simply passing the prop down the hierarchy to its ultimate destination.  This is known in React as "Prop Drilling".

"Prop Drilling" is the way React is designed to work, however, it can be a bit tedious and has led to alternative approaches to delivering state directly to the component that needs it vs. being passed down the hierarchy via props.  Some alternative approaches are listed in the Further Study section.

### UI-Related State

UI-related state is state used to control the dynamic rendering of the UI. For example, you click an [EDIT] button and an `<input>` is displayed instead of a `<div>`.

<details>
<summary>
❓ We've actually defined UI-related state already. What's the name of the variable holding the UI-related state?
</summary>
<br>

<strong><code>showTodos</code></strong>

<hr>
</details>

UI-related state is usually defined in the component that uses it and since no other component would likely need to access its value.

However, if for some reason the UI-related state needed to be accessed higher up in the hierarchy, then it would need to be defined high enough to be accessed by all components that need to access it.

### Computed State

Some state has its value computed from other state.

A good example of computed state would be `winner` state in the game of Tic-Tac-Toe.

<details>
<summary>
❓ What state would be used to compute <code>winner</code>?
</summary>
<br>

**`board`**

<hr>
</details>

Since computed state is derived from other state, computed state does NOT have to be defined using `useState` (see example below).

### How Many State Variables Can We Use?

A Function Component can call `useState` as many times as necessary. For example:

```jsx
export default function App() {
  const [board, setBoard] = useState([0, 0, 0, 0, 0, 0, 0, 0, 0]);
  const [turn, setTurn] = useState(1);
  // winner is computed using board state
  const winner = getWinner(board);
  ...
}
```

However, it's not always necessary to break up state into multiple `useState()` calls because a single state can be a JS object which would hold any number of values in its properties.

For example, if we needed to hold the state for a sign up form, we can do this:

```jsx
export default function SignUpPage() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    password: '',
    pwConfirm: '',
  });
}
```

Instead of this:

```jsx
export default function SignUpPage() {
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [pwConfirm, setPwConfirm] = useState('');
}
```

Grouping related state can result in less code required to update that state (fewer setter functions) and also makes it easier to send that state to the backend.

## 9. Not All Data Needs to Be State

Not all data needs to be defined as state.

Consider the Tic-Tac-Toe app where we might use a `WINNING_COMBOS` array that held nested arrays with winning index patterns.

<details>
<summary>
❓ Why wouldn't <code>WINNING_COMBOS</code> need to be defined as state?
</summary>
<br>

<code>WINNING_COMBOS</code> is a constant lookup data structure that never changes. 

<hr>
</details>

> 👀 Only data that you want to cause a re-render when it changes should be defined as state.

### How to Persist Non-State Data

Since variables are forgotten after a function returns, how we do we persist non-state data?

It depends upon whether a component needs its own copy of that data or not...

#### Component Does **NOT** Need Its Own Copy of the Non-State Data

When there only needs to be one copy of some data because it can be shared by all components, we can simply define a variable outside of the Function Component.

For example:

```jsx
const WINNING_COMBOS = [
  [0, 1, 2],
  [3, 4, 5],
  [6, 7, 8],
  [0, 3, 6],
  [1, 4, 7],
  [2, 5, 8],
  [0, 4, 8],
  [2, 4, 6]
];

export default function App() {
  const [board, setBoard] = useState([0, 0, 0, 0, 0, 0, 0, 0, 0]);
  const [turn, setTurn] = useState(1);
  // winner is computed using board state
  const winner = getWinner(board);
  ...
}
```

#### Each Component Needs Its Own Copy of the Non-State Data

If a Function Component needs to remember its own copy of non-state data between renders, it **can't** define a variable in or outside of the function.

An example of this situation might be a list of components that each have their own timer created with `setInterval`.  It would be necessary for each component to remember the id of its timer so that it can `clearInterval` at some point. 

There is another hook for this scenario:  [useRef](https://reactjs.org/docs/hooks-reference.html#useref).

There's no need to cover it now, but it's good to know that the `useRef` hook allows a Function Component to remember non-state data between renders. Also, data remembered using a "ref" is mutable and can be updated without triggering a re-render.

## 10. React Fundamentals Chart Update

Yup, time to update our [React Fundamentals Chart](https://gist.github.com/jim-clark/cbc87fdf01c22f412737ca121ef70761) before wrapping up with the Essential Questions.

| React Fundamental | Summary |
|---|---|
| ... | ... |
| State | When a component's state is updated, the component re-renders.<br><br>Most state is data-related, i.e., related to the purpose of the application. However, a component can use UI-related state to control the dynamic rendering of its UI.<br><br>The `useState` hook is used to manage state in a Function Component.<br><br>Invoking `useState(<initial value of the state>)` returns an array whose first element is the state's current value and whose second element is a setter function used to update the state's value.<br><br>Only data that you want to cause a re-render when it changes should be defined as state. |

## 11. ❓ Essential Questions (2 mins)

<details>
<summary>
(1) In general, why were hooks added to React?
</summary>
<hr>

Hooks allow Function Components to "remember" state and implement stateful behavior that used to require Class Components.

<hr>
</details>

<details>
<summary>
(2) What React hook is used to manage state in a Function Component?
</summary>
<hr>

<strong><code>useState</code></strong>

<hr>
</details>

<details>
<summary>
(3) How do we update the value of state?
</summary>
<hr>

<strong>By calling the state's setter function.</strong>

<hr>
</details>

<details>
<summary>
(4) True or False:  Only data that you want to cause a re-render when it changes should be defined as state.
</summary>
<hr>

<strong>True</strong>

<hr>
</details>

## 12. Further Study

### Learn More About Hooks

To learn more about hooks, read [Introducing Hooks](https://reactjs.org/docs/hooks-intro.html) in the docs.

### Built-in Hooks and their use cases:

| Hook | Use Case |
|---|---|
|[`useState()`](https://reactjs.org/docs/hooks-reference.html#usestate)|Used to manage state in a Function Component.|
|[`useEffect()`](https://reactjs.org/docs/hooks-reference.html#useeffect)|Used to implement "side effects", e.g., fetching data, using timers, subscriptions, etc.<br>`useEffect()` implements the functionality of class components' `componentDidMount`, `componentDidUpdate` & `componentWillUnmount` with a single hook!|
|[`useRef()`](https://reactjs.org/docs/hooks-reference.html#useref)|In addition to how refs are used to access DOM elements in class components, `useRef()` can be used more generally to "remember" any non-state data that needs to be persisted between renders similar to how we use instance properties in class components. |
|[`useReducer()`](https://reactjs.org/docs/hooks-reference.html#usereducer)|An alternative to `useState()` for when the state is more complex.  It uses a reducer function and "actions" to update state - similar to how Redux does (but not as comprehensive).|
| Other built-in hooks|[`useContext()`](https://reactjs.org/docs/hooks-reference.html#usecontext)<br>[`useMemo()`](https://reactjs.org/docs/hooks-reference.html#usememo)<br>[and other less common hooks here...](https://reactjs.org/docs/hooks-reference.html#useimperativehandle)|

### Alternative State Management Approaches

Note that although there are alternatives to using the `useState` hook, be aware that there's a learning curve with each alternative and that no alternative should be considered until you have mastered the fundamentals of React.

Some alternatives to using `useState` are:

- [Redux](https://redux.js.org/) is a popular real-world state management alternative.  However, it requires quite a bit of setup and is overkill for most apps. Although still popular, Redux has been falling out of favor lately.

- React's [Context API](https://reactjs.org/docs/context.html) can be combined with the [useReducer hook](https://reactjs.org/docs/hooks-reference.html#usereducer) to provide a lighter-weight alternative to Redux.

- [MobX](https://mobx.js.org/README.html) is another popular alternative, like Redux, it's popularity has probably peeked.

## References

- [React Docs - Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)

- [React Docs - JSX In Depth](https://reactjs.org/docs/jsx-in-depth.html)



<img src="https://i.imgur.com/pg98OTd.png">

# React Dev Skills Lab - Part 3

## Intro

This lab will simply ask you to use the `useState` hook to add state to the React Dev Skills app.

Updating that state will be an exercise in part 4.

##### This lab, combined with Parts 1, 2 & 4 is a Deliverable

## Exercises

1. Open your "react-dev-skills" sandbox that you created in Part 1.

2. Use the `useState` hook to add a state value named `skills`.

3. Be sure to name the setter function according to the convention discussed in the lesson.

4. Initialize the state using the same array of skill objects used in part 2.

5. When finished, the skills should continue to be displayed without error:

    <img src="https://i.imgur.com/z1ZMjrG.png">

## This lab combined with Parts 1, 2 & 4 is a Deliverable




<img src="https://i.imgur.com/KBwhRtk.png">

# React "Students" Lab

## Intro

This lab will provide some practice doing the following:

- Creating a UI using a hierarchy of components
- Adding state to a function component with the `useState` hook.
- Passing data as props from a parent to a child component
- Mapping arrays of data into arrays of components

**This lab is a DELIVERABLE**

## Setup

Please complete this lab in a React [CodeSandbox](https://codesandbox.io) named "React Students".

## Minimum Requirements

**The layout and styling of the markup is left up to your discretion.**

1. Use the `useState` hook to add a `students` state value to the `<App>` component and initialize it with the following array of "student" data:

```js
[
  {
    name: 'Cait Yomorta',
    bio: 'Lorem ipsum, dolor sit amet consectetur adipisicing elit. Natus placeat nostrum explicabo? Voluptatibus expedita saepe officia optio, commodi totam ratione laudantium ipsum porro molestias, quasi nulla minus vitae laboriosam corrupti Delectus inventore explicabo est odit incidunt rem a recusandae eum pariatur. Aperiam doloremque blanditiis harum voluptate animi fugit beatae asperiores quo, dignissimos sed illum veniam eum accusantium nulla quod voluptatum',
    scores: [
      {
        date: '2018-02-08',
        score: 77
      },
      {
        date: '2018-04-22',
        score: 92
      },
      {
        date: '2018-09-15',
        score: 68
      }
    ]
  },
  {
    name: 'Holly Baird',
    bio: 'Eum molestiae explicabo deserunt, maiores quod eaque omnis tenetur vero ducimus, magnam autem! Quia facere quaerat eum repudiandae dolorum eligendi iure quae. Eos id possimus accusantium, earum animi modi hic.',
    scores: [
      {
        date: '2018-12-14',
        score: 88
      },
      {
        date: '2019-01-09',
        score: 79
      },
      {
        date: '2019-02-23',
        score: 91
      },
      {
        date: '2019-03-01',
        score: 95
      }
    ]
  },
  {
    name: 'Wes Mungia',
    bio: 'Repudiandae veritatis recusandae quidem tenetur impedit, numquam incidunt enim, adipisci id cupiditate asperiores nam perferendis. Facere odit laborum ipsum autem repellendus natus eius doloremque ullam perferendis. Enim repellendus ut veniam?',
    scores: [
      {
        date: '2018-10-11',
        score: 62
      },
      {
        date: '2018-11-24',
        score: 74
      },
      {
        date: '2018-12-19',
        score: 85
      }
    ]
  }
]
```

2. Code the `<App>` component's JSX to display a `<Student>` component for each student object in the `students` state.

3. Create and code a `<Student>` component that:

    - Accepts a student object as a prop.
    - Renders the student's `name` & `bio` properties.
    - Renders a `<Score>` component for each score object in the student's `scores` property.

4. Create and code the `<Score>` component so that it renders the score object's `date` & `score` properties.

#### This Lab is a Deliverable

As usual, please submit the link to your sandbox as directed.



<img src="https://i.imgur.com/VunmGEq.jpg">

# React Fundamentals - Handling Input and Events

## Learning Objectives

|Students Will Be Able To:|
|---|
| Handle Events in React |
| Optionally Pass Arguments to Event Handlers |
| Use "Controlled Inputs" in React |
| Prevent a `<form>` From Being Submitted to the Server |
| Properly Update Objects/Arrays in State |

## Road Map

- Setup
- Attaching Event Handlers Using Event Props
- Using "Controlled Inputs" in React
- Adding the New To-Do
- Using `<form>` React Elements
- Preventing a `<form>` From Being Submitted
- Validating Data In a `<form>`
- Using State to Handle Multiple Inputs
- The Keys to Programming in React
- Final Version of the Fundamentals of React Chart
- Essential Questions
- Further Study
- References

## Setup

This lesson will build upon the "React To-Do" sandbox we've been working with during the last couple of lessons in [codesandbox.io](https://codesandbox.io/):

<img src="https://i.imgur.com/EPPyLEw.png">

## Attaching Event Handlers Using Event Props

### Browser Events in React

**❓ What are some common browser events we've worked with during SEI so far?**

In case you need to be reminded, [here you go!](https://developer.mozilla.org/en-US/docs/Web/Events).

Like many things in React, event handling is a little different than what we are used to.

Let's see how...

### Connecting Handler Code to Events in React

In React, we do not add event listeners using JavaScript's `addEventListener` method.

Instead, we assign event handling functions to "event" props, e.g., `onClick`, on React Elements (`<div>`, `<p>`, etc.).

> Note: React supports any browser event you will ever need as documented by [this list of supported events](https://reactjs.org/docs/events.html#supported-events)

Let's start by adding a `<button>` to for hiding/showing the to-dos when clicked:

```jsx
return (
  <div className="App">
    <h1>React To-Do</h1>
    {/* Add  button below */}
    <button>{showTodos ? 'HIDE' : 'SHOW'}</button>
    ...
```

> Note that any type of React Element can respond to click events, not just buttons.

Now we can use the `onClick` prop to attach an event handler, **which must be a function (this is important)**:

```jsx
<button onClick={alert}>{showTodos ? 'HIDE' : 'SHOW'}</button>
```

We're just passing the built-in `alert` function as a baby step.  When the button is clicked, React's event system will invoke the provided function, passing to it an event object.

Our goal is to toggle the boolean `showTodos` state value.  We have two approaches we can take:

1. Invoke the existing `setShowTodos` setter function inline, or
2. Write a separate function and provide that to the `onClick`

Since we don't have any significant logic to perform, we'll use option 1 and use option 2 for adding to-dos later.

<details><summary>❓ Due to something important mentioned above, why won't the following approach work?</summary>
<p>

**We need to provide a function, not invoke a function.**

</p>
</details>

```jsx
<button onClick={setShowTodos(!showTodos)}>{showTodos ? 'HIDE' : 'SHOW'}</button>
```

### Passing Arguments to Event Handlers

So, what's the solution if we need to pass arguments to an event handler function?  Check this out:

```jsx
<button onClick={() => setShowTodos(!showTodos)}>{showTodos ? 'HIDE' : 'SHOW'}</button>
```

As you can see, the fix is to wrap the call to `setShowTodos` with a function - thanks to their conciseness, arrow functions are great for this purpose!

Toggle those to-dos!

### Event Handling Summary

- The names for event props are camelCased (`onClick`). In HTML, the attribute would be `onclick`. Here's the [list of events](https://facebook.github.io/react/docs/events.html#supported-events) supported by React.

- The JS expression (always within curly braces) assigned to an event prop must evaluate to a **function**. A function type, **not** a function call (unless that function call returns a function).

- React automatically implements event delegation and makes event handling more efficient in a React app by managing events internally - check out React's [Synthetic Event Object](https://reactjs.org/docs/events.html) to learn more.

## Using "Controlled Inputs" in React

### Adding New To-Dos

To add new to-dos, we could just add additional JSX to the `<App>` component.

However, a better approach would be to create a separate component responsible for inputting a new to-do...

#### 💪 Practice Exercise - Create a new `<NewToDoForm>` Component (5 minutes)

1. Create a `<NewToDoForm>` component in its own module (named according to best practices).

2. `<NewToDoForm>` should just render an `<h2>New To-Do</h2>` for now.

3. In **App.js** below the `<ToDoList>` component, render an `<hr />` followed by the `<NewToDoForm>` component like this:

  <img src="https://i.imgur.com/lHw9V7D.png">

### Forms in React Are Not Required

Forms are not required to wrap input elements in SPAs because we send data to the server using AJAX, not by submitting a form. In fact, we need to prevent forms from being submitted to the server because it will cause the page to reload which SPAs avoid.

However, we often still use forms in React for validation, layout/styling using CSS frameworks, etc.

We'll begin by adding a to-do without using a form. Then, we'll add a form later to perform validation and to learn how to prevent them from accidentally triggering a full-page refresh when submitted.

### Controlled Components (`<input>`)

In a typical HTML page, input elements such as `<input>`, `<textarea>` and `<select>`, maintain their own internal state.

However, handling input the "React way" is different...

  <img src="https://i.imgur.com/YcDo3iJ.png">

1. The value of an input, i.e., what is displayed, is maintained by our own state in the component.

2. When React renders the input, it overrides the input's internal `value` property by binding to the `value` prop.

3. Updating the input's state value requires assigning an event handler function to the `onChange` prop.


This scenario, is what React refers to as a [controlled component/input](https://reactjs.org/docs/forms.html#controlled-components).

### Adding a Controlled `<input>`

Let's add the following JSX to **NewToDoForm.jsx**:

```jsx
export default function NewToDoForm() {
  return (
    <>
      <h2>New To-Do</h2>
      <input placeholder="New To-Do" />
      <button>ADD TO-DO</button>
    </>
  );
}
```

> Reminder: React Elements have props such as `placeholder` that provide the functionality of their HTML attribute equivalents.

Now let's make it a controlled input by first adding state for the `<input>` as mentioned in bullet point number `1.` above.

#### 💪 Practice Exercise - Add `newTodo` State (3 minutes)

1. Use the `useState` hook to add state named `newTodo`.

    > Hint: Don't forget to import `useState`

2. Initialize `newTodo` to an empty string.

3. You know what to name the setter - right?

### The Key to Controlled Inputs:  `value` & `onChange` Props 

All controlled inputs must include the following two props:

- `value`: This prop is used to bind the state to the input's value (what is displayed).

- `onChange`: This event prop will call the provided callback function whenever the user types in the input. Within the callback, we need to update the state variable bound to `value`.

### Bind State to the `value` Prop

Let's start by binding the `newToDo` state you just defined to the `value` prop of the `<input>` in **NewToDoForm.jsx**:

```jsx
<input value={newTodo} placeholder="New To-Do" />
```

Easy peasy - to check it out, try initializing the state to something other than empty string.

### Handling the `onChange` Event

You just saw how the `<input>` displays the value of the state it is bound to using the `value` prop.

However, try typing in the input - nothing happens because we need to update the state as the user types.

Here's a simple way for now:

```jsx
export default function NewToDoForm() {
  const [newTodo, setNewTodo] = useState("");
  return (
    <>
      <h2>New To-Do</h2>
      <input
        value={newTodo}
        onChange={(evt) => setNewTodo(evt.target.value)}
        placeholder="New To-Do" />
      <button>ADD TO-DO</button>
    </>
  );
}
```

When React invokes the handler (function), it passes in an event object as an argument for which we defined a parameter, `evt`. Then, just like in vanilla JS, the event object can be used to access the input's internal value via `evt.target.value`.

### ❓ Review Questions

1. What is wrong with the following code?

    ```jsx
    <div onClick={setStateValue(newValue)}>Click Me!</div>
    ```

2. True or False:  In a SPA, forms are required to send data to the server.

3. What are the two props that must be added to a controlled input in React?

## Adding the New To-Do

Now that we have the `<input>` working and know how to respond to events in React, we can add new to-dos by:

- Adding an `onClick` handler to the [ADD TO-DO] button.

- When the button is clicked, add the new to-do using the `setTodos` setter function.

- Clearing the input for a better UX.

### Adding the `onClick` Handler to the [ADD TO-DO] Button

We're not going to be able to perform all of the required logic inline this time, instead let's write an additional function within **NewToDoForm.jsx**:

```jsx
export default function NewToDoForm() {
  const [newTodo, setNewTodo] = useState("");

  // Add this new handler
  function handleAddTodo() {
    alert(newTodo);
  }

  ...
```

We're alerting the `newTodo` state value as a baby step.

Now let's attach the new handler by adding an `onClick` prop to the button:

```jsx
<button onClick={handleAddTodo}>ADD TO-DO</button>
```

<details><summary>❓ Why didn't we have to wrap <code>handleAddTodo</code> with an arrow function in this case?</summary>
<p>

**We don't need to provide any arguments to `handleAddTodo` when invoking it, thus we can simply provide the function itself.**

</p>
</details>

### Updating the `todos` State

A few questions...

<details><summary>❓ Which component "owns" the <code>todos</code> State?</summary>
<p>

**`<App>`**

</p>
</details>

<details><summary>❓ Which component "owns" the setter function used to update the <code>todos</code> State?</summary>
<p>

**`<App>`**

</p>
</details>

<details><summary>❓ Does the <code>&LT;NewToDoForm></code> have access to the <code>setTodos</code> setter function?</summary>
<p>

**No**

</p>
</details>

So, we could solve our dilemma by passing a reference to `setTodos` as a prop.  However, we also would need to pass a reference to the `todos` state as well to use with the spread operator.

We certainly could pass those props without much hassle, however, it just doesn't feel right - instead, it's a better practice to always update state within the component that owns that state, in this case, `<App>`.

Let's add a new function within **App.js** that we can then pass to `<NewToDoForm>` as a prop:

```jsx
const [showTodos, setShowTodos] = useState(true);

// Add this function
function addTodo(todo) {
  // Replace state, don't mutate it
  setTodos([...todos, todo]);
}
```

As discussed in the last lesson, we are using the spread syntax to include (spread) the current elements of the `todos` array within a new array literal, adding the new todo at the end.

#### 💪 Practice Exercise - Pass `addTodo` to the `<NewToDoForm>` Component (2 minute)

1. Pass the `addTodo` function from **App.js** to the `<NewToDoForm>` component using a prop with the same name.

2. Update `<NewToDoForm>` to destructure the `addTodo` prop being passed to it.

<hr />

Now we're ready to add the to-do by updating the `handleAddTodo` function in **NewToDoForm.jsx**:

```jsx
function handleAddTodo() {
  // alert(newTodo);
  addTodo(newTodo);
}
```

Try it out!

Now let's improve the UX...

#### 💪 Practice Exercise - Reset the `<input>` Back to an Empty String (1 minute)

- Improve the UX by adding a single line of code to `handleAddTodo` that clears out the value displayed in the `<input>`.

  > Hint:  Controlled inputs get their displayed value from state!

## Using `<form>` React Elements

Now that we've shown that using a `<form>` in React is optional, let's refactor "React To-Do" to use a `<form>` so that we can learn how to prevent them from being submitted to the server, etc.

### Add the `<form>` React Element

Let's start by refactoring to use a `<form>`:

```jsx
<form onSubmit={handleAddTodo}>
  <input
    value={newTodo}
    onChange={(evt) => setNewTodo(evt.target.value)}
    placeholder="To-Do"
  />
  <button type="submit">ADD TO-DO</button>
</form>
```

> Key Point: Forms in React will never have an `action` or `method` prop/attribute because they are never submitted to a server!

Note that we've:

- Removed the `onClick` from the button and changed its type to `type="submit"`

- Added the `onSubmit` event prop to the form - this is a more typical approach when working with forms.

With the above refactor, a new to-do will only appear for a second before the form triggers a refresh when the submit button is clicked...


## Preventing a `<form>` From Being Submitted

To prevent a form from being submitted, we need to invoke the `preventDefault()` method on the event object.

First we need to add a parameter to the `handleAddTodo` function to accept the event object that React passes automatically:

```jsx
//
function handleAddTodo(evt) {
  ...
```

Next, we invoke the `preventDefault()` method first thing:

```jsx
function handleAddTodo(evt) {
  evt.preventDefault();
  addTodo(newTodo);
  setNewTodo("");
}
```

Now there's no more page refresh when adding a new to-do!

## Validating Data In a `<form>`

Because all of the data for a form's inputs will be held in state, it's possible to validate that state every time it changes using code in the handler; setting additional state, e.g, `isValid`, accordingly.

However, we can easily take advantage of the form's HTML5 validation capabilities to ensure that data has been entered as desired.

As we saw in the lesson on Regular Expressions, we can add a `required` and `pattern` attribute to HTML inputs to validate their data. React works with those props work too!

For example, let's prevent empty to-dos from being created:

```jsx
<input
  value={newTodo}
  onChange={(evt) => setNewTodo(evt.target.value)}
  placeholder="To-Do"
  required
  pattern=".{4,}"
/>
```

Now, thanks to built-in HTML5 validation, the form cannot be submitted unless at least 4 characters are entered!

We've only scratched the surface of validation built-into browsers.  You can begin to learn more by reading about the comprehensive [constraint validation Web API here](https://developer.mozilla.org/en-US/docs/Web/API/Constraint_validation).

## Using State to Handle Multiple Inputs

We've seen how to handle a single input within a form.  However, we'll usually need to use several inputs for gathering all of the data we need.

Since "React To-Do" is a wrap, let's create a new sandbox where we can add a form with multiple inputs that will also help you with the lab.

### Set Up the New Form

Copy and paste this into the **App.js**:

```jsx
import "./styles.css";

export default function App() {
  return (
    <div className="App">
      <form>
        <label>NAME</label>
        <input name="name" />
        <label>EMOTION</label>
        <select name="emotion">
          <option value="😁">Happy</option>
          <option value="😐">Neutral</option>
          <option value="😠">Angry</option>
        </select>
      </form>
    </div>
  );
}
```

We are only using a `<form>` as a "container" for the inputs - there isn't even a submit button.

Sure, there's only two inputs in this example, but the approach we're going to use applies to any number of inputs.

Here's just a bit of CSS to add to **App.css**:

```css
form {
  display: grid;
  grid-template-columns: auto auto;
  gap: 0.5rem;
  width: 20rem;
  text-align: left;
  font-size: 1.5rem;
}
```

### Do We Really Need a State Variable For Each Input?

Imagine that we had a form with a dozen or more inputs.  Based on what you've seen thus far you might think that you would need to have a dozen or more state variables with their own setter functions, etc.

Having dedicated state for each input is not only verbose, it's also not convenient when having to send that data to a server.

Instead, as we learned in the lesson about state, a single state can be anything, including an object and that's our ticket:

```jsx
export default function App() {
  const [formData, setFormData] = useState({
    name: "",
    emotion: "😁"
  });
  ...
```

It's no coincidence that the name of the properties on the `formData` object match the names assigned to the `name` props on the inputs. Doing so allows for the following concise `onChange` handler that will update the state for any number of inputs.

### Add the `onChange` Handler Function

Here's the only handler function we need:

```jsx
export default function App() {
  const [formData, setFormData] = useState({
    name: "",
    emotion: "😁"
  });

  function handleChange(evt) {
    // Replace with new object and use a computed property
    // to update the correct property
    const newFormData = { ...formData, [evt.target.name]: evt.target.value };
    setFormData(newFormData);
  }
  ...
```

> [Computed property names](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#Computed_property_names) allow for a JS expression to dynamically determine the key of the property.

Similar to how we used the spread operator with arrays, we're using it here to first spread all of the existing properties within a new object literal.  Then, any additional properties are comma separated and are either added to the object, or used to updated existing properties.

### Bind the Handler to the `onChange` Event

Each input needs to have an `onChange` prop added so that the handler is invoked:

```jsx
<input name="name" onChange={handleChange} />
...
<select name="emotion" onChange={handleChange}>
```

> Note: We don't use event delegation in React because React's event system is implementing it automatically behind the scenes.

That's all it takes!  We could use React Developer Tools to verify it's working, but let's add an `<h1>` to display the results instead:

```jsx
...
</form>
<h1>{formData.name} is {formData.emotion}</h1>
```

## The Keys to Programming in React

Now that you've worked a bit with the fundamentals of React, let's look a few **key** thoughts every React developer considers when developing a React application - whether they know it or not:

1. **We code components to render (visualize) application-state**, for example, render a `<ToDoListItem>` component for each to-do in the `todos` application-state array.
2. **We can code components to render other components based upon UI-state**, for example, hide/show a component based upon `showDetails` UI-state, disable a button based upon `isValid`, etc.
3. **In response to user-interaction, we apply any necessary program logic and/or calculations and ultimately update all impacted state causing the components to re-render.**

## Final Version of the Fundamentals of React Chart

Here is the completed [Fundamentals of React Chart](./../react-fundamentals.md) that is excellent to review from time-to-time, make flash cards from, or read before bedtime 😃

The following has been added from this lesson...

| React Fundamental | Summary |
|---|---|
| ... | ... |
| Event Handling | <ul><li>Instead of using `addEventListener`, in React we connect event handlers (functions) to events using event props on React Elements.</li><li>Examples of event props are: `onClick`, `onChange`, `onSubmit`, etc.</li></ul> |
| Handling Input | <ul><li>[Controlled Inputs](https://reactjs.org/docs/forms.html#controlled-components) are the React way to gather input from the user with `<input>`, `<select>` or `<textarea>` React Elements.</li><li>A controlled input must include both `value` & `onChange` props.</li><li>Forms are optional in a SPA but they can be beneficial for validation & CSS layout/formatting. If forms are used, be sure to prevent them from being submitted to the server by calling `preventDefault()` on the event object from within the `onSubmit` event handler.</li></ul> |
| **The Keys to Programming in React** | <ul><li>**We code components to render (visualize) application-state**, for example, render a `<ToDoListItem>` component for each to-do in the `todos` application-state array.</li><li>**We can code components to render other components based upon UI-state**, for example, hide/show a component based upon `showDetails` UI-state, disable a button based upon `isValid`, etc.</li><li>**In response to user-interaction, we apply any necessary program logic and/or calculations and ultimately update all impacted state causing the components to re-render.**</li></ul> |

#### Congrats on Handling Input and Events in React!

## ❓ Essential Questions

1. A controlled input displays the value of the state assigned to its ________ prop.

2. A controlled input must use a ________ prop to bind a handler function.

3. What must the above handler function's code update?

4. What method needs to be invoked to prevent a form from triggering a full-page refresh?

## References

- [React Docs - Synthetic Events](https://reactjs.org/docs/events.html)




<img src="https://i.imgur.com/pg98OTd.png">

# React Dev Skills Lab - Part 4

## Intro

This lab provides an opportunity to practice:

- Using the `value` and `onChange` props to implement controlled inputs.
- Implementing event handlers.
- Updating state by replacing objects instead of mutating them.
- Passing a method from a parent component to a child component via a prop.

##### This lab, combined with Parts 1, 2 & 3 is a Deliverable

## Exercises

1. Open your "react-dev-skills" sandbox that you created back in Part 1.

2. Add state to the existing `<NewSkillForm>` component that will be used to manage the form's state. The state should be initialized as an object with two properties: `name` and `level` - by design, these properties match the names of the properties of the skill objects held in state (App.js). The `name` property should be initialized to an empty string and the `level` property should be initialized to a number of `3`.

3. Add `value` props to each `<option>` tag and assign the **numbers** 1 thru 5 like this:

    ```jsx
    <option value={1}>1</option>
    ```
    > Remember, unlike attributes in HTML which always hold strings, props in React can hold any type of data.

4. Following the steps in the lesson, make the `<input>` and `<select>` controlled inputs that update the form's state you created in step 2.

    > Hint:  As in the lesson, use computed property names so that a single onChange handler can be used for any number of inputs.

5. Make the form's button a submit button and add an `onSubmit` prop to the `<form>`.  Assign an event handler to `onSubmit` and ensure that the form does not trigger a full-page refresh when the button is clicked!

6. Following the steps in the lesson, code the app so that when the [ADD SKILL] button is clicked, the new Dev Skill is added to the `skills` state held in **App.js**. The app should re-render and display the new skill.

    > Hint: App.js needs a function that will update the state and that function will need to be passed to the `<NewSkillForm>` component.

7. For a better UX, after the new skill is added, the form should reset to the same values used to initialized the state.

## This lab combined with Parts 1, 2 & 3 is a Deliverable


<!-- {% raw %} -->

<img src="https://i.imgur.com/VunmGEq.jpg">

# React To-Do - Practice Lab

## Intro

You've learned the basics of a React app including:

- How to compose an app's UI using Function Components 
- How to define a component's UI using JSX
- How to pass props from a parent to a child component
- How to style React Elements
- How to encapsulate state within a component using the `useState` hook
- How to update state with the setter function provided by the `useState` hook
- How to use forms and controlled inputs
- How to handle browser events

This lab will provide you the opportunity to practice the above skills by adding the following user stories to the existing React To-Do app:

- AAU, I want to be able to mark to-dos as completed so that I can remove them from the list.
- AAU, I want to see the text of a completed to-do rendered with a line through it.
- AAU, I want to be able to remove a completed to-do from the list.

## Setup

Continue to build upon the "React To-Do" sandbox we've been working with during the lessons in [codesandbox.io](https://codesandbox.io/):

<img src="https://i.imgur.com/BHDBkZM.png">

## Exercises & Hints

### AAU, I want to be able to mark to-dos as completed so that I can remove them from the list

#### Hints:

- Since each to-do needs to track whether or not it's completed, start by refactoring the `todos` state from being an array of simple strings to an array of to-do objects like the following:

  ```jsx
  const [todos, setTodos] = useState([
    {text: "Have Fun", completed: true},
    {text: "Learn React", completed: false},
    {text: "Learn the MERN-Stack", completed: false}
  ]);
  ```

- The above refactor requires a minor change to `<ToDoListItem>` because the `todo` prop it's receiving is now an object instead of a string - `<ToDoListItem>` should now render the `text` property of `todo`.

- Now when adding a new to-do, an object should be added with a `completed` property set to `false` and its `text` property set to the text of the new to-do.  The app should now be working again - a refresh of the sandbox may be required if it gets "stuck".

- The UI should display a button with a ❌ used to delete the to-do if the to-do is completed.  Otherwise, display a button with a ✔️ used to update the to-do as completed: 

  <img src="https://i.imgur.com/eyyt7Xy.png">

  > The styling is up to you. The only change necessary to display the above is to update `justify-content` to `space-between` in **ToDoListItem.css**:

  <img src="https://i.imgur.com/HLy4DMd.png" width="70%">

- Update a to-do's `completed` property to `true` when the  ✔️ is clicked.  We should update the `todos` state from within the `<App>` component - refer to the existing code that adds a to-do.

- You'll need to pass the function responsible for updating the to-do from `<App>` all the way down to `<ToDoListItem>`. Don't forget to destructure the props!

- Because a to-do is now an object, when updating it, both the `todos` array and the to-do object should be replaced, not mutated. The `map` method can be handy here.<br>
  <details><summary>Don't Peek Unless You Have To...</summary>

  ```js
  function completeTodo(todoIdx) {
    const newTodos = todos.map((t, idx) =>
      idx === todoIdx ? { text: t.text, completed: true } : t
    );
    setTodos(newTodos);
  }
  ```

  </details>

### AAU, I want to see the text of a completed to-do rendered with a line through it

#### Hints:

- Use either the `style` prop or dynamically apply a CSS class with a declaration of<br>`text-decoration: line-through`.

- Regardless of the approach you take, you'll want to wrap the to-do's text with a `<span>` React Element and apply the styling to the `<span>`.<br>

  <details><summary>Don't Peek Unless You Have To...</summary>

  ```js
  <span style={{ textDecoration: todo.completed && "line-through" }}>
    {todo.text}
  </span>
  ```

  </details>

  <img src="https://i.imgur.com/iwMBSi4.png">

### AAU, I want to be able to remove a completed to-do from the list

- Very much like marking a to-do as complete, however, the `filter` method is your go to in this case. 

Congrats!

<img src="https://i.imgur.com/hY21Tbu.png">

## Deliverable?

This lab is **not** a deliverable.

<!-- {% endraw %} -->



