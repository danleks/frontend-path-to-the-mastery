The regular literal syntax `{...}` is used to create new objects, but if we need to create many similar objects, e.g. users, items and so on we should use `new` operator.

## Constructor function
A constructor function typically is an ordinary function with several pecularities:
* there names start with capital letter
* they should be executed only with `new` operator

Example:
```javascript
function User(age) {
    this.age = age;
}

let user = new User(20);
console.log(user.age) // logs 20
```

When executiing function with `new` operator several steps are made:
* a new empty object is created and assigned to `this`
* function body is executed. `this` is modified - adding new properties to it
* this value of `this` is returned

Example
```javascript
function User(age) {
    // this = {} assigning this an empty object
    this.age = age; // executing function body - adding property to this

    // return this (implicitly)
}

let user = new User(20);
```

To make it clear - constructors' main purpose is to implement reusable objects code creation. Not to repeat it using object literals. Technically any function can be executed with `new` operator and the algorithm described will be executed, but it is common agreement to write constructor functions with capital letter.

## Some advanced stuff

If there are a lot of code lines regarding only one single object it can be encapsulated as below:

Example
```javascript
let user = new function() {
    this.age = 2;

    this.say = function(){
        alert(this.age);
    };

    // more complex code 

}
```

Inside a function we can check whether a function is called is `new` operator or not. For this purpose `new.target` is used.

Example:
```javascript
function User() {
    console.log(new.target);
    this.age = 2;

    this.say = function(){
        alert(this.age);
    };
}

User() // logs undefined for new.target
new User() // logs function body

```

## Return from constructors
Basically constructors don't have `return` statement, because constructors role is to write everything to this and then it automatically becomes the result of constructor function.
But there are cases when there can be `return` statement in constructor function. In such a case the rule is simple:
* if `return` is called with a object, then the object is returned instead of `this`
* if `return` is called with a primitive, then `return` is ignored

Example (return obj):
```javascript
const newObj = {
    age: 5
};

function User() {
    this.age = 2;

    this.say = function(){
        alert(this.age);
    };

    return newObj // overwrites this and return newObj
}

console.log(new User().age); // logs 5

```

Example (return is empty || primitive):
```javascript
const newObj = {
    age: 5
};

function User() {
    this.age = 2;

    this.say = function(){
        alert(this.age);
    };

    return 5 // could also be empty

console.log(new User().age); // logs 2
```

The end.
