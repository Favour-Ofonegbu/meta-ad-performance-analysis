# Meta Ad Performance Analysis

### An Interactive Power BI Dashboard for Facebook and Instagram Advertising Performance

---

## Project Overview

Digital advertising generates large volumes of data, but understanding whether advertising campaigns are actually performing well requires more than tracking impressions and clicks.

How many people interacted with the advertisements? Which platform generated more engagement? Which audience groups responded most? Did those interactions translate into purchases? And how can these findings help businesses make better advertising decisions?

The **Meta Ad Performance Analysis** project explores these questions through an interactive Power BI dashboard designed to analyse paid advertising campaigns across Facebook and Instagram.

The project transforms advertising event data, campaign information and user demographics into meaningful insights that help evaluate advertising reach, engagement, conversions, audience behaviour and campaign budget allocation.

## Business Problem

Businesses invest in digital advertising to increase brand visibility, attract potential customers and generate sales. However, without a centralized reporting solution, comparing campaign performance and understanding audience behaviour can become challenging.

The business needed a reporting solution that would provide visibility into:

- Advertising reach and impressions.
- Audience engagement across Facebook and Instagram.
- Campaign conversion performance.
- Audience demographics and geographical distribution.
- Advertising performance across different creative formats.
- Campaign budget allocation.

The objective was to develop an interactive dashboard that would bring these performance indicators together and support data-driven marketing decisions.

## Business Objectives

The project was designed to help the marketing team:

1. Compare advertising performance between Facebook and Instagram.
2. Monitor campaign reach, engagement and conversions.
3. Understand audience engagement patterns across demographic groups.
4. Identify advertising formats contributing most to campaign performance.
5. Analyse geographical and time-based advertising trends.
6. Monitor campaign budget allocation.
7. Identify opportunities for campaign optimization.

## Project Scope

**Included**

- Facebook paid advertising campaigns.
- Instagram paid advertising campaigns.
- Impressions, clicks, shares, comments and purchases.
- Audience demographic analysis.
- Geographical performance analysis.
- Campaign budget analysis.

**Excluded**

- Messenger advertising.
- Audience Network advertising.
- Organic engagement.

## Tools and Technologies

| Technology         | Application                                             |
| ------------------ | ------------------------------------------------------- |
| Microsoft Power BI | Data modelling, visualization and dashboard development |
| DAX                | Creating measures and calculating KPIs                  |
| Power Query        | Data preparation and transformation                     |
| Microsoft Excel    | Supporting data inspection and preparation              |

## Dataset and Data Model

The project uses four interconnected tables, each representing a different aspect of advertising performance.

### 1. ad_events

The central fact table containing records of interactions between users and advertisements.

Key fields:

- `event_id`
- `ad_id`
- `user_id`
- `timestamp`
- `event_type`
- `day_of_week`
- `time_of_day`

The `event_type` field identifies the activity performed, including Impression, Click, Share, Comment and Purchase.

### 2. ads

Contains information about individual advertisements.

Key fields:

- `ad_id`
- `campaign_id`
- `ad_platform`
- `ad_type`
- `target_gender`
- `target_age_group`
- `target_interests`

This table provides information about advertising platforms, creative formats and audience targeting.

### 3. campaigns

Contains campaign-level information.

Key fields:

- `campaign_id`
- `name`
- `start_date`
- `end_date`
- `duration_days`
- `total_budget`

This table supports campaign duration and budget allocation analysis.

### 4. users

Contains demographic and geographical information about users.

Key fields:

- `user_id`
- `user_gender`
- `user_age`
- `age_group`
- `country`
- `location`
- `interests`

This table supports demographic segmentation and geographical analysis.

### Data Model Relationships

The tables are connected through their respective identifiers:

- `ad_events[ad_id]` → `ads[ad_id]`
- `ads[campaign_id]` → `campaigns[campaign_id]`
- `ad_events[user_id]` → `users[user_id]`

