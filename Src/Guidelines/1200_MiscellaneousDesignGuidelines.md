<!--
NOTE: Requires Markdown Extra. See http://michelf.ca/projects/php-markdown/extra/
 --> 

#4. Miscellaneous Design Guidelines

### <a name="ft1200"></a> Throw exceptions rather than returning some kind of status value (FT1200) ![](images/2.png)

A code base that uses return values to report success or failure tends to have nested if-statements sprinkled all over the code. Quite often, a caller forgets to check the return value anyway. Structured exception handling has been introduced to allow you to throw exceptions and catch or replace them at a higher layer. In most systems it is quite common to throw exceptions whenever an unexpected situation occurs.

**Note:** This does not apply when designing API calls where status values should be used.

### <a name="ft1202"></a> Provide a rich and meaningful exception message text (FT1202) ![](images/2.png)

If an exception is to be returned to the user, the message should explain the cause of the exception, and clearly describe what needs to be done to avoid the exception.

### <a name="ft1205"></a> Throw the most specific exception that is appropriate (FT1205) ![](images/3.png)

For example, if a method receives a `null` argument, it should throw `ArgumentNullException` instead of its base type `ArgumentException`.

### <a name="ft1210"></a> Don't swallow errors by catching generic exceptions  (FT1210) ![](images/1.png)

Avoid swallowing errors by catching non-specific exceptions, such as `Exception`, `SystemException`, and so on, in application code. Only top-level code, such as a last-chance exception handler, should catch a non-specific exception for logging purposes and a graceful shutdown of the application.

### <a name="ft1215"></a> Properly handle exceptions in asynchronous code (FT1215) ![](images/2.png)
When throwing or handling exceptions in code that uses `async`/`await` or a `Task` remember the following two rules:

- Exceptions that occur within an `async`/`await` block and inside a `Task`'s action are propagated to the awaiter.
- Exceptions that occur in the code preceding the asynchronous block are propagated to the caller.

### <a name="ft1220"></a> Always check an event handler delegate for `null` (FT1220) ![](images/1.png)

An event that has no subscribers is `null`, so before invoking, always make sure that the delegate list represented by the event variable is not `null`. Furthermore, to prevent conflicting changes from concurrent threads, use a temporary variable to prevent concurrent changes to the delegate.

	event EventHandler Notify;
	
	void RaiseNotifyEvent(NotifyEventArgs args)  
	{
		EventHandler handlers = Notify;  
		if (handlers != null)  
		{  
		    handlers(this, args); 
		
		}
	}

**Tip:** You can prevent the delegate list from being empty altogether. Simply assign an empty delegate like this:

	event EventHandler Notify = delegate {};

### <a name="ft1225"></a> Use a protected virtual method to raise each event (FT1225) ![](images/2.png)
Complying with this guideline allows derived classes to handle a base class event by overriding the protected method. The name of the protected virtual method should be the same as the event name prefixed with `On`. For example, the protected virtual method for an event named `TimeChanged` is named `OnTimeChanged`.

**Note:** Derived classes that override the protected virtual method are not required to call the base class implementation. The base class must continue to work correctly even if its implementation is not called.

### <a name="ft1230"></a> Consider providing property-changed events (FT1230) ![](images/3.png)
Consider providing events that are raised when certain properties are changed. Such an event should be named `PropertyChanged`, where `Property` should be replaced with the name of the property with which this event is associated

**Note:** If your class has many properties that require corresponding events, consider implementing the `INotifyPropertyChanged` interface instead. It is often used in the [Presentation Model](http://martinfowler.com/eaaDev/PresentationModel.html) and [Model-View-ViewModel](http://msdn.microsoft.com/en-us/magazine/dd419663.aspx) patterns.

### <a name="ft1235"></a> Don't pass `null` as the `sender` argument when raising an event  (FT1235) ![](images/1.png)

Often an event handler is used to handle similar events from multiple senders. The sender argument is then used to get to the source of the event. Always pass a reference to the source (typically `this`) when raising the event. Furthermore don't pass `null` as the event data parameter when raising an event. If there is no event data, pass `EventArgs.Empty` instead of `null`.

**Exception:** On static events, the sender argument should be `null`.

### <a name="ft1240"></a> Use generic constraints if applicable (FT1240) ![](images/2.png)
Instead of casting to and from the object type in generic types or methods, use `where` constraints or the `as` operator to specify the exact characteristics of the generic parameter. For example:

	class SomeClass  
	{}
	
	// Don't  
	class MyClass  
	{
		void SomeMethod(T t)  
		{  
			object temp = t;  
			SomeClass obj = (SomeClass) temp;  
		}  
	}
	
	// Do  
	class MyClass where T : SomeClass  
	{
		void SomeMethod(T t)  
		{  
			SomeClass obj = t;  
		}  
	}

### <a name="ft1250"></a> Consider evaluating the result of a LINQ expression before returning it  (FT1250) ![](images/1.png)

Consider the following code snippet
	
	public IEnumerable GetGoldMemberCustomers()
	{
		const decimal GoldMemberThresholdInEuro = 1000000;
		
		var query = 
			from customer in db.Customers
			where customer.Balance > GoldMemberThresholdInEuro
			select new GoldMember(customer.Name, customer.Balance);
		
		return query;  
	}

Since LINQ queries use deferred execution, returning `query` will actually return the expression tree representing the above query. Each time the caller evaluates this result using a `foreach` cycle or similar, the entire query is re-executed resulting in new instances of `GoldMember` every time. Consequently, you cannot use the `==` operator to compare multiple `GoldMember` instances. Instead, consider explicitly evaluating the result of a LINQ query using `ToList()`, `ToArray()` or similar methods.

### <a name="ft1260"></a> Write Code Once (FT1260) ![](images/1.png)

Coding is about finding generic solutions for specific problems. As such in chapter 3 of their book on Refactoring Kent Beck and Martin Fowler describe duplicated code as the most important code smell.

Copying existing code looks like a quick win — why write something anew when it already exists? The point is: copied code leads to duplicates, and duplicates are a problem.

Either reuse (by calling) an existing, generic method in your codebase, or make an existing method more generic.

- **Do not copy code.**
- Do this by **writing reusable, generic code and/or calling existing methods instead.**
- This improved maintainability because **when code is copied, bugs need to be fixed at multiple places**, which is inefficient and error-prone.

