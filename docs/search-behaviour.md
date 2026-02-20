## Search behaviour

> The following sections offer recommendations for how to build explorations that answer common content questions. Think of these as recipes to follow or adapt as you need.
> 
> Unless otherwise stated, leave all options at their default setting. Be careful to enter dimensions and metrics into the Settings column in the order in which they're specified.


If your property has search functionality, by default GA4 will track it. GA4 achieves this by simply looking for the presence of URL query parameters (such as '/s=search+term').
When a user lands on a search results page, this is tracked as a 'view_search_results' event. To identify the page where users initiated their search, we need to use the 'page referrer' dimension (the 'page path and screen class' dimension would simply show the search results page for every query).
If no search data appears to be available, even for a broad date range:
1. Within the property, visit Admin > Data collection and modification > Data streams
2. Select 'Web'
3. In the 'Web stream details' overlay, check that 'Enhanced measurement' is enabled
4. If 'Enhanced measurement' is enabled, look at the 'Measuring' list to see if 'Site search' is enabled
5. If either of the above is not enabled, contact the property admin

Search tracking is one area where the GOV.UK setup on GA4 is significantly different from the default, free tier used in MoJ. The data is also typically on a much larger scale, so GA4 tends to apply more sampling (estimating numbers based on a subset of the data).

### How many searches are conducted from each page?

#### Potential insights
These explorations could help you to:
- measure how often search functionality is being used
- spot pages where above-average proportions of users are conducting internal searches, indicating a potential content discovery problem
- compare internal search activity between mobile and desktop users, to see if anything is harder to find on mobile
- compare internal search activity between users referred from GOV.UK and those not, to see if mainstream content is effectively providing specific information


#### Understand the data
If your site has search functionality, this exploration will show you how many users conducted a search from each page. This will typically be in rough proportion to the popularity of each page, with many more searches on the homepage than elsewhere.
To spot outliers - pages where an above-average percentage of users are reaching for the search function - you'll need to do some simple calculations:
1. Create an exploration using the variables and settings below.
2. Export the data to CSV (see Exporting data ).
3. In a new exploration tab, create a free-form exploration with 'Page location' in rows, and 'Total users' in values. Set 'Show rows' to 500.
4. Again, export the data to CSV.
5. In Excel, import the first CSV (total users who search on each page) into the default 'Sheet1' tab in Excel, selecting 'comma' as the delimiter.
6. Import the second CSV (total users by page) into a second 'Sheet2' tab, again selecting 'comma' as the delimiter.
7. Remove the top 6 rows on each tab (the exploration information which precedes the column headers).
8. In 'Sheet1', rename the 'Total users' column B header: 'Total users searching'.
9. Give column C the header 'Total users', and in the first row of this column add the following formula: =XLOOKUP(A2,Sheet2!A:A,Sheet2!B:B,"Not found")
10. This formula will match the total users values from Sheet2 against the correct URLs in Sheet1. Double-click the bottom right corner of the first row cell where you entered the formula, to autocomplete the whole column (or drag down to fill the whole column manually).
11. Give column D the header '% searches from page', and fill it with column B ('Total users searching') divided by column C ('Total users'). Format the cells as percentage.
12. Sort the Sheet1 by '% searches from page', largest to smallest.


#### Variables

| Field | Value |
|---|---|
| Dimensions | Event name<br>Page referrer<br>Page location |
| Metrics | Total users |
| Segments | 'Mobile traffic' (readymade segment)<br>'Web traffic' (readymade segment)<br>'Users referred from GOV.UK' (new segment):<br>- Include users when: Page referrer contains https://www.gov.uk/ at any point in time<br>'Users NOT referred from GOV.UK' (new segment):<br>- Exclude users when: Page referrer contains https://www.gov.uk/ at any point in time |


#### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Segment comparisons | To compare searches by users referred from GOV.UK or not, add the segments you created:<br>- Users referred from GOV.UK<br>- Users NOT referred from GOV.UK<br>To compare searches by users on mobile vs desktop, instead add the pre-built segments:<br>- Mobile traffic<br>- Web traffic |
| Rows | Page referrer |
| Show rows | 500 |
| Nested rows | No |
| Values | Total users |
| Cell type | Bar chart |
| Filters | Event name<br>- Conditions: exactly matches<br>- Expression: view_search_results |


