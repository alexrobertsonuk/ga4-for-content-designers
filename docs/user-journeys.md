# User journeys and pain points

## Contents

- [Using these explorations](user-journeys?id=using-these-explorations)
- [Where are users coming from?](user-journeys?id=where-are-users-coming-from)
- [What referrals are coming from LLMs (large language models)?](user-journeys?id=what-referrals-are-coming-from-llms-large-language-models)
- [What are the most common user paths through a site or multi-step journey?](user-journeys?id=what-are-the-most-common-user-paths-through-a-site-or-multi-step-journey)
- [Are users repeatedly returning to the same page?](user-journeys?id=are-users-repeatedly-returning-to-the-same-page)
- [How long are users spending on each page?](user-journeys?id=how-long-are-users-spending-on-each-page)
- [What percentage of users are completing a multi-step journey, and how long is it taking them?](user-journeys?id=what-percentage-of-users-are-completing-a-multi-step-journey-and-how-long-is-it-taking-them)
- [How many sessions do users need to complete a multi-step journey?](user-journeys?id=how-many-sessions-do-users-need-to-complete-a-multi-step-journey)
- [Where are non-completing users abandoning a multi-step journey?](user-journeys?id=where-are-non-completing-users-abandoning-a-multi-step-journey)
- [Which pages in a multi-step journey are users commonly moving backwards to?](user-journeys?id=which-pages-in-a-multi-step-journey-are-users-commonly-moving-backwards-to)
- [Do users change device type mid-journey to complete tasks?](user-journeys?id=do-users-change-device-type-mid-journey-to-complete-tasks)
- [What external links are most clicked?](user-journeys?id=what-external-links-are-most-clicked)

## Using these explorations

Each section below describes how to build an exploration that answers a common content question.

Add dimensions and metrics into the Settings column in the order specified. Unless otherwise stated, leave all other settings at their default values.

## Where are users coming from?

### Potential insights

These explorations can help you to:

- assess whether improvements to navigation or incoming links have increased content findability
- identify top external referrers, and prioritise ensuring their information is consistent and up-to-date
- detect underperforming referrers where navigation or signposting may need improvement
- explore the needs of users being referred from external sources, by tracing and evaluating the call to action that they respond to
- identify internal pages that are a disproportionate source of referrals to technical support or contact pages

### Understand the data

The "Page referrer" dimension shows the previous URL visited before the current page.

This may be:

- an external website
- another page within your own site
- empty (no referrer recorded)

