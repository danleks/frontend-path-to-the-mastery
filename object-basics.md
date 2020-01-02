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