# Methods example
```javascript
let user = {
    name: 'Tom',
    height: 183
};

user.sayHi = function(){
    alert('Hello);
}
```

Here a Functiuon Expression is used to create the function and then the value of the functiion is assigned to the property of the object. Later we can call it like this:
```javascript
user.sayHi(); // shows alert with Hello
```

A pre-declared function can also be used as a method:
```javascript
const user = {

};

function sayHi(){
    alert('hi');
}

user.sayHi = sayHi;
user.sayHi();
```
## This in methods
It is a common practice that we may need to access the values of an object with methods.
```javascript
const user = {
    name: 'Tom',
    height: 183,
    sayName() {
        alert(this.name);
    }
};

user.sayName(); // alerts Tom
```

In JavaScript `this` can be used in any function:
```javascript
const user = {
    name: 'Tom',
    height: 183,
};

const newUser = {
    name: 'Bob'
}

function sayName() {
    alert(this.name);
}

user.sayName = sayName;
newUser.sayName = sayName;

user.sayName() // Tom
newUser.sayName() // Bob 

```

