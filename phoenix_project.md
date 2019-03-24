# The Phoenix Project

### A Novel About IT, DevOps, and Helping Your Business Win

### Gene Kim,  Kevin Behr, George Spafford

Sadly I didn't take detailed notes while reading, so what follows is my more
summary thoughts and some notes pulled post-read-through.

The Goodreads reviews are entertainingly all-over-the-place, more than I've
noticed for other books I've read. I found myself torn while reading, as the
characters were caricatures and the author's voice was so plainly obvious it was
constantly breaking the fourth wall. That said, there's legitimate meat to the
ideas, and the parallel to The Goal is worth the effort. 

Because of this, my notes here will treat the book as non-fiction, and focus on
the takeaways worth applying to a software engineering team (by which I mean a
modern-day team that handles its testing, QA, and operations, rather than
expecting others to do those jobs; this may be bias, as these are the only teams
I have known). Thankfully there's a section at the end that summarizes the key
points of the book, so I'm liberally referencing that in the below

#### The Three Ways
The main character's learning of the below formed the basis of the story, and
the guru character brought the main character along as he saw the parallels with
similar approaches in manufacturing. I see many teams that do the first, only
one that did the second, and most that claim to (but usually fail to) do the
last.

* First: left-to-right flow of work from Development to IT Ops to customer
  * AKA, a Kanban board
  * Doesn't really matter what "departments" are involved here; key is
    visualization of flow of work
  * Goal: maximize flow
  * To maximize flow, need:
    * small batch sizes (aka small PRs)
    * small intervals of work
    * never passing defects downstream
    * constantly optimize for global gaols (as opposed to local goals, e.g. fix
      ratios)
  * Need teams to practice:
    * CI/CD
    * environments available on demand
    * limiting work-in-progress
    * building safe systems and orgs that are safe to change
* Second: constant flow of fast feedback from right-to-left at all stages of value
    stream
  * create quality at source; embed or create knowledge where need it
  * Need teams to practice:
    * stopping production line when builds/tests fail in deploy pipeline
    * elevating improvement of daily work over daily work
    * creating fast automated test suites to ensure code always potentially
      deployable
    * shared goals and pain between Development and IT Ops
    * pervasive production telemetry so everyone can see whether code and
      environments are oeprating as designed and customer goals met
* Third: creating culture that fosters continual experimentation and understanding
    repetition and practice is prerequisite to mastery
  * relentlessly improve system of work
  * Need teams to practice:
    * creating culture of innovation and risk taking
    * high trust
    * allocating at least 20% Dev & IT Ops cycles to non-functional requirements
    * constant reinforcement that improvements are encouraged and celebrated

#### The Four Types of Work
In teams I've worked on, the below are all tracked in the same system, though
I've seen teams in my vicinity that don't have the same approach. I don't
understand how a team can understand what is happening within the team and what
is most important without having a visualization of the work in progress and
planned, and hence insist on having all work within whatever tracking system we
use. The author seems to be more used to a world where each of the below is
tracked in separate systems, or in some cases (e.g. apparently all internal IT
projects) not tracked at all.

* Business projects: initiatives that encompass most Development projects
* Internal IT projects: infra or ops needs that business projects create, as
  well as internally generated improvement projects (e.g. automate deployment)
* Changes: Often generated from previous two types of work
* Unplanned/recovery work: Incidents, problems, that come at expense of other
  planned commitments

#### Wait time as a function of hos busy a given resource is

The only graph in the book shows how long work has to wait given how busy the
next resource (ie, work station or person) is. Consider pull request reviews; if
the team is 100% busy with their own work, no one will ever review a PR. If the
team is 1% busy, they will review PRs nearly instantaneously. Assuming you have
more than 1 step required to get code out the door (e.g. maybe you require two
PR approvers, and then someone must approve a roll plan to deploy, and someone
must assist in pre-deploy QA), the busier the team is the longer it takes for
even small changes to make their way to customers. This can have a meaningful
and detrimental impact to the team's productivity. 

There's a few ways to approach this, but one simple one is to do less to do
more. When WIP goes through the system faster because everyone has the time to
do all the things that are rarely tracked in planning software (e.g. code 
review), more ends up actually getting done.


