# How to upgrade the ECK-Operator chart

ECK-Operator is a modified/customized version of an upstream chart. The below details the steps required to update to a new version of the eck-operator package.

1. Navigate to the upstream [chart repo and folder](https://github.com/elastic/cloud-on-k8s/tree/main/deploy/eck-operator) and find the tag that corresponds with the new chart version for this update
    - Check the [upstream release highlights](https://www.elastic.co/guide/en/cloud-on-k8s/current/release-highlights.html) for any major changes or potential conflicts.

2. `git clone` the [eck-operator] repository](https://repo1.dso.mil/big-bang/product/packages/eck-operator) from Repo1 and checkout the `renovate/ironbank` branch.

3. Update the chart version in `./chart/Chart.yaml` and append or bump the `-bb.0` suffix (if missing or incorrect) to the chart version from upstream.

4. Ensure the Big Bang `./chart/Chart.yaml` and the target upstream version `Chart.yaml` align correctly with the following:
    - Check `appVersion` and `bigbang.dev/applicationVersions` in `./chart/Chart.yaml` to make sure they match and have updated to the correct version
    - Check the upstream chart dependencies and compare the dependency versions against the corresponding image tags in `./chart/values.yaml` to make sure they match

    **NOTE:** The Renovate issue may be blocked by one of the following conditions:
    - The upstream chart expects a newer image tag that does not yet exist in Iron Bank
      - If so, ensure that an issue exists in the associated Iron Bank container repository to track the upgrade version. Link the Iron Bank issue to the package Renovate issue for tracking purposes.
    - There is a newer image tag in Iron Bank, but is not yet supported or tested by upstream
    - If the newer image is a [major version](https://semver.org/) bump and/or contains breaking changes, the Renovate issue can be moved to `status::blocked` until the upstream chart catches up. If the newer image is only [a *patch* or *minor* version](https://semver.org/) bump, you can proceed with the Renovate (upgrading the image beyond the version referenced in the upstream chart).

5. Update `upstream.image.tag` in `./chart/values.yaml` to match the updated version in Iron Bank.

6. Update the `helm.sh/images` annotations in `./chart/Chart.yaml` to match updated versions in Iron Bank.

7. Update dependencies and binaries using `helm dependency update ./chart`.

8. Update `CHANGELOG.md` adding an entry for the new version and noting all changes (at minimum should include `Updated eck-operator from x.x.x to x.x.x`).

9. Generate the `README.md` updates by following the [guide in gluon](https://repo1.dso.mil/platform-one/big-bang/apps/library-charts/gluon/-/blob/master/docs/bb-package-readme.md).

10. Push up your changes, add upgrade notices if applicable, validate that CI passes.
    - If there are any failures, follow the information in the pipeline to make the necessary updates.
    - Add the `debug` label to the MR for more detailed information.
    - Reach out to the CODEOWNERS if needed.

11. (_Optional, only required if package changes are expected to have cascading effects on bigbang umbrella chart_) As part of your MR that modifies bigbang packages, you should modify the bigbang [bigbang/tests/test-values.yaml](https://repo1.dso.mil/big-bang/bigbang/-/blob/master/tests/test-values.yaml?ref_type=heads) to target your branch for CI/CD MR testing.

    - To do this, at a minimum, you will need to follow the instructions at [bigbang/docs/developer/test-package-against-bb.md](https://repo1.dso.mil/big-bang/bigbang/-/blob/master/docs/developer/test-package-against-bb.md?ref_type=heads) with changes for ECK-Operator enabled (the below is a reference, actual changes could be more depending on what changes where made to ECK-Operator in the pakcage MR).

### [test-values.yaml](https://repo1.dso.mil/big-bang/bigbang/-/blob/master/tests/test-values.yaml?ref_type=heads)
    ```yaml
    eckOperator:
      enabled: true
      git:
        tag: null
        branch: <my-package-branch-that-needs-testing>
      values:
        istio:
          hardened:
            enabled: true
      ### Additional components of ECK-Operator should be changed to reflect testing changes introduced in the package MR
    ```

12. Complete the manual testing steps in the following section.

13. Once all manual testing is complete, take your MR out of "Draft" status, assign reviewers, and add the review label.

# Testing new ECK-Operator Version

> NOTE: For these testing steps it is good to do them on both a clean install and an upgrade. For clean install, point ECK-Operator to your branch. For an upgrade do an install with ECK-Operator pointing to the latest tag, then perform a helm upgrade with ECK-Operator pointing to your branch.

The following overrides can be used for a bare minimum ECK-Operator deployment:

```yaml
istiod:
  enabled: true
  values:
    hardened:
      enabled: true
istioCRDs:
  enabled: true
istioGateway:
  enabled: true

networkPolicies:
  enabled: true

neuvector:
  enabled: false

monitoring:
  enabled: true

elasticsearchKibana:
  enabled: true
  license:
    trial: true

eckOperator:
  # -- Toggle deployment of ECK Operator.
  enabled: true
  git:
    tag: null
    branch: renovate/ironbank
```

- Ensure that all ECK-Operator pods are up and running.
- Ensure that all elasticsearch-kibana are deploying and running.
- Login to [Prometheus](https://prometheus.dev.bigbang.mil/), validate under `Status` -> `Targets` that all eck-operator targets are showing as up

> When in doubt with any testing or upgrade steps, reach out to the CODEOWNERS for assistance.




