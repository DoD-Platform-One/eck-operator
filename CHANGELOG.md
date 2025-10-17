# Changelog

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---
## [3.1.0-bb.1] (2025-10-14)
### Changed
- Updated the egress-api network policy template to allow setting vpcCidr

## [3.1.0-bb.0] (2025-08-27)
### Changed
- eck-operator updated from 3.0.0 to 3.1.0

## [3.0.0-bb.2] (2025-07-11)
### Added
- Added default value for imagePullSecrets

## [3.0.0-bb.1] (2025-06-26)
### Added
- Added Metrics Service and ServiceMonitor templates for Big Bang compatibility scraping

### Changed
- Refactor chart to Big Bang passthrough chart pattern

## [3.0.0-bb.0] (2025-04-16)
### Changed
- eck-operator updated from 2.16.1 to 3.0.0

## [2.16.1-bb.1] - 2025-3-21
### Added
- Added dnymaic network policy support for operatorless istio

## [2.16.0-bb.1] - 2025-1-23
### Changed
- eck-operator 2.16.0 -> 2.16.1

## [2.16.0-bb.0] - 2024-12-20
### Changed
- eck-operator 2.15.0 -> 2.16.0

## [2.15.0-bb.0] - 2024-12-02
### Changed
- eck-operator 2.14.0 -> 2.15.0

## [2.14.0-bb.1] - 2024-11-22
### Changed
- Added the maintenance track annotation and badge

## [2.14.0-bb.0] - 2024-08-21
### Changed
- eck-operator 2.13.0 -> 2.14.0

## [2.13.0-bb.3] - 2024-08-09
### Changed
- Run pod labels though tpl function in preparation for passing kiali required labels in via umbrella chart

## [2.13.0-bb.2] - 2024-07-02
### Removed
- Removed shared authPolicies set at the Istio level

## [2.13.0-bb.1] - 2024-06-10
### Updated
- Synchronized with upstream chart version 2.13.0

## [2.13.0-bb.0] - 2024-06-07
### Updated
- eck-operator 2.12.1 -> 2.13.0

## [2.12.1-bb.1] - 2024-04-24
### Added
- Support for custom network policy definition via values yaml

## [2.12.1-bb.0] - 2024-03-29
### Changed
- Updated eck-operator chart from 2.11.1 to 2.12.1
- Adopted new metrics port configuration

## [2.11.1-bb.1] - 2024-03-12
### Changed
- Add egress whitelist

## [2.11.1-bb.0] - 2024-02-6
### Changed
- Updated eck-operator chart from 2.11.0 to 2.11.1

## [2.11.0-bb.0] - 2024-01-24
### Changed
- Updated chart from 2.10.0 to 2.11.0

## [2.10.0-bb.1] - 2023-11-25
### Changed
- Adds Istio Authorization Policy support

## [2.10.0-bb.0] - 2023-11-25
### Changed
- Updated chart and IB images from 2.9.0 to 2.10.0

## [2.9.0-bb.3] - 2023-11-08
### Changed
- Updated registry1.dso.mil/ironbank/big-bang/base 2.0.0 -> 2.1.0

## [2.9.0-bb.2] - 2023-10-24
### Changed
- Updating contributing file to link to external github contributions

## [2.9.0-bb.1]
### Changed
- Updated non-root group & user

## [2.9.0-bb.0]
### Changed
- Updated chart and IB images from 2.8.0 to 2.9.0

## [2.8.0-bb.0]
### Changed
- Updated chart and IB images from 2.7.0 to 2.8.0

## [2.7.0-bb.1]
### Changed
- Added OpenShift support

## [2.7.0-bb.0]
### Changed
- Updated chart and IB images from 2.6.1 to 2.7.0

## [2.6.1-bb.0]
### Changed
- Updated chart and IB images from 2.5.0 to 2.6.1

## [2.5.0-bb.0]
### Changed
- Updated chart and IB images from 2.4.0 to 2.5.0

## [2.4.0-bb.0]
### Changed
- Updated chart and IB images from 2.3.0 to 2.4.0

## [2.3.0-bb.0]
### Changed
- Updated chart and IB images from 2.2.0 to 2.3.0

## [2.2.0-bb.2]
### Changed
- Set container securityContext capabilities to drop all

## [2.2.0-bb.1]
### Changed
- Updated BB base image to 2.0.0

## [2.2.0-bb.0]
### Changed
- Updated chart and IB images from 2.0.0 to 2.2.0

## [2.0.0-bb.2]
### Changed
- Modified peer authentication to support validating webhook PERMISSIVE mode
- Made some fixes for the OSCAL schema check

## [2.0.0-bb.1]
### Added
- Added Tempo Zipkin Egress Policy

## [2.0.0-bb.0]
### Changed
- Updated chart and IB images from 1.9.1 to 2.0.0

## [1.9.1-bb.4]
### Changed
- Modified PeerAuthentication to allow for passing in mode

## [1.9.1-bb.3]
### Added
- Update Chart.yaml to follow new standardization for release automation
- Added renovate check to update new standardization

## [1.9.1-bb.2]
### Added
- Added PeerAuthentication yaml to templates that verifies both Istio and mtls are enabled.  This enables Peer Authentication/mTLS for istio communication within the namespace

## [1.9.1-bb.1]
### Added
- Added OSCAL component for ECK Operator with NIST 800-53 controls

## [1.9.1-bb.0]
### Changed
- Updated from 1.8.0 to 1.9.1

## [1.8.0-bb.0]
### Changed
- Updated from 1.7.1 to 1.8.0

## [1.7.1-bb.0]
### Changed
- Updated to 1.7.1
### Added
- Added upgrade job to replace CRDs due to breaking changes

## [1.6.0-bb.3]
### Added
- NetworkPolicy template to allow istiod communication when istio-injected.
- istio enabled toggle value to control conditional for above NetworkPolicy

## [1.6.0-bb.2]
### Changed
- Set resource limits equal to requests in order to resolve OPA container-ratio violations

## [1.6.0-bb.1]
### Added
- Added openshift toggle. Conditionally modifies networkpolicy for DNS.

## [1.6.0-bb.0]
### Changed
- Upgraded from 1.4.0 to 1.6.0

## [1.4.0-bb.4]
### Added
- Network Policy template for Kibana and Elasticsearch specific egress communication. Alleviating intermittent issue with operator not being able to talk to ES endpoint on tcp/9200

## [1.4.0-bb.3]
### Changed
- Locked egress down to only DNS and API

## [1.4.0-bb.2]
### Added
- BigBang specific Network Policy Templates for package.

## [1.4.0-bb.1]
### Changed
- Cleaned up image section in chart values.

## [1.4.0-bb.0]
### Changed
- Upgraded from 1.3.0 version to 1.4.0
