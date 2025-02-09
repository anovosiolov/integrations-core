# Linkerd Integration

## Overview

This check collects distributed system observability metrics from [Linkerd][1].

## Setup

Follow the instructions below to install and configure this check for an Agent running on a host. For containerized environments, see the [Autodiscovery Integration Templates][2] for guidance on applying these instructions.

### Installation

The Linkerd check is included in the [Datadog Agent][3] package, so you don't need to install anything else on your server.

### Configuration

Edit the `linkerd.d/conf.yaml` file, in the `conf.d/` folder at the root of your [Agent's configuration directory][4].
See [sample linkerd.d/conf.yaml][5] for all available configuration options.

### Validation

[Run the Agent's `status` subcommand][6] and look for `linkerd` under the Checks section.

## Data Collected

### Metrics

See [metadata.csv][7] for a list of default metrics provided by this integration.

For linkerd v1, see [finagle metrics docs][8] for a detailed description of some of the available metrics and [this gist][9] for an example of metrics exposed by linkerd.

Attention: Depending on your linkerd configuration, some metrics might not be exposed by linkerd.

To list the metrics exposed by your current configuration, run
```bash
curl <linkerd_prometheus_endpoint>
```
Where `linkerd_prometheus_endpoint` is the linkerd prometheus endpoint (you should use the same value as the `prometheus_url` config key in your `linkerd.yaml`)

If you need to use a metric that is not provided by default, you can add an entry to `linkerd.yaml`.

Simply follow the examples present in the [default configuration][5].

### Service Checks

`linkerd.prometheus.health`:
Returns CRITICAL if the Agent fails to connect to the prometheus endpoint, otherwise returns UP.

## Troubleshooting
Need help? Contact [Datadog support][10].

[1]: https://linkerd.io
[2]: https://docs.datadoghq.com/agent/autodiscovery/integrations
[3]: https://app.datadoghq.com/account/settings#agent
[4]: https://docs.datadoghq.com/agent/guide/agent-configuration-files/#agent-configuration-directory
[5]: https://github.com/DataDog/integrations-core/blob/master/linkerd/datadog_checks/linkerd/data/conf.yaml.example
[6]: https://docs.datadoghq.com/agent/guide/agent-commands/#agent-status-and-information
[7]: https://github.com/DataDog/integrations-core/blob/master/linkerd/metadata.csv
[8]: https://twitter.github.io/finagle/guide/Metrics.html
[9]: https://gist.githubusercontent.com/arbll/2f63a5375a4d6d5acface6ca8a51e2ab/raw/bc35ed4f0f4bac7e2643a6009f45f9068f4c1d12/gistfile1.txt
[10]: https://docs.datadoghq.com/help
