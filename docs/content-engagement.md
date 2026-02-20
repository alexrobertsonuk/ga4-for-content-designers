## Content engagement

> The following sections offer recommendations for how to build explorations that answer common content questions. Think of these as recipes to follow or adapt as you need.
> 
> Unless otherwise stated, leave all options at their default setting. Be careful to enter dimensions and metrics into the Settings column in the order in which they're specified.


'Engagement' measures are not, by themselves, a typical success metric for content designers. Our users often have no choice but to use and engage with our content, and 'engagement' could often indicate users struggling through a site to find something against a stressful deadline.
In context, though, user volumes and engagement analysis can give us a more rounded view, and inform prioritisation and risk assessments based on the volume of potential users impacted.

### How many users access this content?

#### Potential insights
These explorations could help you to:
- prioritise content for improvement
- identify hard-to-discover content
- flag content to consider retiring
- assess the level of risk in moving or changing content
- spot trends in demand for content, for example around policy changes, news coverage or seasonality


#### Understand the data
There are a few simple ways you can find the estimated number of unique users for a page or group of pages. You'll use the same variables for each, but different settings.
The recommended metric to use is 'Total users', which Google defines as "The number of unique users who triggered any event in the specified date range" (source: [GA4] Understand user metrics ). What's most important, though, is simply to be consistent in your choice of metrics. You're looking for design insights, not reporting management information, so absolute numbers are less important than relative differences.

#### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class<br>Device category |
| Metrics | Total users |