### What terms are users searching for internally, from a specific page or site?

#### Potential insights
These explorations could help you to:
- understand the natural language of users
- identify if users are searching for information or calls to action that they're expecting to find on the page, but cannot
- understand if it's clear to users what content is and isn't likely to be available
- track trends in internal search terms, to understand how user needs might be changing over time
- compare internal search terms between mobile and desktop users, to see if anything is harder to find on mobile
- compare internal search terms between users referred from GOV.UK and those not, to see if mainstream content is effectively providing specific information


#### Understand the data
When filtered to the 'Event name' view_search_results, the 'Event count' metric will show you the total number of searches for a given term, while 'Total users' just the unique users who searched. If you sort the table by descending 'Total users' and use the 'Bar chart' cell type, you can see at a glance if certain terms were repeatedly entered by the same users, indicating that search results for that term may be confusing.

#### Variables

| Field | Value |
|---|---|
| Dimensions | Page referrer<br>Event count<br>Event name<br>Search term |
| Metrics | Total users |
| Segments | 'Mobile traffic' (readymade segment)<br>'Web traffic' (readymade segment)<br>'Users referred from GOV.UK' (new segment):<br>- Include users when: Page referrer contains https://www.gov.uk/ at any point in time<br>'Users NOT referred from GOV.UK' (new segment):<br>- Exclude users when: Page referrer contains https://www.gov.uk/ at any point in time |


#### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Segment comparisons | To compare searches by users referred from GOV.UK or not, add the segments you created:<br>- Users referred from GOV.UK<br>- Users NOT referred from GOV.UK<br>To compare searches by users on mobile vs desktop, instead add the pre-built segments:<br>- Mobile traffic<br>- Web traffic |
| Rows | Search term |
| Show rows | 500 |
| Nested rows | No |
| Values | Total users<br>Event count |
| Cell type | Plain text OR Bar chart (it's a minor visual difference) |
| Filters | Event name<br>- Conditions: exactly matches<br>- Expression: view_search_results<br>To see the search terms from an individual page:<br>Page referrer<br>- Conditions: exactly matches<br>- Expression: enter the full URL of the individual page (such as https://ppo.gov.uk/contact/) |


### What terms are users searching for internally, before arriving on a specific page?

#### Potential insights
These explorations could help you to:
- understand if users are searching for content that's already signposted in primary navigation or calls to action, indicating that navigation may need improvement
- identify content that may be over-reliant on internal search for discovery, indicating that navigation or signposting may need improvement
- understand if search results are failing to return relevant content, indicating that search functionality, metadata or the language being used may need improvement


#### Understand the data
With the default GA4 setup there unfortunately isn't a particularly neat way to track internal search terms that led to a specific page. The closest approximation is to look at page referrer URLs that contain search query strings, like "How to make a complaint" in https://ppo.gov.uk/?s=how+to+make+a+complaint. The suggested 'matches regex' filter will capture all pages containing the search query strings that GA4 captures.
With the example of https://ppo.gov.uk/?s=how+to+make+a+complaint, if this page referred a user to /complaints/, we could be fairly confident about the user intent. But if the search term appeared to lead the user to an unrelated top level page, consider the global navigation – the user may have searched for the term, not found anything useful in the search results, and then clicked an unrelated item in the global navigation, rather than on a search result.

#### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class<br>Page referrer |
| Metrics | Total users |


#### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class<br>Page referrer |
| Show rows | 500 |
| Nested rows | Yes |
| Values | Total users |
| Cell type | Bar chart OR Plain text (it's a minor visual difference) |
| Filters | Page referrer<br>- Conditions: matches regex<br>- Expression: .*\?(q=\|s=\|search=\|query=\|keyword=).*<br>To filter results by an individual page, add:<br>Page path and screen class<br>- Conditions: exactly matches<br>- Expression: enter the page path, which is everything after your domain, minus any query strings (for example, the page path for https://helpwithcourtfees.service.gov.uk/questions/fee?locale=en is /questions/fee) |
