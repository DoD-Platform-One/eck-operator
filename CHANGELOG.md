# Changelog

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
