<!-- Warning: Do not manually edit this file. See notes on gluon + helm-docs at the end of this file for more information. -->
# eck-operator

![Version: 2.16.1-bb.1](https://img.shields.io/badge/Version-2.16.1--bb.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 2.16.1](https://img.shields.io/badge/AppVersion-2.16.1-informational?style=flat-square) ![Maintenance Track: bb_integrated](https://img.shields.io/badge/Maintenance_Track-bb_integrated-green?style=flat-square)

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
| nameOverride | string | `"elastic-operator"` |  |
| fullnameOverride | string | `"elastic-operator"` |  |
| managedNamespaces | list | `[]` |  |
| installCRDs | bool | `true` |  |
| replicaCount | int | `1` |  |
| image.repository | string | `"registry1.dso.mil/ironbank/elastic/eck-operator/eck-operator"` |  |
| image.tag | string | `"2.16.1"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.fips | bool | `false` |  |
| priorityClassName | string | `""` |  |
| imagePullSecrets | list | `[]` |  |
| resources.limits.cpu | string | `"200m"` |  |
| resources.limits.memory | string | `"256Mi"` |  |
| resources.requests.cpu | string | `"200m"` |  |
| resources.requests.memory | string | `"256Mi"` |  |
| statefulsetAnnotations | object | `{}` |  |
| statefulsetLabels | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podLabels | object | `{}` |  |
| podSecurityContext.runAsNonRoot | bool | `true` |  |
| podSecurityContext.fsGroup | int | `1001` |  |
| podSecurityContext.supplementalGroups[0] | int | `1001` |  |
| securityContext.allowPrivilegeEscalation | bool | `false` |  |
| securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| securityContext.readOnlyRootFilesystem | bool | `true` |  |
| securityContext.runAsNonRoot | bool | `true` |  |
| securityContext.runAsUser | int | `1001` |  |
| securityContext.runAsGroup | int | `1001` |  |
| nodeSelector | object | `{}` |  |
| tolerations | list | `[]` |  |
| affinity | object | `{}` |  |
| podDisruptionBudget.enabled | bool | `false` |  |
| podDisruptionBudget.minAvailable | int | `1` |  |
| env | list | `[]` |  |
| volumeMounts | list | `[]` |  |
| volumes | list | `[]` |  |
| createClusterScopedResources | bool | `true` |  |
| automountServiceAccountToken | bool | `true` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.automountServiceAccountToken | bool | `true` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.name | string | `""` |  |
| tracing.enabled | bool | `false` |  |
| tracing.config.ELASTIC_APM_SERVER_URL | string | `"http://localhost:8200"` |  |
| tracing.config.ELASTIC_APM_SERVER_TIMEOUT | string | `"30s"` |  |
| refs.enforceRBAC | bool | `false` |  |
| webhook.enabled | bool | `true` |  |
| webhook.caBundle | string | `"Cg=="` |  |
| webhook.certManagerCert | string | `nil` |  |
| webhook.certsDir | string | `"/tmp/k8s-webhook-server/serving-certs"` |  |
| webhook.failurePolicy | string | `"Ignore"` |  |
| webhook.manageCerts | bool | `true` |  |
| webhook.namespaceSelector | object | `{}` |  |
| webhook.objectSelector | object | `{}` |  |
| webhook.port | int | `9443` |  |
| webhook.certsSecret | string | `""` |  |
| hostNetwork | bool | `false` |  |
| softMultiTenancy.enabled | bool | `false` |  |
| kubeAPIServerIP | string | `nil` |  |
| telemetry.disabled | bool | `false` |  |
| telemetry.distributionChannel | string | `"helm"` |  |
| config.logVerbosity | string | `"0"` |  |
| config.metricsPort | int | `0` |  |
| config.metrics.port | string | `"4321"` |  |
| config.metrics.secureMode.enabled | bool | `false` |  |
| config.metrics.secureMode.tls.certificateSecret | string | `""` |  |
| config.containerRegistry | string | `"docker.elastic.co"` |  |
| config.maxConcurrentReconciles | string | `"3"` |  |
| config.caValidity | string | `"8760h"` |  |
| config.caRotateBefore | string | `"24h"` |  |
| config.caDir | string | `""` |  |
| config.certificatesValidity | string | `"8760h"` |  |
| config.certificatesRotateBefore | string | `"24h"` |  |
| config.disableConfigWatch | bool | `false` |  |
| config.exposedNodeLabels[0] | string | `"topology.kubernetes.io/.*"` |  |
| config.exposedNodeLabels[1] | string | `"failure-domain.beta.kubernetes.io/.*"` |  |
| config.ipFamily | string | `""` |  |
| config.setDefaultSecurityContext | string | `"auto-detect"` |  |
| config.kubeClientTimeout | string | `"60s"` |  |
| config.elasticsearchClientTimeout | string | `"180s"` |  |
| config.validateStorageClass | bool | `true` |  |
| config.enableLeaderElection | bool | `true` |  |
| config.elasticsearchObservationInterval | string | `"10s"` |  |
| config.ubiOnly | bool | `false` |  |
| podMonitor.enabled | bool | `false` |  |
| podMonitor.labels | object | `{}` |  |
| podMonitor.annotations | object | `{}` |  |
| podMonitor.interval | string | `"5m"` |  |
| podMonitor.scrapeTimeout | string | `"30s"` |  |
| podMonitor.podTargetLabels | list | `[]` |  |
| podMonitor.podMetricsEndpointConfig | object | `{}` |  |
| serviceMonitor.enabled | bool | `true` |  |
| serviceMonitor.caSecret | string | `""` |  |
| serviceMonitor.caMountDirectory | string | `"/etc/prometheus/secrets/"` |  |
| serviceMonitor.insecureSkipVerify | bool | `true` |  |
| global.manifestGen | bool | `false` |  |
| global.createOperatorNamespace | bool | `true` |  |
| global.kubeVersion | string | `"1.21.0"` |  |
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

