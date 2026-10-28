# Performance Testing - Health360

- Dataset: 5,000 rows x 29 columns (CSV)
- Content: 17 worksheets, 3 dashboards, 1 story
- Load time: about 3 seconds on the published Tableau Public link
- Optimizations: aggregated measures, unused fields hidden, filter actions
  used instead of many separate filters, a limited number of charts per dashboard
- Testing: filters and filter actions checked across all dashboards
- Result: dashboards respond within 1-2 seconds