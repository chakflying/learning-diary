---
layout: post
title:  Importing things in Javascript
---

When I first started learning Javascript, the complexity of importing things is mindblowing. Nowadays we often rely on a build system to handle everything for us, but it would be a nightmare to figure out how the project and its dependencies are put together. So I tried to figure out how things are the way they are.

### Lack of a standard library

I don't know the entire history of Javascript, but it appears that the main focus of its development had been to build a flexible, minimal core with easy to use syntax, so that it is extensible. The result is that many simple functions are left to be implemented by the programmer. Library or packages became a great way to handle commonly used functions, so NPM became really popular. A convention was evolved such that a package would do one thing as good as possible, and that thing only. That way people using it can get the exact functionality they need. But with this huge amount of packages, a standard way to import them became necessary.

#### CommonJS and Node.js

CommonJS was one of the first attempt to create an ecosystem of modules for javascript running outside the browser. It is a specification of how modules should be defined, and centres around the `require('someModule')` syntax. Node.js improved upon that and built npm. The problem is that this method of using a string to identify the module has a prerequisite that the module needed already exist in the current namespace. This would be problematic on the broswer as different pieces of script may be downloaded and executed at different times, particularly when using XHR to load modules.

#### Asynchronous Module Definition (AMD) and RequireJS

AMD tries to improve by encapsulating modules with `define()`, which registers the function first without needing to execute it. That way they can be executed in the right order once everything is loaded. This made it useful for client-side javascript development.

### Webpack

Then one day, Webpack comes along and takes the abstraction up another level. It works by walking through your files, parsing all the `require('')` tags, building a dependency tree, and them compiling them down to one (or more) file. But what happens when you have typescript, coffeescript and other non-compatible files that needs to be imported? Webpack then has loaders to handle transpiling these back to javascript, and also allow things like `babel-loader` to add compatibility to new language features. Furthermore, you can add plugins to Webpack, which modifies the operation of Webpack itself, such as `webpack-visualizer` outputting statistics about the output size and composition. It basicaly solves the entire process of from development to deployment, and hence became so successful today.
