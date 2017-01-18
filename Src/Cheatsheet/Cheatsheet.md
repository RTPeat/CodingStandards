<!--
NOTE: Requires Markdown Extra. See http://michelf.ca/projects/php-markdown/extra/
 --> 
<link href="style.css" type="text/css" rel="stylesheet"/>

<table width="100%">
<tr>
<td class="title">Coding Guidelines for C# Cheat Sheet</td>
<td rowspan="2" style="text-align:right">![logo](images/FISCAL Logo - No Strapline.jpg)</td>
</tr>
<tr>
<td><div class="subTitle">Design & Maintainability</div> (level 1 and 2 only)</td>
</tr>
</table>

<table width="100%">
<tr>
<td class="column" markdown="1">
<div markdown="1" class="sidebar">
**Basic Principles**

* The Principle of Least Surprise   
* Keep It Simple Stupid   
* You Ain’t Gonna Need It  
* Don’t Repeat Yourself
</div>

**Class Design**

*  A class or interface should have a single purpose (FT1000)
*  An interface should be small and focused (FT1003)  
*  Use an interface to decouple classes from each other (FT1005)  
*  Don’t hide inherited members with the `new` keyword (FT1010)  
*  It should be possible to treat a derived object as if it were a base class object (FT1011)  
*  Don’t refer to derived classes from the base class (FT1013)  
*  Avoid exposing the objects an object depends on (FT1014)  
*  Avoid bidirectional dependencies (FT1020)  
*  Classes should have state and behaviour (FT1025)

<br/>
**Member Design**  

* Allow properties to be set in any order (FT1100)  
* Don’t use mutually exclusive properties (FT1110)  
* A method or property should do only one thing (FT1115)  
* Don’t expose stateful objects through static members (FT1125)   
* Return an `IEnumerable<T>` or `ICollection<T>` instead of a concrete collection class (FT1130)   
* Properties, methods and arguments representing strings or collections should never be `null` (FT1135)  
* Define parameters to be as specific as possible (FT1137)   
</td>
<td class="column">
**Miscellaneous Design**  

* Throw exceptions rather than returning status values (FT1200)  
* Provide a rich and meaningful exception message text (FT1202)  
* Don’t swallow errors by catching generic exceptions  (FT1210)  
* Always check an event handler delegate for `null` (FT1220)  
* Properly handle exceptions in asynchronous code (FT1215)  
* Use a protected virtual method to raise each event (FT1225)  
* Don’t pass `null` as the sender parameter when raising an event (FT1235)  
* Use generic constraints if applicable (FT1240)  
* Evaluate the result of a LINQ expression before returning it (FT1250)  

<br/>
**Maintainability**  

* Methods should not exceed 7 statements (FT1500)  
* Make all members `private` and types `internal` by default (FT1501)  
* Avoid conditions with double negatives (FT1502)  
* Don’t use "magic numbers" (FT1515)  
* Only use `var` when the type is very obvious (FT1520)  
* Declare and initialize variables as late as possible (FT1521)  
* Favour Object and Collection Initializers over separate statements (FT1523)  
* Don’t make explicit comparisons to `true` or `false` (FT1525)  
* Don’t change a loop variable inside a `for` or `foreach` loop (FT1530)  
* Avoid nested loops (FT1532)  
</td>
<td class="column">
* Always add a block after keywords such `if`, `else`, `while`, `for`, `foreach` and `case` (FT1535)  
* Always add a `default` block after the last `case` in a `switch` statement (FT1536)  
* Finish every `if`-`else`-`if `statement with an `else`-part (FT1537)  
* Be reluctant with multiple `return` statements (FT1540)  
* Don’t use `if`-`else` statements instead of a simple (conditional) assignment  (FT1545)  
* Encapsulate complex expressions in a method or property (FT1547)  
* Call the most overloaded method from other overloads (FT1551)  
* Only use optional arguments to replace overloads (FT1553)  
* Avoid using named arguments (FT1555)  
* Don’t allow methods and constructors with more than three parameters (FT1561)  
* Don’t use `ref` or `out` parameters (FT1562)  
* Avoid methods that take a `bool` flag (FT1564)  
* Always check the result of an `as` operation (FT1570)  
* Don’t comment-out code (FT1575)  

<br/>
**Framework Guidelines**  

* Use C# type aliases instead of the types from the `System` namespace (FT2201)  
* Build with the highest warning level (FT2210)  
* Use Lambda expressions instead of delegates (FT2221)  
* Only use the `dynamic` keyword when talking to a dynamic object (FT2230)  
* Favor `async`/`await` over the `Task` (FT2235)  
</td>
<tr>

