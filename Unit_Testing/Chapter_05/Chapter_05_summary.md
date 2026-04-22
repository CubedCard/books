# Chapter 5 - Mocks and test fragility

## Key Ideas
- Two types of test doubles
    - Mocks (outgoing interactions)
    - Stubs (incoming interactions)
- CQS (clean architecture) helps
    - All commands are mocks and queries are stubs
    - Commands should not return anything (void), but do something
    - Queries should not do anything, but return something
- Encapsulation is very important
- Mocks are not needed that much as people think

## Core Message
> Do not mock everything.
