# Different Bugs, Different Implementations

For both differences that are mentioned in the report, the `diff` command was used to find the differences
in outputs between the provided implementation and my implementation (left and right respectively).

![Diff Command](/diff_bug_diff_implement_lab_report_resources/diff_cmd.png)

### Difference One

![Difference One](/diff_bug_diff_implement_lab_report_resources/diff_one.png)

For this first difference, the provided implementation returned an empty ArrayList which should
not have been returned as there was no empty link. My implementation returned nothing as to be expected
as this test file `139.md` only has `aaa` enclosed in a code block.

![139.md View](/diff_bug_diff_implement_lab_report_resources/139md_view.png)

![139.md Raw](/diff_bug_diff_implement_lab_report_resources/139md_raw.png)

The problem in the provided implementation is that its checking for links encased within code blocks, but
failing to stop producing and returning an empty ArrayList when a link is not found and is instead thinking
that a potential link exists inside. The lines highlighted below is where the fix needs to be implemented:

![Code Fix For 139](/diff_bug_diff_implement_lab_report_resources/139md_code_fix_lines.png)

### Difference Two

For this second difference, the provided implementation printed out the text as a link whereas my implementation
did not.

![Difference Two](/diff_bug_diff_implement_lab_report_resources/diff_two.png)

Based on the markdown file, nothing should have been returned (the provided implementation is wrong) as it did not contain any valid links as seen below:

![341.md Raw](/diff_bug_diff_implement_lab_report_resources/341md_raw.png)

The problem in the provided implementation is that it fails to take into account other characters
as in this case the asterisk `*` and in its search for code blocks it takes the text as a link and formats
that accordingly.

![341.md Code Fix](/diff_bug_diff_implement_lab_report_resources/341md_code_fix_lines.png)

The program needs to again take into account as with the first difference code blocks not containing
links and also needs to check for other characters overlapping code block sequences or link and title sequences.