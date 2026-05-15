# Exploration setup

## Contents

- [Variables and settings](exploration-setup?id=variables-and-settings)
- [Dimensions and metrics](exploration-setup?id=dimensions-and-metrics)
- [Consistent use of "Total users"](exploration-setup?id=consistent-use-of-quottotal-usersquot)
- [Filters and segments](exploration-setup?id=filters-and-segments)
- [Date ranges](exploration-setup?id=date-ranges)
- [Exporting data](exploration-setup?id=exporting-data)
- [Sharing explorations](exploration-setup?id=sharing-explorations)
- [Handling sampled results](exploration-setup?id=handling-sampled-results)

## Variables and settings

The exploration editor has two configuration columns on the left:

1. **Variables** - where you:
  - name your exploration
  - set your date range
  - load the segments, dimensions and metrics you want to use

2. **Settings** - where you:
  -  select from the segments, dimensions and metrics you've loaded in Variables
  -  choose how the data is displayed in the current tab (on the right of the editor)

You must add dimensions, metrics or segments to the **Variables** column before they can be used in **Settings**.

To use a variable:

- drag it into the appropriate field in **Settings**, or 
- double-click it to add it automatically to a compatible field

The exploration output is displayed to the right of the Variables and Settings columns. Each exploration can contain up to 10 tabs of output.

The **Variables** you choose are available across all tabs within the same exploration, but each tab has its own **Settings** that are configured independently.

Give each exploration a clear, descriptive name, using your organisation's naming conventions if you intend to share with other users.

## Dimensions and metrics

Explorations are built using **dimensions** and **metrics**.

In simple terms:

- **dimensions** describe and group data
- **metrics** measure data and are numerical

For example, the dimension "Device category" paired with the metric "Total users" will show you the total number of unique users who used each device type (desktop, mobile or tablet) within your date range.

### Dimensions

Dimensions describe attributes of data - for example, the page viewed or device used.

Common dimensions include:

- "Page path and screen class" – the path of a webpage after the domain name (for example, /apply/start)  
- "Page referrer" – the full URL of the previous page from which the user arrived
- "Device category" – desktop, mobile or tablet  
- "Event name" – the name of a recorded event (for example "click", "file_download", "scroll")

### Metrics

Metrics are numerical measurements.

Common metrics include:

- "Views" – total number of times a page or screen was loaded 
- "Total users" – number of unique users
- "New users" – number of unique users who interacted for the first time  
- "Event count" – number of times a tracked event occurred

## Consistent use of "Total users"

"Total users" is recommended throughout most of this guide.

Google defines "Total users" as the number of unique users who triggered any event during the selected date range.

This guide is about design insights rather than management reporting - it focuses on identifying patterns and differences in behaviour rather than exact usage numbers. So while "Total users" is not a perfectly precise measure in every context, using a consistent metric supports understanding relative differences between pages, journeys or user groups.

## Filters and segments

By default, an exploration shows data for the entire property within the selected date range.

To analyse a subset of data, use filters or segments.

**Filters** apply only to the current exploration tab, so are created and applied in the Settings column. Filters include or exclude data based on specific criteria (for example, include only a specific page or exclude internal traffic).

**Segments** can be applied to one or more tabs within an exploration, so are created in the Variables column, then applied when needed in the Settings column. Segments define a subset of users, sessions or events.

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

The explorations throughout this guide describe the exact dimensions, conditions and values to use when creating filters or segments.

## Date ranges

When selecting a date range, consider:

1. Property start date – data is only available from when GA4 tracking began for the property.
2. Data retention settings – properties in free GA4 accounts retain data for 2 months by default, but this can be extended to 14 months. Check under:
   Admin > Data collection and modification > Data retention
3. Processing time – longer date ranges will take more time to process.
4. Sampling – longer date ranges increase the likelihood of sampled results. See "Handling sampled results" below.

## Exporting data

To export data from an exploration tab:

1. Select the download icon in the top-right corner.
2. Choose a format (for example, CSV - useful if you want to do further analysis in a spreadsheet).

## Sharing explorations

Explorations are private by default. Even when shared, they remain read-only.

To share an exploration with other users who have access to the same property, use the share icon in the top-right corner of your exploration.

Once shared, the exploration becomes visible to all users of that property. They can find it on the Explore landing page by filtering the **Owner** column to **Not owned by me** or **Owned by anyone**.

To copy and customise an exploration someone else has shared:

1. Open the **Explore** page.
2. Find the shared exploration.
3. Select the **More actions** (three dot) menu to the right of the exploration name.
4. Choose **Duplicate**.

This creates a private, editable copy in your own account.

## Handling sampled results

As your dataset gets larger (such as when using a long date range), GA4 may apply data sampling. Sampling means GA4 uses a subset of data rather than the full dataset, so results are scaled up estimates rather than exact figures.

If sampling is applied, a warning indicator appears in the top-right of the exploration panel. Selecting the indicator shows the percentage of data used in the results. If data is unsampled, a green tick indicator is shown.

In paid-for GA4 360 properties, sampling thresholds are higher and a detailed results option may be available.

To view more detailed results (if available):

1. Select the sampling indicator in the top-right of your exploration.
2. Choose "More detailed results" from the dropdown.

This may increase processing time.

---

<small>GA4 for content designers by Alex Robertson is licensed under <a href="https://creativecommons.org/licenses/by/4.0/">CC BY 4.0</a>.</small>
