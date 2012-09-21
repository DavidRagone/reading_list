#Growing Object Oriented Software, Guided by Tests#
##Steve Freeman and Nat Pryce##


## Part I - Introduction ##
* TDD is deceptively simple; writing tests first moves them from being about keeping bugs away from the users to helping the development team understand the needed features and deliver them reliably and predictably
* Chapter 1 - What is the Point of Test-Driven-Development?
    * need empirical feedback to learn about system & its use; need feedback cycles
    * time box: analyze, design, implement, deploy; repeat
    * optimize for reading code
    * TDD makes testing a _design_ activity; tests clarify ideas about what we want code to do
    * Writing test (first):
        * clarifies acceptance criteria - how can we tell we're done? (design)
        * encourages loosely coupled components - easily tested in isolation and, at higher levels, combined together (design)
        * adds executable description of what code does (design)
        * adds to complete regression suite (implementation)
    * Golden Rule of TDD: Never write new functionality without first writing a failing test
    * acceptance test: exercises the functionality we want to build
    * unit test: underneat acceptance level; red/green/refactor
    * whenever possible, acceptance test should exercise system end-to-en without directly calling its internal code; interacts with system from outisde; exercises both system & process by which it's built and deployed
    * automated build should (triggered by someone checking code into source repo): check out latest version, compile & unit test, integrate & package the system, perform production-like deployment to realistic environment, and exercise the system through its external access points
    * Levels of Testing:
        * Acceptance: Does the whole system work?
        * Integration: Does our code work against code we can't change?
        * Unit: Do our objects do the right thing? Are they convenient to work with?
    * Unit tests are about internal quality - code is easy to understand and change
    * Acceptance/end-to-end tests are about external quality - meets needs of users
    * code should be loosely coupled & highly cohesive
        * elements are coupled if a change in one forces a change in the other
        * cohesion is a measure of whether element's responsibilities form a meaningful unit
* Chapter 2 - Test-Driven Development with Objects
    * object-oriented design focuses more on the communcation between objects (not on the objects themselves)
    * easier to change the system because can focus onw hat we want it to do, not how
    * objects have roles, responsibilities, and collaborators
        * an object is an implementation of one or more roles
        * a role is a set of related responsibilities
        * a responsibility is an obligation to perform a task or know information
        * collaboration is an interaction of objects and/or roles
    * calling object should describe what it wants in terms of the role that the called object plays; let called object decide how to make that happen; known as the Law of Demeter, "Tell Don't Ask"
    * but occassionally ask objects about their state; ask question the object needs answered, isntead of for information for object to figure it out itself
* Chapter 3 - An Introduction to the Tools
    * Details on Java frameworks used in the book's detailed examples (JUnit v4, Hamcrest, jMock2)
    * test fixture: the fixed state that exists at start of test; ensures test is repeatable

## Part II - The Process of Test-Driven Development ##
* Chapter 4 - Kickstarting the Test-Driven Cycle
    * awesome Frank Tibolt quote: "We should be taught not to want for inspiration to start a thing. Action always generates inspiration. Inspiration seldom generates action."
    * start with build deploy and test on a nonexistent system - essential not to leave to later
    * first work out how to build, deploy and test "walking skeleton", then use that infrastructre to write acceptances tests for first meaningful feature
    * is not BDUF; not designing classes and algorithms before code; just making smallest number of decisions to get to TDD cycle
* Chapter 5 - Maintaining the Test-Driven Cycle
    * write acceptance tests using only terminology from app's domain, not underlying tech (databases, web servers)
    * should not have to rework tests from changes to system's tech infrastructure (example of FTP & binary files changing to web services & XML)
    * one passing, an acceptance tests represents a completed feature and should not fail again; a failure means there's been a regression, that we've broken existing code
    * start unit tests with simplest succcess case
    * develop from inputs to outputs
    * instead of testing a method (which tests the what it does, not what it is for), test the features the object should provide; need to know how to use a class to achieve a goal
    * when a feature is difficult to test, ask not just _how_ to test it, but more importantly _why_ it is difficult to test (Listen to the Tests); likely cause is design needs improving
