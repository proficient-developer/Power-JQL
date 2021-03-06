# Power-JQL
https://marketplace.atlassian.com/plugins/proficient.developer.plugins.jira.power-jql/server/overview

## powerIssue
> powerIssue([JQL subquery, optional], "field names", "regex expression")

Flexible and powerful function to use Regex expressions for search in issue fields.
Can be used with 2 or 3 arguments.

#### about regex
A simple example of a regular expression is a (literal) string. For example, the "Hello World" regex matches the "Hello World" string.
. (dot) is another example of a regular expression. A dot matches with any single character; it matches, for example, with "a" or "1".
The following table lists several regular expressions and describes with which search query pattern they would match.

| Regex | Matches |
| ------------- | ------------- |
| this is text  | Matches exactly "this is text"  |
| this\s+is\s+text | Matches the word "this" followed by one or more whitespace characters followed by the word "is" followed by one or more whitespace characters followed by the word "text". |
| ^\d+(\.\d+)? | ^ defines that the pattern of the search query must start with the beginning of a new line. \d+ matches one or several digits. The ? makes the statement in brackets optional. \. matches ".", brackets are used for grouping. Matches for example with "5", "1.5" and "2.21". |

Further Reading: http://www.regular-expressions.info/java.html

#### [text fields]
| Field | JQL | Notes |
| ------------- | ------------- | ------------- |
| summary | issue in powerIssue("summary", ".*") | |
| description | issue in powerIssue("description", ".*") | |

Cases:

| Task | JQL | Notes |
| ------------- | ------------- | ------------- |
| Simple usage - find any issue with the word "amber" in the beginning of the Summary field | issue in powerIssue("summary", "(amber).*") |  |
| Any issue from POWERJQL project, where summary or description contains "text1" or "text2" (case insensitive) | issue in powerIssue("project=POWERJQL", "summary, description", "(?i).&ast;(text1 &#124; text2).&ast;") |  |

#### [user fields]
| Field | JQL | Notes |
| ------------- | ------------- | ------------- |
| assignee | issue in powerIssue("assignee", "Jackson") | |
| reporter | issue in powerIssue("reporter", "Lucas") | |
| creator | issue in powerIssue("creator", "Liam") | |

Cases:

| Task | JQL | Notes |
| ------------- | ------------- | ------------- |
| Any issue where assignee name contains "Michael" (case insensitive) | issue in powerIssue("assignee", "(?i).&ast;(Michael).&ast;") |  |

#### [date fields]
To search by date field use pattern "yyyy/MM/dd HH:mm".

| Field | JQL | Notes |
| ------------- | ------------- | ------------- |
| created | issue in powerIssue("created", "2017.*") | |
| updated | issue in powerIssue("updated", "2017/08/26.*") | |
| due, duedate | issue in powerIssue("due", "2017/08/26.*") | |
| resolutiondate | issue in powerIssue("resolutiondate", "2017/08.*") | |

#### [fixVersion, affectedVersion fields]
| Field | JQL | Notes |
| ------------- | ------------- | ------------- |
| fixVersion | issue in powerIssue("fixVersion", ".*(8\\.5.).*") | to find all tickets with fix versions like 8.5.1, 8.5.2, 8.5.1.1 etc. |
| affectedVersion | issue in powerIssue("affectedVersion", ".*(1\\.0.).*") | to find all tickets with affected versions like 1.0.1, 1.0.2, 1.0.1.1 etc. |

#### [components field] 

#### [watchers field] 

## powerComponent
> powerComponent([JQL subquery, optional], "regex expression")
Can be used with 1 or 2 arguments.

#### examples
Any not resolved issues where any component contains words "mobile" or "dev" in any part of component name (case sensitive):
> component in powerComponent("resolution=EMPTY", ".&ast;(mobile &#124; dev).&ast;")

## powerAttachment
> powerAttachment([JQL subquery, optional], regex expression)

#### examples
> issue in powerAttachment(".&ast;(?=android).&ast;(?=pdf).&ast;")

## powerProject
> powerProject(regex expression)

#### examples
> project in powerProject(".*(Customer).*")
