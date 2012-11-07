## Forward ##
- most useful thing about patterns is forming vocabulary for articulating design decisions

## Preface ##

## Part I - Patterns and Ruby ##
* Chapter 1: Building Better Programs with Patterns
  * complexity of software development makes it easy to miss patterns
of challenges and solutions seen repeatedly
  * separate out the things that change from thsoe that stay the same
  * program to an interface, not an implementation: if related objects
all implement a common interface, can use polymorphism approach and not
couple code to particular classes
  * another way to say this is to program to most general type
possible
  * prefer composition to inheritance:
    * using inheritance means creating two classes bound tgoether by
common implementation core
    * given goal of not having tightly coupled systems, inheritance
dangerous
    * instead of inheritance, assemble functionality from bottom-up;
equip objects with references to objects that supply the funcitonality
we need
    * avoid saying an object is a kind of something; prefer to say it
_has_ something
    * example of pulling out an engine class from Car < Vehicle
  * YAGNI (You Ain't Gonna Need It): principle that says do not
implement features, or design in flexibility, that you don't need right
now

## Part II - Patterns in Ruby ##
* Chapter 3: Varying the Algorithm with the Template Method
  * build an abstract base class with skeletal method (called a template
method)
  * skeletal method drives processing tha tneeds to vary by making calls
to abstract methods, which are supplied by concrete subclasses
  * template method separates stuff that doesn't change from that which
does
  * non-abstract methods that can be overwritten in concrete classes of
the Template ethod are called hook methods
  * hook methods allow concrete classes to choose to override base
implementation, or to accept default of parent
  * best getting here via refactoring
* Chapter 4: Replacing the Algorithm with the Strategy
  * as an alternative to teh template pattern, use delegation: instead
of a plethora of subclasses, have numerous classes for each part of
varying code (exampel is pullin gformatting out of report class, and
have formats inherit from formatting class, wiht report class
initialized with a formatter)
  * pull the algorithm out into a separate object = the Strategy pattern
  * key idea: define family of objects (the strategies) which all do the
same thing, and support exactly the same interface
  * user of the strategy is called the context class; context class can
treat strategies as interchangeable, because all look alike (to it) and
perform some function
  * will need to pass some info from context to strategy (example of the
content in the report that needs formatting); can do so by calling
strategy instance variable witha  context method and passing context
(self) as a param
  * given duck typing, no real need for strategy parent class; just have
different siblings with no common parent
  * a Ruby proc can be used as a strategy - chunk nfo code that knows
how to do something and is wrapped in an object; context simply takes a
block in initialize, then can pass it &a_proc, or even an on-the-fly
do...end block
  * difference between strategy and other patterns (e.g. observer) lies
in their intent
* Chapter 5: Keeping up with the Times with the Observer
  * problem: tieing disparate parts fo a large software system together
without increasing coupling
  * separate out thing that is changing - who gets news about salary
changes in book example - from real guts of rest of the object
  * need list of objects interested in hearing about latest news from
the object
  * @observers = []; methods tneeding to announce change call
notify_observers, which loops over each in array @observers (calling
observer.update(self))
  * GoF called class with the news the subject class; observers are
objects interested in receiving the news
  * Ruby comes with Observable module in stdlib
  * could pass in a block to observers list (assuming it is called
properly)
* Chapter 6: Assembling the Whole from the Parts with the Composite
  * composite pattern suggests building bigger objects from small
sub-objects, and those perhaps from still smaller sub-sub objects
  * Composite Pattern: the sum acts like one of the parts
  * need 3 things to make composite pattern work:
    1. common interface or base class for all objects; GoF called this
       interface/class the component
    2. one or more _leaf_ classes - the simple, individible building
       blocks of the process
    3. at least one higher-level class (teh composite class); is a
       component, but also a higher-level object built from subcomponent
  * common mistake when using composite pattern is assuming only one
level of depth, and making all child components of a composite are leaf objects,
and not other composites; 
  * cool gem for GUI - FXRuby
* Chapter 7: Reaching into a Collection with the Iterator
  * Iterator pattern allows an aggreagte object to provide otuside world
with way to access its collection of sub-objects
  * external iterator: call next item one at a time (holding onto
position); compare to internal, which forces way througha ll elements
immediately
  * danger comes from operating on an iterator when (anything, self or
other) is changing it
* Chapter 8: Getting Things Done with Commands
  * command pattern: instruction to do something (specific)
  * sounds like a Proc object to me
  * separates something that changes from something that does not
  * can create separate class for command-holding (like a Proc), i.e.
when need state or commmand naturally decomposes into several methods
  * gets more complex with need to undo command (think undo in a text
editor)
* Chapter 9: Filling in the Gaps with the Adapter
  * adapter crosses chasm between interface have and interface need
  * in Ruby, can use monkey patching to get the interface we need
(especially useful if the class we're using is already pretty close)
  * or create singleton to add adapter
* Chapter 10: Getting in Front of Your Object with a Proxy
  * when client asks for object, give it one thatlooks like what client
asked for, but is really counterfeit (a proxy)
  * proxy holds reference to "real" object, forwarding calls
  * can use proxy to provide a security layer
  * or as way to package up complexity of client-server interaction
(let proxy live on client, act like subject that lives on server, and
handle passing info back and forth)
  * virtual proxy: does not have reference to real object until client
tries to do something with it
  * instead of writing out all the dummy methods, use method_missing to
pass everything to subject
* Chapter 11: Improving Your Objects with a Decorator
  * decorator used for varying responsibilities of an object
  * can chain decorators together, b/c each takes "real object" and adds
small additional features to that object
  * useful to extend class with the Forwardable module, and use its
provided def delegators method, which takes an instance variable and
methods to forward to that instance variable
* Chapter 12: Making Sure There is Only One with the Singleton
  * singleton is class that can only have one instance and provides
global access to that one instance
  * Ruby provides a singleton module; can just include it to get desired
behavior within a class
* Chapter 13: Pickin gthe Right Class with a Factory
  * technique of pushing decision of which class to use down to a
subclass = Factory Pattern
  * is really just Template Method pattern applied to problem of
creating objects
  * abstract factory is object dedicated to creating a compatible set of
objects
* Chapter 14: Easier Object Construction with the Builder
  * builder class takes charge of assembling all components of a complex
object
  * specify configuration of complex object step-by-step
  * builder instance will return same object it builds if related
"build" method called twice; can solve w/ :reset method that
reinitializes object doing construction
* Chapter 15: Assembling Your System wiht the Interpreter
  * pattern to solve problems that are best served by creating
specialized language and expressing the solution in that language
  * ideally problem is self-contained and has clear/crisp boundaries
  * example: searching for specific objects based on a spec -> a
specialized query language
  * example: creating complex object configurations -> a configuration
language
  * Interpreter pattern helpful if find self creating lots of discrete
chunks of code that seem easy to write by selves, but need to combine in
over-expanding combinations
  * Interpreters work in two phases: 
    1. Parser  reads in program text, produces a data strcture called an
       abstract syntax tree (AST); AST can be executed reasonably
efficiently
    2. AST is evaluated against set of external conditions or context to
       produce desired comuptation(s)
  * ASTs are specialized examples of Composite pattern
  * AST evaluates self by recursively descending down tree

## Part III - Patterns for Ruby ##
* Chapter 16: Opening Up Your System witih Domain-Specific Languages
  * focus on the language, not the interpreter; provide a convenient
syntax
  * external DSL = parser & interpreter
* Chapter 17: Creating Custom Objects with Meta-Programming
  * %Q + class_eval = voodoo
  * attr_reader/writer/accessor live in module Module, included in
Object
* Chapter 18: Convention over Configuration
  * larger, conceptual-based approach to ensuring code is easy to use
and does most common things most easily
