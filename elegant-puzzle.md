# An Elegant Puzzle

### Systems of Engineering Management

### Will Larson


#### Chapter 2 - Organizations
* "excellent organizations grow..." [dmr] but how become excellent?
* marginalia: footer > endnote
* marginalia next to "2.2.1 Four states of a team" - This might be useful. So
  not the connection (between states and solutions), but the alternatives to
hiring are interesting. All four states, however, are poorly defined and not
well thought-through
* "A team is falling behind if each week their backlog is longer than it was the
  week before. Typically, people are working extremely hard but not making much
progress, morale is low, and your users are vocally dissatisfied"
  * [dmr] couldn't you be making a ton of progress _and_ learning a ton about
    what else customers want, hence the growing backlog? not necessarily true
that growing b/c lack velocity
  * [dmr] also, progress relative to what?
* "A team is treading water if they're able to get their critical work
  done...and your users may seem happier because they've learned that asking for
help won't go anywhere" 
  * [dmr] how does that make them happier???
* marginalia: Overall assumption of well-contained unit of team, especially
  relative to business/product()s. Not always clear delinations
* "A team is innovating when their technical debt is sustainably low, morale is
  high, and the majority of work is satisfying new user needs"
  * [dmr] "satifying user needs" can be accomplished w/ no actual innovation,
    low morale, and increased debt
  * [dmr] And testing new ideas is great time to take some debt
* "When the team is falling behind ... easy wins" [dmr] When backlog growing,
  focusing on easy wins makes ton of sense
* marginalia: I'm realizing this entire model assumes the company is growing and
  doing well. Which matches his experience, I think. Easy to manage in those
situations. Bet lots of this falls apart when not growing
* "When the team is treading water ... limit work in progress ... transition
  from personal view of productivity to team view" 
  * [dmr] Not sure there's a time when either of these (limiting WIP and focus
    on team view of productivity) shouldn't be true
* "adding new individuals to a team disrupts that team's gelling process, so
  I've found it much easier to have rapid growth periods for any given team,
followed by consolidation/gelling periods during which the team gels. The
organization will never stop growing, but each team will." [dmr] I like this
style
* "The expected time to complete a new task approaches infinity as a team's
  utilization approaches 100 percent" - [dmr] I should teach this to my team, to
help them understand why I create slack. They seem confused/bored when they
don't have a project to tackle
* "strategy here is to funnel interruptions into an increasingly small area, and
  then automate that area as much as possible. Ask people to file tickets,
create chatbots that automate filing tickets, create a service cookbook, and so
on. With that setup in place, create a rotation for people who are available to
answer questions, and train your team not to answer other forms of
interruptions. This is remarkably uncomfortable because we want to be helpful
humans, but it becomes necessary as the number of interruptions climbs higher"
  * [dmr] Doesn't this just reduce effectiveness of org as a whole? Flies in
    face of previous appreciation of The Goal. Though measurability is nice
* Succession planning: "figure out what you do" [dmr] yeah I should do that
* "Take a look at your calendar and write down your role in meetings"
* "Look back over the past six months for recurring processes, like roadmap
  planning, performance calibrations, or head count decisions, and document your
role in those processes"
* "For each of the individuals you support, in which areas are your skills and
  actions most complementary to theirs? How do you help them? What do they rely
on you for?"

#### Chapter 3 - Tools
* "key tools for leading efficient change are systems thinking, metrics, and
  vision"
* read "Thinking in Systems: A Primer"
* stocks = stuff. "might be the number of trained managers at your company"
* flows = "changes to stocks". "inflows or outflows. Training a new manager is
  an inflow"
* information link "indicates that the valu eof a stock is a factor in the size
  of a flow. The link [shown in the first useful diagram] shows that the time
available for developing features depends on the number of trained managers."
* "every flow is a rate, every stock is a quantity"
* "a stock outside of a diagram's scope will be represented as a cloud,
  indicating that something complex happened there that we're not currently
exploring"
* Accelerate: The Science of Lean Software and DevOp four measures:
  1. *Delivery lead time* is the time from teh creation of code to its use in
     production
  2. *Deployment frequency* is how often you deploy code
  3. *Change fail rate* is how frequency changes fail
  4. *Time to restore service* is the time spent recovering from defects
* "Problem discovery"
  * this and next two are actually good lists
  * See pages 66 - 69
  * First phase of planning cycle: explore different problems you could pick to
    solve. Use these themes to populate problem space:
    * Users' pain
    * Users' purpose
    * Benchmark
    * Cohorts
    * Competitive advantages
    * Competitive moats
    * Compounding leverages
