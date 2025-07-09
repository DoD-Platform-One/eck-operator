<!-- Warning: Do not manually edit this file. See notes on gluon + helm-docs at the end of this file for more information. -->
# eck-operator

![Version: 3.0.0-bb.1](https://img.shields.io/badge/Version-3.0.0--bb.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 3.0.0](https://img.shields.io/badge/AppVersion-3.0.0-informational?style=flat-square) ![Maintenance Track: bb_integrated](https://img.shields.io/badge/Maintenance_Track-bb_integrated-green?style=flat-square)

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
| upstream.nameOverride | string | `"elastic-operator"` |  |
| upstream.fullnameOverride | string | `"elastic-operator"` |  |
| upstream.managedNamespaces | list | `[]` |  |
| upstream.installCRDs | bool | `true` |  |
| upstream.replicaCount | int | `1` |  |
| upstream.image.repository | string | `"registry1.dso.mil/ironbank/elastic/eck-operator/eck-operator"` |  |
| upstream.image.tag | string | `"3.0.0"` |  |
| upstream.image.pullPolicy | string | `"IfNotPresent"` |  |
| upstream.image.fips | bool | `false` |  |
| upstream.priorityClassName | string | `""` |  |
| upstream.imagePullSecrets | list | `[]` |  |
| upstream.resources.limits.cpu | string | `"200m"` |  |
| upstream.resources.limits.memory | string | `"256Mi"` |  |
| upstream.resources.requests.cpu | string | `"200m"` |  |
| upstream.resources.requests.memory | string | `"256Mi"` |  |
| upstream.statefulsetAnnotations | object | `{}` |  |
| upstream.statefulsetLabels | object | `{}` |  |
| upstream.podAnnotations | object | `{}` |  |
| upstream.podLabels | object | `{}` |  |
| upstream.podSecurityContext.runAsNonRoot | bool | `true` |  |
| upstream.podSecurityContext.fsGroup | int | `1001` |  |
| upstream.podSecurityContext.supplementalGroups[0] | int | `1001` |  |
| upstream.securityContext.allowPrivilegeEscalation | bool | `false` |  |
| upstream.securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| upstream.securityContext.readOnlyRootFilesystem | bool | `true` |  |
| upstream.securityContext.runAsNonRoot | bool | `true` |  |
| upstream.securityContext.runAsUser | int | `1001` |  |
| upstream.securityContext.runAsGroup | int | `1001` |  |
| upstream.nodeSelector | object | `{}` |  |
| upstream.tolerations | list | `[]` |  |
| upstream.affinity | object | `{}` |  |
| upstream.podDisruptionBudget.enabled | bool | `false` |  |
| upstream.podDisruptionBudget.minAvailable | int | `1` |  |
| upstream.env | list | `[]` |  |
| upstream.volumeMounts | list | `[]` |  |
| upstream.volumes | list | `[]` |  |
| upstream.createClusterScopedResources | bool | `true` |  |
| upstream.automountServiceAccountToken | bool | `true` |  |
| upstream.serviceAccount.create | bool | `true` |  |
| upstream.serviceAccount.automountServiceAccountToken | bool | `true` |  |
| upstream.serviceAccount.annotations | object | `{}` |  |
| upstream.serviceAccount.name | string | `""` |  |
| upstream.tracing.enabled | bool | `false` |  |
| upstream.tracing.config.ELASTIC_APM_SERVER_URL | string | `"http://localhost:8200"` |  |
| upstream.tracing.config.ELASTIC_APM_SERVER_TIMEOUT | string | `"30s"` |  |
| upstream.refs.enforceRBAC | bool | `false` |  |
| upstream.webhook.enabled | bool | `true` |  |
| upstream.webhook.caBundle | string | `"Cg=="` |  |
| upstream.webhook.certManagerCert | string | `nil` |  |
| upstream.webhook.certsDir | string | `"/tmp/k8s-webhook-server/serving-certs"` |  |
| upstream.webhook.failurePolicy | string | `"Ignore"` |  |
| upstream.webhook.manageCerts | bool | `true` |  |
| upstream.webhook.namespaceSelector | object | `{}` |  |
| upstream.webhook.objectSelector | object | `{}` |  |
| upstream.webhook.port | int | `9443` |  |
| upstream.webhook.certsSecret | string | `""` |  |
| upstream.hostNetwork | bool | `false` |  |
| upstream.dnsPolicy | string | `""` |  |
| upstream.dnsConfig | object | `{}` |  |
| upstream.softMultiTenancy.enabled | bool | `false` |  |
| upstream.kubeAPIServerIP | string | `nil` |  |
| upstream.telemetry.disabled | bool | `false` |  |
| upstream.telemetry.distributionChannel | string | `"helm"` |  |
| upstream.config.logVerbosity | string | `"0"` |  |
| upstream.config.metricsPort | int | `0` |  |
| upstream.config.metrics.port | string | `"4321"` |  |
| upstream.config.metrics.secureMode.enabled | bool | `false` |  |
| upstream.config.metrics.secureMode.tls.certificateSecret | string | `""` |  |
| upstream.config.containerRegistry | string | `"docker.elastic.co"` |  |
| upstream.config.maxConcurrentReconciles | string | `"3"` |  |
| upstream.config.caValidity | string | `"8760h"` |  |
| upstream.config.caRotateBefore | string | `"24h"` |  |
| upstream.config.caDir | string | `""` |  |
| upstream.config.certificatesValidity | string | `"8760h"` |  |
| upstream.config.certificatesRotateBefore | string | `"24h"` |  |
| upstream.config.disableConfigWatch | bool | `false` |  |
| upstream.config.exposedNodeLabels[0] | string | `"topology.kubernetes.io/.*"` |  |
| upstream.config.exposedNodeLabels[1] | string | `"failure-domain.beta.kubernetes.io/.*"` |  |
| upstream.config.ipFamily | string | `""` |  |
| upstream.config.setDefaultSecurityContext | string | `"auto-detect"` |  |
| upstream.config.kubeClientTimeout | string | `"60s"` |  |
| upstream.config.elasticsearchClientTimeout | string | `"180s"` |  |
| upstream.config.validateStorageClass | bool | `true` |  |
| upstream.config.enableLeaderElection | bool | `true` |  |
| upstream.config.elasticsearchObservationInterval | string | `"10s"` |  |
| upstream.config.ubiOnly | bool | `false` |  |
| upstream.podMonitor.enabled | bool | `false` |  |
| upstream.podMonitor.labels | object | `{}` |  |
| upstream.podMonitor.annotations | object | `{}` |  |
| upstream.podMonitor.interval | string | `"5m"` |  |
| upstream.podMonitor.scrapeTimeout | string | `"30s"` |  |
| upstream.podMonitor.podTargetLabels | list | `[]` |  |
| upstream.podMonitor.podMetricsEndpointConfig | object | `{}` |  |
| upstream.serviceMonitor.enabled | bool | `true` |  |
| upstream.serviceMonitor.caSecret | string | `""` |  |
| upstream.serviceMonitor.caMountDirectory | string | `"/etc/prometheus/secrets/"` |  |
| upstream.serviceMonitor.insecureSkipVerify | bool | `true` |  |
| upstream.global.manifestGen | bool | `false` |  |
| upstream.global.createOperatorNamespace | bool | `true` |  |
| upstream.global.kubeVersion | string | `"1.21.0"` |  |
| license.trial | bool | `false` |  |
| license.keyJSON | string | `""` |  |
| networkPolicies.enabled | bool | `false` |  |
| networkPolicies.controlPlaneCidr | string | `"0.0.0.0/0"` |  |
| networkPolicies.additionalPolicies | list | `[]` |  |
| monitoring.enabled | bool | `false` |  |
| openshift | bool | `false` |  |
| istio.enabled | bool | `false` |  |
| istio.hardened.enabled | bool | `false` |  |
| istio.hardened.customAuthorizationPolicies | list | `[]` |  |
| istio.hardened.outboundTrafficPolicyMode | string | `"REGISTRY_ONLY"` |  |
| istio.hardened.customServiceEntries | list | `[]` |  |
| istio.hardened.tempo.enabled | bool | `false` |  |
| istio.hardened.tempo.namespaces[0] | string | `"tempo"` |  |
| istio.hardened.tempo.principals[0] | string | `"cluster.local/ns/tempo/sa/tempo-tempo"` |  |
| istio.mtls.mode | string | `"STRICT"` |  |
| upgradeCrds.enabled | bool | `false` |  |
| upgradeCrds.image.repository | string | `"registry1.dso.mil/ironbank/big-bang/base"` |  |
| upgradeCrds.image.tag | string | `"2.1.0"` |  |

## Contributing

Please see the [contributing guide](./CONTRIBUTING.md) if you are interested in contributing.

---

_This file is programatically generated using `helm-docs` and some BigBang-specific templates. The `gluon` repository has [instructions for regenerating package READMEs](https://repo1.dso.mil/big-bang/product/packages/gluon/-/blob/master/docs/bb-package-readme.md)._

