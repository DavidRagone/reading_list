[The talk](https://www.youtube.com/watch?v=V4fnzHxHXMI)

My notes/reflections:


```
What programs are; their structure & behavior <--|
                                                 |
                                                Workflow
                                                      |
                                                      |--> How we program; our thoughts & activities
```                                                   
Explain the thinking of how to program. No one can explain how we program. We have no idea how software works. All the time has been spent on understanding the "work", not on the "flow".

Ask "how" questions. What actions/thoughts led you to write a good program? Can you exlain your thinking?

Proramming is frightening, in taht no one can explain how they're thinking and writing code. Everyone is either making stuff up as they go or pretending they understand it. Who succeeds in that environment? Either genuinely brilliant people, or people with the overconfidence of having been told they're brilliant their whole lives. That doesn't lead to a diverse or inclusive environment.

```
                        What you do
Feedback. Think about < How you feel >. Reflect. Improve
                        How you think
```                     
Realized overwhelmed by large set of features, so would try to write one little thing, bottom-up. But then the interface for that thing would be wrong. So reflected. Now think & test topdown / outside-in / caller-down. What is the code I wish I had, that I could defer and hand this work out to?

"Taste" is what helps us constrain the choices of how to solve a problem from infinite to finite.

Programs are like directed graphs. Units are nodes. Edges are function calls. We try to write acyclic digraphs. 

Express features as trees. Tree is special subtype of graph. Re-organize, with value object on left, and function and feature behavior on right. Easier to search tree.

Essential complexity: what software is supposed to be doing.
Incidental complexity: everything it actually does. (deploy tooling, app config, depdendencies, framework stuff, etc, style rules, build systems, etc)
As minimalize, want to maximize essential complexity.

Spent more time being productive, in part by avoiding (changing/re-making) arbitrary decisions that don't matter. Just follow the patterns that are there. Lock down arbitrary decisions up front, be more productive

We incur a paging cost and create blind spots by allowing units to grow in size and complexity

Complexity management problems can look/feel like testing problems. Bugs creep in b/c of bad complexity mgmgt

We struggle to predict complexity and how things might change. So instead, we should prepare for how complexity increases over time.

"Searls' Wager":

| | Brain Units | Small Units |
|--|-----------|---------------|
| Constant Complexity | :-\| | :-\| |
| Increasing Complexity | :( | :) |

If complexity goes up, we know that larger units cause problems, whereas smaller ones can accommodate additional complexity without pain.

So on day 1 of every feature, break things up into itty-bitty tiny units. To point where people may criticize. But don't worry, trust that others will go and make them bigger later.

This is a great way to follow single responsibility.


One of three rules for tree of objects:
* Parent nodes: Delegator objects. Don't have logic or branching (maybe one if condition). Mostly just break up work, hand it off to other things. 
* Leaf nodes: core logic of application. Takes inputs, transforms to outputs. Can be written as pure functions, so don't need test doubles, just actually testing real logic. 
* Left nodes: Value objects. Elucidate data, answer questions about data. Don't do feature work here. They're the sludge flowing through pipes of leaf nodes

Worst case, if complexity doesn't increase, is better names and small objects.

Disposable architecture: Realized that future self would always get annoyed by things that present self left to try to help, e.g. tests, commit messages, documentation. Future self always wanted to throw out code and start fresh. So realized, can actually just throw out small objects and re-write them. Don't need to carefully read existing code, add/remove tests, change the code, and try to make as small a mess as possible. So find smallest subtree that encapsulates the change, blow it up, and write to the contract w/ new solution. This does mean that code re-use is a problem, b/c, e.g., a method called in 9 places is really hard to change b/c need to consider 9 different callers.

When hear "you have too many abstractions / too many objects", it's not that you have too many, it's that you're mixing the levels of abstraction on your system. May look like needless abstraction on day one, but on day two, it's easier to change. There's a place for complexity to go. 

Aggressively pull forward disagreements within team forward. Lock in decision, then can be more productive.
