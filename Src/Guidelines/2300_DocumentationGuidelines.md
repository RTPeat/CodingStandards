<!--
NOTE: Requires Markdown Extra. See http://michelf.ca/projects/php-markdown/extra/
 --> 

#9. Documentation Guidelines

### <a name="ft2310"></a> Avoid inline comments  (FT2310) ![](images/2.png)
If you feel the need to explain a block of code using a comment, consider replacing that block with a method with a clear name.

### <a name="ft2316"></a> Only write comments to explain complex algorithms or decisions  (FT2316) ![](images/1.png)
Try to focus comments on the *why* and *what* of a code block and not the *how*. Avoid explaining the statements in words, but instead help the reader understand why you chose a certain solution or algorithm and what you are trying to achieve. If applicable, also mention that you chose an alternative solution because you ran into a problem with the obvious solution.

### <a name="ft2318"></a> Don't use comments for tracking work to be done later  (FT2318) ![](images/3.png)
Annotating a block of code or some work to be done using a *TODO* or similar comment may seem a reasonable way of tracking work-to-be-done. But in reality, nobody really searches for comments like that. Use a work item in Team Foundation Server to keep track of leftovers.
