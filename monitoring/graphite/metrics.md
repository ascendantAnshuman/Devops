# Graphite Metrics

Send website and infrastructure metrics to Graphite using this namespace:

```text
abc.website.cpu.usage_percent
abc.website.memory.usage_bytes
abc.website.network.rx_bytes
abc.website.network.tx_bytes
abc.website.http.available
abc.website.uptime.seconds
```

Example Carbon plaintext metric:

```text
abc.website.http.available 1 1767225600
```

Metric collection can be handled by collectd, Telegraf, StatsD, or a Kubernetes metrics exporter configured to write to Graphite.

