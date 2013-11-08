#Agile Web Development with Rails 4

Note: Rather than my usual chapter-by-chapter notes, I wrote down page numbers.
You'll see those in parentheses (sometimes).

* ```sanitize``` - allow html stylings from a model (e.g. stored in a text field);
  must be trusted
* (102) controller is testing things in the view; great example of how Rails
  over-reaches; MsuperC, not so much MVC
* (104-5) caching w/ #cache view method, in layers
  * top level using latest updated-at full AR model
  * next level for @model.each
  * cache passed Array w/ 2 params, outer seems to be div class name
    (convention?), inner AR model
* so what exactly is ActiveSupport::Concern?
* ```button_to``` defaults to POST
* ```_url``` vs ```_path```
  * url when doing redirect_to, b/c HTTP spec requires fully qualified URL, and
    when changing domains (though I've noticed Chrome at least, and probably
others, don't care if don't give full URL on redirect)
  * path rest of time
* (144) respond w/ js file: ```$("#id").html("<%= escape_javascript render(@thing)
  %>");``` uses partial _thing, updating via ajax
* (148) what happens when you render json: @thing, status: :unprocessable_entity
  (or :created, etc.)? Assume Rails is doing a mapping to appropriate code, e.g.
204
* can use rails ```content_tag("name e.g. div", attrs, &block)``` to do things
  like conditionally hide (display: none) certain html tags
* ```$(document).on "ready page:change", -> ...``` due to turbolinks
* Rails default feed is ATOM
  * cache w/ ```stale?``` method
  * look for template.atom.builder
* (173) route get :method, on: :member (rather than do block for member stuff)
* (176) xml ```@thing.to_xml(include: :some_association)```; probably same for
  to_json
* ```config.action_mailer.delivery_method``` options are ```:smtp```, ```:sendmail```, and ```:test```
  * ```:test``` makes it available via _ActionMailer::Base.deliveries_
* ```rails g model ... :digest``` for passwords
* (198) difference between Rails ```form_for``` and ```form_tag``` ?
  * ```form_tag``` doesn't take an object (```form_for``` builds form for an
    object)
* after hooks are called as part of transaction
* can raise exceptions in after hook to halt execution
* can hide (not report to controller) exception by raising ```ActiveSupport::Rollback```
* optional route section via quotes and parens ```scope '(:locale)'```
* in dev, go to [localhost:3000/rails/info/routes](localhost:3000/rails/info/routes) to see list of routes
* translate text via ```I18n.t``` method, avialable as ```t``` in views
* Rails translation is kinda nice
* how to write own Rack middleware?
* could I serve faster static pages from public?
* (271) Rails loads controller specific layout files from
  app/views/layouts/controller_name.html.erb
* controller names don't have to be pluralized
* (279) what is SQL interval type?
* (280) ```association_count``` rails keeps a counter cache for all child tables
  (nice!)
* (281) Rails considers model objects ```==``` if same class and same primary
  key, so unsaved will be considered the same (b/c id nil for both)
* table with foreign key always ahs the belongs_to declaration
* (285) can pass ```Model.create``` an array of hashews, it'll return array of
  related model objects
* (288) why pass ```Model.where``` an array? -> first is string, rest are values
  to be substituted in
* (288) can name placeholders in SQL strings: ```Model.where("name = :name",
  name: params[:name])
* can pass hash directly to Rails where: ```Model.where(params[:thing])```,
  though this takes all the key-value pairs (could be dangerous)
* explicitly calling ```joins``` or ```select``` results in returned records
  being marked read only
* ```Model.find_by_sql "arbitrary sql"```
* (296) ```Model.update``` takes id and hash of values to update
* ```Model.delete``` and ```delete_all``` bypass callbacks and validations,
  ```destroy``` and ```destroy_all``` call them
* (301) can extract validations to a class, define method w/ that callback that
  takes model, e.g. ```def before_save(model)``` then on AR::B class, do
```before_save Validator.new```
* ActionPack = ActionDispatch, ActionController, ActionView
* (317) can use a concern in routes to share similar subsections
* (320) what class does cookies, headers, request, and session return?
* template vs. view?
* ActionController will call a template directly if no action method is defined
* (325) what is callback used in render :json ?
* (331) session can hold any marshalable object
* contents of session are default encrypted (thankfully)
* default session store is cookies; means more data on every request
* (336) flash is store that persists across two instances (two requests); useful
  for redirects, in which browser is told to make new request; stores values for
one more request, then they are removed
* flash data is stored in the session (so same rules apply)
* (339) callback stops action if run before action and returns false
* (342) view can access controller's instance variables, flash, headers, logger,
  params, request, response, and session
* (348-9) uploading file example (and how to store in db)
* helper files designed to extract view logic
* (353) lots of number helpers, including for %, $, time, ...
* ```simple_format``` is view helper for honoring line and paragraph breaks
* ```excerpt``` truncates string (very useful looking)
* ```cycle``` helper alternates (e.g. for highlighting rows)
* ```link_to_if```, ```link_to_unless```, ```link_to_unless_current```
* (357) can hide email from crawlers w/ ```encode: "javascript"``` option in
  mail_to
* ```auto_discovery_link_tag``` ???
* (360) application layout is used only if controller specific layout is not
  found
* can specify layout to use in controller, and exclude some formats (e.g. rss,
  atom)
* if layout call is passed string, renders that layout; if symbol, assumes
  refers to controller method that determines which layout to use
* (361) rails renders regular template before layout is invoked, so template
  could set instance variable and then can use it in layout
* (362) ```content_for``` and ```yield``` to display page-specific content
* partial useful for ajax update of it