The `ad_events` table serves as the central fact table, while `ads`, `campaigns` and `users` provide descriptive information.

This structure allows advertising activity to be analysed across platforms, campaigns, audience groups and geographical locations.

## Key Performance Indicators (KPIs)

The dashboard tracks the following performance measures:

| KPI                         | Description                                        |
| --------------------------- | -------------------------------------------------- |
| Impressions                 | Number of times advertisements were displayed      |
| Clicks                      | Number of recorded advertisement clicks            |
| Shares                      | Number of times advertisements were shared         |
| Comments                    | Number of recorded comments                        |
| Purchases                   | Number of recorded purchase events                 |
| Engagements                 | Combined total of clicks, shares and comments      |
| CTR                         | Percentage of impressions resulting in clicks      |
| Engagement Rate             | Percentage of impressions resulting in engagements |
| Conversion Rate             | Percentage of clicks resulting in purchases        |
| Purchase Rate               | Percentage of impressions resulting in purchases   |
| Total Budget                | Total budget allocated across campaigns            |
| Average Budget per Campaign | Average budget allocation per campaign             |

### DAX Measures and Calculations

Some of the core calculations used in the project include:

**Impressions**

```dax
Impressions =
COUNTROWS(
    FILTER(
        ad_events,
        ad_events[event_type] = "Impression"
    )
)
```

**Clicks**

```dax
Clicks =
COUNTROWS(
    FILTER(
        ad_events,
        ad_events[event_type] = "Click"
    )
)
```

**Shares**

```dax
Shares =
COUNTROWS(
    FILTER(
        ad_events,
        ad_events[event_type] = "Share"
    )
)
```

**Comments**

```dax
Comments =
COUNTROWS(
    FILTER(
        ad_events,
        ad_events[event_type] = "Comment"
    )
)
```

**Engagements**

```dax
Engagements =
[Shares] + [Clicks] + [Comments]
```

**CTR**

```dax
CTR =
DIVIDE([Clicks], [Impressions], 0) * 100
```

**Engagement Rate**

```dax
Engagement Rate =
DIVIDE([Engagements], [Impressions], 0) * 100
```

**Conversion Rate**

```dax
Conversion Rate =
DIVIDE([Purchases], [Clicks], 0) * 100
```

**Purchase Rate**

```dax
Purchase Rate =
DIVIDE([Purchases], [Impressions], 0) * 100
```

## Dashboard Features and Visualizations

The dashboard was designed to provide a consolidated view of advertising performance while allowing users to explore different metrics interactively.

### 1. KPI Summary Cards

The dashboard presents headline performance indicators, including impressions, clicks, shares, comments, purchases, engagements, conversion rates and budget measures.

These cards provide an immediate overview of campaign performance.

### 2. Platform Filter

An interactive slicer allows users to select Facebook or Instagram.

This enables platform-specific analysis and comparison of advertising performance.

### 3. Dynamic Measure Selection

A dynamic measure selector allows users to switch between supported metrics without creating separate charts for every KPI.

For example, the user can switch between Impressions, Clicks, Shares, Comments, Purchases and Engagements.

### 4. Engagement by Gender

A donut chart displays the distribution of the selected metric across gender categories.

### 5. Engagement by Age

A bar chart compares advertising performance across different age groups.

### 6. Engagement by Country

A geographical map displays advertising activity across countries, using bubble sizes to represent the selected metric.

### 7. Analysis by Month

A calendar heat map displays advertising activity across calendar dates. Darker shades represent higher activity.

### 8. Weekly Engagement Trend

A stacked column chart displays weekly advertising performance, broken down by advertising type.

### 9. Hourly Engagement Trend

An area chart displays advertising activity across the 24 hours of the day, helping identify periods of higher and lower activity.

### 10. Analysis by Ad Type

A matrix compares advertising performance across creative formats and platforms.

It provides a side-by-side view of formats such as Image, Video, Carousel and Story.

## Dashboard Preview

### Facebook Dashboard

