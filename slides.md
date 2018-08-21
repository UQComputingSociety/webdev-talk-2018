---
title: How to Webdev 
author: Max Bo & Neil Ashford
date: 2018-08-23T5:30:00+10
institute: UQCS
theme: Boadilla
---

# Introduction
## Me
- Neil Ashford
- 4th year software engineering
- Committee member
- @artemis
- ashfordneil0@gmail.com
- https://github.com/ashfordneil/dotfiles
- Tutor for CSSE2002, CSSE2010, CSSE2310, COSC3500

## You
- Year?
- Studying?
- CSSE2310?
- Vim? Tmux?

# Letsa go!

## Cameron's ideas

Firstly I think it's good to get some fundamental stuff about how websites work out of the way, since people may wonder how HTML magically turns into a website
- Start off by talking about what a website is
  - A HTTP server
  - Serves files
  - HTML for markup
  - CSS for styling
  - JS for interactivity/custom behaviour
- Show an example hello world website that just serves a simple HTML document (no CSS or JS)
  - Use http-server to serve it
  - Show that you connect via localhost
  - Briefly mention that when a website gets deployed, you expose the port to the world and point a domain to it
  - Discuss what HTML looks like, show some example tags (headings, paragraphs). Show the MDN web docs and how to use the documentation.
- Show how we can load a CSS and JS file with this by adding a reference in the HTML
  - Just basic functionality here
  - The intention is to introduce the CSS and JS syntax, and to explain how each part gets loaded and applied/executed
  
 Now the fundamentals are down, ask for questions on the above as if they don't understand the above they will get lost later.
 
 Now discuss high-level terminology/topics. For each of these, list some examples
 - Static vs Dynamic web sites
 - SPA vs MPA
 - Server-side rendering vs Client-side rendering
 - Web frameworks (e.g. node, flask, django, asp.net, laravel, ruby on rails)
 - NPM
 - ES6/Babel
 - Typescript
 - LESS/SASS
 - React and Angular
 - Boilerplate generators
 
Talk about where to get started
 - Join #webdev
 - Read MDN web docs
 - Recommended resources for react or angular
 
If time permits, then a quick demo of react using create-react-app.

Somewhere in there we should mention how databases, sessions and cookies fit into this.