For internal referrals, the full URL is shown, including the domain and any query string (https://www.example.com/ask-for-help/new?topic=benefits).

For external referrals, you may only see the top-level domain (https://www.example.com), or nothing at all. Many browsers and sites restrict how much referrer information is passed, so external referrer data is often incomplete.

An empty "Page referrer" value may indicate:

- direct traffic (for example, users typing the URL or using a bookmark)
- referrer information blocked by browser or site policy
- the user reopening a page in an inactive browser tab

To more accurately analyse external referrals, pair "Page referrer" with "Landing page + query string" instead of "Page path and screen class". "Landing page + query string" identifies the entry point for a user's session.

For less in-depth analysis, the "Session source" dimension groups external referrers using values such as "google", "bing", or "reddit.com". You may also see "(direct)" for users with no recorded source, and "(not set)" where the source could not be determined.

The "Nested rows" option will group together all pages that share the same referrer, for a more readable overview. Nested rows are limited to 10 rows per item - to see all pages, turn nesting off.

### Variables

| Field | Value |
|---|---|
| Dimensions | Page referrer<br>Landing page + query string<br>Page path and screen class<br>Session source |
| Metrics | Total users |

### Settings: to see categorised external referrers for a whole site

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Session source |
| Show rows | 100 |
| Nested rows | No |
| Values | Total users |
| Cell type | Bar chart or Plain text |

### Settings: to see detailed external referrers for a whole site or specific page

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page referrer<br>Landing page + query string |
| Show rows | 100 |
| Nested rows | Yes |
| Values | Total users |
| Cell type | Bar chart or Plain text |
| Filters | Dimension: Page referrer<br>Condition: does not contain<br>Expression: enter your site or service domain (example.com)<br><br>Dimension: Page referrer<br>Condition: matches regex<br>Expression: `^.+$` This is a regular expression that matches any non-empty value - it excludes rows where no referrer was recorded. Copy it exactly as shown.<br><br>To see external referrals for an individual page, also add:<br><br>Dimension: Landing page + query string<br>Condition: exactly matches<br>Expression: enter the landing page path and any query string (for example, /ask-for-help/new?topic=benefits) |

### Settings: to see detailed internal referrers for a specific page

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page referrer |
| Show rows | 100 |
| Nested rows | Yes |
| Values | Total users |
| Cell type | Bar chart or Plain text |
| Filters | Dimension: Page referrer<br>Condition: contains<br>Expression: enter your site domain (example.com)<br><br>Dimension: Page path and screen class<br>Condition: exactly matches<br>Expression: enter the page path, minus any query string (for example, /ask-for-help/new) |


## What referrals are coming from LLMs (large language models)?

### Potential insights

This exploration can help you to:

- identify pages that users are discovering via LLMs
- assess whether pages regularly referred from LLMs are well signposted for new visitors
- compare behaviour of LLM-referred users with other external referral sources


### Understand the data

This exploration builds on the same referrer-based approach described in "Where are users coming from?", but filters results to known LLM domains:

- chatgpt.com, chat.openai.com (ChatGPT)
- claude.ai (Anthropic)
- copilot.microsoft.com (Microsoft Copilot)
- gemini.google.com (Google Gemini)
- grok.x.ai (Grok/xAI)
- qwen.com (Qwen/Alibaba)
- yiyan.baidu.com (Ernie Bot/Baidu)
- deepseek.com
- kimi.com
- mistral.ai
- perplexity.ai
- poe.com
- you.com

This exploration measures visits where a user clicked through from a known LLM site. It does not capture content that may have been summarised or paraphrased within an LLM response without generating a visit.

Some LLM interfaces operate through mobile apps or embedded environments that do not reliably pass referrer information to the browser. They may also strip the referrer entirely for privacy reasons. In these cases, the visit will often be recorded as "Direct" traffic. As a result, this exploration will under-represent the true volume of LLM-influenced visits. It captures only visits where a referral can be identified.

You may see landing pages grouped as "(not set)". This commonly occurs when visits originate from apps or via a redirect, or where consent or tagging loads after the initial page request.

### Variables

| Field | Value |
|---|---|
| Dimensions | Page referrer<br>Landing page + query string |
| Metrics | Total users |


### Settings: to see referrals from major LLMs to a whole site or specific page

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page referrer<br>Landing page + query string |
| Show rows | 100 |
| Nested rows | Yes |
| Values | Total users |
| Cell type | Bar chart or Plain text |
| Filters | Dimension: Page referrer<br>Condition: matches regex<br>Expression: enter the regex below (this is a regular expression that matches any known LLM domains)<br><br>To see referrals for an individual page, also add:<br><br>Dimension: Landing page + query string<br>Condition: exactly matches<br>Expression: enter the page path and any query string (for example, /ask-for-help/new?topic=benefits) |

### Regex

```text 
^https?://([^/]+\.)?(chat\.openai\.com|chatgpt\.com|claude\.ai|gemini\.google\.com|copilot\.microsoft\.com|perplexity\.ai|poe\.com|you\.com|grok\.x\.ai|mistral\.ai|qwen\.com|kimi\.com|yiyan\.baidu\.com|deepseek\.com)(/|$)
```

## What are the most common user paths through a site or multi-step journey?

### Potential insights

These explorations can help you to:

- identify common paths through a site or transactional service, to help prioritise effort
- assess whether content changes influence the paths users take
- identify drop-off points, loops, or repeated steps
- identify the most common user tasks on a site

### Understand the data

A path exploration creates an interactive Sankey diagram showing the most common next steps users take from a selected page (or the most common previous steps if you build the path backwards from an ending point).

Path explorations have a 10 step ("node") limit, so are best suited to examining specific sections or decision-points of longer or branching journeys.

When you first create a path exploration, GA4 defaults to an "Event name" starting point. To build a page-based path exploration:

1. Select "Start again" (top right of the exploration output).
2. Choose whether you want a "Starting point" or an "Ending point" by selecting the corresponding "Drop or select node" option.
3. Select "Page path and screen class" and choose a page for your start or end point.
4. In the Sankey diagram, click a page (a "node" on the chart) to expand the path step by step, up to 10 total steps.

Setting "View unique nodes only" to "Yes" prevents the same page appearing multiple times across different steps in the diagram. This gives a cleaner view of the overall journey and avoids inflating the apparent complexity of paths where users revisit pages.


### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class |
| Metrics | Total users |


### Settings

| Field | Value |
|---|---|
| Technique | Path exploration |
| View unique nodes only | Yes |
| Values | Total users |


## Are users repeatedly returning to the same page?

### Potential insights

These explorations can help you to:

- identify potential pain points in a user journey
- identify reference or guidance pages that users revisit frequently (which may help to evaluate whether the information should be integrated at the point of need instead)
- highlight potential drop-off points where users exit after repeated views

### Understand the data

The "Views per active user" metric divides the total number of views for a page by the number of active users.

For example, if a page received 100 views from 70 active users, the result would be 1.43 views per active user.

Higher values indicate that users are revisiting the page — either multiple times within a single session, or returning to it across different sessions over the selected date range. This can reflect:

- difficulty progressing
- repeated backwards steps
- users returning to reference material
- refreshes or repeated interactions

This exploration uses "Views" and "Active users" instead of "Total users" to align with the "Views per active user" metric. In GA4, "Active users" counts users who had an "engaged" session (one that lasted longer than 10 seconds, included a conversion event, or included at least 2 page views).

Adding the "Exits" metric allows you to correlate any pages that are frequently revisited with common exit points.

For each page, the total number of exits is less informative than the proportion of views that resulted in an exit (exit rate). GA4 does not display exit rate directly, but you can calculate it by exporting the data:

1. Create the exploration using the variables and settings below.
2. Export the data as CSV.
3. Open the CSV in a spreadsheet.
4. Remove any rows above the column headers so that the first visible row contains the column headers.
5. Insert a new column titled "Exit rate".
6. In the "Exit rate" column, divide the "Exits" values by the "Views" values.
7. Format the result as a percentage.
8. Sort by descending "Exit rate" to identify pages with relatively high proportions of exits.

Pages with both high views per active user and high exit rates may indicate pain points to investigate.


### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class |
| Metrics | Active users<br>Views<br>Views per active user<br>Exits |


### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class |
| Show rows | 100 |
| Nested rows | No |
| Values | Active users<br>Views<br>Views per active user<br>Exits |
| Cell type | Bar chart or Plain text |
| Filters | To analyse a specific page, add:<br><br>Dimension: Page path and screen class<br>Condition: exactly matches<br>Expression: enter the page path (for example, /ask-for-help/new) |



## How long are users spending on each page?

### Potential insights

These explorations can help you to:

- identify pages where users spend longer than average
- identify pages where users spend less time than is likely to be necessary (for instance where content is lengthy or complex), indicating the content may need to be broken up or reformatted
- assess whether content changes influence average time spent
- compare time spent on each page with exits, to spot potential pain points

### Understand the data

GA4 does not include a direct "time spent on page" metric.

Instead, use the "User engagement" metric, which estimates the cumulative time (in seconds) that a page was actively in focus in the user's browser. GA4 calculates engagement time from interactions rather than tracking focus continuously, so these figures are estimates rather than absolutely precise.

To estimate average time spent per page view:

1. Create an exploration using the variables and settings below.
2. Export the data as CSV.
3. Open the CSV in a spreadsheet.
4. Remove any rows above the column headers so that the first visible row contains the column headers.
5. Insert a new column titled "Average time per view (seconds)".
6. In the "Average time per view (seconds)" column, divide the "User engagement" values by the "Views" values.

What to deduce from the average time spent on a page requires contextual analysis. Longer time spent may indicate difficulty progressing, but could also indicate careful reading. Shorter time spent could indicate hasty exits, but could also indicate efficient completion of a task or typical skim-reading.

To compare time spent with exit behaviour, in your spreadsheet:

1. Insert another column titled "Exit rate".
2. In the "Exit rate" column, divide the "Exits" value by the "Views" value.
3. Format as a percentage.
4. Compare your "Exit rate" and "Average time per view (seconds)" values to identify outliers.

Pages with both high average time per view and high exit rates may indicate user pain points to investigate further.

### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class |
| Metrics | User engagement<br>Views<br>Exits |


### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class |
| Show rows | 100 |
| Nested rows | No |
| Values | User engagement<br>Views<br>Exits |
| Cell type | Bar chart or Plain text |
| Filters | To analyse a specific page, add:<br><br>Dimension: Page path and screen class<br>Condition: exactly matches<br>Expression: enter the page path (for example, /ask-for-help/new) |


## What percentage of users are completing a multi-step journey, and how long is it taking them?

### Potential insights
These explorations can help you to:

- benchmark current completion rates and average completion time, and compare these after content changes
- identify page-to-page transitions where drop-off rates are higher than normal
- compare completion rates and times across different user groups, such as mobile vs desktop or new vs returning users

### Understand the data
A funnel exploration can be used to measure how many users complete a defined multi-step journey, and how long it takes them.

Unlike a path exploration, which expands from a start or end point as you click on each "node" (representing a page), a funnel requires you to define each step in advance. You can add up to 10 steps, which makes it suitable for:

- measuring completion between a defined start and end page
- examining a small number of critical steps within a longer journey

Funnel explorations are not designed to map complex branching services in full.

The funnel will calculate:

- the proportion of users who moved from the first defined step to the final step
- the average "Elapsed time" between those steps (when enabled)

When only a start and completion page are defined, "Elapsed time" represents the average time to completion.

This value can be heavily influenced by users who leave and return over multiple days before completing. To better understand typical in-session behaviour, compare new and returning users. Completion time for returning users may include long gaps between visits, while for new users it's more likely to reflect completion within a single visit.

The funnel is set to "closed" by default ("Make open funnel": off). This means only users who begin at the first step are counted. Users who arrive directly at a later step are excluded. This gives a more accurate picture of completion for users who attempt the full journey.


### Variables

| Field | Value |
|---|---|
| Segments | All Users<br>Mobile traffic<br>Web traffic<br><br>(Create a new segment)<br>Type: User segment<br>Title: New users<br>Include users when:<br>- New/returning<br>- exactly matches (=)<br>- new<br><br>(Create a new segment)<br>Type: User segment<br>Title: Returning users<br>Include users when:<br>- New/returning<br>- exactly matches (=)<br>- returning |

### Settings

| Field | Value |
|---|---|
| Technique | Funnel exploration |
| Visualisation | Standard funnel |
| Make open funnel | Off |
| Segment comparisons | Add only one comparison group at a time for clarity.<br><br>To compare device type:<br>- Mobile traffic<br>- Web traffic<br><br>To compare user type:<br>- New users<br>- Returning users |
| Steps | Step 1<br>Title: Start page<br>Condition: Page path and screen class<br>Filter: exactly matches (=)<br>Value: enter the path of the first page on your service<br><br>...is indirectly followed by...<br><br>Step 2<br>Title: Completion page<br>Condition: Page path and screen class<br>Filter: exactly matches (=)<br>Value: enter the path of the final confirmation, summary, or completion page |
| Show elapsed time | On |



## How many sessions do users need to complete a multi-step journey?

### Potential insights

This exploration can help you to:

- estimate how many sessions, on average, it takes users who complete a journey to reach the final page
- assess whether content changes reduce the need for users to return later
- assess the influence of device category (desktop, mobile or tablet) on the average number of sessions to complete


### Understand the data

This method focuses only on users who reached a completion page. It does not include users who started the journey but failed to complete.

Create a segment that includes users who viewed the completion page, and apply it with the "Sessions per active user" metric. This shows the average number of sessions for users who completed the journey.

A session begins when a user starts interacting with your site and ends after a period of inactivity (30 minutes by default, unless your GA4 property settings have been changed). If a user leaves and later returns, this creates a new session. Consequently, users who take breaks before finishing will increase the average number of sessions.

This exploration uses "Active users" instead of the usual "Total users", to correspond with the "Sessions per active user" metric.


### Variables

| Field | Value |
|---|---|
| Dimensions | Device category |
| Metrics | Sessions<br>Active users<br>Sessions per active user |
| Segments | (Create a new segment)<br>Type: User segment<br>Title: Completion page viewed<br>Include users when:<br>- Page path and screen class<br>- exactly matches (=)<br>- enter your completion page path, such as /confirmation |

### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Segment comparisons | Completion page viewed |
| Rows | Device category |
| Show rows | 10 |
| Nested rows | No |
| Values | Active users<br>Sessions<br>Sessions per active user |
| Cell type | Plain text |



## Where are non-completing users abandoning a multi-step journey?

### Potential insights

This exploration can help you to:

- identify pages within a journey where users who did not complete are most frequently exiting
- monitor whether content changes influence exit behaviour at specific steps
- compare abandonment patterns by device category or by users associated with different referring domains


### Understand the data

Funnel and path explorations are limited to 10 defined steps. For longer or more complex services, a free-form exploration provides a more complete view across all pages.

This method focuses only on users who did not reach the completion page within the selected date range.

Users who return after the date range to complete will still be counted here as non-completing. Extending the date range can reduce this effect, but not remove it entirely.

An "Exit" is recorded when a session ends on a page. This does not necessarily mean the user has permanently abandoned the journey - users who pause and return later still generate exits in their earlier sessions.

GA4 does not provide a built-in "exit rate" metric. You can estimate it with:

Exits ÷ Views

This produces the proportion of views that were the final interaction in a session.

To calculate exit rate:

1. Create an exploration using the variables and settings below.
2. Export the data to CSV.
3. Open the CSV in a spreadsheet.
4. Remove any rows above the column headers so that the first visible row contains the data labels.
5. Insert a new column titled "Exit rate".
6. In the "Exit rate" column, divide the "Exits" values by the "Views" values.
7. Format the result as a percentage.
8. Review pages that are part of the transaction journey and compare their relative exit rates.


High exit rates do not automatically indicate a problem. Consider:

- whether the page represents a natural stopping point
- whether users may be pausing intentionally
- how the exit rate compares with adjacent steps in the journey


### Variables

| Field | Value |
|---|---|
| Segments | (Create a new segment)<br>Type: User segment<br>Title: Users who have NOT completed<br>Exclude users when (Exclude from segment permanently):<br>- Page path and screen class<br>- contains<br>- enter the page path of the completion page, such as /confirmation<br><br>(Create a new segment)<br>Type: User segment<br>Title: Users referred from example.com who have NOT completed<br>Include users when:<br>- Session source<br>- contains<br>- example.com (only enter the domain, do not include "www")<br>Exclude users when (Exclude from segment permanently):<br>- Page path and screen class<br>- contains<br>- enter the page path of the completion page, such as /confirmation<br><br>(Create a new segment)<br>Type: User segment<br>Title: Mobile users who have NOT completed<br>Include users when:<br>- Device category<br>- exactly matches (=)<br>- mobile<br>Exclude users when (Exclude from segment permanently):<br>- Page path and screen class<br>- contains<br>- enter the page path of the completion page, such as /confirmation |

### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Segment comparisons | Add only one comparison group at a time for clarity.<br><br>Users who have NOT completed<br><br>OR<br><br>Users referred from example.com who have NOT completed<br><br>OR<br><br>Mobile users who have NOT completed |
| Rows | Page path and screen class |
| Show rows | 100 |
| Nested rows | No |
| Values | Total users<br>Views<br>Exits |
| Cell type | Plain text |



## Which pages in a multi-step journey are users commonly moving backwards to?

### Potential insights

This exploration can help you to:

- identify steps in a journey that may be pain points causing confusion or uncertainty
- identify steps in a journey where users may be reviewing or reconsidering previous answers


### Understand the data

This method identifies backward navigation by comparing:

- Page referrer (the page users came from)
- Page path and screen class (the page users arrived at)

Backward movement is indicated when the destination page is an earlier step in the journey than the referrer page.

The exploration table will include:

- Page path and screen class: the destination page
- Page referrer: the previous page
- Total users: the number of users who moved between those two pages
- Views per active user: the average number of times the destination page was viewed by each active user during the selected date range. To avoid this being skewed higher by users who returned during your date range to work through the service in multiple sessions, this exploration filters to new users only.

To identify potential problem areas, sort the output table by "Views per active user", high to low. Working down the table, look for instances where the "Page path and screen class" is the step immediately prior to the "Page referrer". Rows where the referrer and destination are the same often indicate page refreshes or resubmissions and can typically be ignored, though they may occasionally reflect other in-page interactions.


### Variables

| Field | Value |
|---|---|
| Dimensions | New/Established<br>Page path and screen class<br>Page referrer |
| Metrics | Total users<br>Views per active user |


### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class<br>Page referrer |
| Show rows | 100 |
| Nested rows | No |
| Values | Total users<br>Views per active user |
| Cell type | Plain text |
| Filters | Dimension: New/Established<br>Condition: exactly matches<br>Expression: new<br><br>Dimension: Page referrer<br>Condition: contains<br>Expression: enter your service domain, such as www.example.com, to restrict results to internal navigation |




## Do users change device type mid-journey to complete tasks?

### Potential insights

This exploration can help you to:

- compare the device types of new and returning users, and monitor whether this is influenced by design changes


### Understand the data

This method compares device category for:

- new users - users whose first recorded visit falls within the selected date range
- returning users - users who visited before the date range and came back within it

The two counts are independent and will not add up to total users.

A difference in device type distribution between new and returning users may suggest that some users begin a journey on one device and return on another. Depending on the context, it could equally reflect that different types of users — with different device preferences — make up the new and returning user groups.

### Variables

| Field | Value |
|---|---|
| Dimensions | Device category |
| Metrics | New users<br>Returning users |


### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Doughnut chart |
| Breakdowns | Device category |
| Values | Select one metric at a time:<br>New users<br>OR<br>Returning users |


## What external links are most clicked?

### Potential insights

This exploration can help you to:

- identify which external resources may be most valuable for users
- identify underperforming links which may need to be removed or signposted more effectively
- compare whether external links are clicked more often than primary calls to action, which may indicate that external information needs more effective integration


### Understand the data

This method analyses external link clicks recorded by GA4.

External link clicks are only recorded if automatic click tracking is enabled in your property's settings. If this tracking is enabled, GA4 records:

- the page where the click occurred
- the destination URL of the external link

Enabling nested rows will group external links under the page where they were clicked.

If no external link data appears:

1. Visit "Admin" in the main left-hand navigation.
2. Select "Data collection and modification".
3. Select "Data streams".
4. Select your website stream.
5. Check that "Enhanced measurement" contains "Outbound clicks".

If this setting is not enabled, contact the property administrator.

Some external link clicks may not be recorded due to browser privacy controls, consent configuration, or ad blockers.



### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class<br>Link URL |
| Metrics | Total users |


### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class<br>Link URL |
| Show rows | 100 |
| Nested rows | Yes |
| Values | Total users |
| Cell type | Plain text |

---

<small>GA4 for content designers by Alex Robertson is licensed under <a href="https://creativecommons.org/licenses/by/4.0/">CC BY 4.0</a>.</small>
