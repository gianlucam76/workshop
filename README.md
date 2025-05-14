# workshop
Sveltos Workshop

# Deploy helm chart

[Deploy Cert-Manager](deploy-certmanager-helm-chart.yaml):
- values are set

[Deploy Kyverno Helm chart](deploy-kyverno-helm-chart.yaml):
- values are set
- validateHealths are set

[Deploy nginx ingress](deploy-nginx-ingress-helm-chart.yaml)
- mode is ContinuousWithDriftDetection
- helm options are set
- values are set
- driftExclusions is set

# Deploy YAML

[Deploy Kyverno ClusterPolicies](deploy-kyverno-policies.yaml)
- dependsOn is set
- both ConfigMap and Secret are referenced

# Events
[Deploy EventSource and EventTrigger](events.yaml)
- instructing Sveltos to detect v1.Service with specific labels in any production cluster
- when such an event is detected, create a NetworkPolicy in response
- As soon as we deploy a [Service](service.yaml) matching above event, the NetworkPolicy is created