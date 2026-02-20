## Exploration setup

### Variables and settings
The exploration workspace has 2 setup columns on the left:
- Variables – where you name your exploration, set your date range, and load all the variables you plan to use, but don't explicitly use them (like setting out the ingredients for a recipe)
- Settings – where you piece together your exploration by selecting from your loaded variables, and choosing layout and display options (like creating a recipe from your ingredients)

Once you've loaded the variables you intend to use, you simply drag and drop them into the Settings column, placing them where you want them. Drag and dropping can sometimes be a bit temperamental - you may have to try once or twice. Alternatively, double-clicking on a dimension or metric will add it to the relevant setting (usually 'rows' and 'values' respectively). More on dimensions and metrics in the next section.

To the right of the Variables and Settings columns, your exploration output will be displayed. You can have up to 10 tabs of output, each with unique settings created from your chosen variables (which persist across all tabs).

Be sure to give your exploration a logical name.

### Dimensions and metrics
Dimensions are attributes of data. They describe what it is that you want metrics for. Some common dimensions you'll use are:

- Page path and screen class – the path of a webpage on your site (everything after the domain name; the homepage will be simply '/'), or the 'screen class' equivalent for apps (less relevant in our context)
- Page referrer – the full referring URL, the user's previous page either on your site or from elsewhere (including 'https://' and the domain name, unlike the shorter 'page path')
- Device category – the type of device used (desktop, tablet, mobile)
- Link URL – the destination of a hyperlink
- Event name – tracked user interaction 'events' such as 'click', 'file_download', or 'scroll'

Metrics are your numerical measurements. Some common metrics you'll use are:

- Views – the total number of page views
- Total users – the estimated total number of unique users
- New users – the estimated total number of first-time users
- Event count – the number of times a tracked interaction (such as a click, file download or scroll) was triggered

A useful rule: dimensions describe your data, metrics quantify it (you can multiply a metric, but not a dimension).

#### Consistent use of 'Total users'
This guide is written to support design insight and decision-making, not management reporting. As a result, absolute figures matter less than relative differences and consistent comparison across reports.

Throughout this guide, 'Total users' is recommended as the default metric. Google defines this as "the number of unique users who triggered any event in the specified date range". While this does not produce perfectly precise counts in all contexts, it is stable and comparable, making it well suited to understanding proportions, trade-offs and patterns in user behaviour.

While different metrics answer different questions, using the same metric consistently is essential if you want relative differences between designs, pages or journeys to remain meaningful.

### Filters and segments
By default, an exploration will show you data for the entire property. To see a subset of the data, you can use filters or segments.

- Filters – set in the Settings column, filters quickly include or exclude data based on specific criteria (for example, only include a specific page, or only include users referred from a specific domain). Filters can't be saved to reuse in multiple explorations.
- Segments – created in the Variables column, segments require a few more steps to set up, and are best for seeing side-by-side comparisons (for example, mobile vs desktop users, or new vs returning users). Segments can be saved for reuse in multiple explorations.

To create a segment (figure 3):
1. In the 'Variables' column, select '+' next to 'SEGMENTS'.
2. In the 'Add a new segment' overlay, select 'Create a new segment' (top right).
3. Select 'User segment'.
4. Enter a name for your segment (for example, 'Users referred from [domain name]').
5. Enter your segment conditions (details are provided in the 'Variables' tables for each exploration described later in this guide).


### Date ranges
When selecting a date range for your exploration, consider:
1. Data capture start date. Data is only available from the date the property was set up on GA4. For free tier accounts, data stopped being collected in UA (Universal Analytics) in July 2023, with most properties automatically migrated.
2. Data retention period. Free tier accounts only retain data for 2 months by default. This can be extended by the property admin to 14 months (highly recommended). To verify the property's current setting, go to Admin > Data collection and modification > Data retention.
3. Data processing speeds. Longer date ranges of a year or more will take much longer for GA4 to process.
4. Data sampling. Longer date ranges are more likely to contain sampled data. The data sampling icon, top right in an exploration, will turn from green to red if sampling has been applied. Select this icon to see what percentage of available data is being used. If you're viewing an exploration on a paid enterprise '360' account, you can reduce the impact of sampling by selecting 'More detailed results'.


### Exporting data
To export the data from any exploration tab, select the top right download icon and choose 'CSV'. You can then import this CSV into a spreadsheet.

### Sharing explorations
Explorations are private by default, but you can share them, in read-only mode, with everyone else who has access to the same property. To do so, select the 'share exploration' icon, top right.


### Reducing data sampling
As an additional benefit of the paid enterprise tier, you're able to reduce the impact of any data sampling (estimating total numbers from a subset of the data), by selecting 'More detailed results':

1. At the top right of your exploration output, next to the download and share icons, look for the data sampling icon.
2. If the data sampling icon is a red exclamation mark, open the dropdown and select 'More detailed results'.
