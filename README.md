# Power-JQL
https://marketplace.atlassian.com/plugins/proficient.developer.plugins.jira.power-jql/server/overview

## powerIssue
> powerIssue([JQL subquery, optional], "field names", "regex expression")

Flexible and powerful function to use Regex expressions for search in issue fields.
Can be used with 2 or 3 arguments.

#### about regex
A simple example for a regular expression is a (literal) string. For example, the "Hello World" regex matches the "Hello World" string.
. (dot) is another example for a regular expression. A dot matches any single character; it would match, for example, "a" or "1".
The following tables lists several regular expressions and describes which pattern they would match.

| Regex | Matches |
| ------------- | ------------- |
| this is text  | Matches exactly "this is text"  |
| this\s+is\s+text | Matches the word "this" followed by one or more whitespace characters followed by the word "is" followed by one or more whitespace characters followed by the word "text". |
| ^\d+(\.\d+)? | ^ defines that the patter must start at beginning of a new line. \d+ matches one or several digits. The ? makes the statement in brackets optional. \. matches ".", parentheses are used for grouping. Matches for example "5", "1.5" and "2.21". |
Detailed guide: https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html

#### examples
| Task | JQL | Notes |
| ------------- | ------------- | ------------- |
| Simple usage - find any issue with word "amber" in the beginning of the Summary | issue in powerIssue("summary", "(amber).*") | |


Any issue from POWERJQL project, where summary or description contains "text1" or "text2" (case insensitive):
> issue in powerIssue("project=POWERJQL", "summary, description", "(?i).*(text1|text2).*")


Any issue where assignee name contains "John" (case insensitive):
> issue in powerIssue("assignee", "(?i).*(John).*")


## powerComponent
> powerComponent([JQL subquery, optional], "regex expression")
Can be used with 1 or 2 arguments.

#### examples
Any not resolved issue where component contains words "mobile" or "dev" in any part of component name (case sensitive):
> component in powerComponent("resolution=EMPTY", ".*(mobile|dev).*")

## powerAttachment
> powerAttachment([JQL subquery, optional], regex expression)

#### examples
> issue in powerAttachment(".*(?=android).*(?=pdf).*")

## powerProject
> powerProject(regex expression)

#### examples
> project in powerProject(".*(Customer).*")
