# User journeys and pain points

> Each section below outlines how to build an exploration that answers a specific content question.
> 
> Add dimensions and metrics into the Settings column in the order specified. Unless otherwise stated, leave all other settings at their default values.

## Contents
<!-- {docsify-ignore} -->

<div data-page-toc></div>

By combining the explorations below, you can build an understanding of:

- where users arrive from
- how they move through a site or service
- which pages they visit next
- where users drop off in multi-step journeys
- how long journeys take to complete
- how many sessions are typically required to reach completion

## Where are users coming from?

### Potential insights

These explorations can help you to:

- assess whether improvements to navigation or cross-linking have increased findability
- identify which external sources send the most users to your site, and prioritise ensuring their information is consistent and up-to-date
- detect underperforming referral sources where navigation or signposting may need improvement
- identify the needs of users being referred from external sources, by tracing and evaluating the call to action that they respond to
- identify internal pages that are a disproportionate source of referrals to technical support or contact us pages

### Understand the data

The "Page referrer" dimension shows the previous URL recorded for a page view.

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

Since "Page referrer" reflects the previous page for each "Page path and screen class", it does not always represent the original source of a site visit.

When analysing external referrals, pair "Page referrer" with "Landing page + query string". "Landing page + query string" identifies the first page visited in the session.

For more broad analysis, the "Session source" dimension identifies the external origin of the whole visit, using values such as "google", "bing", or "reddit.com". You may also see "(direct)" for users with no recorded source, and "(not set)" where the source could not be determined.

The "Nested rows" option will group together all the pages which share the same referrer, giving you a more readable overview. Nested rows are limited to 10 rows per item - to see all pages, turn nesting off.

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

- identify content that users are discovering via LLM interfaces
- assess whether LLM-referred landing pages are clear and well signposted for first-time visitors
- compare behaviour of LLM-referred users with other external referral sources


### Understand the data

This exploration builds on the same referrer-based approach described in "Where are users coming from?", but limits results to known LLM domains:

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

Referrals from LLMs differ from many other external sources. Some LLM interfaces operate through mobile apps or embedded environments that do not reliably pass referrer information to the browser. They may also strip the referrer entirely for privacy reasons. In these cases, the visit will often be recorded as "Direct" traffic. As a result, this exploration will under-represent the true volume of LLM-influenced visits. It captures only visits where a referral can be identified.

This exploration also only measures visits where a user clicked through to your site. It does not capture content that may have been summarised or paraphrased within an LLM response without generating a visit.

You may see landing pages grouped as "(not set)". This indicates that GA4 was unable to record a landing page for the session. This commonly occurs when traffic originates from apps, redirects, or where consent or tagging loads after the initial page request. It does not necessarily indicate a tracking error.

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
| Filters | Dimension: Page referrer<br>Condition: matches regex<br>Expression: ``` ^https?://([^/]+\.)?(chat\.openai\.com\|chatgpt\.com\|claude\.ai\|gemini\.google\.com\|copilot\.microsoft\.com\|perplexity\.ai\|poe\.com\|you\.com\|grok\.x\.ai\|mistral\.ai\|qwen\.com\|kimi\.com\|yiyan\.baidu\.com\|deepseek\.com)(/\|$)```<br><br>To see referrals for an individual page, also add:<br><br>Dimension: Landing page + query string<br>Condition: exactly matches<br>Expression: enter the page path and any query string (for example, /ask-for-help/new?topic=benefits) |



## What are the most common user paths through a site or multi-step journey?

### Potential insights

These explorations can help you to:

- identify common paths through a site or transactional service, to help prioritise effort
- assess whether content changes influence the paths users take
- identify drop-off points, loops, or repeated steps
- identify users' most common tasks on a site

### Understand the data

A path exploration creates an interactive Sankey diagram showing the most common next steps users take from a selected page (or the most common previous steps if you build the path backwards from an ending point).

Paths are shown up to 10 steps ("nodes"). For large or branching journeys, use path exploration to examine a specific section or decision point.

Path explorations are designed for a single path view at a time. You can apply a segment, but you cannot view multiple segments side-by-side in the same Sankey chart (for example, mobile vs desktop).

When you first create a path exploration, GA4 defaults to an "Event name" starting point. To build a page-based path exploration:

