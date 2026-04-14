# Chapter 4 - The four pillars of a good unit test

## Key Ideas
- Pillars:
    - Protection against regressions
        - Does it catch bugs?
    - Resistance to refactoring
        - Does the test break and give a false positive when refactoring code?
        - Non-negotiable 
    - Fast feedback
        - How quickly does the test execute?
    - Maintainability
        - How hard is it to understand the test?
        - How many out of process dependencies does it have?
- Perfect tests do not exist, there are always trade-offs
- You need at least a little bit of everything, since the score is the multiplication of all of the (x 0 = 0)
- Pyramid of testing shows the common distribution of tests (end-to-end, integration, unit. In ascending order)
- Black-box testing is when you only look at the outcome
- White-box testing is when you test the process
- You should use black-box testing and then analyze your tests with white-box testing
    - Reminds me of using stryker

## Core Message
> Test the outcome and choose your pain wisely. 
