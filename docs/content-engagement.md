# Content engagement

> Each section below outlines how to build an exploration that answers a specific content question.
> 
> Add dimensions and metrics into the Settings column in the order specified. Unless otherwise stated, leave all other settings at their default values.

Engagement metrics do not, by themselves, indicate content quality or success.

Users may spend longer on a page because they are carefully reading and completing a task, or because they are struggling to find the information they need. Similarly, repeated views of a page may reflect either users finding the content useful or experiencing uncertainty.

When interpreted alongside user volumes and journey data, engagement analysis can help:

- identify high impact pages
- prioritise content reviews
- assess potential user impact of design changes
- highlight patterns that may be useful to explore further

These measures should be interpreted in context rather than treated as standalone indicators of performance.


## How many users access this content?

### Potential insights

These explorations could help you to:

- prioritise content for review or improvement
- identify low-traffic pages that may be difficult to discover
- assess potential impact before moving or restructuring content
- identify changes in demand over time
- compare usage patterns across device categories


### Understand the data

There are several simple ways to measure how many users for a page or group of pages. The same variables can be used with different visualisations and filters.

The recommended metric is "Total users". This represents the number of users who were active on your site or app during the selected date range.

When analysing content usage, consistency of metrics is more important than absolute precision. Relative differences between pages or over time are often more informative than exact counts.

Interpret page usage in context. High volumes may indicate:

- high demand
- strong discoverability
- required navigation pathways

Lower volumes may indicate:

- niche content
- seasonal demand
- limited discoverability


### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class<br>Device category |
| Metrics | Total users |


### Settings: to see every page on a property

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class |
| Show rows | 100 |
| Columns | Device category (optional) |
| Values | Total users |
| Cell type | Plain text |


### Settings: to see a specific page

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class |
| Columns | Device category (optional) |
| Values | Total users |
| Cell type | Plain text |
| Filters | Dimension: Page path and screen class<br>Condition: exactly matches (=)<br>Expression: enter the page path (everything after your domain, excluding query strings) |


### Settings: to see all pages as a line chart over time

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Line chart |
| Granularity | Hour OR Day OR Week (depending on your date range) |
| Values | Total users |
| Anomaly detection | Off |


### Settings: to see a specific page as a line chart over time

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Line chart |
| Granularity | Hour OR Day OR Week (depending on your date range) |
| Breakdowns | Page path and screen class |
| Values | Total users |
| Anomaly detection | Off |
| Filters | Dimension: Page path and screen class<br>Condition: exactly matches (=)<br>Expression: enter the page path (everything after your domain, excluding query strings) |


## How does device usage differ across sections or services?

### Potential insights

These explorations could help you to:

- compare the breakdown of device types (desktop, mobile, tablet) across different sections of your site or service
- assess whether device distribution changes after a redesign
- ensure testing effort reflects the device categories most commonly used
- identify whether certain types of content are more frequently accessed on specific devices

### Understand the data

Device breakdown provides useful context, but comparisons are often more informative than standalone views.

You can compare:

- different sections of the same site
- different services within the same property
- different time periods (for example, before and after a change)

Device distribution may vary depending on:

- task complexity
- referral sources
- user environment
- content type

Interpret differences cautiously. Device mix does not directly indicate user characteristics and may reflect contextual factors such as referral source or time of use.

### Variables

| Field | Value |
|---|---|
| Dimensions | Device category |
| Metrics | Total users |
| Segments | Type: User segment<br>Title: Section A<br>Include users when:<br>- Page path and screen class<br>- contains<br>- /section-a/<br><br>Type: User segment<br>Title: Section B<br>Include users when:<br>- Page path and screen class<br>- contains<br>- /section-b/ |

### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Doughnut chart |
| Segment comparisons | Add only one comparison group at a time.<br><br>For example:<br>- Section A<br>- Section B |
| Breakdowns | Device category |
| Values | Total users |
| Filters | Optional:<br><br>Dimension: Page path and screen class<br>Condition: contains OR exactly matches (=)<br>Expression: enter the section or page path you want to analyse |



## How does engagement differ across pages, sources, or devices?

### Potential insights

These explorations could help you to:

- compare engagement rate across device categories, referral sources, or landing pages
- assess whether different entry points are associated with higher or lower engagement
- evaluate whether changes to page titles or navigation labels that may affect user expectations are associated with changes in engagement

### Understand the data

GA4 reports "Engagement rate" instead of the traditional "bounce rate".

Engagement rate shows the percentage of sessions that met at least one of these conditions:

- the visit lasted longer than 10 seconds
- the user viewed 2 or more pages
- the user completed a key event (if one has been configured)

In simple terms, engagement rate estimates how many visits involved some meaningful interaction.

When you break this down by a dimension (for example, Landing page or Device category), the engagement rate shows the percentage of visits in that group that were engaged.

Engagement rate does not measure how engaging a single page is on its own. A session may include several pages, and engagement is based on the whole session.

Sort by Total users (highest to lowest) to focus on the most significant sources. Smaller volumes may show extreme engagement rates that are not representative.

