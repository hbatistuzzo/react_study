![GitHub top language](https://img.shields.io/github/languages/top/hbatistuzzo/react_study)
![GitHub commit activity](https://img.shields.io/github/commit-activity/m/hbatistuzzo/react_study)
![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/hbatistuzzo/react_study)
![GitHub last commit](https://img.shields.io/github/last-commit/hbatistuzzo/react_study)

> __Warning__ In Progress!


<div align="center">
  <img alt="REACT " width="150" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/react/react-original.svg" />
</div>

<br>

## $\color{orange}{\textrm{First things first}}$

React (React.js or ReactJS) is a free and open-source front-end JavaScript library maintained by Meta and its community. This study will focus on the React Native library for mobile app development, while also covering the essentials from the core library.

🔹React Native: has 2 main parts, the graphical interface (UI, developed with JSX) and the logic through javascript. JSX generates native components either for iOS or Android. The logic will work inside runtimes through Webkit (for iOS) or V8 (for Android).

## $\color{orange}{\textrm{First Attempts!}}$

🔹 `npm install` in the project folder will download and install any 3rd party packages needed for a project, for example the react libraries and the build process tools that transform the React code to code that works in the browser. This is done by the inspection of the package.json file.

🔹 `npm run dev` starts the development server so that we can preview the website where the React app is in action.

Now we can set up the overarching structure of our project:
- a src folder where we will store .jsx and .css code
- an index.html file
- a vite.config.js file

>__OBS:__ JSX stands for JavaScript eXtension, used to describe & create HTML elements in JavaScript in a *declarative* way. it's **not** supported by browsers. React projects come with a build process that transforms JSX code (under the hood) to code that **does work** in the browser.

the App.jsx file _is_ a React component, which in this case is just a javascript function. Well, one that must follow 2 rules:
- function name must start with an uppercase character (PascalCase suggested)
- returns renderable value e.g. the to-be-rendered HTML markup.

Suppose I have code describing a simple header and body:
```
function App() {
  return (
    <div>
      <header>
        <img src="src/assets/react-core-concepts.png" alt="Stylized atom" />
        <h1>React Essentials</h1>
        <p>
          Fundamental React concepts you will need for almost any app you are
          going to build!
        </p>
      </header>
      <main>
        <h2>Time to get started!</h2>
      </main>
    </div>
  );
}

export default App;
```

This constitutes a component. Well I can just add another function above the App function to create a new component, separating the head from the body. We should probably rename our file from App.jsx to Decapitate.jsx now.
> [!TIP]
> Shift + Alt + F to format code in VSC. It'll wrap stuff in parenthesis if needed, etc.

To run it, we just need to "call" the Header function on the App function below:

```
function Header() {
  return (
    <header>
      <img src="src/assets/react-core-concepts.png" alt="Stylized atom" />
      <h1>React Essentials</h1>
      <p>
        Fundamental React concepts you will need for almost any app you are
        going to build!
      </p>
    </header>
  );
}

function App() {
  return (
    <div>
      <Header />
      <main>
        <h2>Time to get started!</h2>
      </main>
    </div>
  );
}

export default App;
```

Now, the index.jsx file imports the App we've created in App.jsx, as seen below:

```
import ReactDOM from "react-dom/client";

import App from "./App.jsx";
import "./index.css";

const entryPoint = document.getElementById("root");
ReactDOM.createRoot(entryPoint).render(<App />);
```

It's then rendered through a method of the ReactDOM library. Hence, the index.jsx is **the entry point of our React App** since it's the first file to be loaded by the index.html file.

Let's reinforce some theoreticals:
- JSX is a syntax extension for JavaScript often used with React to describe what the UI should look like. It allows developers to write HTML-like code directly in their JavaScript files, making it easier to create and manage user interfaces
- It has an easier and more readable syntax
- It's declarative, which means you can describe what the UI should look like in a straightforward manner.

**What does React do with the components you use in the JSX code?**
- When you use components in JSX, React processes them to produce the final UI that appears on the screen. Through a tool like Babel, JSX is translated to plain JavaScript. Components are rendered, React constructs a virtual DOM which is then used to update the real DOM through Reconciliation.

**IN SUMMARY**
- JSX is compiled to React.createElement calls.
- React calls your component functions or methods, producing React elements.
- React builds a virtual DOM tree from these elements.
- React compares the virtual DOM with the previous version to find changes.
- React updates the real DOM efficiently based on these changes.

# $\color{darkgreen}{\textrm{Using and Outputting Dynamic Values}}$

We can output content dynamically, which is, as they say, _the dog's bollocks_. It adds an element of _controlled randomness_, derived at runtime. By creating an array of possible words, we can access one word randomly if we use indexing through the genRandomInt function:

```
const reactDescriptions = ['Fundamental', 'Crucial', 'Core'];

function genRandomInt(max) {
  return Math.floor(Math.random() * (max + 1));
}

function Header() {
  const description = reactDescriptions[genRandomInt(2)]
  return (
    <header>
      <img src="src/assets/react-core-concepts.png" alt="Stylized atom" />
      <h1>React Essentials</h1>
      <p>
        {description} React concepts you will need for almost any app you are
        going to build!
      </p>
    </header>
  );
}
```

Even better, we can do the same with the image that's being used here. We should avoid load images though "img src="src/assets/react-core-concepts.png alt="Stylized atom" />". Instead... We should use an import statement.

```
import reactImg from './assets/react-core-concepts.png'

const reactDescriptions = ['Fundamental', 'Crucial', 'Core'];

function genRandomInt(max) {
  return Math.floor(Math.random() * (max + 1));
}


function Header() {
  const description = reactDescriptions[genRandomInt(2)]
  return (
    <header>
      <img src={reactImg} alt="Stylized atom" />
      <h1>React Essentials</h1>
      <p>
        {description} React concepts you will need for almost any app you are
        going to build!
      </p>
    </header>
  );
}
```

# $\color{darkgreen}{\textrm{Props}}$


![Abhinandan Trilokia](https://raw.githubusercontent.com/Trilokia/Trilokia/379277808c61ef204768a61bbc5d25bc7798ccf1/bottom_header.svg)