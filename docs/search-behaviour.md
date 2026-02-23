## Search behaviour

> The following sections describe how to build explorations that answer common content questions.
> 
> Unless otherwise stated, leave all other settings at their default values. Enter dimensions and metrics into the Tab settings column in the order specified.

This section focuses on internal site search behaviour: searches performed within your own site or service. It does not cover external search engines such as Google.

If your site includes an internal search function, GA4 can automatically record search activity.

When a user performs a search, GA4 records a "view_search_results" event. The search term is captured from recognised URL query parameters (for example, parameters such as q, s, or search). These parameters can also be configured in the property settings.

The "Page path and screen class" dimension will show the search results page itself. To identify where users initiated their search, use the "Page referrer" dimension. This shows the previous page viewed before the search results page loaded.

If no search data appears to be available, even for a broad date range:

1. Go to Admin.
2. Select Data collection and modification.
3. Select Data streams.
4. Select your website stream.
5. Check that automatic search tracking is enabled.

If search tracking is not enabled, contact the property administrator.

   

## How many searches are conducted from each page?

### Potential insights

These explorations could help you to:

- measure how often internal search is used
- identify pages where a relatively high proportion of users initiate a search
- compare internal search activity between device categories
- compare search behaviour between users referred from a specific domain and those who were not


### Understand the data

When a user performs a search, GA4 records a "view_search_results" event.

The "Page referrer" dimension shows the page viewed immediately before the search results page. This represents the page where the search was initiated.

Pages with more users will naturally generate more searches. To understand whether search usage is unusually high on a particular page, calculate the proportion of users on that page who performed a search.

To calculate this proportion:

1. Create the exploration below to identify the number of users who initiated a search from each page.
2. Create a second free-form exploration showing total users by page.
3. Export both datasets to CSV.
4. In a spreadsheet tool, match the two datasets by page path.
5. Divide:

   Total users who initiated a search from the page  
   ÷  
   Total users who viewed the page  

6. Format the result as a percentage.
7. Compare proportions across pages rather than relying on absolute counts.

Interpret higher proportions cautiously. Search usage may reflect:

- difficulty locating content
- users seeking additional detail
- users refining their task
- natural behaviour on complex landing pages


### Variables

| Field | Value |
|---|---|
| Dimensions | Event name<br>Page referrer |
| Metrics | Total users |
| Segments | 'Mobile traffic' (readymade segment)<br>'Web traffic' (readymade segment)<br><br>'Users referred from https://www.example.com/' (new segment):<br>Dimension: Page referrer<br>Condition: contains<br>Expression: https://www.example.com/<br><br>'Users NOT referred from https://www.example.com/' (new segment):<br>Dimension: Page referrer<br>Condition: does not contain<br>Expression: https://www.example.com/ |

### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Segment comparisons | Add only one comparison group at a time for clarity.<br><br>To compare referral source:<br>- Users referred from https://www.example.com/<br>- Users NOT referred from https://www.example.com/<br><br>To compare device type:<br>- Mobile traffic<br>- Web traffic |
| Rows | Page referrer |
| Show rows | 500 |
| Nested rows | No |
| Values | Total users |
| Cell type | Plain text |
| Filters | Dimension: Event name<br>Condition: exactly matches (=)<br>Expression: view_search_results |



## What terms are users searching for internally, from a specific page or site?

### Potential insights

These explorations could help you to:

- understand the language users use when searching
- identify information or tasks users expect to find but cannot locate easily
- assess whether certain topics are unclear or insufficiently signposted
- track changes in internal search terms over time
- compare search terms between device categories
- compare search terms between users referred from a specific domain and those who were not


### Understand the data

When filtered to the "view_search_results" event:

- "Event count" represents the total number of searches performed for a given term
- "Total users" represents the number of unique users who searched for that term

If Event count is substantially higher than Total users for a term, this indicates that some users searched for the same term more than once during the selected date range.

Repeated searches may reflect:

- refinement of search queries
- difficulty locating relevant results
- users returning to the search function across sessions

Interpret repeated searches in context rather than assuming a specific cause.

To analyse search terms:

1. Create the exploration using the variables and settings below.
2. Sort by either Total users or Event count, depending on whether you want to prioritise reach or volume.
3. Review terms in context of the pages where search was initiated, if filtering to a specific page.


### Variables

| Field | Value |
|---|---|
| Dimensions | Event name<br>Search term<br>Page referrer |
| Metrics | Total users<br>Event count |
| Segments | 'Mobile traffic' (readymade segment)<br>'Web traffic' (readymade segment)<br><br>'Users referred from https://www.example.com/' (new segment):<br>Dimension: Page referrer<br>Condition: contains<br>Expression: https://www.example.com/<br><br>'Users NOT referred from https://www.example.com/' (new segment):<br>Dimension: Page referrer<br>Condition: does not contain<br>Expression: https://www.example.com/ |

### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Segment comparisons | Add only one comparison group at a time for clarity.<br><br>To compare referral source:<br>- Users referred from https://www.example.com/<br>- Users NOT referred from https://www.example.com/<br><br>To compare device type:<br>- Mobile traffic<br>- Web traffic |
| Rows | Search term |
| Show rows | 500 |
| Nested rows | No |
| Values | Total users<br>Event count |
| Cell type | Plain text |
| Filters | Dimension: Event name<br>Condition: exactly matches (=)<br>Expression: view_search_results<br><br>To see search terms from an individual page, also add:<br><br>Dimension: Page referrer<br>Condition: exactly matches (=)<br>Expression: enter the full URL of the individual page, including https:// |



## What terms are users searching for internally, before arriving on a specific page?

### Potential insights

These explorations could help you to:

- identify which search terms immediately preceded visits to a specific page
- assess whether users rely on search to reach content that is already available through navigation
- understand whether certain pages are primarily discovered via internal search
- review whether search results appear to guide users to relevant destinations


### Understand the data

GA4 does not directly link an internal search term to the specific page a user selected from the results.

However, you can approximate this behaviour by analysing "Page referrer" values that contain search query parameters.

When a user performs a search, the search term is often included in the URL of the search results page (for example, through parameters such as q, s, search, query, or keyword). If the user then clicks a result, the destination page will record the search results URL as its referrer.

By filtering "Page referrer" to values containing search parameters, you can:

- identify pages that were visited immediately after a search
- review the associated search query strings

This method only works when:

- the search term is present in the URL
- the browser passes referrer information
- the search submission uses URL parameters rather than POST requests

It does not capture search behaviour from interfaces that do not update the URL or where referrer data is restricted.

Interpret results cautiously. If a search referrer appears unrelated to the destination page, consider whether the user may have navigated via global navigation rather than selecting a search result.


### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class<br>Page referrer |
| Metrics | Total users |


### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class<br>Page referrer |
| Show rows | 500 |
| Nested rows | Yes |
| Values | Total users |
| Cell type | Plain text |
| Filters | Dimension: Page referrer<br>Condition: matches regex<br>Expression: .*\?(q=\|s=\|search=\|query=\|keyword=).*<br><br>To filter results by an individual page, also add:<br><br>Dimension: Page path and screen class<br>Condition: exactly matches (=)<br>Expression: enter the page path (everything after your domain, excluding query strings) |