* Chapter 6 - Object-Oriented Style
    * separate concerns: when have teo change behavior of a system, want to change minimal amount of code; because can not predict when change will be needed, we gather together code that will change for the same reason
    * group code by level of abstraction (And aim to keep changes in higher levels, where it's easier to work)
    * style: authors ttend to write message-passing style between objects, but functionally within an object, building up behavior from methods & values that have no side effects
    * eveery object should have a single, clearly defined responsibility; should be able to describe what an object does without using conjunctions ("and", "or")
    * Relationships between objects (heuristics, not rules):
        * Dependencies: services that the object requires from its peers so it can perform its responsibility; object can not function without these and should not be possible to create the object without them
        * Notifications: peers that need to be kept up to date with the object's activity; notifications are "fire and forget" - object neither knows nor cares if peers are "listening"
        * Adjustments: peers that adjust the object's behavior to the wider needs of the system
    * Composite objects (those created outside what the language provides) should hide existence of component parats and the interactions between them, and expose a simpler abstraction to peers
    * context independence: system is easier to change if its objects have no built-in knowledge of the system in which they execute; whatever must known about environment it's running in must be passed in
* Chapter 7 - Achieving Object-Oriented Design
    * test first = describe _what_ we want to achieve before considering _how_
    * need to limit scope of unit tests for them to be understandable & maintainable
    * to construct object for a unit test, need to pass its dependencies to it, which requires knowing what they are
    * mock an object's peers (dependencies, notifications, adjustments), but not its internals
* Chapter 8 - Building on Third Party Code
    * don't mock external resources - it's code you can't control
    * write layer of adapter objects that use the third-party API to implement the interfaces; test these adapters with focused integration tests
    * some exceptions to mocking third-party libraries, e.g. behavior that's hard to trigger (exceptions)

## Part III - A Worked Example ##
* Chapter 9 - Commissioning an Auction Sniper
    * XMPP: the eXtensible Messaging and Presence Protocol
        * a protocol for streaming XML elements across the network
        * originally designed for and named after Jabber, renamed upon submission to IETF for approval as an internet standard
        * used for exchanging structured data in close-to-real-time
    * intro to the design of an app, working through the what to the basic to-do
    * note that it is declared _not_ proper agile process
* Chaper 10 - The Walking Skeleton
    * point is to help us understand requirements well enough to propose & _validate_ a broad-brush system structure
    * for most projects, this takes surprising amount of effort
    * start the walking skeleton with a test
    * write test as if implementation already exists - "programming by wishful thinking"
* Chapter 11 - Passing the First Test
    * testing most basic end-to-end
    * first implementation leaves out lots of details (example of single instance variable instead of real version needing multiple); only purpose of this version of build is to support the test
    * in professional org, expect separate db instance for each developer and also expect min one test rig that represents production environment
* Chapter 12 - Getting Ready to Bid
    * start the next feature of sample app w/ acceptance teset; use these going forward to show incremental progress
    * each acceptance test should force a manageable increase in functionality
    * authors' approach to TDD is to start w/ outside even that triggers the behavior they want to implement and work way into code an object at a time, until reach a visible effect (e.g. sent messsage or log entry) indicating goal was achieved
* Chapter 17 - Teasing Apart Main
    * coding is like rock-climbing: apply the "three-point contact" rule - move one hand/foot at a time to minimize risk of falling off; each move is minimal & safe
    * refactoring is a design activity - need to apply all dev skills simultaneously to it

## Part IV - Sustainable Test-Driven Development ##
* Chapter 20 - Listening to the Tests
    * make the boundaries of an object clearly visible; objects should only deal with values and instances that are local (created/managed within its scope) or passed explicitly
    * logging: distinguish between debug & trasce (diagnostic logging as infrastructure for programmers, on only in dev/test environments) from errors & info (support logging as part of UI, on in production)
    * Bloated Constructor
        * if have long, unwieldy list of arguments, see if any implicit strcuture exists that can tease out to define new concept p acakged as separate object;  look for args always used together and those with same lifetime
        * if has too many responsibilities, needs breaking up; code smell will accompany test smell, as tests for various features will have no relationship with each other
        * if not all the arguments are dependencies, use more default values and only overwrite those for particular test cases
    * in tests, distinguish _stubs_ (simluations of real behavior that help us get the test to pass) and _exceptions_ (assertions we want to make about how an object interacts with its neighbors)
* Chapter 21 - Test Readability
    * tests must express behavior of the code clearly, not just verifyt it
    * write tests in terms of what hte object __does__, not what it __is__
    * authors often write tests "backwards": name it first, then write target code, expections and assertions, finally setup & teardown
    * prioritize expressiveness (and hence readability) over minimizing the source lines
* Chapter 22 - Contstructing Complex Test Data
    * object mother pattern: a class that contains a number of factory methods that create objects for use in tests; makes tests more readable by packaging up the code that creates new object structure, and giving it name


Rest of the book is more advanced than I am ready for; a future read-through is in order
