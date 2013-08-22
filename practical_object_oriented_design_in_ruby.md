## Chapter 1 - Object Oriented Design
* OOD is about managing dependencies; is set of coding techniques that arrange
  dependencies so objects can tolerate change
* don't want objects to know too much about one another
* practical design = not guessing at what future change will be, just accepting
  that something will change

## Chapter 2 - Designing Classes with a Single Responsibility
* foundation of oo-system is the message; most visible organizational structure
  is the class
* design is art of preserving changeability (not reaching perfection)
* you will _never_ know less about a project's right design than at the
  beginning (or than at any present time relative to future)
* easy to change means:
  * changes have no unexpected side effects
  * small changes in requirements require correspondingly small changes in code
  * existing code is easy to re-use
  * easiest way to make a change is to add code that in itself is easy to change
* therefore code you write should be:
  * transparent: consequences of changes should be obvious in code that is
    changing and in distant code that relies on it
  * reasonable: cost of any change should be proportional to the benefits the
    achieves
  * usable: existing code should be usable in new and unexpected contexts
  * exemplary: the code itself should encourage those who change it to
    perpetuate these qualities
* a class should do the smallest possible useful thing
* ways to see if your class is doing too much:
  * interrogate it: "Please, Mr. #{class_name}, what is your #{publicly
    available method}?" If class can respond to method, shoudl make sense in
context of the object
  * describe the class in one sentence; if use word "and", likely has more than
    one responsibility; if use "or", it has multiple unrelated responsibilities
* _don't_ design for unknown future changes; ask self "What is the future cost
  of doing nothing today?" You will never know less than you know right now
* depend on behavior, not data; e.g. attr_reader over @var
* Ruby's Struct class: give its initializer symbols, get back class with
  attr_readers and writers
* methods should have a single responsibility because of benefits:
  * expose previously hidden qualities: when all methods have single
    responsibility, it's infinitely easier to refactor the class itself - makes
thing class is doing more obvious (can start by just plucking out methods that don't belong)
  * avoid need for comments
  * encourage reuse

## Chapter 3 - Managing Dependencies
* an object depends on another object if, when one object changes, the other
  might be forced to change in turn
* types of dependencies
  * name of another class
  * name of a message intend to send to someone other than self
  * arguments that a message requires
  * order of those arguments
* remove external dependencies from complex methods into a method of their own,
  encapsulating them (see, e.g., p.45)
* don't be afraid to use a hash as a parameter to remove input order dependency
* use Hash#fetch to avoid gotchas of hashes in params (use to return default
  value)
* use a wrapping method to isolate external dependencies - allow classes in your
  app to only depend on code you own

## Chapter 4 - Creating Flexible Interfaces
* your app is its messages - reflect living, animated application
* design, therefore, must focus on message - not just what they know
  (responsibilities), who they know (dependencies), but how they talk to one
another
* interface can mean that defined within a class, or that spans across classes
  as a set of messages where the messages themselves define the interfaces - as
if interface defines a virtual class (does she mean like an abstract class?)
* methods of the Public Interface
  * reveal class's primary responsibility
  * are expected to be invoked by others
  * will not change on a whim
  * are safe for others to depend on
  * are thoroughly documented in the tests
* methods of the private interface
  * handle implementation details
  * are not expected to be sent by other objects
  * can change for any reason whatsoever
  * are unsafe for others to depend on
  * may not even be referenced in the tests
* domain objects: represent nouns of an app, have data & behavior, easy to find,
  but be wary - don't want to coerce behavior into them; focus on messages
between them to discover less obvious objects you'll want
* the things an object knows about other objects make up its context
* an object has a single responsibility but expects a context (e.g. some other
  object responds to a particular message)
* objects w/ a simple context are easy to test & reuse
* progression of oo-code has caller of method say (bad to good):
  * "I know what I want and I know how you do it"
  * "I know what I want and I know what you do"
  * "I know what I want and I trust you to do your part"
* Law of Demeter
  * restricts set of objects to which a method may send messages
  * prohibits routing message to third object via second object of different
    type

## Chapter 5 - Reducing Costs with Duck Typing
* concrete code: easy to understand but costly to extend; abstract code:
  obscure at first, but once understood is far easier to change

## Chapter 6 - Acquiring Behavior Through Inheritance
* inheritance defines mechanism for forwarding not-understood messages
* rule for refactoring into inheritance hierarchy: arrange code so can promote
  abstractions rather than demote concretions
* ask "What will happen when I'm wrong?"
* Two costs to every decision:
  1) implementation
  2) changing it when discover first was wrong

## Chapter 7 - Sharing Role Behaviors with Modules
* objects should be allowed (and able) to answer questions of their state; don't
  use intermediary "manager" object to track them
* discussion of oo-inheritance, and Ruby's implementation (composition +
  inheritance)
* use inheritance when:
  * object checks on a variable with name like type or category
  * sending object checks class of receiving to determine what message to send
* honor contract - no subclass that doesn't fully implements superclass
  * means honoring Liskov substitution principle, which states: Let q(x) be a
    property provable about objects x of type T. Then q(y) should be true for
objects y of type S where S is a subclass of T
  * ie, subclass must always be substitutable for its supertype
* template method pattern ftw
* decouple classes:
  * don't send super
  * instead use hook messages to allow subclass to participate while absolving
    it of responsibility for knowing abstract algorithm (e.g. superclass)
* create shallow hierarchies

## Chapter 8 - Combining Objects with Composition
* composition
  * x has a y
  * e.g., bicycle has parts
  * means rather than subclassing MountainBike from Bike, you compose a bike by
    passing in an instance of MountainBikeParts
  * one step further is Part objects that fit a duck type (e.g. w/ name,
    description, needs_spare attributes)
* when to choose what
  * Inheritance for "is-a" relationships
  * Duck-types for "behaves-like-a" relationships
  * Composition for "has-a" relationships

## Chapter 9 - mandatory write tests or else chapter. Watch Sandi's talk at
RailsConf2013 to get better version