Interpret engagement rate in context. Lower values may reflect:

- short informational visits
- users finding what they need quickly
- misaligned expectations

Higher values may reflect:

- longer or more complex tasks
- deeper exploration
- repeated navigation

Engagement rate should be considered alongside user volumes and journey analysis rather than used as a standalone indicator of quality.


### Variables

| Field | Value |
|---|---|
| Dimensions | Device category<br>Landing page<br>Session source |
| Metrics | Engagement rate<br>Total users |


### Settings: to see engagement by referral source

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Session source |
| Show rows | 100 |
| Nested rows | No |
| Values | Engagement rate<br>Total users |
| Cell type | Plain text |


### Settings: to see engagement by landing page

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Landing page |
| Show rows | 100 |
| Nested rows | No |
| Values | Engagement rate<br>Total users |
| Cell type | Plain text |


### Settings: to see engagement by referral source and landing page

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Session source<br>Landing page |
| Show rows | 100 |
| Nested rows | Yes |
| Values | Engagement rate<br>Total users |
| Cell type | Plain text |


### Settings: to see engagement by device type

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Device category |
| Show rows | 100 |
| Nested rows | No |
| Values | Engagement rate<br>Total users |
| Cell type | Plain text |



## How many users scroll to the bottom of a page?

### Potential insights

These explorations could help you to:

- estimate the proportion of users who reach the bottom of a page
- compare scroll behaviour between device types
- assess whether longer pages are likely to be fully viewed
- monitor whether content restructuring changes scroll behaviour


### Understand the data

When automatic scroll tracking is enabled, GA4 records a scroll event when a user reaches approximately 90% of the page depth.

The "Per cent scrolled" dimension typically shows:

- 90 (user reached at least 90% of the page)
- blank (all users, regardless of scroll depth)

GA4 records the 90% scroll event once per page view. It does not record multiple scroll depth levels.

To estimate the proportion of users who reached near the bottom of a page:

1. Create the exploration using the variables and settings below.
2. Identify the number of Total users where "Per cent scrolled" equals 90.
3. Divide this by the Total users value where "Per cent scrolled" is blank (the total number of users who viewed the page).

This produces the proportion of users who reached at least 90% of the page.

Interpret scroll depth cautiously. Not reaching 90% may reflect:

- users finding the information they needed earlier on the page
- short pages where 90% is reached quickly
- users leaving intentionally
- users navigating via in-page links

If no scroll data appears:

1. Go to Admin.
2. Select Data collection and modification.
3. Select Data streams.
4. Select your website stream.
5. Check that 'Enhanced measurement' contains 'Scrolls'.

If scroll tracking is not enabled, contact the property administrator.


### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class<br>Per cent scrolled |
| Metrics | Total users |
| Segments | Mobile traffic<br>Web traffic |


### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Segment comparisons | Add one comparison group at a time for clarity:<br><br>Mobile traffic<br>OR<br>Web traffic |
| Rows | Page path and screen class<br>Per cent scrolled |
| Show rows | 100 |
| Nested rows | Yes |
| Values | Total users |
| Cell type | Plain text |
| Filters | To filter to an individual page:<br><br>Dimension: Page path and screen class<br>Condition: exactly matches (=)<br>Expression: enter the page path (everything after your domain, excluding query strings) |


## How many users are downloading linked files?

### Potential insights

These explorations could help you to:

- include downloadable files in content reviews or audits
- identify which files receive the most interaction
- assess whether downloadable content is heavily relied upon
- prioritise files for review, consolidation, or conversion to HTML where appropriate


### Understand the data

When automatic file download tracking is enabled, GA4 records a "file_download" event when a user clicks a link to a recognised file type.

Common tracked file extensions include:

- .pdf
- .xlsx
- .doc
- .txt
- .rtf
- .csv
- .ppt
- .zip

The metric "Total users" represents the number of unique users who clicked a link to a file during the selected date range.

This method records link clicks, not confirmed successful downloads. It also does not capture downloads triggered without a standard link click.

If no download data appears:

1. Go to Admin.
2. Select Data collection and modification.
3. Select Data streams.
4. Select your website stream.
5. Check that 'Enhanced measurement' contains 'File downloads'.

If file download tracking is not enabled, contact the property administrator.


### Variables

| Field | Value |
|---|---|
| Dimensions | Event name<br>Link text<br>Link URL<br>Page path and screen class |
| Metrics | Total users |


### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class<br>Link text<br>Link URL |
| Show rows | 100 |
| Nested rows | Yes |
| Values | Total users |
| Cell type | Plain text |
| Filters | Dimension: Event name<br>Condition: exactly matches (=)<br>Expression: file_download<br><br>To filter to an individual page:<br><br>Dimension: Page path and screen class<br>Condition: contains OR exactly matches (=)<br>Expression: enter the page path (everything after your domain, excluding query strings) |

---

<small>GA4 for content designers by Alex Robertson is licensed under <a href="https://creativecommons.org/licenses/by/4.0/">CC BY 4.0</a>.</small>

