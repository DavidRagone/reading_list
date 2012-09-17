#Eloquent Ruby, Russ Olsen#


## Part I - The Basics ##
* Chapter 1 - Write Code that Looks Like Ruby 
    * camels for classes, snakes everywhere else
    * blocks: {} for single-statements, do..end for multiple statements
    * ? and ! at the end of ruby method names: not special syntax, just part of the naming convention (? is generally used when the method returns a boolean, ! when the method does something important, e.g. modifying self)
* Chapter 2- Chose the Right Control Structure 
    * unless == if not
    * until == while not
    * code block in #each method introduces a new scope
    * ruby case statement similar to JS switch
    * can write case statements in one line with “when x then y”; if not inline, exclude the “then”
* Chapter 3 - Take Advantage of Ruby’s Smart Collections 
    * array_of_words = %w{ word1 word2 word3 word 4 } #=> [“word1”, “word2”, “word3”, “word”]
    * can actually use any paired elements for open and close of the above, e.g. { }, [ ], <>, $ $, etc.
    * for method to take arbitrary set of arguments, use \* args; \* is called a splat
    * splat can be used in reverse, with an array that you want to turn into arguments
    * if hash is at the end (excluding a block) of arguments in a function call, don’t need the braces { }
    * #inject: if don’t provide first value for result in () (e.g. some_array.inject() { #stuff } ), #inject will skip calling the block for the first element and instead use that element as the initial result
    * can get an object’s public methods by calling object_name.public_methods
* Chapter 4 - Take Advantage of Ruby’s Smart Strings 
    * single-quote strings can only have escaped single-quotes and backslashes (no tabs, newlines, etc.)
    * quote mechanism: %q{ Text with “quotes and ‘s }
    * note that %q will make single-quoted string; %Q double
    * can cancel out new lines in a string with \
    * here document: «EOF lots of multiline text EOF
* Chapter 5 - Find the Right String with Regular Expressions 
    * set - created w/ [ ]; e.g. [aeiou] will match any single lowercase vowel
    * range - specify beginning and end of sequence of characters, separated by a dash, e.g. [0-9] or [a-Z] or [0-9a-f]
    * special regex:
    * \d matches any single digit
    * \w matches any “word character” (including letter, number, & underscore)
    * \s matches any whitespace character
    * | matches either what is before or after, e.g. A|B
    * Ruby RegExp encased between forward slashes /stuff/
    * =~ operator to test whether reg exp matches a string; returns index of start of match (or nil); note this means 0 is a match at start of string
    * can turn off case sensitivity by adding “i” after ending forward slash, e.g. /AM/i
    * \A to match only if string begins with proceeding regexp
    * \z matches unseen end of string (put on end of regexp)
    * ^ to match beginning of any line within text
    * $ to match end of string or end of any line
* Chapter 6 - Use Symbols to Stand for Something 
    * symbols are immutable
    * can only be one instance of any given symbol (so multiple references to it will be pointing to the same object)
* Chapter 7 - Treat Everything Like an Object - Because Everything Is 
    * if you can reference it with a variable, it’s an object
    * #instance_variables - will pull out names of any instances variables in an object; is a reflection-oriented method
    * private methods: can not be called w/ an explicit object reference (e.g. obj_name.private_method_name)
    * protected methods: any instance of a class can call a protected method on any other instance of a class
    * can easily violate private/protected w/ “send” method, e.g. obj_name.send( :private_method_name )
* Chapter 8 - Embrace Dynamic Typing 
    * Ruby does not judge an object by its class hierarchy
    * “the method is either there or it is not”
    * duck typed
* Chapter 9 - Write Specs! 
    * traditional is Test::Unit
    * make tests in class (e.g. DocumentTest < Test::Unit::TestCase ), with a method for each test named starting with test_
    * RSpec == awesome (http://rspec.info)
    * stub: pass in hash of methods as symbols to return
    * mock: slightly more fleshed out stub


## Part II - Classes, Modules, & Blocks ##
* Chapter 10 - Construct Your Classes From Short, Focused Methods 
    * write methods that do one thing (and do it well)
    * composed method technique: advocates dividing class up into methods that have three (3) characteristics:
    * 1) do a single thing; easier to write, understand, and test
    * 2) operate at a single conceptual level; don’t mix high-level logic with nitty-gritty details
    * 3) a name that reflects its purpose
    * one way out: every method should have all logic converge at the bottom for a single return (rather than mix returns throughout the logic)
