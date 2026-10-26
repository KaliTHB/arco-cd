# Argo CD Services

This project explains the main Argo CD services running in the `argocd` namespace.

## Services

- **argocd-server** – Provides the Argo CD web UI and API.
- **argocd-repo-server** – Reads Git repositories and generates Kubernetes manifests.
- **argocd-redis** – Caches data used by Argo CD.
- **argocd-dex-server** – Supports optional single sign-on (SSO).
- **argocd-applicationset-controller** – Creates Argo CD Applications from templates.

## Deployment Flow

1. Store Kubernetes YAML files in Git.
2. Argo CD reads the configuration from Git.
3. Argo CD compares it with the Kubernetes cluster.
4. Argo CD synchronizes changes when sync is triggered or automatic sync is enabled.
5. Kubernetes runs the application Pods.

## Useful Commands

```bash
kubectl get svc -n argocd
kubectl get pods -n argocd
kubectl get applications -n argocd
```

## Notes

- The Services use `ClusterIP`, so they are accessible inside the cluster by default.
- The Application Controller manages synchronization; it is a controller, not a Service.
