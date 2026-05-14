# Content engagement

## Contents

- [Using these explorations](content-engagement?id=using-these-explorations)
- [How many users access this content?](content-engagement?id=how-many-users-access-this-content)
- [How do device types differ across sections or services?](content-engagement?id=how-do-device-types-differ-across-sections-or-services)
- [How does engagement differ across pages, sources, or devices?](content-engagement?id=how-does-engagement-differ-across-pages-sources-or-devices)
- [How many users scroll to the bottom of a page?](content-engagement?id=how-many-users-scroll-to-the-bottom-of-a-page)
- [How many users are downloading linked files?](content-engagement?id=how-many-users-are-downloading-linked-files)


## Using these explorations

For content designers, engagement metrics alone do not indicate content quality or success.

Users may spend longer on a page because they're carefully reading and completing a task, or because they're struggling to find information. Repeated views of a page may reflect users returning to useful reference material, or experiencing uncertainty and difficulty progressing.

However, when interpreted alongside user volumes and journey data, engagement analysis can help:

- identify high impact pages
- prioritise content reviews
- assess potential user impact of design changes
- highlight patterns that may be useful to explore further

Add dimensions and metrics into the Settings column in the order specified. Unless otherwise stated, leave all other settings at their default values.


## How many users access this content?

### Potential insights

These explorations can help you to:

- prioritise content for review, improvement, or clearer signposting
- assess potential impact before moving or restructuring content
- identify changes in demand over time, and across device types


### Understand the data

There are several simple ways to measure user volumes for a page or group of pages. The same variables can be used for each, with different visualisations and filters.

"Total users" represents the number of unique users who triggered any event on your site during the selected date range (including users whose sessions were brief or unengaged).

High user volumes may indicate:

- high demand
- strong discoverability
- mandatory navigation pathways

Lower volumes may indicate:

- niche content
- seasonal dips
- limited discoverability
- duplicated content

"Anomaly detection" in GA4 graphs will highlight statistically unusual data points. It's turned off here to keep the view simple, but can be enabled if you want GA4 to automatically flag unexpected spikes or drops.


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
| Show rows | 10 |
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


## How do device types differ across sections or services?

### Potential insights

These explorations can help you to:

- compare the breakdown of device types (desktop, mobile, tablet) across different sections of your site or service
- assess whether device distribution changes after a redesign
- ensure testing effort reflects the device categories most commonly used

### Understand the data

"Device category" breaks down desktop, mobile and tablet users. It can be helpful to compare devices used across:

- different sections of the same site
- different services within the same property
- different time periods (for example, before and after a change)

Devices used may vary depending on:

- task complexity
- referral sources
- user environment (such as office, home, public transport)
- content type

### Variables

| Field | Value |
|---|---|
| Dimensions | Device category |
| Metrics | Total users |
| Segments | (Create a new segment)<br>Type: User segment<br>Title: Section A<br>Include users when:<br>- Page path and screen class<br>- contains<br>- /section-a/<br><br>(Create a new segment)<br>Type: User segment<br>Title: Section B<br>Include users when:<br>- Page path and screen class<br>- contains<br>- /section-b/ |

### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Doughnut chart |
| Segment comparisons | Add only one comparison group at a time.<br><br>For example:<br>- Section A<br>- Section B |
| Breakdowns | Device category |
| Values | Total users |



## How does engagement differ across pages, sources, or devices?

### Potential insights

These explorations can help you to:

- compare engagement rate across device categories, referral sources, or landing pages
- evaluate whether different entry points are associated with higher or lower engagement
- evaluate whether changes to expectation-setting (such as page titles or signposting) affect engagement

### Understand the data

GA4's "Engagement rate" metric shows the percentage of sessions that met at least one of these conditions:

- the session lasted longer than 10 seconds
- the user viewed 2 or more pages
- the user completed a key event (a specific action marked as significant in your property settings, such as completing a form - not all properties will have these configured)

Engagement rate is calculated across a user's whole session, not per page, so it's best analysed at the property level rather than for individual pages.

One exception to this is the "Landing page" dimension, which tracks the page where users started their session. Since each session can only have one landing page, analysing the engagement rate by landing page can help assess how different entry points influence overall engagement.

Lower engagement rates may reflect users efficiently finding what they need, but could also indicate that users didn't see what they expected and bounced. Higher rates may reflect longer or more complex tasks, but could also indicate difficult and circular navigation.

Engagement rate should be considered alongside user volumes and journey analysis rather than used as a standalone indicator of quality.


### Variables

| Field | Value |
|---|---|
| Dimensions | Device category<br>Landing page + query string<br>Session source |
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
| Rows | Landing page + query string |
| Show rows | 100 |
| Nested rows | No |
| Values | Engagement rate<br>Total users |
| Cell type | Plain text |


### Settings: to see engagement by referral source and landing page

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Session source<br>Landing page + query string |
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

These explorations can help you to:

- identify if a significant proportion of users are not reaching the bottom of a guidance page, indicating the need to review the length (and options for breaking up content), formatting, relevance, and placement of calls to action
- monitor whether content restructuring changes scroll behaviour
- measure whether mobile or desktop users scroll further, and review content to ensure it’s effective on both device types


### Understand the data

When automatic scroll tracking is enabled, GA4 records a scroll event when a user reaches approximately 90% of the page depth.

The "Per cent scrolled" dimension shows either:

- 90 (user reached at least 90% of the page)
- blank (all users, regardless of scroll depth)

GA4 records the 90% scroll event once per page view. It does not record multiple scroll depth levels.

To estimate the proportion of users who reached near the bottom of a page:

1. Create the exploration using the variables and settings below.
2. Identify the number of "Total users" where "Per cent scrolled" equals 90.
3. Divide this by the "Total users" value where "Per cent scrolled" is blank (the total number of users who viewed the page).

This produces the proportion of users who reached at least 90% of the page depth.

Consider whether users not reaching 90% may reflect:

- finding the information they needed earlier on the page
- navigating via in-page links

Also consider very short pages where 90% scroll depth is reached almost immediately by most users, making high rates less informative.

If no scroll data appears:

1. Go to "Admin".
2. Select "Data collection and modification".
3. Select "Data streams".
4. Select your website stream.
5. Check that "Enhanced measurement" contains "Scrolls".

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

These explorations can help you to:

- include downloadable files in content reviews or audits
- assess whether downloadable content is heavily relied upon
- prioritise files for review, consolidation, or conversion to HTML where appropriate


### Understand the data

When automatic file download tracking is enabled, GA4 records a "file_download" event when a user clicks a link to a recognised file type.

Common tracked file extensions include:

- .csv
- .doc, .docx
- .mp3, .mp4
- .pdf
- .ppt, .pptx
- .rtf
- .txt
- .xls, .xlsx
- .zip

The metric "Total users" represents the number of unique users who clicked a link to a file during the selected date range.

This method records link clicks, not confirmed successful downloads. It also does not capture downloads triggered without a standard link click.

The "Link text" dimension captures the visible text of the download link. Links that use icons, images, or non-visible accessible labels may return blank or unexpected values.

If no download data appears:

1. Go to "Admin".
2. Select "Data collection and modification".
3. Select "Data streams".
4. Select your website stream.
5. Check that "Enhanced measurement" contains "File downloads".

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

