# REACT KEY CONCEPTS

## React – What and Why

> **Learning Objectives**
> By the end of this chapter, you will be able to answer the following questions:
>
> -   **What is React?**
> -   React is a JavaScript library that simplifies building (complex) user interfaces for any platform since its platform-agnostic.
> -   **Why would you use React?**
> -   I would use React because it simplifies the creation of (complex) user interfaces by generating and executing DOM-manipulating instructions "under the hood", on my behalf. This leaves me to focus on describing the desired target UI state(s) and the core business logic. I don't have to control all the UI updates and changes manually.
> -   **What is the comparison of web projects build with React, to web projects built with just JavaScript?**
> -   Advanced web projects build with just JavaScript quickly become very cumbersome and error prone because you have to write down all instructions step by step since JavaScript is an _imperative_ code. If you want to listen to a button click and then change some text on the screen, you have to add the code that sets up the event listener and then also the code that selects the to-be-changed element as well as the code that does set a new text for that element. For non-trivial user interfaces, this can lead to lots of overhead work and possible error sources.
> -   React simplifies the creation of (complex) web user interfaces by generating and executing DOM-manipulating instructions "under the hood", on your behalf. As a developer, you can focus on describing the desired target UI state(s) and the core business logic. You don't have to control all UI updates and changes manually. This is what makes React a _declarative_ code.
> -   **How do you create new React web projects?**
> -   I use the [create-react-app tool](https://reactjs.org/docs/create-a-new-react-app.html) to scaffold new React projects which already have all the packages (like `react` and `react-dom`) that are needed to build web projects with React. In addition, those projects also come with some code transformation tools and a workflow that enables the usage of special features like JSX code (markup code for React apps).
> -   New projects can be created with that tool by running `npx create-react-app project-name`.
> -   These projects also provide a development server which can be started via `npm start` to preview the React web app locally and get live updates as you make code changes.

### Introduction

-   **React** is one of the most popular frontend JavaScript libraries—maybe
    even the most popular one. It is currently used by over 5% of the top 1,000 websites and compared to other popular frontend JavaScript frameworks like Angular, React is leading by a huge margin, when looking at key metrics like weekly package downloads via npm (Node Package Manager), which is a tool commonly used for downloading and managing JavaScript packages.
-   Though it is certainly possible to write good React code without fully understanding how React works and why you're using it, you should always aim to understand the tools you're working with as well as the reasons for picking a certain tool in the first place.
-   Therefore, before considering anything about its core concepts and ideas or
    reviewing example code, you first need to understand what React actually is and why it exists. This will help you understand how React works internally and why it offers the features it does.
-   If you already know why you're using React, why solutions like React in general are being used instead of vanilla JavaScript (i.e. JavaScript without any frameworks or libraries, more on this in the next section), and what the idea behind React and its syntax is, you may of course skip this section and jump ahead to the more practice-oriented chapters later in this book.
-   But if you only think that you know it and are not 100% certain, you should definitely follow along with this chapter first.

### What Is React?

-   React is a JavaScript library, and if you take a look at the official webpage (Official React website and documentation: https://reactjs.org), you learn that it's actually a _"JavaScript library for building user interfaces"._
-   But what does this mean?
-   It should be clear what JavaScript is and why you use JavaScript in the browser (React is mostly a browser-side JavaScript library). JavaScript allows you to add interactivity to your website since, with JavaScript, you can react to user events and manipulate the page after it was loaded. This is extremely valuable as it allows you to build highly interactive web user interfaces.
-   But what is a "library" and how does React help with "building user interfaces"?
-   While you can have philosophical discussions about what a library is (and how it differs from a framework), the pragmatic definition of a library is that it's a collection of functionalities that you can use in your code to achieve results that would normally require more code and work from your side. Libraries help you write better and shorter code and enable you to implement certain features more quickly. In addition, since you can focus on your "core business logic", you not only move faster but are also likely to produce better code since you don't have to reinvent the wheel for problems that have been solved before by others.
-   React is such a library — one that focuses on providing functionalities that help you create interactive and reactive user interfaces. Indeed, React deals with more than web interfaces (i.e. websites loaded in browsers). You can also build native mobile devices with React and React Native, which is another library that utilizes React under the hood. No matter which platform you're targeting though, creating interactive user interfaces with just JavaScript can quickly become very complex and overwhelming.
    > **NOTE**
    > The focus of this book is on React in general, and for simplicity, the focus lies on React for websites. With projects like React Native, you can also use React to build user interfaces for native mobile apps. The React concepts covered in this book still apply, no matter which target platform is chosen. But examples will focus on React for web browsers.

### The Problem with "Vanilla JavaScript"

-   Vanilla JavaScript is a term commonly used in web development for referring to "JavaScript without any frameworks or libraries". That means, you write all the JavaScript on your own, without falling back to any libraries or frameworks that would provide extra utility functionalities. When working with vanilla JavaScript, you especially don't use major frontend frameworks or libraries like React or Angular.
-   Using vanilla JavaScript generally has the advantage, that visitors of a website have to download less JavaScript code (as major frameworks and libraries typically are quite sizeable and can quickly add 50+ kb of extra JavaScript code that has to be downloaded).
-   The downside of relying on vanilla JavaScript is, that you, as the developer, must implement all functionalities from the ground up on your own. This can be errorprone and highly time consuming. Therefore, especially more complex user interfaces and websites can quickly become very hard to manage with vanilla JavaScript.
-   React simplifies the creation and management of such user interfaces by moving
    from an imperative to a declarative approach. Though this is a nice sentence, it can be hard to grasp if you haven't worked with React or similar frameworks before. To understand it and the idea behind "imperative vs declarative approaches" and why you might want to use React instead of just vanilla JavaScript, it's helpful to take a step back and evaluate how vanilla JavaScript works.
-   Here's a short code snippet that shows how you could handle the following user
    interface actions with vanilla JavaScript:

1. Add an event listener to a button to listen for "click" events.
1. Replace the text of a paragraph with new text once a click on the button occurs.

```js
const buttonElement = document.querySelector("button");
const paragraphElement = document.querySelector("p");

function updateTextHandler() {
    paragraphElement.textContent = "Text was changed!";
}

buttonElement.addEventListener("click", updateTextHandler);
```

-   This example is deliberately kept simple, so it's probably not looking too bad or overwhelming. It's just a basic example to show how code is generally written with vanilla JavaScript (a more complex example will be discussed below). But even though this example is very straightforward and easy to digest, working with vanilla JavaScript will quickly reach its limits for feature-rich user interfaces and the code to handle various user interactions therefore also becomes more complex. Code can quickly grow significantly, and therefore maintaining it can become a challenge.
-   In the preceding example, code is written with vanilla JavaScript and, therefore, imperatively. This means that you write instruction after instruction, and you describe every step that needs to be taken in detail.
-   The code shown above could be translated to these more human-readable instructions:

1. Look for an **HTML** element of type `button` to obtain a reference to the first button on the page.
2. Create a constant (i.e., a data container) named `buttonElement` that holds that `button` reference.
3. Repeat step 1 but get a reference to the first element that is of type of `p`.
4. Store the paragraph element reference in a constant named `paragraphElement`.
5. Add an event listener to the `buttonElement` that listens for click events and triggers the `updateTextHandler` function whenever such a `click` event occurs.
6. Inside the `updateTextHandler` function, use the paragraphElement to set its `textContent` to "Text was changed!".

-   Do you see how every step that needs to be taken is clearly defined and written out in the code?
-   This shouldn't be too surprising because that is how most programming languages work: you define a series of steps that must be executed in order. It's an approach that makes a lot of sense because the order of code execution shouldn't be random or unpredictable.
-   But when working with user interfaces, this imperative approach is not ideal. Indeed, it can quickly become cumbersome because, as a developer, you have to add a lot of instructions that despite adding little value, cannot simply be omitted. You need to write all the DOM (**Document Object Model**) instructions that allow your code to interact with elements, add elements, manipulate elements. etc.

> **NOTE**
> This book assumes that you are familiar with the DOM (Document Object Model). In a nutshell, the DOM is the "bridge" between your JavaScript code and the HTML code of the website with which you want to interact. Via the built-in DOM API, JavaScript is able to create, insert, manipulate, delete, and read HTML elements and their content. You can learn more about the DOM in this article: https://academind.com/tutorials/what-is-the-dom.

-   Modern web user interfaces are often quite complex, with lots of interactivity going on behind the scenes. Your website might need to listen for user input in an input field, send that entered data to a server to validate it, output a validation feedback message on the screen, and show an error overlay modal if incorrect data is submitted.
-   This is not a complex example in general, but the vanilla JavaScript code for implementing such a scenario can be overwhelming. You end up with lots of DOM selection, insertion, and manipulation operations, as well as multiple lines of code that do nothing but manage event listeners. And keeping the DOM updated, without introducing bugs or errors, can be a nightmare since you must ensure that you update the right DOM element with the right value at the right time. Below, you will find a screenshot of some example code for the described use-case.
-   **NOTE**
-   The full, working, code can be found on GitHub at https://packt.link/tLSLU.
-   If you take a look at the JavaScript code in the screenshot (or in the linked repository), you will probably be able to imagine how a more complex user interface is likely to look.

```html
<!-- examples\example-1\vanilla-javascript\index.html -->

<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta
            name="viewport"
            content="width=device-width, initial-scale=1.0"
        />
        <title>Vanilla JavaScript Example</title>
        <link rel="preconnect" href="https://fonts.googleapis.com" />
        <link
            rel="preconnect"
            href="https://fonts.gstatic.com"
            crossorigin
        />
        <link
            rel="stylesheet"
            href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap"
        />
        <link rel="stylesheet" href="styles.css" />
        <script src="app.js"></script>
    </head>
    <body>
        <header>
            <h1>Create a New Account</h1>
        </header>
        <main>
            <form>
                <div class="form-control">
                    <label for="email">Email</label>
                    <input type="email" id="email" />
                </div>
                <div class="form-control">
                    <label for="password">Password</label>
                    <input type="password" id="password" />
                </div>
                <button>Create User</button>
            </form>
        </main>
        <footer>
            <p>(c) Maximilian Schwarzmuller</p>
            <p>
                This is just a dummy example - not a fully functional
                website or anything like that.
            </p>
        </footer>
    </body>
</html>
```

```css
/* examples\example-1\vanilla-javascript\styles.css */

* {
    box-sizing: border-box;
}

html {
    font-family: "Roboto", sans-serif;
}

body {
    margin: 0;
    background-color: #f6f5fb;
    color: #262527;
}

header {
    margin-top: 3rem;
    height: 5rem;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #2d0d58;
}

footer {
    text-align: center;
    color: #6a666e;
}

button {
    font: inherit;
    padding: 0.5rem 1.5rem;
    border-radius: 4px;
    background-color: #d36f11;
    border: 1px solid #d36f11;
    color: white;
    cursor: pointer;
}

button:hover,
button:active {
    background-color: #d39611;
    border-color: #d39611;
}

main form {
    max-width: 30rem;
    margin: 2rem auto;
    padding: 2rem;
    border-radius: 6px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
    background-color: #2d0d58;
    color: white;
    text-align: center;
}

label {
    display: block;
    font-weight: bold;
    margin-bottom: 0.5rem;
}

input {
    width: 80%;
    font: inherit;
    padding: 0.25rem;
    background-color: #f3edfb;
    border: none;
    border-radius: 4px;
}

input:focus {
    background-color: #dcc3fd;
}

.form-control {
    margin-bottom: 1rem;
}

.backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    z-index: 1;
    background-color: rgba(0, 0, 0, 0.7);
}

.modal {
    position: fixed;
    top: 20vh;
    left: calc(50% - 20rem);
    width: 40rem;
    z-index: 2;
    border-radius: 6px;
    overflow: hidden;
    background-color: white;
}

.modal header h2 {
    margin: 0;
}

.modal section {
    padding: 1rem;
}

.modal__actions {
    text-align: right;
}
```

```js
// examples\example-1\vanilla-javascript\app.js

const emailInputElement = document.getElementById("email");
const passwordInputElement = document.getElementById("password");
const signupFormElement = document.querySelector("form");

let emailIsValid = false;
let passwordIsValid = false;

function validateEmail(enteredEmail) {
    /*
    In reality, we might be sending the entered email address to a backend API 
    to check if a user with that email exists already. Here, this is faked with 
    help of a promise wrapper around some dummy validation logic.
    */
    const promise = new Promise(function (resolve, reject) {
        if (enteredEmail === "test@test.com") {
            reject(new Error("Email exists already"));
        } else {
            resolve();
        }
    });
    return promise;
}

function validatePassword(enteredPassword) {
    if (enteredPassword.trim().length < 6) {
        throw new Error(
            "Invalid password - must be at least 6 characters long."
        );
    }
}

async function validateInputHandler(inputType, event) {
    const targetElement = event.target;
    const enteredValue = targetElement.value;

    let validationFn = validateEmail;
    if (inputType === "password") {
        validationFn = validatePassword;
    }

    const errorElement = document.getElementById(
        inputType + "-error"
    );
    if (errorElement) {
        errorElement.remove();
    }

    let isValid = true;

    try {
        await validationFn(enteredValue);
    } catch (error) {
        const errorElement = document.createElement("p");
        errorElement.id = inputType + "-error";
        errorElement.textContent = error.message;
        targetElement.parentElement.append(errorElement);
        isValid = false;
    }

    if (inputType == "email") {
        emailIsValid = isValid;
    } else {
        passwordIsValid = isValid;
    }
}

function submitFormHandler(event) {
    event.preventDefault();

    let title = "An error occured";
    let message =
        "Invalid input values - please check your entered values.";

    if (emailIsValid && passwordIsValid) {
        title = "Success!";
        message = "User created successfully!";
    }
    openModal(title, message);
}

function openModal(title, message) {
    const backdropElement = document.createElement("div");
    backdropElement.className = "backdrop";

    const modalElement = document.createElement("aside");
    modalElement.className = "modal";
    modalElement.innerHTML = `
        <header>
            <h2>${title}</h2>
        </header>
        <section>
            <p>${message}</p>
        </section>
        <section class="modal__actions">
            <button>Okay</button>
        </section>
    `;
    const confirmButtonElement = modalElement.querySelector("button");

    backdropElement.addEventListener("click", closeModal);
    confirmButtonElement.addEventListener("click", closeModal);

    document.body.append(backdropElement);
    document.body.append(modalElement);
}

function closeModal() {
    const modalElement = document.querySelector(".modal");
    const backdropElement = document.querySelector(".backdrop");

    modalElement.remove();
    backdropElement.remove();

    emailInputElement.addEventListener(
        "blur",
        validateInputHandler.bind(null, "email")
    );
    passwordInputElement.addEventListener(
        "blur",
        validateInputHandler.bind(null, "password")
    );
}

emailInputElement.addEventListener(
    "blur",
    validateInputHandler.bind(null, "email")
);

passwordInputElement.addEventListener(
    "blur",
    validateInputHandler.bind(null, "password")
);

signupFormElement.addEventListener("submit", submitFormHandler);
```

-   This example JavaScript file already contains roughly 110 lines of code. Even after minifying ("minifying" means that code is shortened automatically, e.g. by replacing long variable names with shorter ones and removing redundant whitespace; in this case via https://javascript-minifier.com/) it and splitting the code across multiple lines thereafter (to count the raw lines of code), it still has around 80 lines of code. That's a full 80 lines of code for a simple user interface with only basic functionality. The actual business logic (i.e., input validation, determining if and when overlays should be shown, and defining the output text) only makes up a small fraction of the overall codebase—around 20 to 30 lines of code, in this case (around 20 after minifying).
-   That's roughly 75% of code spent on pure DOM interaction, DOM state management,and similar boilerplate tasks.
-   As you can see by these examples and numbers, controlling all the UI elements and their different states (e.g., whether an info box is visible or not) is a challenging task and trying to create such interfaces with just JavaScript often leads to complex code that might even contain errors.
-   That's why the imperative approach, wherein you must define and write down single step, has its limits in situations like this. This is the reason why React provides utility functionalities that allow you to write code differently: with a declarative approach.

> **NOTE**

-   This is not a scientific paper, and the preceding example is not meant to act as an exact scientific study. Depending on how you count lines and which kind of code you consider to be "core business logic", you will end up with higher or lower percentage values. The key message doesn't change though: Lots of code (in this case most of it) deals with the DOM and DOM manipulation—not with the actual logic that defines your website and its key features.

### React and Declarative Code

-   Coming back to the first, simple, code snippet from above, here's that same code snippet, this time using React:

```jsx
import { useState } from "react";

function App() {
    const [outputText, setOutputText] = useState("Initial text");

    function updateTextHandler() {
        setOutputText("Text was changed!");
    }

    return (
        <>
            <button onClick={updateTextHandler}>
                Click to change text
            </button>
            <p>{outputText}</p>
        </>
    );
}
```

- This snippet performs the same operations as the first did with just vanilla JavaScript:

1. Add an event listener to a button to listen for `click` events (now with some  React-specific syntax: `onClick={…}`).
1. Replace the text of a paragraph with new text once the click on the button occurred.

- Nonetheless, this code looks totally different—like a mixture of JavaScript and HTML. And indeed, React uses a syntax extension called **JSX** (i.e., JavaScript with embedded XML). For the moment, it's enough to understand that this JSX code will work because of a **pre-processing** step that's part of the build workflow of every React project.
- Pre-processing means that certain tools, which are part of React projects, analyze and transform the code before its deployed. This allows for development-only syntax like JSX which would not work in the browser and is therefore transformed to regular JavaScript before deployment. (You'll get a thorough introduction into JSX in Chapter 2, Understanding React Components and JSX.)

### How React Manipulates the DOM

### Introducing Single Page Applications

### Creating a React Project

### Summary and Key Takeaways

### What's Next?

### Test Your Knowledge!

**1. What is React?**

-   React (or React.js) is a JavaScript library that simplifies building (complex) user interfaces.
-   It's exposed through the [react](https://www.npmjs.com/package/react) package, and combined with the [react-dom](https://www.npmjs.com/package/react-dom) package, you can use it to build advanced, highly interactive and reactive web user interfaces.
-   React is platform-agnostic though, you can also use it with other platforms - most notably, you can build native mobile apps with React and the [react-native](https://www.npmjs.com/package/react-native) package.

**1. Which advantage does React offer over vanilla JavaScript projects?**

-   With "vanilla JavaScript" (i.e. JavaScript without any extra libraries or frameworks), you have to write all code instructions yourself.
-   For basic web apps and user interfaces, this is typically no problem but for more advanced use-cases, it can quickly become very cumbersome and error prone to use just vanilla JavaScript (also see the next question: _Imperative vs declarative code_).
-   React simplifies the creation of (complex) web user interfaces by generating and executing DOM-manipulating instructions "under the hood", on your behalf. As a developer, you can focus on describing the desired target UI state(s) and the core business logic. You don't have to control all UI updates and changes manually.

**1. What’s the difference between imperative and declarative code?**

-   With **imperative code**, you write down all instructions step by step. If you want to listen to a button click and then change some text on the screen, you have to add the code that sets up the event listener and then also the code that selects the to-be-changed element as well as the code that does set a new text for that element. For non-trivial user interfaces, this can lead to lots of overhead work and possible error sources.
-   When writing code _declaratively_, you don't write down all steps that lead to a certain result. Instead, as a developer, you describe the target (UI) state(s) and let some library (in this case: React) figure out how to get there. This allows you to skip the overhead work of selecting DOM elements and changing them manually and focus on your core business logic instead.

**1. What is a Single-Page-Application (SPA)?**

-   A SPA is a web app that is technically served on one page (one HTML document) only. That page loads some JavaScript code (typically combined with some library like React) that takes care about updating the page content based on different user actions. To the user, it might seem like they are navigating different pages but technically, it's the same page's DOM getting updated behind the scenes.
-   You can even listen to changes in the page path to update the DOM based on path changes - this increases the "multi page feeling". When working with React, the react-router package is the most popular package for listening to such path changes and updating the UI based on any changes.

**1. How can you create new React projects and why do you need such a more complex project setup?**

-   New React projects can be created in different ways but one of the most popular and easiest ways of setting up a new React project is to use the[ create-react-app tool](https://reactjs.org/docs/create-a-new-react-app.html).
-   This is a tool which you can use to scaffold new React projects which already have all the packages (like react and react-dom) that are needed to build web projects with React. In addition, those projects also come with some code transformation tools and a workflow that enables the usage of special features like _JSX code_ (markup code for React apps).
-   New projects can be created with that tool by running `npx create-react-app project-name`.
-   These projects also provide a development server which can be started via `npm start` to preview the React web app locally and get live updates as you make code changes.
