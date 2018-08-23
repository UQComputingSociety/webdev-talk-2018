---
title: Frontend Webdev in 2018
author: Max Bo & Neil Ashford
date: 2018-08-23T5:30:00+10
institute: UQCS
theme: Boadilla
---

# Introduction
## Us
- Be skeptical
- Max Bo + Neil Ashford
- Committee
- @mb / max@maxbo.me
- @artemis / ashfordneil0@gmail.com
- Each over a year of professional web dev experience

## You
- Year?
- Studying?
- Experience with web dev?
- Coming to the hackathon next week?

## Why Webdev
- Personal sites
- Job market
- Hackathons
- Kinda fun to play with, and you can get results fast

## What Happens When You Type google.com
- Find the server
- Connect over HTTP
- Get given a HTML page
- Download the things the HTML page links to
- Rendering and parsing
- Interact with the page
- Page interacts back

# Letsa Go
## Web Architectures
- Static sites
- Dynamic sites
- Single Page App (SPA)
- Multiple Page App (MPA)
- Server-side vs Client-side rendering

## Writing a Web Server
- Use a framework
- Templating
- REST
- GraphQL

## Databases
- Good for scaling / reliability / persistence
- ORMs
- prepared statements

## Serving Your Code _Fast_
- You have lots of resources
- Each file is a separate round-trip
- Use a bundler
- Live code reload
- Minifying and tree shaking
- Makes using libraries so much more feasible on the frontend
- Can compile (transpile) your code

## Libraries Like its ${CURRENT_YEAR}
- `<script src="https://somecdn.com/library.js.min"></script>`
- `node_modules/`, the good and the bad
- Package managers (`yarn`)

