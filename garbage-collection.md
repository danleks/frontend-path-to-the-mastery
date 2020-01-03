# Garbage collection
All of the created primitives and objects in JS are stored in memory. The question is what is happening to those things after they are no longer needed ?

## Reachability
Reachability is the main concept of memory management in JS. Values that are usable or accessible somehow are reachable and guaranteed to be stored in memory.
1. There is a set of inherently reachable values, that cannot be deleted for some obvious reasons.
* Global vars
* Local vars and params of the current func
* Vars and params of other funcs on the current chain of nested calls

These values are called *roots*.

2. Any other value is considered reachable when it is reached from a root by a reference or a chain of references. For example, if an object in local memory has a property that is referencing another object, that object is considered to be reachable.

A background process that is monitoring all objects and removes those unreachable is called *garbage collection*.

Some examples:
```javascript
// user has a reference to the object
let user = {
    name: 'Tom',
    height: 183
};
```

The example above demonstrates that the global var user keeps the reference to the object, thus making it reachable. If we overwrite the var, the reference is lost and the object can be garbage collected and deleted.
```javascript
// user is overwritten
let user = null;
```
One more example with 2 references to the same obj:
```javascript
// user has a reference to the object
let user = {
    name: 'Tom',
    height: 183
};

let newUser = user; // newUser also has reference to the same obj
```
Now we have 2 references to the object. If we delete one of the references: `let user = null` the object will be still reachable, thanks to the one more reference `newUser`.

It is important to note once again, that reachability is considered from the root value. So if the root value is no longer referencing objects, no matter how futher those objects are referencing each other, they will be garbage collected. 

The end...
