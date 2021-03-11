# helm-chart-snyk-broker

Helm chart used to deploy a [Snyk Broker](https://github.com/snyk/broker) into Kubernetes. Currently supports GitHub Enterprise as the SCM.

### Requirements

This chart requires already having generated a Snyk Broker token and GitHub Enterprise token.

### Installing the Chart

To install the chart with the release name `my-broker-release`:

```bash
helm upgrade [-i] --name my-broker-release . -f <your-config-file>.yaml
```

### Uninstalling the Chart

To uninstall the `my-broker-release` deployment:

```bash
helm delete my-broker-release
```

### Configuration

The following table lists the configurable parameters of the Event Exporter chart and their default values.

| Parameter                  | Description                                                                                            | Default value                                                                 |
| :-----------------------   | :----------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------- |
| `name`                     | Release name                                                                                           | `snyk-broker`                                                                 |
| `image.tag`                | Broker image tag                                                                                       | `github-enterprise`                                                               |
| `image.repository`         | Image repository                                                                                       | `snyk/broker`                                                                 |
| `image.pullPolicy`         | Image pull policy                                                                                      | `IfNotPresent`                                                                |
| `replicas`                 | Desired number of Broker pods                                                                          | `1`                                                                           |
| `resources`                | Broker pod CPU/memory resource requests/limits                                                         | `{requests: {cpu: 200m, memory: 200Mi}, limits: {cpu: 300m, memory: 300Mi }}` |
| `github.url`               | Hostname of your GitHub Enterprise deployment                                                                     | None                                                                          |
| `github.api_url`               | API endpoint of your GitHub Enterprise deployment                                                                     | None                                                                          |
| `github.graphql_url`               | graphql endpoint of your GitHub Enterprise deployment                                                                     | None                                                                          |
| `github.token`             | GitHub Enterprise personal access token with full repo, read:org and admin:repo_hook scopes                                                       | None                                                                          |
| `github.useExistingSecret` | Whether a GitHub Enterprise token secret already exists, if set to `false` one will be automatically generated    | `false`                                                                       |
| `github.secretName`        | GitHub Enterprise token secret name                                                                               | `github-token`                                                                |
| `github.secretKey`         | Key under which the GitHub Enterprise token is found in the secret                                                | `token`                                                                       |
| `broker.url`               | The address at which the Broker client will be accessible                                              | None                                                                          |
| `broker.token`             | Snyk Broker token                                                                                      | None                                                                          |
| `broker.useExistingSecret` | Whether a Broker token secret already exists, if set to `false` one will be automatically generated    | `false`                                                                       |
| `broker.secretName`        | Broker token secret name                                                                               | `broker-token`                                                                |
| `broker.secretKey`         | Key under which the Broker token is found in the secret                                                | `token`                                                                       |
| `ca`                       | Location (within the Broker image) to provide an internal CA certificate.                              | None                                                                          |
| `deployment.annotations`   | Deployment annotations                                                                                 | `{}`                                                                          |
| `deployment.labels`        | Deployment labels                                                                                      | `{}`                                                                          |
| `service.type`             | Kubernetes service type                                                                                | `ClusterIP`                                                                   |
| `service.port`             | Kubernetes service port                                                                                | `8000`                                                                        |
| `service.targetPort`       | Kubernetes service target port, the PORT environment variable in Broker will also be set to this value | `8000`                                                                        |
| `service.nodePort`         | Kubernetes service node port                                                                           | None                                                                          |
| `service.annotations`      | Kubernetes service annotations                                                                         | `{}`                                                                          |
| `service.labels`           | Kubernetes service labels                                                                              | `{}`                                                                          |
| `ingress.enabled`          | Enables Ingress                                                                                        | `false`                                                                       |
| `ingress.annotations`      | Ingress annotations                                                                                    | `{}`                                                                          |
| `ingress.labels`           | Ingress labels                                                                                         | `{}`                                                                          |
| `ingress.hosts`            | Ingress host names                                                                                     | None                                                                          |
| `ingress.tls`              | Ingress TLS configurations                                                                             | None                                                                          |
