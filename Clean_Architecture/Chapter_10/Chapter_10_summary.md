# Chapter 10 - The Interface Segregation Principle

## Key Ideas
The name itself kind of says it all. If you don't use it, do not depend on it.
This reminds me of a conversation I have had at work. Where a colleague said
that I could go even a step further. I had just implemented an interface for
all my CRUD repositories. The "going further" would have been to separate these
even further. Like the ISP says. If I had repositories that do not need the
delete, why would I give them access to it? This also can cause unnecessary
bugs, dependencies and redeploys / recompilations. 

## Core Message
> Do not depend on what you do not use.
