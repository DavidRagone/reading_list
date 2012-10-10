# Pickaxe #

#Programming Ruby 1.9: The Pragmatic Programmers' Guide #

## Dave Thomas, Chad Fowler, Andy Hunt ##


### Part 1 - Facets of Ruby ###
Chapter 2: Ruby.new
* when creating string literal, single-quote version results in minimal Ruby processing; double-quote version results in more processing, due to looking for substitutions & interpolation
* global variables begin with $; instance variables @; class variables @@
* Array ltieral created w/ []
* can specify a default value in a Hash: Hash.new(0) would set 0 as the default (meaning what is returned when a key is not found; the default default is nil)
* puts & print can write to any I/O object
* gets returns next line from STDIN
* ARGV array contains each argument passed to running program via command line
* ARGF is special I/O object that acts like all contents of all files whose names were paased on the command line

Chapter 3: Classes, Objects, and Variables
* Uniform Access Principle: hiding difference between instance variables and calculated values (e.g. within an @price instance varaible and price_in_cents() and prince_in_cents=(new_value) methods); result is shielding from implementation of your class
* distinguish internal state of class from how that state appears on outside (to users of your class)
* initialize method sets up environment for object, leaving it in a useable state; other methods then use that state
* protected methods: can be invoked only by objects of hte defining class and its subclasses
* private methods: cannot be called with an explicity receiver - receiver is always self; can only be called in context of current object
* can set public/protected/private via private :method_name (in addition to traditional private, followed by defining each private method)
* varaibles are references to objects, but not objects themselves

