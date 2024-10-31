# Bluejay metrics
In this directory you can find all the existing metrics in bluejay. In each metrics you can find 3 files:
- **metric.md**: Describes the metric and explains step by step how it is constructed.
- **metric.json**: json file in which the metric is located to be able to use it
- **test-metric.json**: json file that allows you to test the operation of the metric. You can find a tutorial on how the collector-event metrics test endpoint works [here](https://docs.governify.io/development/services/collectors/collector-events/#test-computation-endpoint-for-metrics).

## Catalog

| Metric  | Description             | API         | Type      |
|---------|-------------------------|-------------|-----------|
| COUNT_INPROGRESSISSUES_MEMBER | Number of issues in the "In Progress" column assigned to a member.  | GithubGQL        | Member     |

