# Object basics

## Creation
In order to create an object two types of declarations can be used:
* object constructor
`const user = new Object();`
* object literal
`const user = {};`

Usually an object is created with a literal.

## Properties
New properties can be added into an object as "key:value" pairs. We can add, remove and read values from an object. To access a value the dot notation is used:
```javascript
const user = {
    name: 'Tom',
    height: 183
};

console.log(user.name); // Tom
console.log(user.height); // 183
```

To remove a property,`delete` operator can be used:
```javascript
delete user.name
```
If a property name consists of several words, the dot nonation cannot be used. For this purpose square brackets is a perfect solution.
```javascript
const user = {
    'sings songs': true,
};

console.log(user[sings songs]); // true
```
### Computed properties
Square brackets can be used within object literal what is called a *computed property*.
```javascript
let color = 'white'; // set it or get from the user, e.g. using pompt()

const pallet = {
    [color]: true,
};

console.log(pallet.white); // logs true
```

Computed property allows to set a property name dynamically, in the example above from a variable. It is also possible to use more complex expressions inside square brackets:
```javascript
let color = 'white'; // set it or get from the user, e.g. using pompt()

const pallet = {
    [color + 'is a new black']: true,
};

console.log(pallet.white); // logs true
```

## Existence check
To check if a property exists a strict comparison to `undefined` can be used:
```javascript
const user = {
    name: 'Tom',
};

console.log(user.name === undefined) // logs false, the property exists
console.log(user.age === undefined) // logs true, no such a property
```

There is also a special operatior `in` for checking if a property exists. It works according to a pattern below:
```javascript
'key' in object
```

Key must be a property name - a quoted string, if quotes are omitted it means that property name should be taken from a variable:
```javascript
const user = {
    name: 'Tom',
};

console.log('name' in user) // logs true, user.name exists
console.log('age' in user) // logs false, no such a property
```

In case when object property stores explicit `undefined`, strict comparison to `undefined` will fail as a property does exist:
```javascript
const user = {
    name: undefined,
};

console.log(user.name === undefined) // logs true, but the property exists
```

In such a case opertor `in` can be used. It is a good practice not to explicitly assign non-existing values `undefined`, but `null` for unknown values.

## Looping through an object
To loop through an object a `for..in` loop can be used:
```javascript
const user = {
    name: 'Tom',
    age: 20,
    height: 183
};

for (let key in user) {
    console.log(key); // logs name, age, height
    console.log(user[key]); // logs Tom, 20, 183
}
```

It should be noted that object properties are ordered in a special way. It means that integer properties are sorted and the rest appers in creation order.

## Copying
One of the key differences of an object from a primitive value is that objects are stored in memory and copied by 'reference'. A variable stores not the object itself but a reference to it.
```javascript
const user = {
    name: 'Tom',
    age: 20,
    height: 183
};

const newUser = user; // copied the reference

```
Above example shows that two variables store a refence to the same object, not an independent copy of an object. So if we change an object using `newUser` reference, `user` reference will track this change too:
```javascript
const user = {
    name: 'Tom',
    age: 20,
    height: 183
};

const newUser = user; // copied the reference

newUser.name = 'Andrew';

console.log(user.name) // logs Andrew, not Tom

```
### Comparing objects
Two objects are equal, if two variables reference the same object:
```javascript
const user = {
    name: 'Tom',
    age: 20,
    height: 183
};

const newUser = user; // copied the reference

console.log(user === newUser) // logs true, reference to the same object

```

But if the reference to the same-looking object is stored in different variables, then these objects are not equal.
```javascript
const user = {
    name: 'Tom',
    age: 20,
    height: 183
};

const newUser = {
    name: 'Tom',
    age: 20,
    height: 183
};

console.log(user === newUser) // logs false, reference to different objects

```