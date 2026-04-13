# Features

![Feature Overview](../assets/images/feature.png)

Product ships with a broad set of built-in capabilities. This page gives you a high-level tour of each major feature area.

## Real-Time Collaboration

Multiple team members can work on the same project simultaneously. Changes are broadcast over a WebSocket connection with operational-transform conflict resolution — no more "who saved last wins."

### Presence Indicators

See exactly who is viewing or editing a resource in real time:

- **Green dot** — currently active
- **Yellow dot** — idle for more than 2 minutes
- **Gray dot** — viewing but not editing

### Comments & Annotations

Attach threaded comments to any resource, line of configuration, or pipeline step. Comments support Markdown and can mention `@teammates` to send notifications.

!!! tip "Keyboard shortcut"
    Press ++cmd+shift+m++ on macOS (or ++ctrl+shift+m++ on Windows/Linux) to open the comment panel from anywhere in the UI.

---

## Analytics Dashboard

The built-in analytics dashboard provides real-time and historical metrics without requiring a separate observability stack.

### Available Metrics

| Metric | Description | Retention |
|--------|-------------|-----------|
| Request rate | Requests per second across all endpoints | 90 days |
| Error rate | Percentage of 4xx/5xx responses | 90 days |
| P99 latency | 99th percentile response time | 30 days |
| Resource usage | CPU, memory, and storage per resource | 14 days |
| Pipeline throughput | Records processed per minute | 30 days |

### Custom Dashboards

Create custom dashboards by combining any available metrics into a grid layout:

```yaml
# dashboard.yml
name: "Pipeline Health"
panels:
  - type: timeseries
    title: Throughput (records/min)
    metric: pipeline.throughput
    window: 1h

  - type: stat
    title: Error Rate (last 5m)
    metric: pipeline.error_rate
    threshold:
      warn: 0.01
      critical: 0.05

  - type: heatmap
    title: Latency Distribution
    metric: pipeline.latency_p99
    window: 24h
```

---

## Integrations

Product connects natively with the tools your team already uses.

| Integration | Description |
|-------------|-------------|
| :simple-slack: **Slack** | Send notifications to channels or DMs when pipelines fail, succeed, or need review. |
| :simple-github: **GitHub** | Trigger pipeline runs on pull requests, push events, or tag creation via GitHub Actions. |
| :simple-amazonaws: **AWS** | Read from S3, write to RDS, invoke Lambda, or stream from Kinesis with zero-config auth via IAM roles. |
| :simple-googlecloud: **Google Cloud** | Ingest from BigQuery, Pub/Sub, and Cloud Storage. Authenticate with Workload Identity. |
| :simple-datadog: **Datadog** | Forward all Product metrics and logs directly to your Datadog account. |
| :material-webhook: **Webhooks** | Send HTTP POST events to any endpoint for custom integrations. Includes HMAC signature verification. |

---

## Access Control

Role-based access control (RBAC) is available on all plans.

### Built-in Roles

```
Owner
├── Admin
│   ├── Editor
│   │   └── Viewer
│   └── Billing Manager
└── API Service Account
```

### Custom Roles (Enterprise)

Define granular permissions with a policy language:

```json
{
  "role": "pipeline-operator",
  "permissions": [
    { "resource": "pipeline", "actions": ["read", "run", "stop"] },
    { "resource": "log",      "actions": ["read"] },
    { "resource": "dataset",  "actions": ["read"] }
  ]
}
```

!!! warning "Permission inheritance"
    Permissions are additive — a user with both `Viewer` and `pipeline-operator` roles has the union of both sets of permissions.

---

## Data Export

Export any dataset or pipeline output in multiple formats:

=== "CSV"

    ```bash
    product export my-dataset --format csv --output ./data.csv
    ```

=== "Parquet"

    ```bash
    product export my-dataset --format parquet --output ./data.parquet
    ```

=== "JSON Lines"

    ```bash
    product export my-dataset --format jsonl --output ./data.jsonl
    ```

=== "PDF Report"

    ```bash
    # Export a formatted PDF report of a resource's summary page
    product report my-dataset --format pdf --output ./report.pdf
    ```

---

## Next Steps

- [Video Demo](video-demo.md) — watch these features in action
- [Installation](../getting-started/installation.md) — set up your environment
