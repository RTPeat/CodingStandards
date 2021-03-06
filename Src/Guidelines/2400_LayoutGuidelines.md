<!--
NOTE: Requires Markdown Extra. See http://michelf.ca/projects/php-markdown/extra/
 --> 

#10. Layout Guidelines

### <a name="ft2400"></a> Use a common layout  (FT2400) ![](images/1.png)

- Try to keep the length of each line under 130 characters.

- Use an indentation of 4 spaces, and don't use tabs

- Keep one space between keywords like `if` and the expression, but don't add spaces after `(` and before `)` such as: `if (condition == null)`.

- Add a space around operators like `+`, `-`, `==`, etc.

- Always follow the keywords `if`, `else`, `do`, `while`, `for` and `foreach` with opening and closing braces, even though the language does not require it. 

- Always put opening and closing braces on a new line.
- Don't indent object Initialisers and initialise each property on a new line, so use a format like this: 
	
		var dto = new ConsumerDto()
		{  
			Id = 123,  
			Name = "Microsoft",  
			PartnerShip = PartnerShip.Gold
		}

- Don't indent lambda statements and use a format like this:

		methodThatTakesAnAction.Do(x =>
		{ 
			// do something like this 
		}

- Put the entire LINQ statement on one line, or start each keyword at the same indentation, like this:
		
		var query = from product in products where product.Price > 10 select product;

  	or
	
		var query =  
		    from product in products  
		    where product.Price > 10  
		    select product;

- Start the LINQ statement with all the `from` expressions and don't interweave them with restrictions.
- Add parentheses around every comparison condition, but don't add parentheses around a singular condition. For example `if (!string.IsNullOrEmpty(str) && (str != "new"))`

- Add an empty line between multi-line statements, between members, after the closing parentheses, between unrelated code blocks, around the `#region` keyword, and between the `using` statements of different root namespaces.


### <a name="ft2402"></a> Order and group namespaces according to the company  (FT2402) ![](images/3.png)

	// Microsoft namespaces are first
	using System;
	using System.Collections;
	using System.XML;
	
	// Then any other namespaces in alphabetic order
	using Fiscal.Business;
	using Fiscal.Standard;
	using Telerik.WebControls;
	using Telerik.Ajax;

### <a name="ft2406"></a> Place members in a well-defined order  (FT2406) ![](images/1.png)
Maintaining a common order allows other team members to find their way in your code more easily. In general, a source file should be readable from top to bottom, as if reading a book, to prevent readers from having to browse up and down through the code file.

1. Private fields and constants (in a region)
2. Public constants
3. Public read-only static fields
4. Factory Methods
5. Constructors and the Finaliser
6. Events 
7. Public Properties
8. Other methods and private properties in calling order

### <a name="ft2407"></a> Be reluctant with `#regions` (FT2407) ![](images/1.png)
Regions can be helpful, but can also hide the main purpose of a class. Therefore, use `#regions` only for:

- Private fields and constants (preferably in a `Private Definitions` region).
- Nested classes
- Interface implementations (only if the interface is not the main purpose of that class)
