# Testing And Debugging

In the past two labs, we took a look at testing a program whose
function was to parse markdown type files and return all elements
present by print line. 


## Infinite Loop Error

One of the first errors that was encountered with a .md file was that
if the file contained any uncommented symbols, the program would enter
an infinite for loop as it did not know how to parse them which would
eventually result in an OutOfMemory Exception, shutting down the
program.

![Infinite Loop Case](/debug_lab_report_resources/infinite_loop_case.png)

![Out Of Memory Error](/debug_lab_report_resources/out_of_memory_error.png)

The fix:

![Infinite Loop Fix](/debug_lab_report_resources/infinite_loop_fix.png)

The fix as seen is the insertion of an if statement that checks if
the next open bracket is at a valid index as a negative index would
result in a invalid continuation. If the index is invalid or "Out of Bounds"
the break line statement would be executed, causing the while loop to break,
preventing an infinite loop from occurring.

## Image Outputted As Link

Another error was that of an image reference being outputted as a link.

![Image Error Case](/debug_lab_report_resources/image_error_case.png)

The fix:

![Image Error Fix](/debug_lab_report_resources/image_error_fix.png)

The fix was to use another if conditional as similar to the previous
error, but to now check for if a reference in a file is an image by searching
for the "!" symbol before an open bracket. If true, the program would continue
while skipping the image and only proceeding to add and print out valid
links as seen as through the second if statement that checks if the boolean
conditional "ifImage" is false.

## Plain Text 