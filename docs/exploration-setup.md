# Exploration setup

## Variables and settings

The exploration workspace has two configuration columns on the left:

- **Variables** – where you:
  - name your exploration
  - set your date range
  - load the segments, dimensions and metrics you want to use

- **Settings** – where you:
  -  select from the segments, dimensions and metrics you've loaded in Variables
  -  choose how the data is displayed in the current tab (on the right of the screen)

You must first add dimensions, metrics or segments to the **Variables** column before they can be used in **Settings**.

To use a variable:

- drag it into the appropriate field in **Settings**, or  
- double-click it to add it automatically to a compatible field

To the right of the Variables and Settings columns, the exploration output is displayed.

Each exploration can contain up to 10 tabs of output.

The **Variables** you choose are available across all tabs within the same exploration, but each tab has its own **Settings** that are configured independently.

Give each exploration a clear, descriptive name.

## Dimensions and metrics

Explorations are built using **dimensions** and **metrics**.

A practical distinction:

- **Dimensions** group data and describe it.
- **Metrics** measure data and are numerical.

### Dimensions

Dimensions describe attributes of your data — for example, which page was viewed or which device was used.

Common dimensions include:

- **Page path and screen class** – the path of a webpage after the domain name (for example '/apply/start')  
- **Page referrer** – the full URL of the previous page from which the user arrived
- **Device category** – desktop, mobile or tablet  
- **Event name** – the name of a recorded event (for example 'click', 'file_download', 'scroll')

### Metrics

Metrics are numerical measurements.

Common metrics include:

- **Views** – total number of page or screen views  
- **Total users** – number of unique users during the selected date range  
- **New users** – number of unique users who interacted for the first time  
- **Event count** – number of times a tracked event occurred

## Consistent use of 'Total users'

This guide focuses on identifying patterns and differences in behaviour to support design insight and decision-making, rather than reporting exact audience numbers.

For that reason, **Total users** is used as the default metric in most examples.

Google defines Total users as the number of unique users who triggered any event during the selected date range.

It is not a perfectly precise measure in every context, but it is consistent and comparable. This makes it useful for understanding relative differences between pages, journeys or user groups.

Different metrics answer different questions. However, using a consistent metric across similar explorations makes comparisons clearer and easier to interpret.

## Filters and segments

By default, an exploration shows data for the entire property within the selected date range.

To analyse a subset of data, use filters or segments.

- **Filters** – created and applied in the Settings column. Filters include or exclude data based on specific criteria (for example, include only a specific page or exclude internal traffic). Filters apply only to the current tab.

- **Segments** – created in the Variables column, applied in the Settings column. Segments define a subset of users, sessions or events, and can be applied to one or more tabs within the exploration.

Segments are particularly useful for side-by-side comparisons (for example, mobile vs desktop users, or new vs returning users).

### Creating a filter

1. In the Settings column, scroll to **Filters**.
2. Select **+ Drop or select dimension or metric**.
3. Choose a dimension or metric.
4. Select a condition (for example, "exactly matches", "contains" or ">").
5. Enter a value.

### Creating a segment

1. In the Variables column, select the **+** next to **Segments**.
2. Choose **Create a new segment**.
3. Select the segment type (for example, "User segment").
4. Enter a name.
5. Add one or more conditions.

The exploration sections in this guide provide the exact dimensions, conditions and values to use for each exploration.

## Date ranges

When selecting a date range, consider:

1. **Property start date** – data is only available from when GA4 tracking began for the property.
2. **Data retention settings** – in free tier GA4 properties, data retention is 2 months by default and can be extended to 14 months. Check under:
   Admin > Data collection and modification > Data retention
3. **Processing time** – longer date ranges may take more time to process.
4. **Sampling** – longer date ranges increase the likelihood of sampled results. See "Handling sampled results" below.

## Exporting data

To export data from an exploration tab:

1. Select the download icon in the top-right corner.
2. Choose a format (for example, CSV).

Exported files can be opened in a spreadsheet for further analysis.

## Sharing explorations

Explorations are private by default.

To share an exploration in read-only mode with other users who have access to the same property:

1. Select the share icon in the top-right corner.
2. Confirm sharing.

Shared explorations cannot be edited by other users unless they duplicate them.

## Handling sampled results

As your dataset gets larger (for example, when using a long date range), GA4 may apply data sampling. Sampling means GA4 uses a subset of data rather than the full dataset, so results are scaled up estimates rather than exact figures.

If sampling is applied, an indicator appears in the top-right of the exploration panel. Selecting the indicator shows the percentage of data used in the results.

In paid-for GA4 360 properties, sampling thresholds are higher and a detailed results option may be available.

To view more complete results (if available):

1. Select the sampling indicator in the top-right of the results panel.
2. Choose the detailed results option.

This may increase processing time.

---

<small>GA4 for content designers by Alex Robertson is licensed under <a href="https://creativecommons.org/licenses/by/4.0/">CC BY 4.0</a>.</small>
