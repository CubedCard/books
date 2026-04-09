# Chapter 2 - What is a unit test?

In 2.1 and 2.2, the author discusses the differences between the Classical and
London style of unit testing.

## Classical

This is the way of testing that most developers are used to. You call a method
of a class. That method might require a different class to be initialised. So
you initialise it using dummy data. The method is called and then the result is
asserted (AAA: Arrange, Act, and Assert).

However, when this test failed, it is not directly clear what caused this
failure. It could be the method that was tested, or the other class that was
needed.

## London

That brings us to the London style of testing. Here a unit is a class. So only
one class should be tested in a test. This makes the setup of test files pretty
easy. If you introduce a new class, you need to introduce a new test file too.

The testing is achieved using mocking. The other class that was needed for the
classic test is mocked. In this mocking it is set what the other class' methods
will return and then asserted how many times the resulting methods were called.

The difference between these two comes from the definition of what a unit is.
Is a unit a class? This is something to think about and define for yourself and
your projects.

## Three rules 

There are three rules that make a test a unit test.

They are the following:
1. A unit test verifies a single unit of behaviour .
2. Does it quickly.
3. And does it in isolation from other tests.

## Types

When a test violates at least one of these, it is an integration test.

End-to-end tests are tests that test end to end. So from system to user. An
example might be an UI-test. These require a lot of dependencies.

## Why classical might be better

The London way sounds appealing when you see that it shows the exact test that
fails, while the classical style might show multiple tests that fail after one
breaking change. This is not a bad thing though. Because multiple tests failed,
it shows that it was an important part of the code. The London style also
defines a unit as a class, while a unit should (according to the author) be a
unit of behaviour. 

## Core Message
> Use classical.
