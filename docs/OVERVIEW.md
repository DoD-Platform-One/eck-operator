# ECK Operator

## Overview

This repository contains the Big Bang package for the Elastic Cloud on Kubernetes (ECK) operator. It wraps the upstream [Elastic chart](https://github.com/elastic/cloud-on-k8s) and adds Big Bang integration for Istio, network policies, monitoring, and Iron Bank images.

## ECK-Operator

[ECK](https://www.elastic.co/docs/deploy-manage/deploy/cloud-on-k8s) is Elastic's Kubernetes operator for managing Elastic Stack applications by way of Kubernetes custom resources. It can be used to deploy and manage Elasticsearch, Kibana, Elastic Agent, APM Server, Beats, Enterprise Search, and other supported Elastic workloads on Kubernetes.

## How it works

When installed, ECK Operator adds the Elastic CRDs and deploys an operator pod that reconciles those resources. In Big Bang, this package is commonly paired with the [elasticsearch-kibana](https://repo1.dso.mil/big-bang/product/packages/elasticsearch-kibana) package, but it can also support other ECK-managed Elastic workloads as needed.

### Additional Links

- [Elastic official website](https://www.elastic.co/)
- [Elastic Forum](https://discuss.elastic.co/c/orchestration/eck/79)
