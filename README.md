# Binding application state with DOM elmenets
## Problem description
In pure JS elements from DOM (the view layer) are not binded to the state of the application. This problem is solved in frameworks like Angular.
However such binding might be useful also in pure JS (TS). 
There is an element in DOM having a property 'x', and we want to get and object (o), that we would use as a variable (getting value from it, setting value to it), 
but setting value to this DOM element would change (o) the property 'x' in DOM would change. Moreover we would like to have (o) changed any time an user interacts 
with the DOM element. 

## Solution:

A singleton object, that uses a MAP to remember all bindings. Each binding is a proxy element that is created on demand with the function, is added to the MAP data
base, and having its reference returned to the place the function was called. Now, setting something on this returned reference cauess proxy trap to 
change the state value (under the proxy), and manipulate DOM. 
At the time the function is called, an event listeners is created onfocusout event, so every change made to the DOM element is visible in the state.
