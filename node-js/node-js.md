# What is Node JS (or simply Node).
It is a ***runtime environment*** for executing JavaScript code outside of browsers. Mostly used for building API's (Application Programming Interface).

### Advantages of Node over other frameworks and tools
1. Great for prototyping and agile development.
2. Super fast and highly scalable. 
Once PayPal rebuild their Java and Spring based application using Node and following discoveries were made: 
    1. Build twice as fast  
    2. 33% fewer lines of code
    3. 40% fewer lines
    4. 2x request/sec
    5. 35% faster response time
3. Large ecosystem of open-source libraries.

### Node Architecture
Every browser has JavaScript Engine (engine that translates the JavaScript code into the machine code) and they are different in each browser => JS code may work slightly differently in different browsers.
v8 (Chrome's engine) is embedded inside C++ program -> Node. It contains of the same JS engine, but has different objects which provide environment for JS code. Ex: in browser we have **document** object , but in Node we have objects like fs, http.
>Node consists of the v8 engine , but with additional modules that give us capabilities not given to us inside the browsers. Also , JS runtime environment is different. 

### How Node works.
Node is *asynchronous* by default , meaning that single thread is used to handle multiple requests. Applications build with frameworks like ASP.NET (asynchronous is possible) or Rails , work in synchronous way by default (thread waits until a request is handled. Want more requests? Increase the number of threads, which is increasing the hardware).
>In Node, single thread serves different requests. If database querying is needed , thread doesn't wait for database to return the data, instead, it serves another client. When the database prepares the result , it puts a message inside ***Event Queue***. Node monitors this queue every time, and when there is a message, it will take it out and process it. Node should not be used for CPU intensive apps , it is good to be used for I/O-intensive apps.



### Global object
Global objects are those objects , which we can access anywhere in any files (ex: console). Ex of global functions: setTimeout, setInterval.
All the variables and functions defined globally we can access via ***global*** object. All the global functions belong to 'global' object

>We should avoid creating global variables ( problem with overriding ), use modules instead.