<table width="100%" class="footer">
<tr>
<td>
  Fiscal Technologies   
  Version %semver% (%commitdate%)  
</td>
<td style="text-align:right">
  [www.csharpcodingguidelines.com](http://www.csharpcodingguidelines.com)  
  [www.continuousimprover.com](www.continuousimprover.com)  
  [www.fiscaltechnologies.com](http://www.fiscaltechnologies.com/)  
</td>
</tr>
</table>

<table width="100%" style="page-break-before: always;">
 <tr>
  <td class="title">Coding Guidelines for C# 3.0, 4.0 and 5.0 Cheat Sheet</td>
  <td markdown="1" rowspan="2" style="text-align:right">![logo](images/FISCAL Logo - No Strapline.jpg)</td>
 </tr>
 <tr>
 <td><div class="subTitle">Naming & Layout</div> (level 1 and 2 only)</td>
 </tr>
</table>

<table width="100%">
<tr>
<td class="column" markdown="1">
<div class="sidebar">

|**Pascal Casing**||
|:-------------------------------|-----------|
|Class, Struct					|`AppDomain`|
|Interface 						|`IBusinessService`|
|Enumeration type 				|`ErrorLevel`
|Enumeratiion values			|`FatalError`
|Event 							|`Click`
|Protected field 				|`MainPanel`
|Const field 					|`MaximumItems`
|Read-only static field&nbsp;&nbsp;			|`RedValue`	
|Method 						|`ToString`
|Namespace 						|`System.Drawing`
|Property 						|`BackColor`
|Type Parameter					|`TEntity`
| |  
|<br/>**Camel Casing**||
|Private field					|`listItem`
|Variable 						|`listOfValues`
|Const variable					|`maximumItems`
|Parameter 						|`typeName`

</div>

<br/>
**Naming**  

* Use US English (FT1701)
* Don’t include numbers in variables, parameters and type members  (FT1704)
* Don’t prefix fields (FT1705)
* Don’t use abbreviations (FT1706)
* Name members, parameters or variables according its meaning and not its type (FT1707)
* Name types using nouns, noun phrases or adjective phrases (FT1708)
* Don’t repeat the name of a class or enumeration in its members (FT1710)
* Avoid short names or names that can be mistaken with other names (FT1712)
* Name methods using verb-object pair (FT1720)
* Name namespaces using names, layers, verbs and features (FT1725)
</td>
<td class="column">

* Use an underscore for irrelevant lambda parameters (FT1739)


**Documentation**  

* Write comments and documentation in US English (FT2301)
* Document all public, protected and internal types and members (FT2305)
* Avoid inline comments (FT2310)
* Only write comments to explain complex algorithms or decisions (FT2316)
* Don’t use comments for tracking work to be done later (FT2318)
<br/>

**Layout**

* Maximum line length is 130 characters.
* Indent 4 spaces, don’t use Tabs
* Keep one white-space between keywords like `if` and the expression, but don’t add white-spaces after `(` and before `)`.
* Add a white-space around operators, like `+`, `-`, `==`, etc.
* Always add parentheses after keywords `if`, `else`, `do`, `while`, `for` and `foreach`
* Always put opening and closing parentheses on a new line.
* Don’t indent object initializers and initialize each property on a new line.
* Don’t indent lambda statements
* Put the entire LINQ statement on one line, or start each keyword at the same indentation.
* Add braces around comparison conditions, but don’t add braces around a singular condition. 
</td>
<td class="column">

<div markdown="1" class="sidebar">
**Empty lines**

* Between members
* After the closing parentheses
* Between multi-line statements
* Between unrelated code blocks 
* Around the `#region` keyword
* Between the `using` statements of different root namespaces.
</div>

<div class="sidebar">
**Member order**

1.	Private fields and constants
1.	Public constants
1.	Public read-only static fields
1.	Factory Methods
1.	Constructors and the Finalizer
1.	Events 
1.	Public Properties
1.	Other methods and private properties in calling order
</div>

<div markdown="1" class="sidebar">
**Important Note**

These coding guidelines are an extension to Visual Studio's Code Analysis functionalty, so make sure you enable that for all your projects. Check the full document for more details.
</div>

<td/>
<tr>

<table width="100%" class="footer">
<tr>
 <td>
   Fiscal Technologies    
   Version %semver% (%commitdate%)   
 </td>
 <td style="text-align:right">
  [www.csharpcodingguidelines.com](http://www.csharpcodingguidelines.com)  
  [www.continuousimprover.com](www.continuousimprover.com)  
  [www.fiscaltechnologies.com](http://www.fiscaltechnologies.com/)  
  </td>
</tr>
</table>
