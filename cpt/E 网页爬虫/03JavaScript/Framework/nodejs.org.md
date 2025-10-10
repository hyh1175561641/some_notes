








https://nodejs.org/en








# Getting Started
## Introduction to Node.js
https://nodejs.org/en/learn/getting-started/introduction-to-nodejs



Introduction to Node.js

Node.js is an open-source and cross-platform JavaScript runtime environment. It is a popular tool for almost any kind of project!

Node.js runs the V8 JavaScript engine, the core of Google Chrome, outside of the browser. This allows Node.js to be very performant.

A Node.js app runs in a single process, without creating a new thread for every request. Node.js provides a set of asynchronous I/O primitives in its standard library that prevent JavaScript code from blocking and generally, libraries in Node.js are written using non-blocking paradigms, making blocking behavior the exception rather than the norm.

When Node.js performs an I/O operation, like reading from the network, accessing a database or the filesystem, instead of blocking the thread and wasting CPU cycles waiting, Node.js will resume the operations when the response comes back.

This allows Node.js to handle thousands of concurrent connections with a single server without introducing the burden of managing thread concurrency, which could be a significant source of bugs.

Node.js has a unique advantage because millions of frontend developers that write JavaScript for the browser are now able to write the server-side code in addition to the client-side code without the need to learn a completely different language.

In Node.js the new ECMAScript standards can be used without problems, as you don't have to wait for all your users to update their browsers - you are in charge of deciding which ECMAScript version to use by changing the Node.js version, and you can also enable specific experimental features by running Node.js with flags.
An Example Node.js Application

The most common example Hello World of Node.js is a web server:

const { createServer } = require('node:http');

const hostname = '127.0.0.1';
const port = 3000;

const server = createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});

JavaScript
Copy to clipboard

To run this snippet, save it as a server.js file and run node server.js in your terminal. If you use mjs version of the code, you should save it as a server.mjs file and run node server.mjs in your terminal.

This code first includes the Node.js http module.

Node.js has a fantastic standard library, including first-class support for networking.

The createServer() method of http creates a new HTTP server and returns it.

The server is set to listen on the specified port and host name. When the server is ready, the callback function is called, in this case informing us that the server is running.

Whenever a new request is received, the request event is called, providing two objects: a request (an http.IncomingMessage object) and a response (an http.ServerResponse object).

Those 2 objects are essential to handle the HTTP call.

The first provides the request details. In this simple example, this is not used, but you could access the request headers and request data.

The second is used to return data to the caller.

In this case with:

res.statusCode = 200;

JavaScript
Copy to clipboard

we set the statusCode property to 200, to indicate a successful response.

We set the Content-Type header:

res.setHeader('Content-Type', 'text/plain');

JavaScript
Copy to clipboard

and we close the response, adding the content as an argument to end():

res.end('Hello World\n');

JavaScript
Copy to clipboard
Next How to install Node.js










## How to install Node.js
## How much JavaScript do you need to know to use Node.js?
## Differences between Node.js and the Browser
## The V8 JavaScript Engine
## An introduction to the npm package manager
## ECMAScript 2015 (ES6) and beyond
## Node.js, the difference between development and production
## Node.js with WebAssembly
## Debugging Node.js
## Profiling Node.js Applications
## Security Best Practices

# TypeScript
## Introduction to TypeScript
## Running TypeScript code using transpilation
## Running TypeScript with a runner
## Running TypeScript Natively


# Asynchronous Work
## Asynchronous flow control
## Overview of Blocking vs Non-Blocking
## JavaScript Asynchronous Programming and Callbacks
## Discover JavaScript Timers
## The Node.js Event Loop
## The Node.js Event Emitter
## Understanding process.nextTick()
## Understanding setImmediate()
## Don't Block the Event Loop


# Manipulating Files
## Node.js file stats
## Node.js File Paths
## Working with file descriptors in Node.js
## Reading files with Node.js
## Writing files with Node.js
## Working with folders in Node.js
## How to work with Different Filesystems


# Command Line
## Run Node.js scripts from the command line
## How to read environment variables from Node.js
## How to use the Node.js REPL
## Output to the command line using Node.js
## Accept input from the command line in Node.js


# Modules
## How to publish a Node-API package
## Anatomy of an HTTP Transaction
## ABI Stability
## Backpressuring in Streams


# Diagnostics
## User Journey
## Memory
## Live Debugging
## Poor Performance
## Flame Graphs

# Test Runner
## Discovering Node.js's test runner
## Using Node.js's test runner
## Mocking in tests






