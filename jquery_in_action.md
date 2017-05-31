# jQuery in Action
## Bear Bibeault & Yehuda Katz

### Chapter 1: Introducing jQuery
* unobstrusive JS = separate behavior from structure (same as using
stylesheets to separate style from structure)
* jQuery focuses on retrieving elements from HTML pages and performing
   operations upon them
* $ === jQuery
* $(document).ready(function() { ... }); === $(function() { ... });
* coolness: $('<p>new words</p>').insertAfter('#someId');
* jQuery is easily extendable: $.fn.newFunction = function() { ... }
* jQuery can be extended with plugins equally easily

### Chapter 2: Creating the wrapped element set
* use slew of CSS selectors (including those from CSS3)
* container selector (e.g. li:has(a)) - matches all <li> elements that
contain an <a>; not same as "li a", which selects all a's inside li's
* by position
  * :first
  * :last
  * :first-child, last-child
  * :only-child
  * :nth-child(n)
  * :nth-child(even|odd)
  * :nth-child(Xn+y) - nth child computed by formula, e.g. 3n + 1
(returns the item after every 3rd item)
  * :even, :odd
  * :eq(n) - the nth matching element
  * :gt(n) - matches elements after (and excluding) the nth matching
element
  * :lt(n)
* note nth-child starts counting at 1, while others start at 0
* see list on pp. 28 for more, e.g. :button, :checked, :disabled,
:hidden
* :not filter - p:not(:hidden)
* useful to alter set during chaining: index(), add(), not(), filter(),
end()
* relationships: see pp.43, e.g. children(), next(), nextAll(), prev(),
siblings()
* contains() returns new wrapped set based on text passed as param

### Chapter 3: Bringing pages to life with jQuery
* attr when used to change an attribute can take a function
* attr hwen used to update multiple attributes can be passed a JS object
* removeAttr(name) removes specified attribute from all matched elements
* stop user from double submitting a form:
  $("form").submit(function() { $(":submit", this).attr("disabled",
"disabled"); });
* _this_ pointer refers to apge element to which event was bound while
operating inside event handlers
* hasClass(name): returns boolean
* html(), html(text), text(), text(content)
* source moved if destination identifies one target, copied (remaining
in original location) if destination denotes multiple target elements
* form elements: val() returns value of first element in matched set;
likewise, val(value) sets fora ll matched elements

### Chapter 4: Events are where it happens!
* Netscape Event Model, aka Basic Event Model, aka Browser Event Model,
aka DOM Level 0 Event Model
* when event handler is fired, instance of calss named Event is passed
to the handler as its first parameter in most browsers
* event bubbling: when event triggered on an element in DOM tree, event
handling mechanism of browser checks if a handler has been established
for that particular event on that element, and if so, invokes it
  * after target element, event model works through all parents,
checking if they have established handler for that event
  * can stop event from continuing to propogate, call
event.stopProgagation(); (and Event.cancelBubble = true in IE ?)
* extra coolness added by DOM Level 2 spec (e.g. multiple listeners)
* jQuery Event Model: previously bind(), now on() - not omething htey
   knew when writing this in 2008

### Chapter 8: Talk to the server with AJAX
* XMLHttpRequest === XHR
* $.get(url, params, callback); callback requires response body as first
param and status as second
* $.getJSON(url, params, callback)
* when want full control over the request: $.ajax(options) -- see pp.
251 for options
* $.post(url, params, callback)
* ajax global functions: ajaxStart(callback), ajaxSend(...),
ajaxSuccess(...), ajaxError(...), ajaxComplete(...), ajaxStop(...)
