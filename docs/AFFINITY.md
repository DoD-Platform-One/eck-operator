# Node Affinity & Anti-Affinity with ECK Operator

Affinity is supported for the ECK operator pod through the upstream chart values passed under `upstream`. If you want to schedule the operator on specific nodes, use `upstream.nodeSelector`, `upstream.affinity`, and optionally `upstream.tolerations`.

It is useful to have a basic understanding of node affinity before customizing these values. The upstream Kubernetes documentation [provides a good walkthrough](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#affinity-and-anti-affinity).

## Values for NodeSelector

Use `upstream.nodeSelector` for simple node selection. For example, to schedule the operator only on nodes labeled `node-type=operator`:

```yaml
upstream:
  nodeSelector:
    node-type: operator
```

## Values for Affinity

Use `upstream.affinity` to define Kubernetes affinity rules. The value format matches the pod-level affinity structure used by Kubernetes. Example:

```yaml
upstream:
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
          - matchExpressions:
              - key: node-type
                operator: In
                values:
                  - operator
```

## Values for Anti-Affinity

Use `upstream.affinity` in the same way for anti-affinity rules. Example:

```yaml
upstream:
  affinity:
    podAntiAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        - topologyKey: kubernetes.io/hostname
          labelSelector:
            matchLabels:
              dont-schedule-with: operator
```