#### Settings: to see every page on a property

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class |
| Show rows | 100 |
| Columns | Device category (if you'd like to see the breakdown by device) |
| Values | Total users |
| Cell type | Bar chart OR Plain text (it's a minor visual difference) |


#### Settings: to see a specific page

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class |
| Columns | Device category (if you'd like to see the breakdown by device) |
| Values | Total users |
| Cell type | Plain text |
| Filters | Page path and screen class<br>- Conditions: exactly matches<br>- Expression: enter the page path, which is everything after your domain, minus any query strings (for example, the page path for https://helpwithcourtfees.service.gov.uk/questions/fee?locale=en is /questions/fee) |


#### Settings: to see all pages as a line chart over time

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Line chart |
| Granularity | Hour OR Day OR Week (depending on your date range) |
| Values | Total users |
| Anomaly detection | Off |


#### Settings: to see a specific page as a line chart over time

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Line chart |
| Granularity | Hour OR Day OR Week (depending on your date range) |
| Breakdowns | Page path and screen class |
| Values | Total users |
| Anomaly detection | Off |
| Filters | Page path and screen class<br>- Conditions: exactly matches<br>- Expression: enter the page path, which is everything after your domain, minus any query strings (for example, the page path for https://helpwithcourtfees.service.gov.uk/questions/fee?locale=en is /questions/fee) |


### How do user device types compare with the GOV.UK benchmark?

#### Potential insights
These explorations could help you to:
- identify if the breakdown of device types (desktop, mobile, tablet) for your users deviates from the norm
- ensure that design effort and testing reflects the real world device breakdown


#### Understand the data
In isolation, your percentage of users by device type (desktop, mobile, tablet) is useful data. But it's much more instructive to compare with a benchmark like GOV.UK - with tens of millions of monthly users - to spot deviations from the norm.
Choose a long date range (a month to a year), and compare the breakdown for your property with the breakdown for GOV.UK.
If your property has above average:
- desktop users - it may indicate that users are in office-based environments or need larger screens to complete tasks
- mobile users - it may indicate that users are younger than average, more often referred from social media, or not seeking to complete a complex task

Mouse over the chart segments to see the underlying data.

#### Variables

| Field | Value |
|---|---|
| Dimensions | Device category |
| Metrics | Total users |


#### Settings: to see a doughnut chart of total users by device (compare your property with GOV.UK)

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Doughnut chart |
| Breakdowns | Device category |
| Values | Total users |


### What factors influence user engagement with this site or service?

#### Potential insights
These explorations could help you to:
- identify factors that influence user engagement, such as device type, referral source or landing page
- identify where users may need the context to be set more effectively, either on a landing page or by the external referrer
- assess whether metadata changes (such as page titles and descriptions in search results) increase engagement, indicating improved setting of user expectations


#### Understand the data
GA4 no longer has a traditional 'bounce rate' metric. Instead it focuses on 'engagement rate', which measures the percentage of sessions that meet GA4's engagement criteria.
A session is considered 'engaged' if it meets at least one of the following conditions:
1. Lasts longer than 10 seconds
2. Has 2 or more page views
3. Includes a 'key event' (a high value user action, set by an admin, which isn't configured by default in most properties)

Unlike traditional bounce rate, engagement rate is calculated at the session level, not per page. The engagement rate shown for a page reflects the percentage of engaged sessions that included that page - not how engaging that page was on its own. A low-engagement page may lower the overall session's engagement rate, but the metric doesn't isolate engagement for that page alone. Because engagement rate is session-based, it's best analysed at the property level rather than for individual pages.
One exception to this is the 'Landing page' dimension, which tracks the page where users started their session. Since each session can only have one landing page, analysing the engagement rate by landing page can help assess how different entry points influence overall engagement.
Low engagement might indicate:
- for search engine referrals - metadata (page title, description) isn't setting the right expectations
- for mobile users - content needs usability improvements for smaller screens
- for specific landing pages - the page needs to set the context more effectively, or make it easier for users to quickly find the correct starting point
- for specific referrers - context and expectations need setting more effectively by the referrer


#### Variables

| Field | Value |
|---|---|
| Dimensions | Device category<br>Landing page<br>Page referrer<br>Session source |
| Metrics | Engagement rate<br>Total users |


#### Settings: to see engagement by referral source

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Session source |
| Show rows | 100 |
| Nested rows | No |
| Values | Engagement rate<br>Total users |
| Cell type | Bar chart OR Plain text (it's a minor visual difference) |


#### Settings: to see engagement by landing page

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Landing page |
| Show rows | 100 |
| Nested rows | No |
| Values | Engagement rate<br>Total users |
| Cell type | Bar chart OR Plain text (it's a minor visual difference) |


#### Settings: to see engagement by referral source AND landing page

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page referrer<br>Landing page |
| Show rows | 100 |
| Nested rows | Yes |
| Values | Engagement rate<br>Total users |
| Cell type | Bar chart OR Plain text (it's a minor visual difference) |
| Filters | Page referrer<br>- Conditions: does not contain<br>- Expression: enter your property domain, such as helpwithcourtfees.service.gov.uk<br>Page referrer<br>- Conditions: matches regex<br>- Expression: ^.+$ (this matches any text that contains at least one character, filtering out empty page referrer values that represent unknown referral sources)<br>Landing page<br>- Conditions: matches regex<br>- Expression: ^.+$ (this matches any text that contains at least one character, filtering out empty landing page values) |


#### Settings: to see engagement by device type

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Device category |
| Show rows | 100 |
| Nested rows | No |
| Values | Engagement rate<br>Total users |
| Cell type | Bar chart OR Plain text (it's a minor visual difference) |


### How many users scroll to the bottom of guidance pages?

#### Potential insights
These explorations could help you to:
- identify if a significant proportion of users are not reaching the bottom of a guidance page, indicating the need to review the length (and options for breaking up content), formatting, relevance, and placement of calls to action
- measure whether mobile or desktop users scroll further, and review content to ensure it's effective on both device types


#### Understand the data
The default 'Per cent scrolled' dimension only has two possible values: 90 or blank. 90 indicates that users scrolled down 90% or more of the page depth, while blank simply includes all users. If you pair the 'Per cent scrolled' dimension with the 'Total users' metric, a 'Per cent scrolled' value of 90 will correspond with just the number of users who scrolled to the end of a page, and a blank value with all users.
To calculate the percentage of users who scrolled to the bottom of a specific page, divide the number of 'Total users' where 'Per cent scrolled' = 90 by the 'Total users' where 'Per cent scrolled' = blank.
If no scroll data appears to be available, even for a broad date range:
1. Within the property, visit Admin > Data collection and modification > Data streams
2. Select 'Web'
3. In the 'Web stream details' overlay, check that 'Enhanced measurement' is enabled
4. If 'Enhanced measurement' is enabled, look at the 'Measuring' list to see if 'Scrolls' is enabled
5. If either of the above is not enabled, contact the property admin


#### Variables

| Field | Value |
|---|---|
| Dimensions | Page path and screen class<br>Per cent scrolled |
| Metrics | Total users |
| Segments | 'Mobile traffic' (readymade segment)<br>'Web traffic' (readymade segment) |


#### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Segment comparisons | Mobile traffic<br>Web traffic |
| Rows | Page path and screen class<br>Per cent scrolled |
| Show rows | 100 |
| Nested rows | Yes |
| Values | Total users |
| Cell type | Bar chart OR Plain text (it's a minor visual difference) |
| Filters | To filter results by an individual page, add:<br>Page path and screen class<br>- Conditions: exactly matches<br>- Expression: enter the page path, which is everything after your domain, minus any query strings (for example, the page path for https://helpwithcourtfees.service.gov.uk/questions/fee?locale=en is /questions/fee) |


### How many users are downloading linked files?

#### Potential insights
These explorations could help you to:
- conduct a content audit that includes downloadable content as well as HTML pages
- prioritise downloads such as PDFs to remove or convert into HTML content


#### Understand the data
When a user clicks a link that contains a common file name extension, GA4 will record it as a 'file_download' event. File extensions tracked include:
- .pdf
- .xlsx
- .doc
- .txt
- .rtf
- .csv
- .ppt
- .zip

If no download data appears to be available, even for a broad date range:
1. Within the property, visit Admin > Data collection and modification > Data streams
2. Select 'Web'
3. In the 'Web stream details' overlay, check that 'Enhanced measurement' is enabled
4. If 'Enhanced measurement' is enabled, look at the 'Measuring' list to see if 'File downloads' is enabled
5. If either of the above is not enabled, contact the property admin


#### Variables

| Field | Value |
|---|---|
| Dimensions | Event name<br>Link text<br>Link URL<br>Page path and screen class |
| Metrics | Total users |


#### Settings

| Field | Value |
|---|---|
| Technique | Free-form |
| Visualisation | Table |
| Rows | Page path and screen class<br>Link text<br>Link URL |
| Show rows | 100 |
| Nested rows | Yes |
| Values | Total users |
| Cell type | Plain text OR Bar chart (it's a minor visual difference) |
| Filters | Event name<br>- Exactly matches<br>- file_download<br>To filter results by an individual page, add:<br>Page path and screen class<br>- Conditions: contains<br>- Expression: enter the page path, which is everything after your domain, minus any query strings (for example, the page path for https://helpwithcourtfees.service.gov.uk/questions/fee?locale=en is /questions/fee) |
