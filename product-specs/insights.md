# Insights

## Product Overview

Centralized analytics dashboard for practice performance. Surfaces key metrics across scheduling, communications, payments, and patient engagement in one view.

## Key Features

### Dashboard
- At-a-glance KPIs: production, collections, new patients, no-show rate
- Date range selector with presets (today, this week, this month, YTD, custom)
- Multi-location rollup with per-location drill-down
- Provider-level performance comparison

### Scheduling Metrics
- Appointment volume (booked, completed, cancelled, no-show)
- Online booking conversion rate
- Average time-to-book (from search to confirmation)
- Recall compliance rate
- Waitlist fill rate
- Chair utilization by operatory

### Communication Metrics
- Reminder confirmation rate
- Two-way message volume and response time
- Campaign performance (open rate, click rate, unsubscribe rate)
- Review request conversion rate
- Average star rating over time

### Financial Metrics
- Production by provider and procedure type
- Collections rate (collected / billed)
- Outstanding balance aging
- Payment plan adoption rate
- Average patient payment amount

### Patient Metrics
- New patient acquisition (by source: online, referral, walk-in)
- Patient retention / churn
- Form completion rate
- Average patient satisfaction score
- Reactivation rate (patients returning after 12+ month gap)

## Data Model

### MetricSnapshot
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| metric_key | string | Machine-readable metric name |
| value | number | Metric value |
| unit | enum | `count` · `percent` · `cents` · `minutes` · `rating` |
| dimension | object | Grouping keys (provider_id, location_id, date) |
| period | enum | `daily` · `weekly` · `monthly` |
| computed_at | datetime | |

### Report
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| name | string | Report name |
| metrics | array | List of metric_keys included |
| filters | object | Applied filters (date range, location, provider) |
| schedule | object | Auto-send schedule (null if manual) |
| recipients | array | Email addresses for scheduled delivery |
| created_by | string | Staff user ID |

## User Flows

### Morning Practice Review
1. Practice manager opens Insights dashboard
2. Default view shows current week KPIs vs. prior week
3. Manager filters to specific provider to review performance
4. Drills into no-show rate; sees breakdown by day and appointment type
5. Exports report as PDF for team meeting

## Acceptance Criteria
- Dashboard loads within 3 seconds
- Data refreshed every 15 minutes from EHR sync
- All metrics filterable by location, provider, and date range
- Export to CSV and PDF
- Role-based access (practice owner sees all; provider sees own metrics)