* "Problem selection"
  * Once identified possible problems, narrow down to specific problem
    portfolio. Consider:
    * Surviving the round
    * Surviving the next round
    * Winning rounds
    * Consider different time frames
    * Industry trends
    * Return on investment
    * Experiments to learn
* "Solution validation"
  * have explicit solution validation phase rather than jumping in w/ most
    difficult approach
    * Write customer letter
    * Identify prior art
    * Find reference users
    * Prefer experimentation over analysis
    * Find path more quickly traveled (expensive to build in entirety)
    * Justify switching costs
* "Strategies are grounded documents which explain the trade-offs and action that
  will be taken to address a specific challenge"
  * vs vision, strategy is approach to specific hallenge (vs gentle aligning
    pressure), practical (vs aspirational), variable time frame (vs long-term),
accurate and detailed (vs illustrative and directional), and can be written as
often as useful (vs as few as possible)
  * see: Good Strategy / Bad Strategy by Richard Rumelt
  * start off w/ diagnosis: theory describing the challenge at hand
    * call out factors and constraints that define challenge
    * have thorough problem statement
  * second step: identify policies that will apply to address challenge.
    describes general approach that you'll take, are often trade-offs between
two competing goals
  * when apply guiding principles to diagnosis, get actions. "this is going to
    be uncomfortable, but I think it can work" is ideal outcome.
* "visions describe a future in which [the tradeoffs described in strategy docs]
  are no longer mutually exclusive. An effective vision helps folks think beyond
the constraints of their local maxima"
  * "details are used to illustrate the dream vividly, not to prescriptively
    constrain its possibilities"
  * composed of:
    * one-to-two sentence aspirational statement
    * value prop: how will you be valuable to your users and to your company?
    * what capabilities will the product, platform, or team need in order to
      deliver on your value prop?
  * will know vision is succeeding when people reference the doc to make their
    own decisions
* Metrics and baselines
  * "There is a moment in every company's growth when top-level planning shifts
    from discussing specific projects to talking about goals. This happens
recursively across each scope of leadership, as areas of accountability become
too broad or complex for their leaders to consistently understand every
project's details."
  * Good goals have:
    * Target: where want to reach
    * Baseline: where you are today
    * Trend (current velocity)
    * Time frame (bounds change)
  * Helpful to have baseline (counter) metrics. Identify when should pause
    pursuing goals and instead invest in platform quality
* on migrations: "The fact that something stops working at significantly
  increased scale is a sign that it was designed appropriately to the previous
constraints rather than being over-designed"
  * [dmr] except if you should have anticipated the scale and built for the
    future
* Defining teams and groups. Consider:
  * Can you write a crisp mission statement for each team?
  * Would you personally be excited to be a member of each of the teams as well
    as to be the manager of each of those teams?
  * Put teams that work together (especially poorly) as close together as
    possible
  * Can you define clear interfaces for each team?
  * Can you list the areas of ownership for each team?
* When rolling out changes, "if necessary, hold an organization all-hands, *but
  probably try not to*. People don't process well in large groups, and the best
discussions take place in small rooms". [dmr] This feels often missed. Large
changes are often considered for extensive period of time by leads, but then
when rolled out often those leads forget that they've had days/weeks/months to
build context and consider tradeoffs, and assume they can simply send an email
or have an all-hands. Need time and space for people to think and process
* Controls
  * are the mechanisms you use to align with other leaders you work with
    * *Metrics* align on outcomes (while leaving flexibility for how outcomes
      achieved)
    * *Visions* ensure you agree on long-term direction while preserving
      short-term flexibility
    * *Strategies* confirm you have shared understanding of current constraints
      and how you will address them
    * others include org design, headcount and transfers, roadmaps, performance
      reviews
  * Degree of alignment (apply to each control):
    * *I'll do it* Best used sparingly, but when do, be explicit that you will
      handle something
    * *Preview* "I'd like to be involved early and often". An area where aren't
      on same page, will avoid redoing work
    * *Review* "I'd like to weigh in before it gets published or rolled out, but
      we're probably aligned on the topic"
    * *Notes* "I'd like to follow but don't have much I can add to" Likely
      aligned, and likely far-reaching initiative, where want to be able to
      represent their work
    * *No surprises* We're aligned, but need updates to keep mental model in
      tact. I'm evaluated on my ability to stay on top of new problems
    * *Let me know* "We're well aligned on this, since my colleagues have done it
      efore and done it well. I want them to let me know if something comes up
      that I can help with, but otherwise I'm totally confident it'll go well, so we
      don't need to talk about this much"
  * Controls + Alignment = Interface between you and folks you support
  * use to identify if micromanaging. If can't imagine world where you don't
    preview everyone's work, probably time to reflect on what's holding you back
    from letting the team thrive
