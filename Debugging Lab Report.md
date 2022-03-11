# Expected Outcomes and Debugging

[**My Implementation**](https://github.com/ThestralMoon/markdown-parse)

[**Reviewed Implementation**](https://github.com/ucsd-cse15l-w22/markdown-parse)

## Snippet One

### My Program

For my implementation of MarkdownParse, getLinks() should return the list
of links in the documents, but the test fails as the fourth link is not returned.

![Test Fail](/snippet_debugging_lab_report_resources/snippet_one_test_fail.png)

### Reviewed Implementation

![Test Pass](/snippet_debugging_lab_report_resources/rw_snippet_one_test_pass.png)
*As it can be seen above, the test case passed and thus was not shown. Only test fails are shown by JUnit*

For the implementation that was reviewed during the lab session, the program ran
as expected with the test passing and returning all the valid links in the file, but
does share the expected output for the second link with my implementation as the second link
contains a backtick at the start of it which can be just cleared by using
String.contains() and String.replace() to check if the links are in correct format.

### Program Fix

For this error in particular, it would take a small code change as to simply check
if there is a backtick present that is blocking the link ahead from being read using an if statement
and checking the index of the tick and the next open parenthesis (within range).

## Snippet Two

### My Program

For this snippet in particular, my program as I am expecting should be throwing a 
StringIndexOutOfBoundsException due to double closed brackets. The test passed in the sense that 
it caught the exception, but it failed as it threw the error.

![Test Fail](/snippet_debugging_lab_report_resources/snippet_two_test_fail.png)

### Reviewed Implementation

![Test Fail](/snippet_debugging_lab_report_resources/rw_snippet_two_test_fail.png)

The test failed as I was expecting the implementation to be able to parse through the nested
link as well, but it did not and as a result the test failed although all other links were
returned as expected with the third link having a format issue adding parenthesis at the end of it.

### Program Fix

For this error I don't think it would take a small code change to make the test pass and produce
the expected link outputs as one part would require checking for nested links potentially using a loop to index through,
and the next part would require checking for nested brackets inside the hyperlink format.

### Snippet Three

For this last snippet, I was expecting another StringIndexOutOfBoundsException due to the second link having
text between it and it's closing parenthesis. The test passed as the method
did throw the exception, but at the same time failed due to it not returning the expected
links present in the file.

![Test Fail](/snippet_debugging_lab_report_resources/snippet_three_test_fail.png)

### Reviewed Implementation

I was expecting the same outcome with the reviewed implementation and the test failing as a result.

![Test Fail](/snippet_debugging_lab_report_resources/rw_snippet_three_test_fail.png)

### Program Fix

For this error I do not think it would a small code change to make the test pass and produce
the expected link outputs due to the more complex nature of the snippet in question created by:
missing closing parenthesis, plain text and whitespace after links, and line breaks. The fix in question
would have to include multiple additions as to check if the indices of the starting and ending parenthesis
are in range of the last link string, taking the link strings and then reformatting them by clearing up
unwanted whitespace and then returning them as the links found, and also checking for whitespace and line
breaks for the titles as to avoid IndexOutOfBounds exceptions thrown for the brackets not being found.