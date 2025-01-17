---
title: 'Analytics'
description: 'Create custom metrics using SQL queries in Analytics Dashboard'
---

## Overview

Hardal Analytics provides comprehensive insights into your application's performance and user behavior through both pre-built metrics and custom SQL queries. The analytics dashboard offers cookieless tracking capabilities while maintaining user privacy.

## Default Dashboard Metrics

The analytics dashboard comes with several pre-configured metric categories:

### Realtime Metrics
- Active users
- Current page views
- Live sessions
- User engagement

### Consent Metrics
- Consent rates
- Opt-in/opt-out trends
- Consent management performance

### Basic Metrics
- Total page views
- Unique visitors
- Session duration
- Bounce rates

### System Metrics
- Server response times
- Error rates
- API performance
- System health indicators

### Advanced Metrics
- User flow analysis
- Conversion funnels
- Custom event tracking
- Attribution analysis

## Creating Custom Dashboards

You can create custom metrics and dashboards using SQL queries to analyze your data in ways specific to your needs.

### How to Create a Custom Metric

1. Navigate to the Analytics Dashboard
2. Click on "Create Metric" button
3. Fill in the following information:
   - Metric Title: Give your metric a descriptive name
   - Description: Explain what the metric tracks
   - SQL Query: Write your custom SQL query
   - Visualization Type: Choose how to display your data (Table, Line Chart, Bar Chart, etc.)
   - Chart Color: Customize the appearance of your visualization

### Example SQL Queries

Here are some common custom metric queries:

```sql
-- User retention by day
SELECT 
    DATE(created_at) as date,
    COUNT(DISTINCT user_id) as retained_users
FROM sessions
GROUP BY DATE(created_at)
ORDER BY date DESC;

-- Page performance analysis
SELECT 
    path,
    AVG(load_time) as avg_load_time,
    COUNT(*) as views,
    COUNT(DISTINCT user_id) as unique_visitors
FROM page_views
GROUP BY path
ORDER BY views DESC;

-- Conversion funnel
SELECT 
    step_name,
    COUNT(*) as total_users,
    COUNT(*) * 100.0 / LAG(COUNT(*)) OVER (ORDER BY step_order) as conversion_rate
FROM funnel_steps
GROUP BY step_name, step_order
ORDER BY step_order;
```

### Tips for Custom Metrics

- Use appropriate time ranges in your queries for meaningful trends
- Include filters to focus on specific user segments
- Optimize queries for performance
- Use appropriate aggregations (COUNT, AVG, SUM) based on your needs
- Consider adding WHERE clauses to exclude irrelevant data

### Available Tables

Your custom queries can access the following main tables:

- `sessions`: User session data
- `page_views`: Individual page view events
- `events`: Custom event tracking
- `users`: User profile information
- `telemetry`: System performance data

Remember to test your queries thoroughly before saving them as metrics to ensure they provide accurate and meaningful insights for your analytics needs.


<Tip>
For more information on how to use the Analytics Dashboard, please contact suppoFrt team at support@usehardal.com
</Tip>