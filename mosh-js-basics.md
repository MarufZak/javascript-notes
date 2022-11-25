# Factory functions

``` js
function createCircle(radius){
    return {
        radius,
        draw(){
            console.log('draw');
        }
    }
};

const circle1 = createCircle(5);
```

# Constructor Function

``` js
// uses camel case notation
function Circle(radius){ 
    this.radius = radius;
    this.draw = function(){
        console.log('draw')
    }
};
const circle1 = new Circle(4); // what happens under the hood? 
```

# Constructor property
>Every object in js has **Constructor** , it's the reference to fn that was used to create the object

![Example](assets/1.png)

---

![Example](assets/2.png)

*Object() is built-in constructor function that constructs the objects*

### There are several built-in constructor functions in JS:
> let obj = { }; === let x = new Object(); <- happens under the hood
* Number(). But we use number literal (5 , 6 , 3)
* String(). But we use string literal ('hello', 'world')
* Boolean(). But we use boolean literal (true, false)
* Function().
  
> Functions are objects. Constructor function of functions is Function, with help of what we can create objects.
All functions have methods: call , apply. 

# Value types and Reference Types. (Primitives and objects)
## Value types:

1. Number
2. String
3. Boolean
4. Symbol
5. undefined
6. null
   
``` js
let x = 5;
let y = x;

x = 10;

console.log(x); // 10 
console.log(y); // 5
```

> ***Primitives are copied by their value.***

```js
let x = 10;

function increment(number){
    number++
};

increment(x);

console.log(x); // 10
```

In the example above, x has primitive value, when it is given as an argument to function , the value is copied , so original value didn't change. 

## Reference types: 
(all of them are objects)
1. Object
2. Function
3. Array

``` js
let x = {
    value: 5
};
let y = x;

x.value = 10;

console.log(x); // { value: 10 }
console.log(y); // { value: 10 }
```

> Basically , reference types are just references to address in the memory. When assigning y = x, we assign the address , which is the same.  
***Objects (reference types) are copied by their reference to address in memory***

``` js
let obj = { value: 10 };

function increment(obj){
    obj.value++
};

increment(obj);

console.log(obj.value); // 11
```
In the example above , object (reference type) was given as an argument , it is reference type , so when we change it in function , we change its value in location , so original value is also changed.


# Enumerating properties

``` js
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