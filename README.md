# Snowflake Health Check Monitor

Native App for real-time Compute, Performance & Security monitoring across your Snowflake account.

## Overview

Snowflake Health Check Monitor delivers 23+ KPIs and visualizations across three dashboards — Cost, Performance, and Security — all powered directly from your Account Usage schema with zero data movement.

## Features

### Cost & Usage Dashboard
- Total credits billed across all service types with period-over-period comparison
- Daily average spend
- Credits by service type (ranked horizontal bar chart with data labels)
- Daily credit trend (all services)
- Credits by warehouse
- Top cost driver identification

### Performance Dashboard
- Total queries with trend comparison
- Average query duration with trend
- Cache hit rate
- Failed query tracking with delta
- Daily query volume with overlaid duration
- Top users by query count
- Top 20 slowest queries with query text preview

### Security Dashboard
- Total logins with trend comparison
- Failed login tracking with delta
- Failure rate percentage
- Unique users count
- Daily login activity (success vs failed)
- Authentication method distribution
- Top users by failed logins
- Client type analysis
- Recent failed login details (last 50)

### Smart Filtering
- View by: All Services, By Service Type, By Warehouse, By Role, By User
- Dynamic multiselect adapts to selected category
- Date range: Last 7, 30, 90 days, or Custom date picker

### UX Features
- Blue gradient color scheme (#50a3b1 to #b8dae0)
- Data labels on all charts
- Tooltip icons on every KPI card and chart title
- Period-over-period comparison on all KPI cards
- SQL injection prevention
- NaN-safe error handling

### Built-in Setup Page
- One-click privilege grant via Snowflake Permission SDK (Native App)
- Manual setup flow with access verification for standalone Streamlit
- Environment display (current role, warehouse, user)

## Data Sources

All data sourced from `SNOWFLAKE.ACCOUNT_USAGE`:
- `METERING_DAILY_HISTORY` — credits billed by service type
- `WAREHOUSE_METERING_HISTORY` — warehouse-level credit breakdown
- `QUERY_HISTORY` — query execution metrics
- `LOGIN_HISTORY` — login security data

## Prerequisites

For Native App consumers:
```sql
GRANT IMPORTED PRIVILEGES ON DATABASE SNOWFLAKE TO APPLICATION <app_name>;
```

## Quick Start

1. Install from Snowflake Marketplace
2. Launch the app — Setup page loads automatically
3. Click **Grant** when prompted (Native App) or run the SQL shown
4. Dashboard loads automatically once access is verified

## App Files

| File | Description |
|------|-------------|
| `manifest.yml` | App manifest with version, privileges, and artifact references |
| `setup.sql` | Creates app role, schema, and Streamlit object on install |
| `environment.yml` | Conda dependencies (plotly, native-apps-permission SDK) |
| `compute_monitor_app.py` | Streamlit dashboard code |

## Documentation

| Document | Description |
|----------|-------------|
| [Architecture](docs/ARCHITECTURE.md) | System design, data flow, tech stack, security measures |
| [User Guide](docs/USER_GUIDE.md) | How to use each tab, filter, KPI, and chart |
| [Permissions](docs/PERMISSIONS.md) | Required privileges, what they unlock, granular alternatives |
| [Version History](docs/VERSION_HISTORY.md) | Changelog |

## Data Latency

Account Usage views have up to 2–3 hours of latency. Recent activity may not appear immediately.

## Built By

[Infojini Consulting Pvt Ltd](https://www.infojiniconsulting.com)

## Support

For questions or issues, contact: support@infojiniconsulting.com
