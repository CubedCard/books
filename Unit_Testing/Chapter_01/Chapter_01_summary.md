# Chapter 1 - The Bigger Picture
The first part mostly talks about what to expect of this book. It also discusses what usually goes wrong in the unit testing scene. When comparing the trajectory of projects without tests, with good tests, and with bad tests, they noticed some interesting things. 

Firstly, when no tests were written at all, the amount of effort needed for progress would initially be very low and then exponentially grow. This would result in many bugs and low maintainability. 

The second project initially required more effort to take off. Once there, it was a very consistent (almost linear) when comparing progress to effort.

Lastly, the project with tests, but not good ones. This project, interestingly enough, started off quite similar to the second one, but then quickly started going into the same direction as the first project. 

## Indications
Later, the author talks more about how to indicate if a project has good or bad testing. Stuff like test and branch coverage are discussed. Both are good indications if you have bad or too little tests. However, the opposite is not true. For example, a project with a test coverage below 60% probably needs some extra testing. On the other side, a project with 90 or even 100% test coverage does not necessarally indicate that the project contains good tests. 

Furthermore, the author describes a situation where the developers of a company were forced to uphold a certain coverage standard. This eventually resulted in the worst test you could imagine. Some of the tests would be wrapped in a try-catch and not even assert anything. This made the company lower the coverage, until there was no requirement anymore. 

## Key Takeaway
> More code, more problems.