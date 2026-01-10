# Chapter 5 — Decoupling (Part 1)

## Core Idea
Decoupling is about reducing hidden dependencies between parts of a system so changes stay local and predictable. The less one component knows about another’s internals, the more flexible and maintainable the system becomes.

## Domain-Centered Design
- Domain logic should live in one central place.
- This mirrors DDD: keep business rules in the domain, not scattered across UI, services, or infrastructure.
- Centralizing logic reduces duplication and prevents behavior from diverging across the codebase.

## Global State = Hidden Coupling
- Global variables are effectively **implicit parameters** to every function that can access them.
- This makes code harder to reason about, test, and reuse.
- Global config files are slightly better, but still introduce shared, ambient state that couples unrelated parts of the system.

## The “Dots” Smell
- Excessive chaining like `a.b.c.d.e` is a warning sign.
- Each dot represents knowledge about another object’s internal structure.
- Long dot chains increase coupling and fragility — small changes ripple outward.
- The more dots you need, the more likely responsibilities are misplaced.

## Mental Model
- Dependencies should be **explicit**, not hidden.
- Data and behavior should travel together.
- If many things must change together, they probably belong together.

## Key Takeaway
> Coupling hides complexity; decoupling makes it visible and manageable.
