# ai-grid-catalog

Model catalog for the cloud69 AI Grid: models and subscriptions delivered by the
hub's Argo CD ApplicationSets (see `apps/acm-models` in sjug/ai-grid-tenant) and
written by the provider console.

Layout, as the ApplicationSets expect it:

```
catalog/
  models/<model>/deployment/   LLMInferenceService + NetworkPolicy  (ai-grid-internal-models)
  models/<model>/catalog/      ExternalModel + MaaSModelRef         (models-as-a-service)
  clusters/<cluster>/          kustomization listing the models that run on that cluster
  ingress/                     kustomization listing the models every ingress site registers
  subscriptions/<name>.yaml    MaaSSubscription + MaaSAuthPolicy
```

An empty catalog generates no Applications. Never put credentials here; the
console's token can push to this repository.
