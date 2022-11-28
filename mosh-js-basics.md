# Factory functions

```js
function createCircle(radius) {
  return {
    radius,
    draw() {
      console.log("draw");
    },
  };
}

const circle1 = createCircle(5);
```

# Constructor Function

```js
// uses camel case notation
function Circle(radius) {
  this.radius = radius;
  this.draw = function () {
    console.log("draw");
  };
}
const circle1 = new Circle(4); // what happens under the hood?
```

# Constructor property

> Every object in js has **Constructor** , it's the reference to fn that was used to create the object

![Example](assets/1.png)

---

![Example](assets/2.png)

_Object() is built-in constructor function that constructs the objects_

### There are several built-in constructor functions in JS:

> let obj = { }; === let x = new Object(); <- happens under the hood

- Number(). But we use number literal (5 , 6 , 3)
- String(). But we use string literal ('hello', 'world')
- Boolean(). But we use boolean literal (true, false)
- Function().

> Functions are objects. Constructor function of functions is Function, with help of what we can create objects.
> All functions have methods: call , apply.

# Value types and Reference Types. (Primitives and objects)

## Value types:

1. Number
2. String
3. Boolean
4. Symbol
5. undefined
6. null

```js
let x = 5;
let y = x;

x = 10;

console.log(x); // 10
console.log(y); // 5
```

> **_Primitives are copied by their value._**

```js
let x = 10;

function increment(number) {
  number++;
}

increment(x);

console.log(x); // 10
```

In the example above, x has primitive value, when it is given as an argument to function , the value is copied , so original value didn't change.

## Reference types:

(all of them are objects)

1. Object
2. Function
3. Array

```js
let x = {
  value: 5,
};
let y = x;

x.value = 10;

console.log(x); // { value: 10 }
console.log(y); // { value: 10 }
```

> Basically , reference types are just references to address in the memory. When assigning y = x, we assign the address , which is the same.  
> **_Objects (reference types) are copied by their reference to address in memory_**

```js
let obj = { value: 10 };

function increment(obj) {
  obj.value++;
}

increment(obj);

console.log(obj.value); // 11
```

In the example above , object (reference type) was given as an argument , it is reference type , so when we change it in function , we change its value in location , so original value is also changed.

# Enumerating properties

```js
const obj = {
    a: 5,
    b: 10
};
for (const key of object) {
    console.log(key); // Error: Object is not iterable
}

// But we can do next:

for (const key of Object.keys(obj)) {  // Object.keys returns array of object's keys
    console.log(key);  // a , b
    console.log(obj[key]); // 5 , 10
}


// Object.entries

This is method of Object (constructor function), which returns an array with [key,pair] values

const arr = Object.entries({ name: 'Mike', age: 34 });

console.log(arr); // [ ['name' , 'Mike']  ,  ['age' , 34]  ]


// Check whether element exists in object

console.log( 'name' in { name: 'Mike' } ); // true


```

# Cloning object

> (all methods copy first level of object only)

1. **_for in_** loop

```js
let obj1 = {
  a: 1,
  b: 2,
  c: {
    d: 3,
  },
};

let obj2 = {};

for (key in obj1) {
  obj2[key] = obj1[key];
}

console.log(obj2); // { a: 1 , b: 2, c: { d: 3 }  }
```

2. **_Object.assign_**

```js
let obj1 = {
  a: 1,
  b: 2,
  c: {
    d: 3,
  },
};

let obj2 = Object.assign({}, obj1); // joins two objects

console.log(obj2); // { a: 1 , b: 2, c: { d: 3 }  }
```

3. **_Spread operator {...}_**

```js
let obj1 = {
  a: 1,
  b: 2,
  c: {
    d: 3,
  },
};

let obj2 = { ...obj1 };

console.log(obj2); // { a: 1 , b: 2, c: { d: 3 }  }
```

# Garbage collection

In JavaScript , when you create an  object, the memory is automatically allocated to this object. When we are done using it , the memory is automatically deallocated. JavaScript engine has so-called **Garbage Collector**. Its job is to find the variables and constants that are no longer used , and to deallocate the memory that was allocated for them earlier.



# String
```js
1. String primitives.
const message = 'hi'; // typeof string


2. String object.
const message = new String('hi'); // typeof object


When we put dot after a string primitive , JS Engine wraps it with String object, so we can work with it like it is an object with methods and properties.


-----------------------------------------------

Some string object methods:
1. message.includes(smth); // returns if a string has smth
2. message.index(smth); // returns the index smth start at
3. message.replace(a,b); // returns a string with replaced with b, does not change the original value.
4. message.trim(); // returns a string with removed spaces at the start and at the end of the string. Does not change its original value.

-----------------------------------------------

\ means 'ignore the next character'; 
Example: 'My name is Ma'ruf' // error
'My name is Ma\'ruf' // no error , ' is ignored



```