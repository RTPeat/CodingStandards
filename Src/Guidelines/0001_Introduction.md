<!--
NOTE: Requires Markdown Extra. See http://michelf.ca/projects/php-markdown/extra/
 --> 

#1. Introduction#
##1.1. What is this?##

This document attempts to provide guidelines (or coding standards if you like) for coding in C# that are both useful and pragmatic. These guidelines are representative to what we at [Fiscal Technologies](http://www.fiscaltechnologies.com/) do in our day-to-day work. Notice that not all guidelines have a clear rationale. Some of them are simply choices we made at Fiscal Technologies.

Visual Studio's [Static Code Analysis](http://msdn.microsoft.com/en-us/library/dd264939.aspx) (which is also known as FxCop) and [StyleCop](http://stylecop.codeplex.com/) can already automatically enforce a lot of coding and design rules by analysing the compiled assemblies. You can configure it to do that at compile time or as part of a continuous or daily build. This document just provides an additional set of rules and recommendations that should help us achieve a more maintainable code base.

##1.2. Why would you use this document?##

Although some might see coding guidelines as undesired overhead or something that limits creativity, this approach has already proven its value for many years. This is because not every developer:

- is aware that code is generally read 10 times more than it is changed;
- is aware of the potential pitfalls of certain constructions in C#;
- is up to speed on certain conventions when using the .NET Framework such as `IDisposable` or the deferred execution nature of LINQ;
- is aware of the impact of using (or neglecting to use) particular solutions on aspects like security, performance, multi-language support, etc;
- realises that not every developer is as capable, skilled or experienced to understand elegant, but potentially very abstract solutions;

##1.3. Basic principles##

There are many unexpected things you may run into during your work, each deserving at least one guideline. Unfortunately, we still need to keep this document within a reasonable size. However, that doesn't mean that something is okay just because it is not mentioned in this document.

In general, if there is a discussion with a colleague about a smell that this document does not cover, you should refer back to a set of basic principles that apply to all situations, regardless of context. These include:

- **The Principle of Least Surprise (or Astonishment)**: you should choose a solution that everyone can understand, and that keeps them on the right track.
- **Keep It Simple Stupid (a.k.a. KISS)**: the simplest solution is more than sufficient.
- **You Ain't Gonna Need It (a.k.a. YAGNI)**: create a solution for the problem at hand, not for the ones you think may happen later on. Can you predict the future?
- **Don't Repeat Yourself (a.k.a. DRY)**: avoid duplication within a component, a source control repository or  a [bounded context](http://martinfowler.com/bliki/BoundedContext.html), without forgetting the [Rule of Three](http://lostechies.com/derickbailey/2012/10/31/abstraction-the-rule-of-three/) heuristic.
- In general, generated code should not need to comply with coding guidelines. However, if it is possible to modify the templates used for generation, try to make them generate code that complies as much as possible.

*Regardless of the elegance of someone's solution, if it is too complex for the ordinary developer to understand, exposes unusual behaviour, or tries to solve many possible future issues, it is very likely the wrong solution and needs redesign. The worst response a developer can give you to these principles is: "But it works?".* 


