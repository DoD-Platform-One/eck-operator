# Upgrading ECK-Operator

ECK-Operator is a modified/customized version of an upstream chart. The below details the steps required to update to a new version of the eck-operator package.

1. Check the [upstream release hilights](https://www.elastic.co/guide/en/cloud-on-k8s/current/release-highlights.html) for any major changes or potential conflicts.

1. Navigate to the [upstream chart repo and folder](https://github.com/elastic/cloud-on-k8s/tree/main/deploy/eck-operator) and find the tag that corresponds with the new chart version for this image update. Typically, in this package, the application version and helm chart version are the same. 

1. Checkout the `renovate/ironbank` branch. This branch will already have the updates you need for the images.

1. From the root of the repo run `kpt pkg update chart@${chart-version} --strategy alpha-git-patch` replacing `${chart-version}` with the version tag you got in step 1. You may be prompted to resolve some conflicts - choose what makes sense (if there are BB additions/changes keep them, if there are upstream additions/changes keep them).

1. Modify the `version` in `Chart.yaml` - you will want to append `-bb.0` to the chart version from upstream.

1. Update eck-operator custom resource definitions
    ```
    helm dependency update ./chart
    ```

1. Update `CHANGELOG.md` adding an entry for the new version and noting all changes (at minimum should include `Updated eck-operator to x.x.x`).

1. Generate the `README.md` updates by following the [guide in gluon](https://repo1.dso.mil/platform-one/big-bang/apps/library-charts/gluon/-/blob/master/docs/bb-package-readme.md).

1. Push up your changes, validate that CI passes. If there are any failures follow the information in the pipeline to make the necessary updates and reach out to the team if needed.

1. Perform the steps below for manual testing. CI provides a good set of basic smoke tests but it is beneficial to run some additional checks.

# Testing Changes

Follow testing steps for [elasticsearch-kibana](https://repo1.dso.mil/big-bang/product/packages/elasticsearch-kibana/-/blob/main/docs/DEVELOPMENT_MAINTENANCE.md#manual-testing-for-updates)
