# User Guide

## Launching the App

1. Open **Snowsight**
2. Navigate to **Apps** (left sidebar)
3. Click **Snowflake Health Check Monitor**

## Setup Page

On first launch, the app checks for required permissions. If not yet granted:
- **Native App**: Click the **Grant** button (uses Snowflake Permission SDK)
- **Manual**: Run the SQL command displayed on screen

Once permissions are verified, the dashboard loads automatically.

## Navigation

The app has three main tabs at the top:
- **Cost & Usage** — Credit consumption analysis
- **Performance** — Query execution metrics
- **Security** — Login and authentication monitoring

## Filters

### Date Range
Located at the top of each dashboard:
- **Last 7 Days** — Quick view of recent activity
- **Last 30 Days** — Default monthly view
- **Last 90 Days** — Quarterly analysis
- **Custom** — Pick specific start and end dates

### Category Filter
- **All Services** — Aggregate view across everything
- **By Service Type** — Filter by Warehouse, Pipe, AI Services, Auto Clustering, etc.
- **By Warehouse** — Filter by specific warehouse(s)
- **By Role** — Filter by role(s) that executed queries
- **By User** — Filter by specific user(s)

When a category is selected, a multiselect dropdown appears with all available values. All are selected by default.

> Note: Filters apply to the current tab. Switching tabs resets the filter context.

## Cost & Usage Dashboard

| KPI Card | Description |
|----------|-------------|
| Total Credits | Sum of all credits consumed in the selected period |
| Daily Average | Total credits divided by number of days |
| Compute Credits | Credits used for warehouse compute |
| Cloud Services Credits | Credits used for cloud services layer |

**Charts:**
- **Credits by Service Type** — Horizontal bar chart ranking all service types by credit usage
- **Daily Credit Trend** — Time series showing daily credit consumption
- **Credits by Warehouse** — Bar chart showing top warehouses by credit usage

## Performance Dashboard

| KPI Card | Description |
|----------|-------------|
| Total Queries | Count of all queries executed |
| Avg Duration | Mean query execution time in seconds |
| Cache Hit Rate | Percentage of queries served from cache |
| Failed Queries | Count of queries that did not succeed |

**Charts:**
- **Daily Query Volume** — Bar chart with overlaid average duration line
- **Query Type Distribution** — Breakdown by SELECT, INSERT, CREATE, etc.
- **Top Users by Query Count** — Bar chart of most active users
- **Top 20 Slowest Queries** — Table with query ID, text preview, duration, warehouse, and user

## Security Dashboard

| KPI Card | Description |
|----------|-------------|
| Total Logins | Count of all login events |
| Failed Logins | Count of unsuccessful login attempts |
| Failure Rate | Failed logins as a percentage of total |
| Unique Users | Distinct users who logged in |

**Charts:**
- **Daily Login Activity** — Stacked bar chart (success vs failed)
- **Authentication Methods** — Distribution of auth types (Password, SSO, Key Pair, OAuth, etc.)
- **Client Types** — Breakdown by JDBC, Python, Snowsight, ODBC, etc.
- **Top Users by Login Count** — Most active users
- **Top Users by Failed Logins** — Users with most failures
- **Recent Failed Logins** — Table showing last 50 failed login details

## Tips

- Hover over any chart for detailed tooltips
- KPI cards show period-over-period comparison (▲/▼ with percentage)
- Hover over the ℹ️ icon next to any KPI or chart title for an explanation
- Use the date range filter to zoom into specific incidents