* 3.9 Career narratives
  * "most folks are always at the furthest point in their career, each change a
    step into the unknown, with limited visibilty into the upcoming
    opportunities that their company can provide"
  * identify the skills needed to do the job you want (e.g. head of engineering)
    and find ways to apply those in current role. Don't need to wait to get
    there. E.g. org design, process design, business strategy, recruiting,
    mentoring, coaching, public speaking, written communication, broad personal
    network, broad foundation from product eng to infrastructure eng. Find
    opportunities in current role to practice these
* Three rules for speaking to the media
  * Answer the question you want to be asked. Don't accept question's implicit
    frame; (re-)frame it yourself. See book _Don't Think of An Elephant_ by
    Goerge Lakoff
  * Stay positive. Find positive framing and stick to it
  * Speak in threes. Find three concise points, make them your refrain, refer
    back to them repeatedly

#### Chapter 4 - Approaches
* "consistency is a precondition of fairness"
* rather than write policies, recommends writing norms, "which provide
  nonbinding recommendations...[that] don't require escalations to address
  ambiguities or edge cases"
* "Folks who communicate a "no" effectively are not the firmest speakers, nor do
  they make frequent use of the word itself. They are able to convincingly
  explain their team's constraints and articulate why the proposed path is either
  unattainable or undesirable"
* Most frequent topics for disagreement:
  * *velocity* - why is this taking so long?
    * response: provide compelling explanation of how team finishes work
    * partial work has no value, and the team's defining constraints are often in
      the finishing stages
    * one solution is to build kanban board to display constraints (need not
      maintain)
    * this allows to focus on core constraint
    * then need to describe what's preventing you from solving for it
  * *prioritization* - why can't you work on this, more important project?
    * document all incoming asks (roadmap, migrations, complaints, surprise
      opportunities), develop guiding principles for how work is selected
    * need to accept that plans will change, and have clear point in time when
      that's on the table (e.g. sprint planning meeting, quarterly okr review)
* "with the right people, any process works, and with the wrong people, no
  process works"
* in midsize, rapidly growing company, parts are growing quickly, with emphasis
  on execution, other parts largely stabilized, with ideas becoming more valued
  currency. Metaphor: growth plates (middle part of bone doesn't grow, plate
  does)
  * small startup or at growth plate of any company, dealing with new problems
    * not necessarily novel, but problems company has never prioritized long
      enough to get usable solution out the door
    * [dmr] this is SQ now. APIs generally and OP JS in particular
    * execution is focus. surplus of fairly obvious ideas, but constrained
      bandwidth for evaluating them
    * adding more ideas is counter-productive
    * hard to consistently do the basics well, b/c won't have enough time to do
      them well. have to get comfortable doing as well as time constraints
      allow, sometimes that will lead to being mediocre at things you're passionate
      about
  * outside growth plates, working on problems with known solutions
    * slow-growth environments used to be high-growth environments, "which means
      they were once run by sonmeone who was a sufficiently effective executor
      to evolve them into slow-growth"
    * can do basics as manager very well (build relationships, gel team, work w/
      them on career development)
* pursue scope, not growing headcount. take responsibility for success of
  increasingly important and complex facets of the organization and company. Lot
  less competition for hard work than headcount
* project-managing an initiative working w/ 50 EMs is far better learning
  opportunity than managing an org of 50, and builds same skills

#### Chapter 5 - Culture
* most effective way to provide opportunity (to those in org) is through
  structured application of good process; as lightweight as possible, rigorous
  enough to consistently work
* "The more fully you embrace optimizing for your collective peers, the closer
  your priorities will mirror your manager's"
* hiring manager-of-managers
  * *Partnership* have they been effective partners to their peers, and to the
    team that they've managed?
  * *Execution* can they support the team in operational excellence?
  * *Vision* Can they present a compelling, energizing vision of the future
    state of their team and scope?
  * *Strategy* Can they identify the necessary steps to transform the present
    into their vision?
  * *Spoken and written communication* Can they convey complicated topics in
    both written and verbal communication? Can they do all this while being
    engaging and tuning the level of detail to their audience?
  * *Stakeholder management* Can they make others, especially executives, feel
    heard? Can they make these stakeholders feel confident that they'll address
    any concerns?

