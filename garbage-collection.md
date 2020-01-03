# Garbage collection
All of the created primitives and objects in JS are stored in memory. The question is what is happening to those things after they are no longer needed ?

## Reachability
Reachability is the main concept of memory management in JS. Values that are usable or accessible somehow are reachable and guaranteed to be stored in memory.
1. There is a set of inherently reachable values, that cannot be deleted for some obvious reasons.
* Global vars
* Local vars and params of the current func
* Vars and params of other funcs on the current chain of nested calls

These values are called *roots*.