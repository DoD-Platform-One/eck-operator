<!-- Warning: Do not manually edit this file. See notes on gluon + helm-docs at the end of this file for more information. -->
# eck-operator

![Version: 3.2.0-bb.1](https://img.shields.io/badge/Version-3.2.0--bb.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 3.2.0](https://img.shields.io/badge/AppVersion-3.2.0-informational?style=flat-square) ![Maintenance Track: bb_integrated](https://img.shields.io/badge/Maintenance_Track-bb_integrated-green?style=flat-square)

Elastic Cloud on Kubernetes (ECK) operator

## Upstream References

- <https://github.com/elastic/cloud-on-k8s>

## Upstream Release Notes

- [Find upstream chart's release notes and CHANGELOG here](https://github.com/elastic/cloud-on-k8s/releases)
- [Find upstream application's release notes and CHANGELOG here](https://www.elastic.co/guide/en/cloud-on-k8s/current/eck-release-notes.html)

## Learn More

- [Application Overview](docs/overview.md)
- [Other Documentation](docs/)

## Pre-Requisites

- Kubernetes Cluster deployed
- Kubernetes config installed in `~/.kube/config`
- Helm installed

Kubernetes: `>=1.21.0-0`

Install Helm

https://helm.sh/docs/intro/install/

## Deployment

- Clone down the repository
- cd into directory

```bash
helm install eck-operator chart/
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| istio.enabled | bool | `true` |  |
| istio.injection | string | `"enabled"` |  |
| istio.mtls.mode | string | `"STRICT"` |  |
| istio.sidecar.enabled | bool | `true` |  |
| istio.sidecar.outboundTrafficPolicyMode | string | `"REGISTRY_ONLY"` |  |
| istio.authorizationPolicies.enabled | bool | `true` |  |
| istio.authorizationPolicies.generateFromNetpol | bool | `true` |  |
| networkPolicies.enabled | bool | `false` |  |
| networkPolicies.egress.definitions.elasticsearch.to[0].namespaceSelector | object | `{}` |  |
| networkPolicies.egress.definitions.elasticsearch.to[0].podSelector.matchLabels."common.k8s.elastic.co/type" | string | `"elasticsearch"` |  |
| networkPolicies.egress.definitions.elasticsearch.to[0].ports[0].port | int | `9200` |  |
| networkPolicies.egress.definitions.elasticsearch.to[0].ports[0].protocol | string | `"TCP"` |  |
| networkPolicies.egress.definitions.kibana.to[0].namespaceSelector | object | `{}` |  |
| networkPolicies.egress.definitions.kibana.to[0].podSelector.matchLabels."common.k8s.elastic.co/type" | string | `"kibana"` |  |
| networkPolicies.egress.definitions.kibana.to[0].ports[0].port | int | `5601` |  |
| networkPolicies.egress.definitions.kibana.to[0].ports[0].protocol | string | `"TCP"` |  |
| networkPolicies.egress.from.elastic-operator.to.definition.kubeAPI | bool | `true` |  |
| networkPolicies.egress.from.elastic-operator.to.definition.elasticsearch | bool | `true` |  |
| networkPolicies.egress.from.elastic-operator.to.definition.kibana | bool | `true` |  |
| networkPolicies.egress.from.elastic-operator.to.k8s.tempo/tempo:9411 | bool | `true` |  |
| networkPolicies.ingress.to.elastic-operator:8080.from.k8s.monitoring/prometheus | bool | `true` |  |
| networkPolicies.additionalPolicies | list | `[]` |  |
| monitoring.enabled | bool | `false` |  |
| serviceMonitor.enabled | bool | `false` |  |
| serviceMonitor.additionalLabels | object | `{}` | Additional labels for the service monitor |
| serviceMonitor.interval | string | `"30s"` | Scrape interval. If not set, the Prometheus default scrape interval is used. |
| serviceMonitor.metricRelabelings | list | `[]` | MetricRelabelConfigs to apply to samples after scraping, but before ingestion. ref: https://github.com/prometheus-operator/prometheus-operator/blob/main/Documentation/api.md#relabelconfig |
| serviceMonitor.scheme | string | `"https"` | Customize tls parameters for the service monitor |
| serviceMonitor.tlsConfig | object | `{}` |  |
| serviceMonitor.relabelings | list | `[]` | RelabelConfigs to apply to samples before scraping ref: https://github.com/prometheus-operator/prometheus-operator/blob/main/Documentation/api.md#relabelconfig |
| serviceMonitor.enableHttp2 | bool | `false` | Enable HTTP/2 for the service monitor scraping endpoint. Default is false for compatibility. |
| openshift | bool | `false` |  |
| license.trial | bool | `false` |  |
| license.keyJSON | string | `""` |  |
| upgradeCrds.enabled | bool | `false` |  |
| upgradeCrds.image.repository | string | `"registry1.dso.mil/ironbank/big-bang/base"` |  |
| upgradeCrds.image.tag | string | `"2.1.0"` |  |
| upstream.imagePullSecrets[0].name | string | `"private-registry"` |  |
| upstream.image.repository | string | `"registry1.dso.mil/ironbank/elastic/eck-operator/eck-operator"` |  |
| upstream.image.tag | string | `"3.2.0"` |  |
| upstream.image.pullPolicy | string | `"IfNotPresent"` |  |
| upstream.image.fips | bool | `false` |  |
| upstream.resources.limits.cpu | string | `"200m"` |  |
| upstream.resources.limits.memory | string | `"256Mi"` |  |
| upstream.resources.requests.cpu | string | `"200m"` |  |
| upstream.resources.requests.memory | string | `"256Mi"` |  |
| upstream.podSecurityContext.runAsNonRoot | bool | `true` |  |
| upstream.podSecurityContext.fsGroup | int | `1001` |  |
| upstream.podSecurityContext.supplementalGroups[0] | int | `1001` |  |
| upstream.securityContext.allowPrivilegeEscalation | bool | `false` |  |
| upstream.securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| upstream.securityContext.readOnlyRootFilesystem | bool | `true` |  |
| upstream.securityContext.runAsNonRoot | bool | `true` |  |
| upstream.securityContext.runAsUser | int | `1001` |  |
| upstream.securityContext.runAsGroup | int | `1001` |  |
| upstream.config.metrics.port | string | `"8080"` |  |

## Contributing

Please see the [contributing guide](./CONTRIBUTING.md) if you are interested in contributing.

---

_This file is programatically generated using `helm-docs` and some BigBang-specific templates. The `gluon` repository has [instructions for regenerating package READMEs](https://repo1.dso.mil/big-bang/product/packages/gluon/-/blob/master/docs/bb-package-readme.md)._