#### Chapter 6 - Careers
* build map of past year. write down each transition (meaningful change in how
  you work, e.g. manager changed, team's mission redefined, major reorg). What
  skills did you rely on to navigate the transition? What skills did the
  transition give you an opportunity to develop?
* interview suggestion: do prepared presentation instead of impromptu. [dmr]
  it's your choice how prepared you want to be. Can prepare even w/o knowing
  topic
* career ladders
  * rule of thumb: any ladder w/ more than 10 individuals should be fully
    fleshed out, smaller functions can survive w/ something rough
  * open invitation to folks in role to improve their ladder
  * establish template for shared themes across every ladder

#### Chapter 7 Appendix
* Measuring effective ~sprint~ process
  * team knows what they should work on
  * team knows why work is valuable
  * team can determine if work is complete
  * team knows how to figure out what to do next
  * stakeholders can learn what team is working on
  * stakeholders can learn what team plans to work on next
  * stakeholders know how to influence team's plans

* Books found useful (dmr: skipping ones I've read or don't plan to)
  * _Thinking in Systems: A Primer_, by Donella H. Meadows
  * _Don't Think of an Elephant! Know Your Values and Frame the Debate_, by George Lakoff
  * _Slack: Getting Past Burnout, Busywork, and the Myth of Total Efficiency_, by Tom DeMarco
  * _The Mythical Mon-Month_, by Frederick Brooks
  * _Good Strategy / Bad Strategy: The Difference and Why it Matters_, by Richard Rumelt
  * _The Three Signs of a Miserable Job_, by Patrick Lencioni
  * _Finite and Infinite Games_, by James P. Carse
  * _INSPIRED: How to Create Tech Products Customers Love_, by Marty Cagan
  * _Fierce Conversations: Achieving Sucess at Work and in Life, One Conversation at a Time_, by Susan Scott
  * _Becoming a Technical Leader: An Organic Problem-Sovling Approach_, by Gerald M. Weinberg
  * _The Leadership Pipeline: How to Build the Leadership Powered Company_, by Ram Charan, Steve Drotter, and Jim Noel
  * _The Secrets of Consulting: A Guide to Giving and Getting Advice Successfully_, by Gerald M. Weinberg
  * _Death by Meeting_, by Patrick Lencioni
  * _The Advantage: Why Organizational Health Trumps Everything Else in Business_, by Patrick Lencioni
  * _Rise: 3 Practical Steps for Advancing Your Career, Standing Out as a Leader, and Liking Your Life_, by Patty Azzarello

* Papers found useful
  * "Dynamo: Amazon's Highly Available Key-Value Store"
  * "Hints for Computer System Design"
  * "Big Ball of Mud"
  * "The Google File System"
  * "On Designing and Deploying Internet-Scale Services"
  * "CAP Twelve Years Later: How the 'Rules' Have Changed"
  * "Harvest, Yield, and Scalable Tolerant Systems"
  * "MapReduce: Simplified Data Processing on Large Clusters"
  * "Dapper, a Large-Scale Distriburted Systems Tracing Infrastructure"
  * "Kafka: a Distributed Messaging System for Log Processing"
  * "Wormhold: Reliable Pub-Sub to Support Geo-Replicated Internet Services"
  * "Borg, Omega, Kubernetes"
  * "Large-Scale Cluster Management at Google with Borg"
  * "Omega: Flexible, Scalable Schedulers for Large Compute Clusters"
  * "Mesos: A Platform for Fine-Grained Resource Sharing in the Data Center"
  * "Design Patterns for Container-Based Distributed Systems"
  * "Raft: In Search of an Understandable Consensus Algorithm"
  * "Paxos Made Simple"
  * "SWIM: Scalable Weakly-Consistent Infection-Style Process Group Membership
    Protocol"
  * "The Byzantine Generals Problem"
  * "Out of the Tar Pit"
  * "The Chubby Lock Service for Loosely-Coupled Distributed Systems"
  * "Bigtable: A Distributed Storage System for Structured Data"
  * "Spanner: Google's Globally-Distributed Database"
  * "Security Keys: Practical Cryptopgraphic Second Factor for the Modern Web"
  * "BeyondCorp: Design to Deployment at Google"
  * "Availability in Globally Distributed Storage Systems"
  * "Still All on One Server: Perforce at Scale"
  * "Large-Scale Automated Refactoring Using ClangMR"
  * "Source Code Rejuvanation is not Refactoring"
  * "Searching for Build Debt: Experiences Managing Technical Debt at Google"
  * "No Silver Bullet - Essence and Accident in Software Engineering"
  * "The UNIX Time-Sharing System"
