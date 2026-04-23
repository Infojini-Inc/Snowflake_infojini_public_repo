# Deployment Guide

## For Consumers (Installing from Marketplace)

### Step 1: Find the App
1. Open Snowsight
2. Navigate to **Data Products** → **Marketplace**
3. Search for **Snowflake Health Check Monitor**
4. Click **Get**

### Step 2: Install
1. Choose a warehouse for installation
2. Click **Install**
3. Wait for the installation to complete

### Step 3: Grant Permissions
After installation, the app needs access to Account Usage data:

```sql
GRANT IMPORTED PRIVILEGES ON DATABASE SNOWFLAKE TO APPLICATION SNOWFLAKE_HEALTH_CHECK_MONITOR;
```

Or use the one-click **Grant** button on the app's Setup page.

### Step 4: Launch
1. Go to **Apps** in Snowsight
2. Click **Snowflake Health Check Monitor**
3. The dashboard loads automatically

## For Providers (Publishing Updates)

### Prerequisites
- ACCOUNTADMIN role
- Application package `COMPUTE_MONITOR_PKG` exists
- Provider profile approved on Snowflake Marketplace

### Updating the App

1. Upload updated code to the application package stage:
```sql
PUT file:///path/to/compute_monitor_app.py
  @COMPUTE_MONITOR_PKG.STAGE_CONTENT.APP_CODE/code/
  AUTO_COMPRESS=FALSE OVERWRITE=TRUE;
```

2. Create a new patch or version:
```sql
-- New patch (minor fix)
ALTER APPLICATION PACKAGE COMPUTE_MONITOR_PKG
  ADD PATCH FOR VERSION V1
  USING '@COMPUTE_MONITOR_PKG.STAGE_CONTENT.APP_CODE';

-- New version (feature release)
ALTER APPLICATION PACKAGE COMPUTE_MONITOR_PKG
  ADD VERSION V2
  USING '@COMPUTE_MONITOR_PKG.STAGE_CONTENT.APP_CODE';
```

3. Set the release directive:
```sql
ALTER APPLICATION PACKAGE COMPUTE_MONITOR_PKG
  SET DEFAULT RELEASE DIRECTIVE
  VERSION = V2 PATCH = 0;
```

4. Consumers will be upgraded automatically on next app launch.

## Troubleshooting

| Issue | Solution |
|-------|----------|
| "Insufficient privileges" on launch | Run the GRANT IMPORTED PRIVILEGES command above |
| Empty dashboards | Account Usage has 2–3 hour latency; wait and refresh |
| App not visible in Snowsight Apps | Ensure installation completed; check with SHOW APPLICATIONS |
