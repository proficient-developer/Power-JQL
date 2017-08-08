# Power-JQL
https://marketplace.atlassian.com/plugins/proficient.developer.plugins.jira.power-jql/server/overview

## powerIssue
> powerIssue([JQL subquery, optional], "field names", "regex expression")

Flexible and powerful function to use Regex expressions for search in issue fields.
Can be used with 2 or 3 arguments.

### powerIssue examples
Simple usage - find any issue with word "amber" in the beginning of the Summary:
> issue in powerIssue("summary", "(amber).*")


Any issue from POWERJQL project, where summary or description contains "text1" or "text2" (case insensitive):
> issue in powerIssue("project=POWERJQL", "summary, description", "(?i).*(text1|text2).*")


Any issue where assignee name contains "John" (case insensitive):
> issue in powerIssue("assignee", "(?i).*(John).*")


## powerComponent
> powerComponent([JQL subquery, optional], "regex expression")
Can be used with 1 or 2 arguments.

### powerComponent examples
Any not resolved issue where component contains words "mobile" or "dev" in any part of component name (case sensitive):
> component in powerComponent("resolution=EMPTY", ".*(mobile|dev).*")

## powerAttachment
> powerAttachment([JQL subquery, optional], regex expression)

### powerAttachment examples
> issue in powerAttachment(".*(?=android).*(?=pdf).*")

## powerProject
> powerProject(regex expression)

### powerProject examples
> project in powerProject(".*(Customer).*")
