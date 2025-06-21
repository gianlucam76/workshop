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
- post the ConfigMap with [disallow latest tag](kyverno-disallow-latest-tag.yaml) and the ConfigMap with [disallow empty ingress host](kyverno-disallow-empty-ingress-host.yaml)

# Events
[Deploy EventSource and EventTrigger](events.yaml)
- instructing Sveltos to detect v1.Service with specific labels in any production cluster
- when such an event is detected, create a NetworkPolicy in response
- As soon as we deploy a [Service](service.yaml) matching above event, the NetworkPolicy is created

# Events With CEL
[Deploy EventSource and EventTrigger](events-with-cel.yaml)
- instructing Sveltos to detect v1.Service with specific labels in any production cluster
- when such an event is detected, create a NetworkPolicy in response
- As soon as we deploy a [Service](service.yaml) matching above event, the NetworkPolicy is created

# Tier
- [Deploy Prometheus and Grafana](prometheus-grafana.yaml)
- [Try to downgrade Grafana with new ClusterProfile](grafana-conflict.yaml)
- Set tier and see how that wins

# Techsupport

Ask Sveltos to collect [techsupport](techsupport.yaml) and delivery to slack (it requires setting up a Secret first with [Slack credentials](https://projectsveltos.github.io/sveltos/features/techsupport/#delivery-options))