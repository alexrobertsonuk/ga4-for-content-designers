# Exploration setup

## Variables and tab settings

The exploration workspace has two configuration columns on the left:

- **Variables** – where you name your exploration, set your date range, and define the components available to your exploration, including:
  - segments  
  - dimensions  
  - metrics  

- **Tab settings** – where you configure the current tab by selecting from the loaded variables and defining layout and display options.

You must first add dimensions, metrics or segments to the **Variables** column before they can be used in the tab settings.

To use a variable:

- drag it into the appropriate field in **Tab settings**, or  
- double-click it to add it automatically to a compatible field (for example, dimensions are typically added to Rows, metrics to Values).

To the right of these columns, the exploration output is displayed.

Each exploration can contain up to 10 tabs. Variables are shared across all tabs within the same exploration, but tab settings are configured independently.

Give each exploration a clear, descriptive name.

## Dimensions and metrics

**Dimensions** describe attributes of your data. They define how data is grouped.

Common dimensions include:

- **Page path and screen class** – the path of a webpage after the domain name (for example '/apply/start'), or the equivalent screen identifier for apps  
- **Page referrer** – the full referring URL from which the user arrived  
- **Device category** – desktop, mobile or tablet  
- **Link URL** – the destination of a tracked link click  
- **Event name** – the name of a recorded event (for example 'click', 'file_download', 'scroll')

**Metrics** are numerical measurements.

Common metrics include:

- **Views** – the total number of page or screen views  
- **Total users** – the number of unique users who triggered any event during the selected date range  
- **New users** – the number of users who interacted for the first time during the selected date range  
- **Event count** – the number of times a tracked event was triggered  

A practical distinction: dimensions group data, metrics measure it.

## Consistent use of "Total users"

This guide is written to support design insight and decision-making. As a result, absolute figures matter less than relative differences and consistent comparison across reports.

For that reason, **Total users** is used as the default metric throughout most examples.

Google defines Total users as "the number of unique users who triggered any event in the specified date range". While this does not produce perfectly precise counts in all contexts, it is stable and comparable, making it well suited to understanding proportions and patterns in user behaviour.

Different metrics answer different questions. However, using a consistent metric across similar explorations supports meaningful comparison.

## Filters and segments

By default, an exploration shows data for the entire property within the selected date range.

To analyse a subset of data, use filters or segments.

- **Filters** – applied within the Tab settings column. Filters include or exclude data based on specific criteria (for example, include only a specific page or exclude internal traffic). Filters apply only to the current tab.

- **Segments** – created in the Variables column. Segments define a subset of users, sessions or events and can be applied to one or more tabs within the exploration. Segments can also be reused within the same exploration.

Segments are particularly useful for side-by-side comparisons (for example, mobile vs desktop users, or new vs returning users).

To create a segment:

1. In the Variables column, select the **+** next to **Segments**.
2. Choose **Create a new segment**.
3. Select the segment type (for example, 'User segment').
4. Enter a name.
5. Define the segment conditions.

## Date ranges

When selecting a date range, consider:

1. **Property start date** – data is only available from when GA4 tracking began for the property.
2. **Data retention settings** – in free-tier GA4 properties, event-level data retention is 2 months by default and can be extended to 14 months. Check under:
   Admin > Data collection and modification > Data retention
3. **Processing time** – longer date ranges may take more time to process.
4. **Sampling** – large date ranges increase the likelihood of sampled results in the free tier.

If sampling is applied, an indicator appears in the top-right of the exploration panel. Selecting the indicator shows the percentage of data used in the results.

In GA4 360 (enterprise tier), a detailed results option may be available to reduce the impact of sampling.

## Exporting data

To export data from an exploration tab:

1. Select the download icon in the top-right corner.
2. Choose a format (for example, CSV).

Exported files can be opened in spreadsheet software for further analysis.

## Sharing explorations

Explorations are private by default.

To share an exploration in read-only mode with other users who have access to the same property:

1. Select the share icon in the top-right corner.
2. Confirm sharing.

Shared explorations cannot be edited by other users unless they duplicate them.

## Reducing data sampling (GA4 360)

In GA4 360 properties, sampling thresholds are higher and a detailed results option may be available.

If sampling is indicated in an exploration:

1. Select the sampling indicator in the top-right of the results panel.
2. If available, choose the detailed results option.

This may increase processing time.
