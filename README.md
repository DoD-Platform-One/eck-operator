<!-- Warning: Do not manually edit this file. See notes on gluon + helm-docs at the end of this file for more information. -->
# eck-operator

![Version: 3.1.0-bb.0](https://img.shields.io/badge/Version-3.1.0--bb.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 3.1.0](https://img.shields.io/badge/AppVersion-3.1.0-informational?style=flat-square) ![Maintenance Track: bb_integrated](https://img.shields.io/badge/Maintenance_Track-bb_integrated-green?style=flat-square)

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
| istio.enabled | bool | `false` |  |
| istio.hardened.enabled | bool | `false` |  |
| istio.hardened.customAuthorizationPolicies | list | `[]` |  |
| istio.hardened.outboundTrafficPolicyMode | string | `"REGISTRY_ONLY"` |  |
| istio.hardened.customServiceEntries | list | `[]` |  |
| istio.hardened.tempo.enabled | bool | `false` |  |
| istio.hardened.tempo.namespaces[0] | string | `"tempo"` |  |
| istio.hardened.tempo.principals[0] | string | `"cluster.local/ns/tempo/sa/tempo-tempo"` |  |
| istio.mtls.mode | string | `"STRICT"` |  |
| networkPolicies.enabled | bool | `false` |  |
| networkPolicies.controlPlaneCidr | string | `"0.0.0.0/0"` |  |
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
| upstream.image.tag | string | `"3.1.0"` |  |
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

