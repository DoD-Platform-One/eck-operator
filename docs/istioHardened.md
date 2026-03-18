# Istio Hardened

This package uses the shared Big Bang `bb-common` Istio integration rather than a package-specific `istio.hardened.enabled` value.

The ECK Operator chart exposes the following Istio-related values in [`chart/values.yaml`](../chart/values.yaml):

- `istio.enabled`
- `istio.injection`
- `istio.mtls.mode`
- `istio.sidecar.enabled`
- `istio.sidecar.outboundTrafficPolicyMode`
- `istio.authorizationPolicies.enabled`
- `istio.authorizationPolicies.generateFromNetpol`

When `istio.enabled` is set to `true`, the chart renders shared Big Bang Istio resources through `bb-common`. When `istio.mtls.mode` is `STRICT`, the chart also renders a webhook `PeerAuthentication` resource for the operator webhook endpoint.

For package use inside Big Bang, enable the package alongside the required Istio components in the parent `bigbang` chart. See [`docs/dev-overrides.yaml`](./dev-overrides.yaml) for a local example and the [Big Bang package integration Istio guidance](https://docs-bigbang.dso.mil/latest/docs/developer/package-integration/istio-hardened/) for the broader platform expectations.
