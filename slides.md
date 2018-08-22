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

## Serving Your Code _Fast_
- You have lots of resources
- Each file is a separate round-trip
- Use a bundler
- Live code reload
- Minifying and tree shaking
- Makes using libraries so much more feasible on the frontend

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
- TODO (write about generators)

# Conclusion
## Thanks
:realheart:

## Cheat Sheet and Resources
- github pages, vultr, AWS, GCP, azure
- flask, django, express, koa, ASP.net, SpringBoot
- webpack, parceljs
- react (create-react-app), angular, vue
- Mozilla Developer Network (MDN)
- flexbox, grid
- caniuse.com
- #webdev