![Facebook Dashboard](Images/Facebook_Dashboard.png)

### Instagram Dashboard

![Instagram Dashboard](Images/Instagram_Dashboard.png)

## Key Dashboard Insights

The dashboard provides several perspectives for understanding advertising performance.

### Overall Advertising Performance

The reported overall dashboard figures include:

| Metric      | Reported Value |
| ----------- | -------------: |
| Impressions |           216K |
| Clicks      |          25.4K |
| Shares      |           1.3K |
| Comments    |           2.6K |
| Purchases   |           1.3K |
| Engagements |          29.3K |

These figures provide an overview of the volume of recorded advertising activity.

### Conversion Performance

The reported performance rates include:

| Metric          | Reported Value |
| --------------- | -------------: |
| CTR             |         11.76% |
| Engagement Rate |         13.56% |
| Conversion Rate |          5.21% |
| Purchase Rate   |          0.61% |

These measures help evaluate how recorded advertising activity progresses from impressions to clicks and purchases.

### Audience Analysis

The gender and age visualizations provide insight into how advertising activity is distributed across audience categories.

This can help the marketing team investigate which demographic segments are responding more strongly to campaigns.

### Geographical Analysis

The country map helps identify geographical concentrations of advertising activity and provides a basis for further market analysis.

### Time-Based Analysis

The calendar, weekly and hourly visualizations help identify periods of higher and lower advertising activity.

These patterns can support further investigation into campaign scheduling and timing.

### Advertising Format Analysis

The ad-type matrix and weekly trend allow different creative formats to be compared using the selected performance measures.

This helps identify formats that contribute more to advertising activity.

## Business Recommendations

Based on the analytical perspectives provided by the dashboard, the following actions are worth investigating:

1. **Platform Optimization:** Compare Facebook and Instagram performance before making platform-specific budget allocation decisions.
2. **Audience Optimization:** Investigate demographic segments with stronger engagement and conversion outcomes.
3. **Creative Optimization:** Evaluate the performance of different advertising formats.
4. **Campaign Scheduling:** Investigate periods of higher advertising activity when planning campaign delivery.
5. **Geographical Optimization:** Compare country-level activity with purchases and advertising costs.
6. **Conversion Improvement:** Investigate potential gaps between advertisement clicks and completed purchases.
7. **Budget Monitoring:** Compare allocated campaign budgets with actual advertising expenditure and business outcomes.

## Project Limitations

- Impressions represent advertisement displays, not unique individuals reached.
- Target audience demographics and actual user demographics are different measures.
- Engagements include clicks, shares and comments.
- Allocated campaign budgets do not necessarily represent actual advertising expenditure.
- Revenue information is required for a complete ROI or ROAS analysis.
- Purchase attribution methods are not specified in the supplied project documentation.

## Conclusion

The Meta Ad Performance Analysis project demonstrates how Power BI can be used to transform advertising event data into meaningful business insights.

By connecting advertising events, campaign information, audience demographics and budget allocations, the dashboard provides a consolidated view of Facebook and Instagram advertising performance.

It enables users to move beyond basic performance figures and explore the relationship between advertising reach, engagement, conversions, audience behaviour and creative formats.

Ultimately, the project highlights how data analytics can support better marketing decisions by turning raw advertising records into actionable business intelligence.

---

## Repository Structure

```text
meta-ad-performance-analysis/
│
├── README.md
│
├── Documentation/
│   ├── Business_Requirements_Document.pdf
│   ├── Domain_Knowledge_Document.pdf
│   ├── Dashboard_Insights.pdf
│   └── Project_Explanation.pdf
│
├── Dashboard/
│   └── Meta_Ad_Performance.pbix
│
├── Images/
│   ├── Facebook_Dashboard.png
│   └── Instagram_Dashboard.png
│
├── DAX/
│   └── Measures.dax
│
└── .gitignore
```

## Author

**Meta Ad Performance Analysis**

_Power BI | Data Analytics | Business Intelligence_