1. Select "Start again" (top right of the exploration output)
2. Choose whether you want a "Starting point" or an "Ending point" by selecting the corresponding "Drop or select node" option
3. Select "Page path and screen class" and choose a page for your start or end point
4. In the Sankey chart, click a page (a "node" on the chart) to expand the path step by step, up to 10 total steps

Setting "View unique nodes only" to "Yes" prevents the same page appearing multiple times across different steps in the chart. This gives a cleaner view of the overall journey and avoids inflating the apparent complexity of paths where users revisit pages.


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

- identify circular or repeated navigation patterns
- detect backwards steps within a multi-step service
- identify reference or guidance pages that users revisit frequently (for example, to evaluate whether the information should be integrated at the point of need instead)
- highlight potential drop-off points where users exit after repeated views

### Understand the data

The "Views per active user" metric divides the total number of views for a page by the number of active users who viewed it.

For example, if a page received 100 views from 70 active users, the result would be 1.43 views per active user.

Higher values may indicate that users are revisiting the page — either multiple times within a single session, or returning to it across different sessions over the selected date range. This can reflect:

- difficulty progressing
- repeated backwards steps
- users returning to reference material
- refreshes or repeated interactions

This exploration uses "Active users" instead of "Total users" because the "Views per active user" metric is calculated using active users. In GA4, "Active users" counts users who had an "engaged" session (one that lasted longer than 10 seconds, included a conversion event, or included at least 2 page views).

Interpret this metric in context. Compare pages against others within the same site or service rather than relying on a fixed threshold.

Adding the "Exits" metric allows you to identify pages that are both frequently revisited and common exit points.

The absolute number of exits is less informative than the proportion of views that result in an exit (exit rate). GA4 does not display exit rate directly, but you can calculate it by exporting the data:

1. Create the exploration using the variables and settings below.
2. Export the data as CSV.
3. Open the CSV in a spreadsheet.
4. Remove any rows above the column headers so that the first visible row contains the column headers.
5. Insert a new column titled "Exit rate".
6. In the "Exit rate" column, divide the "Exits" value by the "Views" value.
7. Format the result as a percentage.
8. Sort by "Exit rate" to identify pages with relatively high proportions of exits.

Pages with both high views per active user and high exit rates may indicate user difficulties that are worth investigating further.


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
- compare time spent on each page with exits, to identify behaviour patterns

### Understand the data

GA4 does not include a direct "time spent on page" metric.

Instead, use the "User engagement" metric, which measures the cumulative time (in seconds) that a page was actively in focus in the user's browser. This is an approximation — GA4 calculates engagement time from events rather than tracking focus continuously, so treat these figures as directional rather than precise.

To estimate average time spent per page view:

1. Create an exploration using the variables and settings below.
2. Export the data as CSV.
3. Open the CSV in a spreadsheet.
4. Remove any rows above the column headers so that the first visible row contains the column headers.
5. Insert a new column titled "Average time per view (seconds)".
6. In the "Average time per view (seconds)" column, divide the "User engagement" value by the "Views" value.

This produces an estimate of average engaged time per page view. Note that this figure averages across all views, including repeat views by the same user. A user who visits the same page three times contributes three views to the calculation.

Interpret this metric in context. Longer time spent may indicate:

- careful reading
- task completion
- difficulty progressing
- repeated visits

Shorter time spent may indicate:

- quick completion
- skimming
- immediate exits

To compare time spent with exit behaviour, in your spreadsheet:

1. Insert another column titled "Exit rate".
2. In the "Exit rate" column, divide the "Exits" value by the "Views" value.
3. Format as a percentage.
4. Compare your "Exit rate" and "Average time per view (seconds)" values to identify outliers.

Pages with both high average time per view and high exit rates may indicate user difficulties that are worth investigating further.

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
These explorations could help you to:

- benchmark current completion rates and average completion time, and compare these after content changes
- identify page-to-page transitions where drop-off rates are higher than normal
- compare completion rates and times across different user groups, such as:
  - mobile vs desktop
  - new vs returning users

### Understand the data
A funnel exploration can be used to measure how many users complete a defined multi-step journey, and how long it takes them.

Unlike a path exploration, which expands dynamically in a non-linear way, a funnel requires you to define each step in advance. You can add up to 10 steps. This makes it suitable for:

- measuring completion between a defined start and end page
- examining a small number of critical steps within a longer journey

It is not designed to map complex branching services in full.

The funnel will calculate:

- the proportion of users who move from the first defined step to the final step
- the average "Elapsed time" between those steps (when enabled)