* Chapter 11 - Define Operators Respectfully 
    * binary operators (e.g. 2.+(3) ) require two objects; unary (e.g. -2) only one
    * unary operators defined via operator@, e.g. +@
* Chapter 12 - Create Classes that Understand Equality 
    * four equality methods: #eql?, #equal?, #==, #===
    * #equal? tests for object identity (references to identically same obj)
    * default behavior of == is same as equal? (at least as in Object class, inherited down through structure unless changed), so most often need to override in custom classes
    * #kind_of? returns true if instance or subclass of arg
    * #=== used in case statements (specifically w/ Regexp; a string == regexp is false always, but matching string === regexp will be true)
    * #eql? used in hash table (along with #hash function) to hash and bucket (and return values); so if update one of them in custom class, make sure to update the other to match
* Chapter 13 - Get the Behavior You Need with Singleton and Class Methods 
    * singleton method: a method designed for exactly one object instance (unsupported by numeric classes and symbols); defined by saying def instance.method_name; or can write class « instance_name, proceeded by regularly written definitions
    * class methods are singleton methods
    * class methods are attached to a class; instances of the class will not know anything about them
    * self is always the thing before the period when you called the class method
* Chapter 14 - Use Class Instance Variables 
    * class variables start with @@
    * when creating (setting) or looking up (getting) class variable, Ruby first looks for it all the way up the inheritance tree, sets it where it finds it, or if not found in the class written in
    * this makes class variables more like global variables with a slightly restricted realm; “vertical global variables”
    * class instance variable: vanilla, single @instance variables that find themselves attached to a class
    * works because inside a class method, self is always the class; this sets the instance variable on the class’s object
    * to access, call the right class method (see pp 175); e.g. in initialize
    * rather than write getter/setter, use attr_accessor (but keep in mind that class methods are singleton methods on a class)
    * class « self; attr accessor :some_variable; end
    * module variables are represented same as class variables: w/ @@
* Chapter 15 - Use Modules as Name Spaces 
    * a class is both a factory (makes new instances) and a container (holds methods and constants)
    * module is just a container; can hold methods, constants, classes, and other modules
    * to access a class in a module, write ModuleName::ClassName
* Chapter 16 - Use Modules as Mixins 
    * can share methods across otherwise unrelated classes by simply putting the methods (as instance methods) in a module, and then in the classes including the module (via ‘include ModuleName’ )
    * benefit of mixin (modules) is not having to restructure entire inheritance tree; can only have one superclass, but infinite modules included
    * if want mixin’s methods to be class methods, rather than instance methods, use ‘extend’ instead of ‘include’; is same as singleton approach: class « self; include Module; end