## How to Not Write JavaScript
- `[] == 0` and `"0" == 0` but `[] != "0"`
- `"1" + 2 == "12"` but `"1" - 2 == -1`
- What if you didn't have to write JavaScript
- TypeScript, flow (:/), elm (://), coffee script (:///), webassembly (...)

## How _to_ Write JavaScript (or similar)
- `const` if you can, `let` if you can't, `var` never
- `async` and `await`
- You don't need jquery
- The story with `this`
```js
function foo(x) {
}

const foo = (x) => {
}
```
- ECMAscript

## CSS ~~2, Electric Boogaloo~~ 3
- Flex, grid, and why the browser is better at calculating sizes than you are
- `em` vs `px`
- Responsive design
- Removing the boilerplate from CSS
- Libraries - make an informed decision

## Frameworks for Front End
- Dynamically change the HTML on your page
- Saves you from dealing with XSS
- Separation of concerns
    - You deal with data and layout
    - The framework deals with rendering, performance and security
- TODO

## Where to Start

![](images/how-it-feels.png)

## 

![](images/js-bundling.png)

## 

![](images/create-react-app.png)

## 

![](images/vue-cli.png)

## 

![](images/angular-cli.png)

## A case study

## 

![](images/create-react-app-whats-included.png)

## 

![](images/create-react-app-userguide.png)

## 

![](images/create-react-app-deployment.png)


- `cd ~ && npx create-react-app --scripts-version=react-scripts-ts talk && cd talk && yarn start`
- `code ~/talk && git init && git add package.json public/ README.md src yarn.lock .gitignore`

##

```
my-app
--- README.md
--- node_modules
--- package.json
--- .gitignore
--- public
|   --- favicon.ico
|   --- index.html
|   --- manifest.json
--- src
    --- App.css
    --- App.js
    --- App.test.js
    --- index.css
    --- index.js
    --- logo.svg
    --- registerServiceWorker.js
```

##

![](images/sass.png)

##

![](images/cra-sass.png)


##

```diff
diff --git a/src/App.tsx b/src/App.tsx
index c1bc27c..2d716ed 100644
--- a/src/App.tsx
+++ b/src/App.tsx
@@ -1,19 +1,47 @@
 import * as React from 'react';
 import './App.css';
 
-import logo from './logo.svg';
+interface ITodo {
+  userId: number
+  id: number
+  title: string
+  completed: boolean
+}
 
-class App extends React.Component {
+interface IState {
+  todos: ITodo[]
+}
+
+class App extends React.Component<{}, IState> {
+  constructor(props: {}) {
+    super(props)
+
+    this.state = {
+      todos: []
+    }
+  }
+
+  public componentDidMount() {
+    return fetch('https://jsonplaceholder.typicode.com/todos')
+          .then(response => response.json())
+          .then(json => this.setState({ todos: json }))
+  }
+
+  public renderTodo = (todo: ITodo) => {
+    const { userId, title, completed } = todo
+    const status = completed ? 'completed' : 'not completed'
+
+    return (
+      <div>
+          {`${userId} has ${status} ${title}`}
+      </div >
+    )
+  }
+  
   public render() {
     return (
       <div className="App">
-        <header className="App-header">
-          <img src={logo} className="App-logo" alt="logo" />
-          <h1 className="App-title">Welcome to React</h1>
-        </header>
-        <p className="App-intro">
-          To get started, edit <code>src/App.tsx</code> and save to reload.
-        </p>
+        {this.state.todos.map(this.renderTodo)}
       </div>
     );
   }
```

##

![](images/firebase-what-you-get.png)

##

![](images/create-firebase.png)

##



```diff
diff --git a/package.json b/package.json
index a5dfd6a..46f1ae8 100644
--- a/package.json
+++ b/package.json
@@ -3,6 +3,7 @@
   "version": "0.1.0",
   "private": true,
   "dependencies": {
+    "firebase": "^5.4.0",
     "react": "^16.4.2",
     "react-dom": "^16.4.2",
     "react-scripts-ts": "2.17.0"
diff --git a/src/App.tsx b/src/App.tsx
index 2d716ed..4b8bf91 100644
--- a/src/App.tsx
+++ b/src/App.tsx
@@ -1,3 +1,4 @@
+import * as firebase from 'firebase';
 import * as React from 'react';
 import './App.css';
 
@@ -9,22 +10,43 @@ interface ITodo {
 }
 
 interface IState {
-  todos: ITodo[]
+  todos: Map<string, ITodo>
 }
 
+const config = {
+  apiKey: "AIzaSyCn3VxVXEEj2-aE7wq3P77MP_JaVJADtyk",
+  authDomain: "uqcs-webdev-talk-2018.firebaseapp.com",
+  databaseURL: "https://uqcs-webdev-talk-2018.firebaseio.com",
+  messagingSenderId: "444811468582",
+  projectId: "uqcs-webdev-talk-2018",
+  storageBucket: "uqcs-webdev-talk-2018.appspot.com"
+};
+
+firebase.initializeApp(config);
+
 class App extends React.Component<{}, IState> {
+  public fref = firebase.database().ref()
+
   constructor(props: {}) {
     super(props)
 
     this.state = {
-      todos: []
+      todos: {} as Map<string, ITodo>
     }
   }
-
+  
   public componentDidMount() {
-    return fetch('https://jsonplaceholder.typicode.com/todos')
-          .then(response => response.json())
-          .then(json => this.setState({ todos: json }))
+    this.fref.on('value', this.firebaseCallback);
+  }
+
+  public componentWillUnmount() {
+    this.fref.off('value', this.firebaseCallback);
+  }
+
+  public firebaseCallback = (snapshot: firebase.database.DataSnapshot | null) => {
+    if (snapshot) {
+      this.setState({ todos: snapshot.val() });
+    }
   }
 
   public renderTodo = (todo: ITodo) => {
@@ -41,7 +63,9 @@ class App extends React.Component<{}, IState> {
   public render() {
     return (
       <div className="App">
-        {this.state.todos.map(this.renderTodo)}
+        {Object.keys(this.state.todos).map(key => {
+          return this.renderTodo(this.state.todos[key])
+        })}
       </div>
     );
   }
```




![](pwaa-step-by-step.png)


# Conclusion
## Thanks
:realheart:

## Cheat Sheet and Resources
- github pages, vultr, AWS, GCP, azure
- Progressive Web App (PWA)
- flask, django, express, koa, ASP.net, SpringBoot
- webpack, parceljs
- react (create-react-app), angular, vue
- Mozilla Developer Network (MDN)
- flexbox, grid
- caniuse.com
- ECMAscript, typescript, flow
- #webdev
