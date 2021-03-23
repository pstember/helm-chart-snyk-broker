# helm-chart-snyk-broker

Helm chart used to deploy a [Snyk Broker](https://github.com/snyk/broker) into Kubernetes. Currently only supports container registries.

### Requirements

This chart requires already having generated a Snyk Broker token and ACR credentials.

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
| `image.tag`                | Broker image tag                                                                                       | `container-registry-agent`                                                    |
| `image.repository`         | Image repository                                                                                       | `snyk/broker`                                                                 |
| `image.pullPolicy`         | Image pull policy                                                                                      | `IfNotPresent`                                                                |
| `replicas`                 | Desired number of Broker pods                                                                          | `1`                                                                           |
| `resources`                | Broker pod CPU/memory resource requests/limits                                                         | `{requests: {cpu: 200m, memory: 200Mi}, limits: {cpu: 300m, memory: 300Mi }}` |
| `cr.url`             | URL of your CR agent (including scheme and - port) to which brokered requests would be forwarded.      | None                                                                          |
| `cr.credentials`           | Base64-encoded credentials json used by agent to access container registry                             | None                                                                          |
| `cr.useExistingSecret`     | Whether a CR token secret already exists, if set to `false` one will be automatically generated        | `false`                                                                       |
| `cr.secretName`            | CR token secret name                                                                                   | `cr-token`                                                                |
| `cr.secretKey`             | Key under which the CR token is found in the secret                                                    | `token`                                                                       |
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
