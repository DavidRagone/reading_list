# Getting Started with Twitter Flight, Tom Hamshere

## Chapter 1 - What is Flight?

* piggybacks DOM to provide app structure
* utilize DOM events to act as interface between (its) components
* provides constructor interface (+ interface for mixins and DOM access)
* event driven interfaces
  * component instances attached to DOM nodes (component's root node)
  * events triggered within a component are initiated on the component's root
    node and bubble up tree using standard HTML event model
  * default is component listens to events on its root node
* should be no parent-child relationships between components
* makes components independent and reusable, not relying on others
* as a mustache component renders HTML, Flight UI components render behavior


## Chapter 2 - The Advantages of Flight
* simple format followed by most of its methods; learn one, learn all
* blah blah blah simple organized components blah blah


## Chapter 3 - Flight in the Wild
* oh look Twitter uses it


## Chapter 4 -
* how to install things called Flight


## Chapter 5 - Components
* a component is a constructor function
* Flight provides components with set of utilities (e.g. event handling, DOM
  node selection)
* each component instance is attached to a DOM node
* functionality is shared between components via mixins
* two types of components: User Interface and Data
* only UI components should modify the DOM or listen to user-initiated events
* Data components manage data storage, requests, and manipulation
* within component definition, context (this) always refers to the component
  instance
* components are defined using the AMD CommonJS format
* steps to create a component:
  * define component using define(function() { })
  * use requireJS to load flight's component lib: ```var defineComponent =
    require('flight/lib/component');```
  * return constructor for component: ```return defineComponent(taskData);```
  * define component: ```function taskData() { // do stuff }```
* steps to use the component:
  * in separate file, using define syntax, write function that requires the
    component files, and then attach them to the DOM
  * ```define(function (require) { });```
  * ```var HelloWorld = require('component/hello_world');``` (where string is
    path to the component)
  * export the components: ```return initialize;```
  * define the usage (attach to DOM): ```function initialize() {
    HelloWorld.attachTo(document); }```


## Chapter 6 - UI Components
* most components are attached to elements (e.g. forms, buttons, lists)
* in addition to listening to events, components will emit their own (for others
  to listen to, presumably)
* components can also "interrogate" the DOM and modify the DOM


## Chapter 7 - Data Components
* data components act as interface btwn UI and storage layers
* should attach all data components to the document, allowing them to receive UI
  events from entire app
* agnostic to document structure
* UI components should never be aware of which data components they are
  interacting with
* generally named to describe their payload: dataTask, dataTasks, dataSettings
* sometimes data elements will trigger events to describe an interesting moment
  in the data process; example: to help app show a spinner when content is
loading, data component might trigger an event such as
dataWaitingForAsynchronousResponse and dataReceivedAsynchronousResponse to allow
the UI to show and the spinner (but that will be done by separate UI component,
which listens)
* event handlers: accept two parameters: a jQuery event, followed by a data object (the one
    passed to the trigger method)
* this book needs some bloody editing. desperately

## Chapter 8 - Event Naming
* be smart about names, as this is the interface
* suggestions
  * Data request: a request from UI for data, e.g. uiNeedsTask
  * UI event: produced by UI, handled by both UI and data components
  * don't separate events into user-initiated actions and actions performed by
    UI components
  * Data event: contains data; prefix followed by payload, e.g. dataTask,
    dataTags
  * Data error: e.g. dataTaskError; good practice to include original request
    (event data payload from data/UI event) and response from server

## Chapter 9 - Mixins
* create similar to components, minus ```defineComponent```
* include in components by requiring them (in addition to ```defineComponent```
  and then including in ```return defineComponent(component, mixin);```
* mixins will override similarly named methods declared in a component that
  imports the mixin
* can use before, after, and around methods for any method, not just initialize
  ```this.after('someMethod', function() { }```
* good way to handle customizing behavior inherited from mixin
* before, after, around are part of Flight's "Advice" API

# Chapter 10 - Templating and Event Delegation
* interesting tool called [Hogan](http://twitter.github.com/hogan.js)
* mostly skipped reading, as seems a bit orthoganal to Flight itself; but worth
  revisiting templating topic

# Chapter 11 - Web Application Performance
skipped

# Chapter 12 - Testing
* includes example BDD (Jasmine) test
* see [jasmine-flight](http://github.com/flightjs/jasmine-flight)
* I'd like to also unit test components...

# Chapter 13 - Complexities of Flight Architecture
* ...
