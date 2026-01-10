# Chapter 4 — Pragmatic Paranoia

## Core Idea
Assume things will go wrong. Design systems that fail **early, loudly, and safely** instead of silently corrupting state. A crash with a clear cause is far better than a system that limps along producing nonsense.

## Design by Contract
- Code should enforce clear expectations about what is valid.
- Preconditions, postconditions, and invariants define what *must* be true.
- When a contract is violated, the program should stop immediately.

## Fail Early (Crash, Don’t Trash)
- Errors should surface as soon as possible.
- Late failures are hard to diagnose; early failures are obvious.
- Throw exceptions and assert assumptions before invalid data spreads.
- “Dead programs tell no lies.”

## Assertions and Assertive Programming
- Assertions document assumptions and catch impossible states.
- Leave assertions **enabled**, even in production.
- Tests can never cover all real-world scenarios; production will always find new edge cases.
- Strong assertions can dramatically increase the value and reliability of a codebase.

## Finish What You Start
- If a function acquires a resource, it should also release it.
- Opening files, locking resources, or allocating memory must be paired with cleanup.
- Exceptions make this especially important.
- Use constructs like `finally`, `defer`, or context managers to guarantee cleanup.

## Act Locally
- Handle errors and responsibilities as close as possible to where they occur.
- Avoid spreading cleanup or recovery logic across distant parts of the system.
- Local reasoning keeps complexity under control.

## Don’t Outrun Your Headlights
- Don’t design for distant or speculative futures.
- Over-engineering locks you into assumptions that may be wrong.
- Build for what you know now, but make replacement easy.
- Refactoring is cheaper than predicting the future.

## Core Message
> Be constructively paranoid: enforce assumptions, fail fast, clean up after yourself, and avoid designing beyond what you can clearly see.