When only a start and completion page are defined, "Elapsed time" represents the average time between first reaching the start page and reaching the completion page.

This value can be heavily influenced by users who leave and return over multiple days before completing. To better understand typical in-session behaviour, compare:

- new users
- returning users

Completion time for returning users may include long gaps between visits, while for new users it is more likely to reflect completion within a single visit.

The funnel is set to "closed" by default ("Make open funnel": off). This means only users who reach the first defined step are counted in the completion calculation. Users who arrive directly at a later step are excluded. This gives a more accurate picture of completion for users who attempt the full journey.


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

This exploration could help you to:

- estimate how many sessions, on average, it takes users who complete a journey to reach the final page
- assess whether content or structural changes reduce the need for users to return later
- compare whether session requirements differ depending on device category


### Understand the data

This method focuses only on users who reached the completion page. It does not reflect users who started the journey but failed to complete.

Create a segment that includes users who viewed the completion page, and use it with the "Sessions per active user" metric. This shows the average number of sessions for users who completed the journey.

A session begins when a user starts interacting with your site and ends after a period of inactivity (30 minutes by default, unless your GA4 property settings have been changed). If a user leaves and later returns, this creates a new session. As a result, users who take breaks before finishing will increase the average number of sessions.

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

This exploration could help you to:

- identify pages within a journey where users who did not complete are most frequently exiting
- monitor whether content changes influence exit behaviour at specific steps
- compare abandonment patterns by device category or by users associated with different referring domains


### Understand the data

Funnel and path explorations are limited to 10 defined steps. For longer or more complex services, a free-form exploration provides a more complete view across all pages.

This method focuses only on users who did not reach the completion page within the selected date range.

Users who return after the date range to complete will still be counted here as non-completing. Extending the date range can reduce this effect, but it does not remove it entirely.

An "Exit" is recorded when a session ends on a page. This does not necessarily mean the user has permanently abandoned the journey. Users who pause and return later will still generate exits in earlier sessions.

GA4 does not provide a built-in "exit rate" metric. You can estimate it with:

Exits ÷ Views

This produces the proportion of views that were the final interaction in a session.

To calculate exit rate:

1. Create an exploration using the variables and settings below.
2. Export the data to CSV.
3. Open the CSV in a spreadsheet.
4. Remove any rows above the column headers so that the first visible row contains the data labels.
5. Insert a new column titled "Exit rate".
6. In the "Exit rate" column, divide the "Exits" column by the "Views" column.
7. Format the result as a percentage.
8. Review pages that are part of the transaction journey and compare their relative exit rates.


High exit rates do not automatically indicate a problem. Interpretation should consider:

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

This exploration could help you to:

- identify steps in a journey that may be causing confusion or uncertainty for users
- identify steps in a journey where users may be reviewing or reconsidering previous answers


### Understand the data

This method identifies backward navigation by comparing:

- Page referrer (the page users came from)
- Page path and screen class (the page users arrived at)

Backward movement occurs when the destination page represents an earlier step in the journey than the referrer page.

The table will include:

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




## Do users change devices mid-journey to complete tasks?

### Potential insights

This exploration could help you to:

- compare the device distribution of new and returning users
- identify whether returning users are more likely to use a different device category than new users
- monitor whether design changes reduce differences between device categories over time


### Understand the data

This method compares device category for:

- new users - users whose first recorded visit falls within the selected date range
- returning users - users who visited before the date range and came back within it

The two counts are independent and will not add up to total users.

A difference in device distribution between new and returning users may suggest that some users begin a journey on one device and return on another. However, it could equally reflect that different types of users — with different device preferences — make up the new and returning user groups. This method cannot distinguish between the two.

When reviewing the chart, compare the proportion of each device category between new and returning users.

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

This exploration could help you to:

- identify which external links are most frequently clicked
- review whether some links receive little interaction
- compare whether external links are clicked more often than primary calls to action
- assess whether users are leaving the service to seek additional information


### Understand the data

This method analyses external link clicks recorded by GA4.

External link clicks are only recorded if automatic click tracking is enabled in your property's settings. If this tracking is enabled, GA4 records:

- the page where the click occurred
- the destination URL of the external link

Enabling nested rows groups external links under the page where they were clicked.

If no external link data appears:

1. Go to Admin.
2. Select Data collection and modification.
3. Select Data streams.
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