* Chapter 17 - Use Blocks to Iterate 
    * can check whether method was called with a block w/ ‘yield if block_given?’
    * blocks can take arguments, which you supply as arguments to yield;
    * def do_something_with arg; yield(“Hello World”) if block_given; end
    * do_something_with_arg { |message| puts “The message is #{message}” }
    * #will result in “The message is Hello World”
    * Enumerable Module can be included in a class as long as an #each method is defined in that class (relies on that method for much of its methods); also helpful to define #<=> (which compares two instances of the object, returning -1, 0, or 1 depending on which larger or if same)
    * break: when called form inside a block, break will trigger a return out of the method that called the block
    * an explicity return from inside a block causes the method that defined (not called) the block to return
* Chapter 18 - Execute Around with a Block 
    * what code blocks do well is to deliver code where it is needed
    * uses yield to run a block not listed in params
    * idea of burying details in a method that takes a block is technique called ‘execute around’
    * code blocks drag along the scope in which they were created; technical term for this scope-dragging property is closure
    * a closure is a block
    * only pass from app to execute around method args used in the execute around method, not the block
    * can have execute around method pass args from the method to the block (see mid 227 for example)
* Chapter 19 - Save Blocks to Execute Later 
    * passing block as explicit parameter via &block can be called w/ block.call (can check if block is missing with #nil?)
    * object version of a block (such as passed via &block) is an instance of the Proc class
    * lambda takes a code block and returns the corresponding Proc


## Part III - MetaProgramming ##
* Chapter 20 - Use Hooks to Keep Your Program Informed 
    * ruby hook is some way to specify the code to be executed when something specific happens
    * inherited hook fires when new subclass is created (def self.inherited; end); written in the superclass
    * module analog of inherited is included (written in the module)
    * $! is a global variables Ruby sets to the last exception raised
* Chapter 21 - Use #method_missing for Flexible Error Handling 
    * method_missing runs if called method can not be found anywhere up the ineritance tree; can override it in any class
* Chapter 22 - Use #method_missing for Delegation 
    * delegation - idea that an object might secretly use another object to get part of the job done
    * can use #method_missing and #send to have an object make any unknown calls to another
    * #super: forwards method call (including args) up class hierarchy
    * BasicObject: introduced in Ruby 1.9, is stripped-down, superclass of Object
    * note: lots of really awesome code in this  Chapter, too much to include detailed notes
* Chapter 23 - Use #method_missing to Build Flexible West 
    * can use #method_missing and a general method to check for multiple, similar methods; return super unless match (via =~)
    * note that this magic will muck up #respond_to? method; default #respond_to? only known about real methods (though can just rewrite #respond_to? based on same match =~)
    * note: lots of really awesome code in this  Chapter, too much to include detailed notes
* Chapter 24 - Update Existing Classes with Monkey Patching 
    * ruby has open classes - can change behavior of a class at any time
    * “last def win” principle
    * fun lore (fact?): guerilla —> gorilla —> monkey (patching)
    * #alias_method: copies a method implementation; alias_method :new_method_name :old_method_name; allows for several names doing same thing
    * can use alias_method to not have to re-write method again just to add some functionality (see bottom pp 298)
    * #remove_method :method_name deletes a method
    * #blank? is a String method added in Rails (via ActiveSupport)
* Chapter 25 - Create Self-Modifying Classes 
    * ruby class definitions are executable; read in by interpreter, then executed sequentially
    * can put control flow in class definitions to define two methods w/ same name, w/ which one used based on a constant value when class is loaded
    * Alternatively, can write class method that does same thing, which then allows for calling that method to change the instance method made available; make sure call method inside class
    * __FILE__ is ruby-supplied, set to path of source file of current class
* Chapter 26 - Create Classes that Modify Their Subclasses 
    * #class_eval method takes a string and evaluates it as if it were code that appeared in the class body
    * preferable to class_eval, however, is to use #define_method
    * to use #define_method, call it w/ the name of the new method and a block; result is new method w/ given name which will execute the block when called; parameters of the block become parameters of the new method


## Part IV - Pulling it All Together ##
* Chapter 27 - Invent Internal DSLs 
    * DSL = Domain Specific Language
    * Rake, RSpec, ActiveRecord are examples of internal DSLs
    * internal DSL means it’s built atop (or within) an existing language
    * note: lots of really awesome code in this  Chapter, too much to include detailed notes
* Chapter 28 - Build External DSLs for Flexible Syntax 
    * can build an external DSL using Ruby (but will need to write own parser)
    * difference is really a matter of writing a parser to handle non-Ruby syntax; Ruby does compiling
    * Treetop is “a language for describing languages”; it reads in a file that describes the syntax of your language and produces Ruby code that can parse the language
* Chapter 29 - Package Your Programs as Gems 
    * YARV (Yet Another Ruby VM) is written in C (and took over from MRI after 1.9 transition)
    * Rubinius: aims to produce an implementation of Ruby written in Ruby
    * YARV added an extra step between the parse tree and execution: turns the output of parsing  into a (more or less) flat list of byte code; YARV then executes the byte codes; result is dramatically faster execution