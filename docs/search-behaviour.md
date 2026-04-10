# Search behaviour

> Each section below outlines how to build an exploration that answers a specific content question.
> 
> Add dimensions and metrics into the Settings column in the order specified. Unless otherwise stated, leave all other settings at their default values.

This section focuses on internal site search behaviour: searches performed within your own site or service.

GA4 does not show the search terms users typed into external search engines such as Google. These queries are not shared with GA4. To analyse search engine queries, you will need access to Google Search Console or a similar tool.

If your site includes an internal search function, GA4 can record search activity when it detects recognised search query parameters in the page URL (for example, parameters such as "q", "s", or "search"). These parameters can also be configured in the property settings.

When a user performs a search, GA4 records a "view_search_results" event. In reports, this typically appears as activity on the search results page.

The "Page path and screen class" dimension shows the search results page itself. To understand where the search was initiated, use the "Page referrer" dimension. This shows the page the user was viewing immediately before the search results page loaded.

If no search data appears to be available, even when using a broad date range, check that search tracking is enabled:

1. Go to Admin.
2. Select Data collection and modification.
3. Select Data streams.
4. Select your website stream.
5. Check that 'Enhanced measurement' contains 'Site search'.

If search tracking is not enabled, contact the property administrator.

   

## How many searches are conducted from each page?

### Potential insights

These explorations could help you to:

- measure how often internal search is used
- identify pages where a relatively high proportion of users go on to perform a search
- compare internal search activity between device categories
- compare search behaviour between users associated with a specific referral domain and those not


### Understand the data

When a user performs a search, GA4 records a "view_search_results" event.

The "Page referrer" dimension shows the page viewed immediately before the search results page. This represents the page where the search was likely initiated.

Pages with more users will naturally tend to generate more searches. Absolute counts alone do not indicate whether search usage is high relative to page traffic.

To understand relative usage, calculate the proportion of users on each page who went on to perform a search:

1. Create the exploration below to show how many users searched from each page
2. Create a second free-form exploration showing total users by page for the same time period (dimension: Page path and screen class, metric: Total users).
3. Export both datasets to CSV.
4. In a spreadsheet tool, match the datasets by page path (for example, using VLOOKUP or an equivalent function).
5. Calculate: Users who searched from the page ÷ Total users who viewed the page  
6. Format the result as a percentage.
7. Compare proportions across pages rather than relying on absolute counts.

Interpret higher proportions in context. Search usage may reflect:

- users not immediately finding what they need
- users looking for more specific information
- users refining or continuing a task
- expected behaviour on pages with broad or complex content

### Variables

| Field | Value |
|---|---|
| Dimensions | Event name<br>Page referrer |
| Metrics | Total users |
| Segments | Mobile traffic<br>Web traffic<br><br>Type: User segment<br>Title: Users referred from example.com<br>Include users when:<br>- Session source<br>- contains<br>- example.com (only enter the domain, do not include "www.")<br><br>Type: User segment<br>Title: Users NOT referred from example.com<br>Exclude users when (Exclude from segment permanently):<br>- Session source<br>- contains<br>- example.com (only enter the domain, do not include "www.") |

### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Segment comparisons | Add only one comparison group at a time for clarity.<br><br>To compare referral source:<br>- Users referred from example.com<br>- Users NOT referred from example.com<br><br>To compare device type:<br>- Mobile traffic<br>- Web traffic |
| Rows | Page referrer |
| Show rows | 500 |
| Nested rows | No |
| Values | Total users |
| Cell type | Plain text |
| Filters | Dimension: Event name<br>Condition: exactly matches (=)<br>Expression: view_search_results |


## What terms are users searching for internally?

### Potential insights

These explorations could help you to:

- understand the natural language of users
- identify information or tasks users expect to find but cannot locate easily
- assess whether certain topics are unclear or insufficiently signposted
- track changes in internal search terms over time
- compare search terms between device categories
- compare search terms between users associated with a specific referral domain and those not


### Understand the data

When filtered to the "view_search_results" event:

- "Event count" represents the total number of searches performed for a given term
- "Total users" represents the number of unique users who searched for that term

If Event count is substantially higher than Total users for a term, this indicates that some users searched for the same term more than once during the selected date range. Sort the table by descending Total users and use the Bar chart cell type to see at a glance if certain terms were repeatedly entered by the same users.

Repeated searches may reflect:

- users not finding relevant results immediately
- users returning to search across sessions

Interpret repeated searches in context.

### Variables

| Field | Value |
|---|---|
| Dimensions | Event name<br>Search term<br>Page referrer |
| Metrics | Total users<br>Event count |
| Segments | Mobile traffic<br>Web traffic<br><br>Type: User segment<br>Title: Users referred from example.com<br>Include users when:<br>- Session source<br>- contains<br>- example.com (only enter the domain, do not include "www.")<br><br>Type: User segment<br>Title: Users NOT referred from example.com<br>Exclude users when (Exclude from segment permanently):<br>- Page referrer<br>- contains<br>- example.com (only enter the domain, do not include "www.") |

### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Segment comparisons | Add only one comparison group at a time for clarity.<br><br>To compare referral source:<br>- Users referred from example.com<br>- Users NOT referred from example.com<br><br>To compare device type:<br>- Mobile traffic<br>- Web traffic |
| Rows | Search term |
| Show rows | 500 |
| Nested rows | No |
| Values | Total users<br>Event count |
| Cell type | Plain text |
| Filters | Dimension: Event name<br>Condition: exactly matches (=)<br>Expression: view_search_results<br><br>To see search terms from an individual page, also add:<br><br>Dimension: Page referrer<br>Condition: exactly matches (=)<br>Expression: enter the full URL of the individual page, including https:// |



## What search terms are leading users to a specific page?

### Potential insights

These explorations could help you to:

- identify which search terms preceded visits to a specific page
- assess whether users rely on search to reach content that is already available through navigation
- understand whether certain pages are primarily discovered via internal search
- review whether search results appear to guide users to relevant destinations


### Understand the data

GA4 does not directly link a search term to the specific page a user selected from the search results.

You can approximate this by analysing "Page referrer" values that contain search query parameters.

When a user performs a search, the search term is often included in the URL of the search results page (for example, through parameters such as "q", "s", "search", "query", or "keyword"). If the user then clicks a result, the destination page will record the search results URL as its referrer.

By filtering "Page referrer" to values containing search parameters, you can:

- identify pages that were visited immediately after a search
- review the associated search query strings

This method only works when:

- the search term is present in the URL
- the browser passes referrer information
- the search submission uses URL parameters rather than POST requests

It does not capture search behaviour from interfaces that do not update the URL or where referrer data is restricted.

Interpret results cautiously. If a search referrer appears unrelated to the destination page, the user may have navigated via global navigation rather than selecting a search result.


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
| Filters | Dimension: Page referrer<br>Condition: matches regex<br>Expression: `.*\?(q=\|s=\|search=\|query=\|keyword=).*`<br><br>To filter results by an individual page, also add:<br><br>Dimension: Page path and screen class<br>Condition: exactly matches (=)<br>Expression: enter the page path (everything after your domain, excluding query strings) |

---

<small>GA4 for content designers by Alex Robertson is licensed under <a href="https://creativecommons.org/licenses/by/4.0/">CC BY 4.0</a>.</small>