Chapter 4: Containers, Blocks, and Iterators
* can have additional block-level variables by having a semi-colon: arr.each { |value; square| .... #code }, where square is local to the block, so won't affect external variables of same name
* parameters to a block always local to the block
* iterator = a method that can invoke a block
* via yield, can pass parameters to blocks and receive values from them
* enumerators can be useful objects; can use them to iterate in different ways with methods of Enumerable module
* writing '->' is equivalent to writing 'lambda'

Chapter 5: Sharing Functionality: Inheritance, Modules, and Mixins
* super keyword: Ruby sends messages to parent of current object, asking it to invoke method of same name as the method invoking super; it passes the parent's method the parameters passed to super; important when subclass has different method (e.g. initialize) that still needs parent's functionality
* include method makes refernece to a Module; require before include if module in separate file
* Comparable module requires <=> method; Enumerable, each

Chapter 6: Standard Types
* write integers iwth optional sign and optional base indictor: 0 for octal, 0d for decimal (default), 0x for hex, 0b for binary; followed by string of digits
* create string w/ a 'here' document: start it by identifying a terminating sequence (e.g. <<END_OF_STRING), end it with that same sequence
* Struct: data structure that contains given set of attributes
* Ranges can be made of objects you define; requires object respond to 'succ' method (returns next in sequence) and <=> method
* can use === with a range to see if a value falls within the interval represented by the range: (1..10) === 5 #=> true

Chapter 7: Regular Expressions
* can create a regexp object with %r syntax
* =~ is positive math; !~ is negative match
* after a match, can call pre_match, post_match, and index using [0] on MatchData to get the three parts of the matched object

Chapter 8: More About Methods
* can't put args with default values after splat

Chapter 9: Expressions
* commands enclosed by backtick (`) or %x will be executed by underling OS; exit status of command available in global variables $?
* && returns second argument, if both truthy, else first
* equal? returns true if receiver and argument have same Object ID
* can have "then" within "if" clauses (and elsif, else)
* can use case with and without a target: case [optional target]; withouyt, specify boolean for each when
* break terminates the immediately enclosing loop; control resumes at statment following the block
* redo repeats current iteration of loop from start without re-evaluating condition or fetching next element
* next skips to end of loop, going to next iterator

Chapter 10: Exceptions, catch, and throw
* exceptions let you package info about an error into an object; that object is propagated back up the calling stack automatically until the runtime system finds code that explicitly declares it knows how to handle that exception
* can make own exception class by making it sublcass of StandardError
* begin, rescue, end
* rescue Exception: will process all exceptions; if end rescue block with raise, re-raises the exception (essentially code between becomes intermediate steps)
* can have multiple rescues in begin block, specifying multiple exceptions to catch
* at end of rescue caluse, can give name of local variable to receive matched exception (e.g. rescue SyntaxError, NameError => boom)
* ensure goes after last rescue clause; contains code that will always be executed as the block terminates
* can use retry within a rescue
* catch/throw: if throw occurs, Ruby finds catch location in code for same symbol above, and unwinds the stack to that point, then terminates the block

Chapter 11: Basic Input and Output
* base class for input and output = IO
* subclasses File, BasicSocket
* StringIO: acts like FileIO, but takes string input (instead of file); great for testing

Chapter 12: Fibers, Threads, Processes
* fibers allow for thread-like appearance without the complexity
* continuation: added by requiring continuation library, is a way of storing state of running web app between requests (see pp 157, top)
* b/c many ruby extension libraries are not thread-safe (they were written for old threading model), Ruby uses native OS threads but only operates on a single thread at a time

Chapter 13: Unit Testing
* Ruby 1.8 came with Nathaniel Talbott's Test::Unit pre-installed; 1.9 comes with Ryan Davis' MiniTest
* TestUnit usage: 
    require 'test/unit'
    class TestRoman < Test::Unit::TestCase
      def test_2
        assert_equal("i", .....)
        assert_equal(......)
      end
    end
* include minitest instead via: require 'minitest/unit'
* methods that hold the assertions must have names starting with 'test'
* setup/teardown methods auto-run before/after tests
* if put test in file called test_other_file_name.rb, tests run by just running file

Chapter 14: When Trouble Strikes!
* invoke standard debugger by using '-r debug' option when running file
* in vi, run Ruby code with :w !ruby
* to run scripts with warnings enabled: -w
* Ruby profile library, use command-line option '-r profile', will produce list of methods, with frequency run and time to execute


### Part II - Ruby in Its Setting ###
Chapter 15: Ruby and Its World
* useful ruby options: '-c' checks syntax only; '-I directories' specifies directors to be prepended to $LOAD_PATH ($)
* ARGV: all strings passed to file when run, as array
* ARGF: convenience objects; ARGV w/ auto open and close of files
* OS environment variables available via the hash-like ENV
* find where ruby looks for libs: ruby -e 'puts $:'
* gem query --details --remote --name-matches NameofGem
* can add '-t' option when installing a gem to auto-run its test-suite
* rake task named default will execute by running just 'rake'
* 'rake -T' to see list of all rake tasks for which there is a description

Chapter 16: Namespace, Sources files, and Distribution
* names of clases & modules are constants: the name used for a class (e.g. String) is a Ruby constant containing the object representing that class
* file locations: 
    anagram/ <- top level
            bin/ <- command-line interface goes here
            lib/ <- library files, broken up by functionality
            test/ <- test files

Chapter 17: Character Encoding
* 1.9 allows non-ASCII encoding 

Chapter 18: Interactive Ruby Shell
* irb within irb: use 'jobs' to see all open/running, and 'fg' to switch


### Part III - Ruby Crystallized ###
Chapter 22: The Ruby Language
* is a reference to the core Ruby language

Chapter 23: Duck Typing
* don't check kind_of; embrace duck_typing, catch Exceptions if need be
* try the #respond_to? method
* symbol#to_proc is ~ half as fast as regular block version (so take note of it in performance critical code)

Chapter 24: Metaprogramming
* singleton methods: are specific to a particular object
* creation of a singleton method creates an anonymous class to hold that method; called a singleton class or eigenclass
* class methods are really singleton methods on the class object
* some really cool examples of how Ruby's class hierarchy works, especially given singletons, and include/extend
* define_method: takes name of a method and block; use inside another method, e.g. class-level singleton, to do meta-programming; run in each inheriting class the 'super' method, which will create the define_method method

