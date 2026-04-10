# Chapter 03 - The Anatomy of a unit test

## Key Ideas

- All tests should follow the AAA pattern
- Multiple AAA patterns should not be allowed in a unit test (integration is
  fine)
- More than one line in the act-section is a red flag -> this reminded me of
  the save changes after update or create
- The AAA comments are only needed if a test has a very big arrange-section,
  since then empty lines as separators would not work
- Distinguish the SUT by naming it SUT (System Under Test)
- Constructors can help, but usually you want a private helper method to help
  you with your setup phase
- Name tests so they are readable in plain English
- Parameterized tests help with reducing the amount of test. Think about
  `InlineData` and `Theory`
- `Fact` is used as a name instead of `Test` for a reason. You are telling what
  it is, not what it should be
- `Theory` is a collection of facts
- Assertion libraries, such as fluent assertions, help with making the
  assertions more readable (closer to English)

## Core Message
> English motherfucker, do you speak it?
