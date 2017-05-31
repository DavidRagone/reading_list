# JavaScript: The Good Parts
## Douglas Crockford

### Chapter 1: Good Parts
* DOM is the API of hte browser; not JS's fault
* good: functions, loose typing, dynamic objects, expressive object
literal notation
* bad: global variables-based programming model
* objects creatable simply by listing their components; inherit
properties directly from other objects, not a class
* JS depends on global variables for linkage

### Chapter 2: Grammar
* can not use reserved words (see list pp 6-7) as name of object
property in an object literal or following a dot in a refinement
* JS has singl enubmer type,r epresented as 64-bit float point
* NaN is a number value (!), and is not equal to any value, including
itself
* Infinity is all #'s greater than 1.79769313486231570e+308
* strings: immutable, same if have same characters ('c' + 'a' + 't' ===
'cat')
* var: when used inside of function, defines function's private
variables
* falsy values: false, null, undefined, empty string, numbers 0 & null

### Chapter 3: Objects
* objects in JS are mutable keyed collections
* arrays, functions, regexps, and objects are all objects
* object is container of properties, where property has a name and a
value; name can be any string, including empty, value can be any JS
value except undefined
* objects can contain other objects (can easily represent tree/graph
structures)
* object literal: curly braces surrounding 0+ name/value pairs
* objects are passed by reference, never copied
* every object is linked to a prototype object from which it can inherit
properties; all objects created from object literal are linked to
Object.prototype
* prototype link used only in retrieval; if try to retrieve property
value from an object and object lacks the property name, JS attempts to
retrieve from prototype, all the way up to Object.prototype
* hasOwnProperty only looks at object, not its prototype
* suggestion to create a single global variable for your app to
namespace and avoid complications with other libs

### Chapter 4: Functions
* functions in JS are objects
* every function created with 2 hidden properties: its context and code
that implements its behavior
* every function is created with a prototype property, whose value is an
object w/ a constructor property whose value is the function(???)
* b/c fucntions are objects themselves, they can be used like any other
value: stored in variables, objects, arrays; passed as args to
functions; be returned from functions
* functions can have methods (b/c they're objects)
* no error if incorrect # of args passed to fucntion; if too many
passed, extras ignored; if too few, undefined value substituted for
missing
* method invocation pattern: function stored as property of an object;
_this_ keyword bound to that object
* function invocation pattern: when invoked, _this_ is bound to global
object, not to _this_ of any outer function (language design mistake)
  * workaround w/in an object is for object to define variable and
assign it value of _this_; inner function will have access to _this_
through that variable; by convention, name of variable is _that_
* constructor invocation pattern:
  * if function invoked with new prefix, new object created with hidden
link to the value of function's prototype member, and _this_ will be
bound to that new object
  * use of this style (new Foo()) of constructor functions __not__
recommended
* apply invocation pattern: functions can have methods; _apply_ method
allows us to construct an array of arguments to use to invoke a function
and to choose the value of _this_
* arguments parameter: gives function access to all args supplied with
the invocation, including excess args not assigned to params; arguments
is not an array - has length property, but lacks all other array methods
* _return_ statement causes early return w/o executing rest of statement
* function always returns a value; if _return_not specified, _undefined_
is returned; if function invokved w/ new prefix and return value is not
an object, _this_ (the new object) is returned instead
* Exceptions
  * _throw_ statement interrupts execution of function, and should be
given an object w/ name property that identifies the type of the
exception, and a descriptive _message_ property; can add other
properties
* can augment basic types (functions, arrays, strings, numbers, regexs,
booleans) by accessing their prototype
* JavaScript has function scope, not block scope - params & vars defined
in a function are not visible outside the function, and vars defined
anywhere w/in a function are available everywhere within the function
  * because of function scope, best to declare all vars at the top of
the function body
  * inner functions get access to params & vars of functions defined
within (excluding _this_ and _arguments_)
  * function has access to context in which it was created - called
_closure_
* Asynchronous requests: provide callback function to be invoked when
response received; async function returns immediately, hence
non-blocking; function passed (callback) will be called whenever
response is available
* Modules
  * can use functions and closures to make modules
  * module: function or object that presents an interface but hides its
state and implementation
  * by using functions to produce modules, can almost completely
eliminate use of global variables
  * module pattern: function that defines private variables and
functions; creates privileged functions, which, thorugh closure, have
access to private variables and functions; returns the privileged
functions or stores them in an accessible place
* cascades: for methods that would have no return value b/c they just
change/set state of the object, if return _this_, can call many methods
on same object in sequence
* Currying: functions are avlues, so can manipulate function values,
e.g. produce a new function by combining function and an argument
* Memoization: see awesome function example on pp. 45

### Chapter 5: Inheritance
* prototypal: objects inherit directly from other objects
* JS conflicted about prototypal nature; unnecessary indirection
requiring objects being produced by constructor functions
  * when function object created, _Function_ constructor that produces
the function object runs code like:
    this.prototype = { constructor: this };
  the new function object is given a prototype property whose value is
an object containing a constructor property whose value is the new
function object
  * prototype object is place where inherited traits are to be deposited
  * every function gets prototype object b/c JS doesn't provide way of
determining which functions are intended to be used as constructors
* convention of having all (and only) constructor functions written w/
leading capital letter
* better off just never using "new"; JS has better options
* object specifiers: pass function an object that contains specification
of the object to be created (like JSON)
* Prototypal:
  * use Object.create(someOtherObject);
  * get copies
  * use differential inheritance: by customizing new object, we specify
differences from object on which it is based
* Functional:
  * provides privacy
  * functional constructor: write it to
    1) create new object
    2) optionally define private instance variables/methods (ordinary
vars of the function)
    3) augment new object w/ methods, which have privileged access to
params and vars defined in second step
    4) return the new object

### Chapter 6: Arrays
* array: a linear allocation of memory in which elements are accessed by
integers used to compute offsets; fast - JS doesn't have this
* JS provides an object w/ array-like characteristics; converts array
subscripts into strings used to make properties
* JS arrays have a length property (note: property, not method); length
is largest integer property name in array plus one; not necessarily same
as nubmer of properties in array (e.g. by creating property with large
number, skew length property)
  * can set length explicitly; larger length won't allocate more space,
but smaller will delete properties with subscript greater or equal to
new length

