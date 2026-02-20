# User journeys and pain points

> The following sections describe how to build explorations that answer common content questions.
> 
> Unless otherwise stated, leave all other settings at their default values. Enter dimensions and metrics into the Tab settings column in the order specified.

By combining these explorations, you can build an understanding of:

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

For internal referrals, the full URL is shown, including the domain and any query string (for example, https://example.com/questions/fee?locale=en).

For external referrals, you may only see the top-level domain (for example, https://www.gov.uk). Many sites and browsers limit the referrer information passed, so the specific referring page is often unavailable.

An empty "Page referrer" value may indicate:

- direct traffic (for example, typing the URL or using a bookmark)
- referrer information blocked by browser or site policy
- a previously opened page being revisited without a recorded referrer (for example, if the user keeps the page open in an inactive tab, and later reopens that tab, the referrer is unknown)

Because "Page referrer" reflects the previous page for each page view, it does not always represent the original source of the visit. If a user arrives from an external site and then navigates through multiple pages, each page will record the previous internal page as its referrer.

The "Page path and screen class" dimension shows only the path portion of a URL (for example, /questions/fee).

When analysing external referrals, pair "Page referrer" with "Landing page + query string" rather than "Page path and screen class".

"Landing page + query string" identifies the first page visited in the session. If you instead use "Page path and screen class", later page views in the same visit may appear associated with the original external referrer, inflating counts for non-landing pages.

The "Nested rows" option groups secondary rows beneath their primary row, making it easier to see how landing pages relate to each referrer.

Nested rows are limited to 10 rows per parent item. For example, only the top 10 landing pages will be shown under each referrer.

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
| Filters | Dimension: Page referrer<br>Condition: does not contain<br>Expression: enter your site or service domain (for example, example.com)<br><br>Dimension: Page referrer<br>Condition: matches regex<br>Expression: ^.+$ (matches any non-empty referrer value)<br><br>To see external referrals for an individual page, also add:<br><br>Dimension: Landing page + query string<br>Condition: exactly matches<br>Expression: enter the full landing page URL including https:// and any query string |

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
| Filters | Dimension: Page referrer<br>Condition: contains<br>Expression: enter your site domain (for example, example.com)<br><br>Dimension: Page path and screen class<br>Condition: exactly matches<br>Expression: enter the page path of the target page (for example, /ask-for-help/new) |


## What referrals are coming from LLMs (large language models)?

### Potential insights

This exploration can help you to:

- identify content that users are discovering via LLM interfaces
- assess whether LLM-referred landing pages are clear and well signposted for first-time visitors
- compare behaviour of LLM-referred users with other external referral sources


### Understand the data

This exploration builds on the same referrer-based approach described in "Where are users coming from?", but limits results to known LLM domains.

Common LLM referral domains include:

- openai.com and chat.openai.com (ChatGPT)
- claude.ai (Anthropic)
- copilot.microsoft.com (Microsoft Copilot)
- gemini.google.com (Google Gemini)
- perplexity.ai
- poe.com
- mistral.ai
- qwen.ai
- kimi.com
- ernie.baidu.com
- deepseek.com
- grok.com and x.ai

Referrals from LLMs differ from many other external sources. Some LLM interfaces operate through mobile apps or embedded environments that do not reliably pass referrer information to the browser. As a result, this exploration will under-represent the true volume of LLM-influenced visits. It captures only visits where a referral can be identified.

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
| Filters | Dimension: Page referrer<br>Condition: matches regex<br>Expression: ^https?://([^/]+\.)?(openai\.com\|chatgpt\.com\|claude\.ai\|copilot\.microsoft\.com\|gemini\.google\.com\|perplexity\.ai\|poe\.com\|mistral\.ai\|qwen\.ai\|kimi\.com\|ernie\.baidu\.com\|deepseek\.com\|grok\.com\|x\.ai)(/|$)<br><br>To see referrals for an individual page, also add:<br><br>Dimension: Landing page + query string<br>Condition: exactly matches<br>Expression: enter the full landing page URL including https:// and any query string |



### What are the most common user paths through a site or multi-step journey?

#### Potential insights
These explorations could help you to:
- identify the top paths through a branching transactional service, to help prioritise effort
- measure whether content changes influence top paths
- identify drop-off points or looping behaviour
- identify users' 'top tasks' on a site


#### Understand the data
A 'path exploration' creates an interactive Sankey diagram that allows you to click on a specific page (represented as a 'node') to reveal the most common pages that followed (or those that came before, if you're tracking backwards from an end point). It's limited to 10 steps, so not sufficient to map out full user journeys in a large transactional service. Instead, focus on important sections, such as critical branches or steps currently being iterated.
Due to the higher visual complexity of a path exploration, you cannot add more than one segment at a time, so side-by-side segment comparisons (for example mobile vs desktop paths) are not possible.
When you first create a path exploration, you'll be presented with a not particularly useful 'Event name' view. You'll need to select 'Start again' to customise it.
To customise your path exploration (figure 8):
1. Select 'Start again', to the top right of the exploration output.
2. Select either 'STARTING POINT' or 'ENDING POINT', depending on whether you want to view user journeys from or up to a specific page path
3. Whichever you've chosen, select 'Page path and screen class' and choose a page
4. In the resulting Sankey chart, click on each page path to expand the chart to the next step, up to 10 total steps.


#### Variables

| Field | Value |
|---|---|
| Metrics | Total users |


#### Settings

| Field | Value |
|---|---|
| Technique | Path exploration |
| View unique nodes only | Yes |
| Values | Total users |


### Are users repeatedly returning to the same page?

#### Potential insights
These explorations could help you to:
- identify navigation issues, circular or 'ping-pong' journeys, where users may be forced to return to the same page repeatedly
- identify where users in a linear or branching service are struggling to progress, taking repeated backwards steps
- build a case to break up guidance or reference material that users are forced to return to repeatedly, instead displaying it at the point it's most needed
- find pages where users may be abandoning a service in frustration, having repeatedly returned to the same page before exiting


#### Understand the data
The 'Views per active user' metric divides the total number of views a whole property or individual page received by the total number of active users. If a page received 100 views from 70 users, each user viewed that page on average 1.43 times. Research suggests that anything over 1.4 views per active user indicates a potential navigation problem worth exploring.
By adding 'Exits' data, you can identify pages with high views per user that are also common exit points from the site or service. If these pages aren't where you'd expect the user to exit, it could suggest users giving up on searching for information after going round in circles.
Sort the exploration table by maximum 'Views per active user' or 'Exits' to identify possible problem pages. Note though that the absolute number of exits alone isn't always that useful. What's more important is the exit rate (the percentage of page views that were exits). You can find this by exporting the data and adding a simple calculation in a new column:
1. Create an exploration using the variables and settings below.
2. Export the data to CSV (see Exporting data ).
3. Import the CSV into an Excel spreadsheet, selecting 'comma' as the delimiter.
4. Remove the top 6 rows (the exploration information which precedes the column headers).
5. Insert a new column to the right of 'Exits', and title it 'Exit rate'.
6. In this 'Exit rate' column, divide the values in 'Exits' by 'Views', and format as percentage.
7. Sort the table by 'Exit rate', largest to smallest.
8. Identify pages with the highest exit rates that also have above-average 'Views per active user' values. These pages may be frustrating dead-ends.


#### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class |
| Metrics | Active users<br>Views<br>Views per active user<br>Exits |


#### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class |
| Show rows | 100 |
| Nested rows | No |
| Values | Active users<br>Views<br>Views per active user<br>Exits |
| Cell type | Bar chart OR Plain text (it's a minor visual difference) |
| Filters | To see an individual page rather than a whole site or service, add the following:<br>Page path and screen class<br>- Conditions: exactly matches<br>- Expression: enter the path of the individual page (such as /questions/fee), omitting the domain and any query string at the end |


### How long are users spending on each page?

#### Potential insights
These explorations could help you to:
- identify pages that are taking users longer to understand or interact with than expected
- measure whether content formatting or language changes reduce the average time spent on a page, demonstrating content design reducing the so-called 'time tax' on users
- compare time spent on each page with exit rates, to spot pages that may be confusing dead ends where users eventually give up
- identify pages where much less time is spent on average than is likely to be necessary (for instance where content is lengthy or complex), indicating the content may be better broken up or reformatted


#### Understand the data
Unlike Universal Analytics (UA), GA4 does not have a simple 'Time spent on page' metric. The accuracy of time spent data has been improved, but you now need to take a few extra manual steps to calculate it. To do this, you'll need to divide the 'User engagement' metric - which displays the total cumulative time spent on a page - by the 'Views' metric. This will give you the average time spent per page view.
1. Create an exploration using the variables and settings below.
2. Export the data to CSV (see Exporting data ) .
3. Import the CSV into an Excel spreadsheet, selecting 'comma' as the delimiter.
4. The 'User engagement' values will automatically be converted from long-form days and hours format (such as '35d 03h') to total seconds.
5. Remove the top 6 rows (the exploration information which precedes the column headers).
6. Add a new column and title it 'Average time spent (secs)'.
7. In this 'Average time spent (secs)' column, divide 'User engagement' by 'Views'.
8. Sort the table by your new 'Average time spent (secs)' column, largest to smallest.
9. To see if pages with above-average time spent also have higher exit rates, add another new column and title it 'Exit rate'.
10. In this 'Exit rate' column, divide 'Exits' values by 'Views', and format as percentage.
11. Compare high exit rates with the average time spent on the page, looking for outliers to investigate.


#### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class |
| Metrics | User engagement<br>Views<br>Exits |


#### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class |
| Show rows | 100 |
| Nested rows | No |
| Values | User engagement<br>Views<br>Exits |
| Cell type | Bar chart OR Plain text (it's a minor visual difference) |
| Filters | To see an individual page rather than a whole site or service, add the following:<br>Page path and screen class<br>- Conditions: exactly matches<br>- Expression: enter the page path, which is everything after your domain, minus any query strings (for example, the page path for https://helpwithcourtfees.service.gov.uk/questions/fee?locale=en is /questions/fee) |


### What percentage of users are completing a multi-step journey, and how long is it taking them?

#### Potential insights
These explorations could help you to:
- benchmark current completion rates and durations, and then identify if content design changes improve these values
- identify specific page-to-page transitions where drop-off rates are higher than normal
- understand which circumstances are leading to the highest or speediest completion rates – for example, if users referred from GOV.UK or an internal guidance page are more likely to complete, or if completion is more common on desktop than mobile


#### Understand the data
While user 'funnels' are usually associated with e-commerce, a 'funnel exploration' can be used to explore average completions and durations for any multi-step journey. Unlike the more fluid and non-linear 'path exploration' view, which expands as you click on a page, a funnel exploration requires you to define in advance each page in a multi-step journey.
A maximum of 10 steps (individual URLs in a multi-step journey) can be added. This means a funnel exploration is not sufficient for fully mapping out long or branching services. Instead, create steps for just your start and end pages (figure 9), or a small number of specific steps in between.
User 'segments' are particularly useful in a funnel exploration – they enable you to identify whether different user groups have different completion rates and durations. For instance, you can compare users referred from GOV.UK with users who were not, getting a broad indication of whether mainstream content might be improving or speeding up completion rates. Alternatively, you can see whether completion is more likely on mobile or desktop. You can then revisit these completion rates after relevant design changes.
The 'Elapsed time' value in a funnel exploration shows you the average time elapsed between your funnel steps. With the exploration settings below, it will show you the average time to complete the entire transaction. This will be heavily distorted by users who return over many days to gradually work their way through a long transaction. To better estimate how long the transaction typically takes in a single session, you can segment the exploration by new and returning users. The 'Elapsed time' for new users who complete an entire transaction at once will usually be measured in minutes, while for returning users can be days.

#### Variables

| Field | Value |
|---|---|
| Segments | 'All Users' (readymade segment)<br>'Mobile traffic' (readymade segment)<br>'Web traffic' (readymade segment)<br>'Users referred from GOV.UK' (new segment):<br>- I nclude users when: Page referrer contains https://www.gov.uk/ at any point in time<br>'Users NOT referred from GOV.UK' (new segment):<br>- Exclude users when: Page referrer contains https://www.gov.uk/ at any point in time<br>'New users' (new segment):<br>- Include users when: New/returning exactly matches (=) new NOT at any point in time<br>'Returning users' (new segment):<br>- Include users when: New/returning exactly matches (=) returning NOT at any point in time |


#### Settings

| Field | Value |
|---|---|
| Technique | Funnel exploration |
| Visualisation | Standard funnel |
| Make open funnel | Off |
| Segment comparisons | All Users<br>To compare users referred from GOV.UK or not, add the segments you created:<br>- Users referred from GOV.UK<br>- Users NOT referred from GOV.UK<br>To compare users on mobile vs desktop, instead add the pre-built segments:<br>- Mobile traffic<br>- Web traffic<br>To compare new vs returning users, instead add the segments you created:<br>- New users<br>- Returning users |
| Steps | Step 1:<br>- Rename the step 'Start page'<br>- Condition: Page path and screen class<br>- Filter: exactly matches (=)<br>- Enter the path of the first step in a transaction (note: not the GOV.UK 'start' button page, but the first page on your own service domain or subdomain)<br>…'is indirectly followed by'…<br>Step 2:<br>- Rename the step 'Completion page'<br>- Condition: Page path and screen class<br>- Filter: exactly matches (=)<br>- Enter the path of the final step in a transaction, like a completion or summary page |
| Show elapsed time | On |


### How many sessions on average do users need to complete a multi-step journey?

#### Potential insights
This exploration could help you to:
- measure what proportion of users are able to complete a transaction in a single session, and if this is improved after a significant content design change
- identify if any circumstances (such as referral from GOV.UK) or devices (mobile vs desktop) make it more likely that users will complete in fewer sessions


#### Understand the data
You can learn more about users who completed a transaction by creating a segment that only includes users who viewed the final page. For this segment, you can then compare the number of total sessions with the number of total users. You can use this to calculate how many sessions, on average, it takes users to complete the transaction. A session "initiates when a user… views a page" and "ends (times out) after 30 minutes of user inactivity" (source: [GA4] Session ).
GA4 does not have an 'Average sessions per user' metric, but this is easy to calculate by dividing the number of sessions by the number of total users:
1. Create an exploration using the variables and settings below.
2. Export the data to CSV (see Exporting data ).
3. Import the CSV into an Excel spreadsheet, selecting 'comma' as the delimiter.
4. Remove the top 6 rows (the exploration information which precedes the column headers).
5. Add a new column titled 'Average sessions per user'.
6. In this 'Average views per user' column, divide 'Sessions' column by 'Total users'.
7. Sort the table by 'Average sessions per user', largest to smallest.


#### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class<br>Device category |
| Metrics | Sessions<br>Total users |
| Segments | 'Completion page (all)' (new segment):<br>- Include users when: Page path and screen class exactly matches (=) enter your completion page path, such as /confirmation NOT at any point in time<br>'Completion page (via GOV.UK)' (new segment):<br>- Include users when: Page path and screen class exactly matches (=) enter your completion page path, such as /confirmation NOT at any point in time AND Page referrer contains https://www.gov.uk at any point in time<br>'Completion page (NOT via GOV.UK)' (new segment):<br>- Include users when: Page path and screen class exactly matches (=) enter your completion page path, such as /confirmation NOT at any point in time AND Page referrer does not contain https://www.gov.uk at any point in time |


#### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Segment comparisons | Completion page (all)<br>Completion page (via GOV.UK)<br>Completion page (NOT via GOV.UK) |
| Rows | Device category |
| Show rows | 10 |
| Nested rows | No |
| Values | Sessions<br>Total users |
| Cell type | Bar chart OR Plain text (it's a minor visual difference) |


### Where are non-completing users abandoning a multi-step journey?

#### Potential insights
This exploration could help you to:
- identify points in a multi-step journey where new users are dropping off and not completing (before the end of your specified date range)
- monitor the influence of content changes on abandonment rates at specific points in a multi-step journey
- understand if factors like device type or referral from GOV.UK influence abandonment rates, to inform further investigation


#### Understand the data
While funnel and path explorations can be useful to spot drop-off points through a user journey, they're limited to 10 steps and so insufficient for large journeys. This free-form exploration will instead provide a breakdown of abandonment across every page.
With large transactional services, it's common for users to complete the transaction over multiple sessions. These users are not 'abandoning' the service, but simply pausing until later, yet the last page in each session will still be recorded by GA4 as an 'exit'. To avoid skewing the figures as much as possible, this exploration focuses solely on the segment of users who did not complete the transaction within the specified date range. This isn't perfect, since some of these users will return in the future to complete, but the impact is reduced the longer you make the date range.
There is no 'exit rate' metric in GA4, but this is straightforward to estimate by dividing 'Exits' by 'Views':
1. Create an exploration using the variables and settings below.
2. Export the data to CSV (see Exporting data )
3. Import the CSV into an Excel spreadsheet, selecting 'comma' as the delimiter.
4. Remove the top 6 rows (the exploration information which precedes the column headers).
5. Remove the far right 3 columns each titled 'Totals'.
6. Insert a new column to the right of 'Exits', and title it 'Exit rate'.
7. In this 'Exit rate' column, divide the 'Exits' by 'Views', and format as percentage.
8. Sort the table by 'Exit rate', largest to smallest.
9. Work your way down the list of URLs, identifying those that form part of the transaction and have the highest 'Exit rate' percentages.


#### Variables

| Field | Value |
|---|---|
| Segments | 'All users who have NOT completed' (new segment):<br>- Exclude from segment permanently<br>- Exclude users when: Page path and screen class contains enter the page path of the completion page for your service, such as /confirmation at any point in time<br>'GOV.UK-referred users who have NOT completed' (new segment):<br>- Include users when: Page referrer contains https://www.gov.uk/ at any point in time<br>- Exclude from segment permanently<br>- Exclude users when: Page path and screen class contains enter the page path of the completion page for your service, such as /confirmation at any point in time<br>'Mobile users who have NOT completed' (new segment):<br>- Include users when: Device category exactly matches mobile NOT at any point in time<br>- Exclude from segment permanently<br>- Exclude users when: Page path and screen class contains enter the page path of the completion page for your service, such as /confirmation at any point in time |


#### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Segment comparisons | All users who have NOT completed<br>OR<br>GOV.UK-referred users who have NOT completed<br>OR<br>Mobile users who have NOT completed |
| Rows | Page path and screen class |
| Show rows | 100 |
| Nested rows | No |
| Values | Total users<br>Views<br>Exits |
| Cell type | Plain text |


### Which pages in a multi-step journey are users commonly moving backwards to?

#### Potential insights
This exploration could help you to:
- identify pages in a multi-step journey that are causing confusion or uncertainty for users, feel like dead-ends, or present new information that prompts reconsideration of previous answers


#### Understand the data
This exploration is similar to Are users repeatedly returning to the same page? , but will help you to hone in on backwards navigation in a multi-step journey.
The exploration output will present you with 4 columns, from left to right:
- Page path and screen class - the page users arrived at
- Page referrer - the page users came from
- Total users - the number of users who navigated from the 'Page referrer' to the 'Page path and screen class'
- Views per active user - the average number of times the 'Page path and screen class' was viewed by each user during your date range. A high value (typically over 1.4) suggests that users are returning to the page more than normal. To avoid this being skewed higher by users who returned during your date range to work through the service in multiple sessions, this exploration filters to new users only.

You'll need to do a little sifting through the data to spot problem areas:
1. Sort the table by 'Views per active user', high to low.
2. Start to work your way down the rows, comparing the 'Page path and screen class' with the 'Page referrer'. You're looking for instances where the 'Page path and screen class' is the step immediately prior to the 'Page referrer'.
3. You'll notice that these are often the same page, which can be caused by users refreshing the page. Ignore these instances.
4. If you spot a 'Page path and screen class' that's a backwards step from the 'Page referrer', look at: 'Views per active user' to gauge how often this is happening compared with other backwards steps 'Total users' to see how many users were affected in your date range


#### Variables

| Field | Value |
|---|---|
| Dimensions | New/Established<br>Page path and screen class<br>Page referrer |
| Metrics | Total users<br>Views per active user |


#### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class<br>Page referrer |
| Show rows | 100 |
| Nested rows | No |
| Values | Total users<br>Views per active user |
| Cell type | Plain text |
| Filters | New/Established<br>- Conditions: exactly matches<br>- Expression: new<br>Page referrer<br>- Conditions: contains<br>- Expression: enter your site domain, such as helpwithcourtfees.service.gov.uk, to filter to only internal page navigation<br>If your 'Page referrer' data is noisy with lots of little-used customised URLs (for example, containing query strings with tracking codes), try adding:<br>Total users<br>- Conditions: ><br>- Expression: 10 |


### Do users change devices mid-journey to complete tasks?

#### Potential insights
These explorations could help you to:
- identify if returning users have switched device type (desktop, mobile, tablet), indicating this may be necessary to overcome usability barriers or more easily complete a task
- quantify whether design changes have successfully lowered usability barriers for specific device types


#### Understand the data
To understand if users are switching device once they've seen your site or service, you can compare the device breakdown for 'new users' vs 'returning users'. Often users are initially referred from mobile-first GOV.UK, then realise that a larger screen is required to complete a service, and return on desktop.
Your date range will capture all new users, but only those who returned within the same date range. This will cause the true number of returning users to be slightly under-represented. For a more accurate picture, always select the longest possible date range for this exploration.
Mouse over the chart segments to see the underlying data.

#### Variables

| Field | Value |
|---|---|
| Dimensions | Device category |
| Metrics | New users<br>Returning users |


#### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Doughnut chart |
| Breakdowns | Device category |
| Values | New users<br>OR<br>Returning users |


### What external links are most clicked?

#### Potential insights
These explorations could help you to:
- identify which external resources appear most valuable to users
- identify underperforming links which may need to be removed or signposted more effectively
- measure whether external links are clicked more than primary calls to action, which may indicate that external information needs more effective integration


#### Understand the data
Enabling 'nested rows' is particularly useful for this exploration, as it will group all clicked external links by the page where they're found.
If no external link data appears to be available, even for a broad date range:
1. Within the property, visit Admin > Data collection and modification > Data streams
2. Select 'Web'
3. In the 'Web stream details' overlay, check that 'Enhanced measurement' is enabled
4. If 'Enhanced measurement' is enabled, look at the 'Measuring' list to see if 'Outbound clicks' is enabled
5. If either of the above is not enabled, contact the property admin


#### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class<br>Link URL |
| Metrics | Total users |


#### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class<br>Link URL |
| Show rows | 100 |
| Nested rows | Yes |
| Values | Total users |
