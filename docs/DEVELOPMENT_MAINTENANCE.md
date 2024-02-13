# How to upgrade the ECK-Operator chart

ECK-Operator is a modified/customized version of an upstream chart. The below details the steps required to update to a new version of the eck-operator package.

1. Navigate to the upstream [chart repo and folder](https://github.com/elastic/cloud-on-k8s/tree/main/deploy/eck-operator) and find the tag that corresponds with the new chart version for this update
    - Check the [upstream release highlights](https://www.elastic.co/guide/en/cloud-on-k8s/current/release-highlights.html) for any major changes or potential conflicts.

2. Checkout the `renovate/ironbank` branch.


3. From the root of the repo run `kpt pkg update chart@<tag> --strategy alpha-git-patch`, where `<tag>` is found in step 1, checkout the chart/Kptfile ref for tag naming
    - Run a KPT package update
    ```
    kpt pkg update chart@tempo-<tag> --strategy alpha-git-patch
    ```

4. Modify the version in Chart.yaml and append -bb.0 to the chart version from upstream. See Update main chart section of this document.

5. Update eck-operator dependencies and binaries using `helm dependency update ./chart`
    ```
    helm dependency update ./chart
    ```

6. Update `CHANGELOG.md` adding an entry for the new version and noting all changes (at minimum should include `Updated eck-operator to x.x.x`).

7. Generate the `README.md` updates by following the [guide in gluon](https://repo1.dso.mil/platform-one/big-bang/apps/library-charts/gluon/-/blob/master/docs/bb-package-readme.md).

8. Push up your changes, add upgrade notices if applicable, validate that CI passes.
    - If there are any failures, follow the information in the pipeline to make the necessary updates.
    - Add the `debug` label to the MR for more detailed information.
    - Reach out to the CODEOWNERS if needed.

9. Perform the steps below for manual testing. CI provides a good set of basic smoke tests but it is beneficial to run some additional checks.

# Modifications made to upstream

## chart/values.yaml

* updated `image.repository` to iron bank for hardened images
```yaml
image:
  # repository is the container image prefixed by the registry name.
  repository: docker.elastic.co/eck/eck-operator
```

* updated `resources` limits and resources
```yaml
# resources define the container resource limits for the operator.
resources: # Limits equal to request to provide QOS per BB Charter
  limits:
    cpu: 200m # Values pulled from PB IL2 cluster
    memory: 256Mi
  requests:
    cpu: 200m
    memory: 256Mi
```

* Add fsGroup and supplementalGrousp to `podSecurityContext`
```yaml
# podSecurityContext defines the pod security context for the operator pod.
podSecurityContext:
  runAsNonRoot: true
  fsGroup: 1001
  supplementalGroups: [1001]
```

* Add runAsUser and runAsGroup to `securityContext`
```yaml
# securityContext defines the security context of the operator container.
securityContext:
  allowPrivilegeEscalation: false
  capabilities:
    drop:
      - ALL
  readOnlyRootFilesystem: true
  runAsNonRoot: true
  runAsUser: 1001
  runAsGroup: 1001
```

* `config.metricsPort` set to 4321
```yaml
config:
  # logVerbosity defines the logging level. Valid values are as follows:
  # -2: Errors only
  # -1: Errors and warnings
  #  0: Errors, warnings, and information
  #  number greater than 0: Errors, warnings, information, and debug details.
  logVerbosity: "0"

  # metricsPort defines the port to expose operator metrics. Set to 0 to disable metrics reporting.
  metricsPort: "4321"
```

* Added `license` values
* Added `networkPolicies` values
* Added `monitoring` values
* Added `openshift` values
* Added `istio` values
* Added `upgradeCrds` values

## chart/templates/bigbang/*
* Added BigBang Network Policies as applicable
* Added BigBang Authorization Policies as applicable
* Added OpenShift CRDS as applicable


# Testing new ECK-Operator Version

> NOTE: For these testing steps it is good to do them on both a clean install and an upgrade. For clean install, point ECK-Operator to your branch. For an upgrade do an install with ECK-Operator pointing to the latest tag, then perform a helm upgrade with ECK-Operator pointing to your branch.

ECK-Operator can be installed standalone and is not dependent on any other packages.

The following overrides can be used for a bare minimum ECK-Operator deployment:

```yaml
kiali:
  enabled: false

kyverno:
  enabled: false

kyvernoPolicies:
  enabled: false
  values:
    validationFailureAction: "audit"

kyvernoReporter:
  enabled: false

promtail:
  enabled: false

loki:
  enabled: false

neuvector:
  enabled: false
  values:
    k3s:
      enabled: true

tempo:
  enabled: false

monitoring:
  enabled: false

grafana:
  enabled: false

addons:
  metricsServer:
    enabled: false

eckOperator:
  # -- Toggle deployment of ECK Operator.
  enabled: true
  git:
    tag: null
    branch: renovate/ironbank
```

- Ensure that all ECK-Operator pods are up and running.

> When in doubt with any testing or upgrade steps, reach out to the CODEOWNERS for assistance.




